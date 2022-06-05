# XREngine Bridge - Unreal

XREngine &lt;> Unreal Engine Backend Bridge

Unreal SDK XREngine Alpha
- User Management API
- Server Party Matchmaker
- Unreal Game Server Lifecycle System
- Unreal Blueprints XREngine SDK

CMS and marketplace services coming soon

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

![image](https://user-images.githubusercontent.com/5104160/172028597-08e4c4cc-973b-4e4a-924a-1f508dfb4711.png)



Agones Actions

![unreal_bp_actions](https://user-images.githubusercontent.com/5104160/172027649-676723a1-a5d1-46f0-9406-eb2aa429cf18.png)

