# xrengine-unreal
XREngine &lt;> Unreal Engine Backend Bridge

Unreal SDK XREngine Alpha
- User Management API
- Server Party Matchmaker
- Unreal Game Server Lifecycle System
- Unreal Blueprints XREngine SDK

## Setup

This guide assumes you have a working linux dedicated server build of you game.
- https://docs.unrealengine.com/4.27/en-US/InteractiveExperiences/Networking/HowTo/DedicatedServers/
- old guides 
   - https://michaeljcole.github.io/wiki.unrealengine.com/Dedicated_Server_Guide_(Windows_&_Linux)/
   - https://medium.com/swlh/building-and-hosting-an-unreal-engine-dedicated-server-with-aws-and-docker-75317780c567

Preinstall Requirements
- VaRest https://github.com/ufna/VaRest
   - https://www.notion.so/VaRest-UE4-Plugin-40b98c54fc184033b60a42e0e4753536
- Agones SDK w/ Unreal tools https://agones.dev/site/docs/guides/client-sdks/unreal/

other functionality of Agones can be done via adding a node in Blueprints.
![unreal_bp_actions](https://user-images.githubusercontent.com/5104160/172027649-676723a1-a5d1-46f0-9406-eb2aa429cf18.png)

