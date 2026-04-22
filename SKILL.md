# Scenepad Skill Spec

Scenepad is a lightweight format to describe conversations, flows, and scenarios visually and in code.

## Core Ideas
- Everything is a **scene**
- A scene contains **actors**, **messages**, and **layout**
- Output can be rendered as diagrams or interactive HTML

## Scene Structure
- actors: participants in the flow
- steps: ordered interactions
- layout: panel or sequence

## Example (pseudo)
scene:
  actors: [User, API, Service]
  steps:
    - User -> API: Request
    - API -> Service: Process
    - Service -> API: Response
    - API -> User: Result