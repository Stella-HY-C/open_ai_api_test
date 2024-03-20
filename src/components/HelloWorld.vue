<template>
  <div>
    <div>처음 시작화면</div>
    <button @click="insertAPI">API 요청하기</button>
  </div>
</template>

<script>
import OpenAI from "openai";

export default {
  name: "HelloWorld",
  setup() {
    const openai = new OpenAI({
      apiKey: process.env.VUE_APP_OPENAI_API_KEY, // This is the default and can be omitted
      dangerouslyAllowBrowser: true,
    });

    const insertAPI = async () => {
      const completion = await openai.chat.completions.create({
        messages: [{ role: "system", content: "You are a helpful assistant." }],
        model: "gpt-3.5-turbo",
      });
      console.log(completion.choices[0]);
    };

    return { insertAPI };
  },
};
</script>

<style lang="scss" scoped></style>
