# mcutils
A collection of utilities for interacting with Minecraft servers.

## Documentation
### extractor.py
A tool to extract the client jar file.
```python
from utils import extractor

#extract the client jar file
print("Downloading and extracting the client...")
extractor_obj = extractor.Extractor("1.16.5")
extracted_path = extractor_obj.extract_jar()
print("Client extracted to:", extracted_path)

#get a list of death messages
death_messages = extractor_obj.get_death_messages()
```
### rcon.py
Interface with the Minecraft RCON protocol. 
```python
from utils import rcon

#send a command to the local server

rcon = rcon.RCON("127.0.0.1", 25575, "password")
output = rcon.send_cmd("list")
print(output)

rcon.close()
```

### query.py
Interface with the Minecraft query protocol.
```python
from utils import query

#query the local server

query_obj = query.Query(("127.0.0.1", 25565))
full_stat = query_obj.full_stat()
basic_stat = query_obj.basic_stat()

print(full_stat)
```

### ping.py
Ping any Minecraft server above version 1.7.
```python
from utils import ping

#ping the local server

pinger = ping.Pinger(("127.0.0.1", 25565))
stats = pinger.ping()
print(stats)
```

### motd_renderer.py
Generate a nearly pixel-perfect image of what a server would look line in the client's server list.
```python
from utils import motd_renderer

#query the local server

renderer = motd_renderer.MOTDRenderer()
image = renderer.get_full_image(title="Hypixel", address=("mc.hypixel.net", 25565))
image.save("/tmp/img.png", "PNG")
```
Generated image:

![example of a generated image](https://raw.githubusercontent.com/ading2210/mcutils/main/images/motd.png)