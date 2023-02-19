# chat-react
使用openai接口开发在线chatgpt

## 使用
安装
```js
npm install
```
运行
```js
npm run dev
```
目前使用的是固定的API keys，可以自定义修改key；将 `process.env.OPENAI_API_KEY`替换成自己的key

```js
const { Configuration, OpenAIApi } = require("openai");
const configuration = new Configuration({
  apiKey: process.env.OPENAI_API_KEY,
});
const openai = new OpenAIApi(configuration);
const response = await openai.createCompletion({
  model: "text-davinci-003",
  prompt: "JS有几种数据类型？",
  max_tokens: 600,
  temperature: 0.5,
});

// 打印 API 返回的结果
console.log(response.data.choices[0].text);
```
- `createCompletion`: 是自动完成，它跟官网的回话方式一致；

- `max_tokens`: 表示最大的令牌数量，可以理解为返回的字符数量，大多数内容 2048 内，当然 max_tokens 返回接口的速度越慢。

- `temperature`: 0-1 之间，参数表示生成文本中的随机性或不可预测性程度。较高的值将产生更具创造性和多样性的输出，而较低的值会产生更可预测和重复的文本。
