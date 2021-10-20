# Vosk Voice To Text (VTT) client

[Vosk Server](https://alphacephei.com/vosk/server) is an open source Voice-To-Text server based on Vosk-API, and provides real-time voice transcription over WebSocket (and other protocols).

This Python script is based off their [`test_microphone.py`](https://github.com/alphacep/vosk-server/blob/master/websocket/test_microphone.py) example, and acts as a client interface with a Vosk server. It currently outputs transcription results as OSC over UDP, but the plan is to expand this much further.

Please see the Vosk GitHub repo for details on the server and instructions on how to host your own:

[https://github.com/alphacep/vosk-server](https://github.com/alphacep/vosk-server)

---

Future plans include:
- Javascript/HTML5 interface.
- Allowing transcriptions to be sent via RESTful API.
- Implementing transcription retention in a database.
- Transcription of imported audio files.
- Visualisations and analysis (word-clouds, tables, etc).

---

### Dependencies

**Note:** You'll need access to a Vosk VTT server. See the link at the top for details on running your own.

If you're using Docker, it's as easy as:
```
docker run -d -p 2700:2700 alphacep/kaldi-en:latest
```


- Python
- pyaudio
- websockets
- python-osc

---

### Usage

To simple view the streaming transcription in the console log, run `python3 vtt.py <server_url>:<port>`, replacing <server_url> and <port> with your Vosk server details, for example:
```
python3 vtt.py localhost:2700
```
  
If you'd like to send the transcription via OSC, add these arguments to the run command: `-ip <osc_ip> -port <osc_port>`. These default to `localhost` and `9600`. For example:
```
python3 vtt.py localhost:2700 -ip localhost -port 5110
```
