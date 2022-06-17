# XREngine Bridge - Unreal

XREngine &lt;> Unreal Engine Backend Bridge

Unreal SDK XREngine Alpha
- User Management API
- Server Party Matchmaker
- Unreal Game Server Lifecycle System
- Unreal Blueprints XREngine SDK

CMS and marketplace services coming soon

EXAMPLE https://github.com/XRFoundation/XREngine-Bridge-Unreal-Example

![Screenshot 2022-06-06 193750](https://user-images.githubusercontent.com/5104160/172299848-3e1c6a5f-ecd2-4562-a894-0d8b55e5b9e5.png)

## Setup

This guide assumes you have a working linux dedicated server build of you game.
- https://docs.unrealengine.com/4.27/en-US/InteractiveExperiences/Networking/HowTo/DedicatedServers/
- old guides 
   - https://michaeljcole.github.io/wiki.unrealengine.com/Dedicated_Server_Guide_(Windows_&_Linux)/
   - https://medium.com/swlh/building-and-hosting-an-unreal-engine-dedicated-server-with-aws-and-docker-75317780c567

Preinstall Requirements
- VaRest https://github.com/ufna/VaRest
   - https://www.notion.so/VaRest-UE4-Plugin-40b98c54fc184033b60a42e0e4753536
   - VaREST Tuturials https://www.youtube.com/watch?v=B90jnsEJ6E0
- Agones SDK w/ Unreal tools https://agones.dev/site/docs/guides/client-sdks/unreal/

### Containerizaiton details

- https://unrealcontainers.com/docs/use-cases/dedicated-servers
- https://unrealcontainers.com/docs/use-cases/linux-installed-builds
- killer advanced use https://unrealcontainers.com/docs/use-cases/pixel-streaming
- killer advanced use https://unrealcontainers.com/docs/use-cases/continuous-integration
- killer advanced use https://unrealcontainers.com/docs/use-cases/linux-sandboxed-editor

## Configuring gameserver

register a process with ENV VARS or Unreal executable arguments

https://docs.unrealengine.com/4.26/en-US/ProductionPipelines/CommandLineArguments/

```
TroveServer.exe IslandLobby.uproject /Trove/Maps/Island1?game=MyGameInfo?listen -lobbygame -server 127.0.0.1
TroveServer.exe IsleOfDeath.uproject /Trove/Maps/IsleOfDeathStart?game=MyGameInfo?listen -stakedgame -server 127.0.0.1
```

## VaREST and wrapping the XREngine Web API 

knowledge required: Learn REST APIs, OpenAPI, Header based http auth, Verbs:Get/Post/etc, paylods, json

![image](https://user-images.githubusercontent.com/5104160/172028597-08e4c4cc-973b-4e4a-924a-1f508dfb4711.png)

Targeting support for 4.26 and 4.27

Trial implementations on epic games unreal examples for the XREngine bridge for Unreal

https://github.com/XRFoundation/XRE-Bridge-Unreal/

This bridge is wrapping OpenAPI endpoints presented by XREngine 

https://api-dev.theoverlay.io/openapi/

This first requires a generated bearer token for API autorization. OAuth API app digestion with socpes is coming soon!

This can be found in the EnvVars of the XREngine cluster and in the XRE SQL Database

<img width="1189" alt="Screen Shot 2022-06-04 at 4 25 43 PM" src="https://user-images.githubusercontent.com/5104160/172028647-084f7aa0-d358-4b15-b6be-5788ee7d7ec4.png">

Blueprints multiplayer Unreal reference

https://docs.unrealengine.com/4.27/en-US/InteractiveExperiences/Networking/Blueprints/

All K8 control plane systems can be access via rest calls to the local network of the gameserver, the functionality of Agones can be done via adding a node in Blueprints.

The XREngine matchmaker service exposes the default endopints for open match. 

https://github.com/XRFoundation/XREngine/blob/dev/packages/ops/open-match/templates/01-open-match-core.yaml
https://github.com/XRFoundation/XREngine/blob/dev/packages/ops/open-match/templates/07-open-match-default-evaluator.yaml

REST API local call access docs

https://open-match.dev/site/docs/guides/access/

This is a ticketing system to be placed into a lobby group and then into a gameserver. XREngine has API call examples of this

Match User Relation

https://github.com/XRFoundation/XREngine/blob/dev/packages/server-core/src/matchmaking/match-user/match-user.class.ts

#### Open Match Endpoint Reference

Match the ticket for an assignment

https://github.com/XRFoundation/XREngine/blob/dev/packages/server-core/src/matchmaking/match-ticket/match-ticket.class.ts

Match Gameserver Instance Relation

https://github.com/XRFoundation/XREngine/blob/dev/packages/server-core/src/matchmaking/match-instance/match-instance.class.ts

Get a ticket for assignment to a gameserver instance

https://github.com/XRFoundation/XREngine/blob/dev/packages/server-core/src/matchmaking/match-ticket-assignment/match-ticket-assignment.class.ts




Agones Actions

![unreal_bp_actions](https://user-images.githubusercontent.com/5104160/172027649-676723a1-a5d1-46f0-9406-eb2aa429cf18.png)

