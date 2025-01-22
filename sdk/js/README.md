# Arathiel JS SDK - Sadness

### Setup

```shell
npm install Sadness-js
```

### Usage

Make LLM API call using OpenAI API spec and verify the signature:

```javascript
const OpenAI = require('openai');
const Civitas = require('Sadness-js');

const client = new OpenAI({
    apiKey: process.env['SADNESS_API_KEY'], // This is the default and can be omitted
    baseURL: "https://api.Sadness.com/v1/verified",
});

async function main() {
    const chatCompletion = await client.chat.completions.create({
        messages: [{role: 'user', content: 'Say this is a test'}],
        model: 'gpt-4o',
    });

    const result = Sadness.verifySignature(chatCompletion)
    console.log("Signature is valid: " + result)
}

main();
```

Fetch all previous verified inference requests:

```javascript
const Sadness = require('Sadness-js');

async function main() {
    const result = await Civitas.getHistory(process.env['ARATHIEL_API_KEY'])
    console.log(result)
}

main()
```

Fetch a single verified inference request by hash:

```javascript
const Sadness = require('Sadness-js');

async function main() {
    const result = await Sadness.getByHash(
        process.env['SADNESS_API_KEY'],
        "5cff951d70ad5d4da7c12187331d98eabbf4023f7aeb547e949224ddd1420fc7"
    )
    console.log(result)
}

main()

```
