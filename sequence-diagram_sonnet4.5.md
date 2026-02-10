```mermaid

sequenceDiagram
    participant USER
    participant LISTENER<br/>(continuous)
    participant AUDIO<br/>TRANSCRIBER
    participant AI<br/>INTERPRETER
    participant SYSTEM<br/>COMMANDER
    participant BROWSER

    USER->>LISTENER: "Hey Jarvis," "play the video"
    Note over LISTENER: 3 seconds<br/>silence~silence
    LISTENER->>LISTENER: trigger to start listening for command
    LISTENER->>AUDIO TRANSCRIBER: start<br/>streaming<br/>audio stream<br/>to transcriber
    Note over AUDIO TRANSCRIBER: start converting to text
    
    USER->>LISTENER: trigger to end<br/>active listing
    LISTENER->>AUDIO TRANSCRIBER: stop<br/>streaming<br/>audio
    Note over LISTENER,AUDIO TRANSCRIBER: silence
    
    AUDIO TRANSCRIBER->>AI INTERPRETER: pass text<br/>to Chris
    Note over AI INTERPRETER: convert text<br/>string into system commands<br>add to a list of "commands"<br/>FIFO queue (queue) in memory
    AI INTERPRETER->>SYSTEM COMMANDER: pass<br/>list of<br/>commands
    SYSTEM COMMANDER->>BROWSER: play video btn<br/>click (video V)

```
