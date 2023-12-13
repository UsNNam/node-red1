## node-red-contrib-speech-to-text-ubos

The speech to text API provides two endpoints, transcriptions and translations, based on our state-of-the-art open source large-v2 Whisper model.

<img width="100%"  alt="Ubos - End-to-End Software Development Platform" src="https://ubos.tech/wp-content/uploads/2023/03/cropped-Group-21015-1.png">

<h3 align="center">
  <b><a href="https://ubos.tech/">UBOS</a></b>
  •
  <a href="https://community.ubos.tech/">Community</a>
  •
  <a href="https://www.youtube.com/@ubos_tech">Youtube</a>
  •
  <a href="https://discord.com/invite/dt59QaptH2">Discord</a>
  •
  <a href="https://github.com/UBOS-tech">GitHub</a>
</h3>

<div align="center">
 
[![flow](https://img.shields.io/badge/platform-Node--RED-red)](https://flows.nodered.org/node/node-red-contrib-speech-to-text-ubos)
[![npm](https://img.shields.io/npm/v/node-red-contrib-speech-to-text-ubos)](https://www.npmjs.com/package/node-red-contrib-speech-to-text-ubos)
 
</div>

### Quick Start

Install with the built in <b>Node-RED Palette manager</b> or using npm:
```
npm install node-red-contrib-speech-to-text-ubos
```

## Setup

When editing the nodes properties, to get your `OPENAI_API_KEY` visit https://platform.openai.com/account/api-keys click "+ Create new secret key" then copy and paste the "API key" into the nodes `API_KEY` property value.

To get your `Organization` visit https://platform.openai.com/account/org-settings then copy and paste the "OrganizationID" into the nodes `Organization` property value.

## Properties
 Only whisper-1 is currently available.

 - **[Required]** `msg.OPENAI_API_KEY`: This is the API key provided by OpenAI. It is necessary for authentication when making requests to the OpenAI API.

1. When `msg.type` is set to `transcriptions`:
    - **[Required]** `msg.file`: The audio file object (not file name) to transcribe, in one of these formats ***mp3***, ***mp4***, ***,mpeg***, ***mpga***, ***m4a***, ***wav***, or ***webm***. For example
   ```js
    msg.file = {
        "value": msg.req.files[0].buffer,
        "options": {
            "filename": msg.req.files[0].originalname
        }
    };
   ```
    - `msg.prompt`: An optional text to guide the model's style or continue a previous audio segment. The [prompt](https://platform.openai.com/docs/guides/speech-to-text/prompting) should match the audio language.

    - `msg.response_format`: The format of the transcript output, in one of these options: ***json***, ***text***, ***srt***, ***verbose_json***, or ***vtt***.
    - `msg.temperature`: The sampling temperature, between 0 and 1. Higher values like 0.8 will make the output more random, while lower values like 0.2 will make it more focused and deterministic. If set to 0, the model will use [log probability](https://en.wikipedia.org/wiki/Log_probability) to automatically increase the temperature until certain thresholds are hit.
    - `msg.language`: The language of the input audio. Supplying the input language in [ISO-639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) format will improve accuracy and latency.

2. When `msg.type` is set to `translations`:
    - **[Required]** `msg.file`: The audio file object (not file name) to transcribe, in one of these formats ***mp3***, ***mp4***, ***,mpeg***, ***mpga***, ***m4a***, ***wav***, or ***webm***. For example
   ```js
    msg.file = {
        "value": msg.req.files[0].buffer,
        "options": {
            "filename": msg.req.files[0].originalname
        }
    };
   ```
    - `msg.prompt`: An optional text to guide the model's style or continue a previous audio segment. The [prompt](https://platform.openai.com/docs/guides/speech-to-text/prompting) should match the audio language.

    - `msg.response_format`: The format of the transcript output, in one of these options: ***json***, ***text***, ***srt***, ***verbose_json***, or ***vtt***.
    - `msg.temperature`: The sampling temperature, between 0 and 1. Higher values like 0.8 will make the output more random, while lower values like 0.2 will make it more focused and deterministic. If set to 0, the model will use [log probability](https://en.wikipedia.org/wiki/Log_probability) to automatically increase the temperature until certain thresholds are hit.

## Demo

[Test video](https://ubos.tech/wp-content/uploads/2023/06/demo-speech-to-text.mp4)
<div align="center">
  
  ![speech-to-text-demo](https://github.com/UBOS-tech/node-red-contrib-speech-to-text-ubos/assets/41735477/5f6a41d0-19ef-48e4-9244-7319756c46ee)
  
</div>

### Bugs reports and feature requests

Please report any issues or feature requests at <a href="https://github.com/UBOS-tech/node-red-contrib-speech-to-text-ubos/issues">GitHub</a>.

## License

[MIT License](https://github.com/UBOS-tech/node-red-contrib-speech-to-text-ubos/blob/main/LICENSE)
