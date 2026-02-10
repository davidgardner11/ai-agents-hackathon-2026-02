```mermaid

sequenceDiagram
    participant U as USER
    participant L as LISTENER
    participant AT as AUDIO<br/>TRANSCRIBER
    participant AI as AI<br/>INTERPRETER
    participant SC as SYSTEM<br/>COMMANDER
    participant B as BROWSER

    Note over L: Passive listening
    U->>L: "Hey Jarvis..."
    L->>L: trigger to start active listening for commands
    U->>L: "...play the video and turn up the volume by 20%."

    L->>AT: start streaming audio to AUDIO TRANSCRIBER
    AT->>AT: start converting to text

    Note over L: 2 seconds of silence
    L->>L: trigger to stop active listening, go into stand-by mode
    L->>AT: stop streaming audio


    AT->>AI: pass text to AI INTERPRETER
    Note over L: stand-by mode: all listening on hold

    AI->>AI: convert text into system commands<br/>add system commands to FIFO queue

    AI->>SC: pass FIFO queue to SYSTEM COMMANDER

    SC->>B: [play video] 

    SC->>B: [turn up volume 20%]

    SC->>L: notify LISTENER to restart passive listening
    Note over L: Restart passive listening

```
