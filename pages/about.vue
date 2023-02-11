<template>
    <div>
        <h1>About Us</h1>
        <p>This is me.</p>
    </div>
    <div>
        <button @click="enableCustomLayout">Update layout</button>
    </div>
    <FormKit
      type="form"
      @submit="submit"
      submit-label="登録する"
      incomplete-message="入力内容に不備があるよ">
      <FormKitSchema :schema="schema"/>
    </FormKit>
</template>

<script lang="ts" setup>
function enableCustomLayout() {
  setPageLayout('custom');
}
definePageMeta({
  layout: 'default',
});
useHead({
  title: 'Aboutページ',
  meta: [
    {
      name: 'description',
      content: 'Aboutページ',
    },
  ],
});

import { FormKitSchemaNode } from '@formkit/core';

// 名前を入力するスキーマを定義（前述のJSONにシリアライズできる云々はこれ）
const nameFormSchema: FormKitSchemaNode = {
  $cmp: "FormKit",
  props: {
    type: "text",
    label: "名前",
    name: "nameForm",
    // 必須 + 文字列の長さは 0文字から30文字 まで
    validation: "required|length:0,30",
    // 検証タイミングはユーザがinputの値を変更した後
    validationVisibility: "dirty",
    // バリデーションの内容によってエラーメッセージを出しわけ
    validationMessages: {
      required: "名前を入力してください",
      length: "名前は30文字以内で入力してください。",
    }
  }
};

// 表示させたいフォームのスキーマを登録（複数可）
const schema = [nameFormSchema];

const submit = async (e: {nameForm: string}) => {
  console.log(e);
  console.log(schema);
  await useFetch('http://localhost:8080/api/v1/posts', {
    method: 'POST',
    body: schema,
  });
};
</script>
