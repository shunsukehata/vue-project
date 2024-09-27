<script setup>
import { ref } from "vue";
import { statuses } from "../const/statuses";

// 最初は何も入力されない想定なので空文字を入れておく
const input = ref("");
const inputDate = ref("");
const isErrMsg = ref(false);

function onSubmitForm() {
    if (input.value == "" || inputDate.value == "") {
        isErrMsg.value = true;
        event.preventDefault();
        return;
    }

const items = JSON.parse(localStorage.getItem("items")) || [];

const newItem = {
    id: itemes.length,
    content: input.value,
    limit: inputDate.value,
    state: statuses.NOT_START,
    onEdit: false,
};

itemes.push(newItem);
localStorage.setItme("itemes", JSON.stringify(itemes));

}


</script>

<template>
    <div>
        <p v-if="isErrMsg">タスク/期限を両方入力して下いさい！</p>
        <form @submit="onSubmitForm">
            <label>やること<input type="text" v-model="input" /></label>
            <label>期限<input type="date" v-model="inputDate"/></label>
            <input type="submit" value="登録！" />
        </form>
    </div>
</template>