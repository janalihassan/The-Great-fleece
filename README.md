# The Great Fleece

A Unity 3D stealth heist game by Jan Ali Hassan. You sneak through a guarded gallery with point-and-click movement, get past guards and security cameras, steal a keycard and reach the exit. The story plays out in cinematic cutscenes built with Cinemachine and Timeline.

![The Great Fleece gameplay screenshot](https://janalihassan.dev/images/The_Great_fleece-1.png)

▶️ [Watch the gameplay video](https://janalihassan.dev/videos/The_Great_Fleece.mp4) · 🌐 [More of my games at janalihassan.dev](https://janalihassan.dev/#library) · 💼 [LinkedIn post](https://lnkd.in/p/dHCnMGXM)

## Features

- **Click-to-move:** left-click anywhere and the player walks there on a NavMesh, with walk and idle animations.
- **Guard AI:** guards patrol their own waypoint routes back and forth, and wait 5 to 7 seconds at each end before turning around.
- **Coin distraction:** right-click to throw a coin (once per run). Every guard leaves its patrol and walks to where the coin landed.
- **Getting caught:** walk into a guard's line of sight, or into a security camera's view cone, and the "captured" cutscene plays. A camera that spots you turns red and stops sweeping first.
- **Keycard objective:** grab the keycard from the sleeping guard, which plays its own cutscene. The exit only triggers the win cutscene once you have the card.
- **Cutscenes:** Timeline sequences for the intro, the sleeping guard, getting captured and the ending, plus one for the main menu. The intro alone cuts between 15 Cinemachine shots. Press `S` to skip the intro.
- **Voiceovers:** trigger zones in the level play one-off voice lines through a central audio manager.
- **Fixed camera angles:** the camera jumps to preset angles as you move between areas and stays aimed at the player.
- **Menus:** a main menu, a loading screen with a progress bar, and a pause menu on `Esc` (resume, restart, main menu, quit).

## Controls

| Input | Action |
| --- | --- |
| Left mouse button | Move to the clicked point |
| Right mouse button | Throw a coin to distract the guards |
| `Esc` | Pause |
| `S` | Skip the intro cutscene |

## Built with

- Unity 2019.4.40f1 (built-in render pipeline)
- C#
- Cinemachine 2.6.17 and Timeline 1.2.18 for the cutscenes
- Unity NavMesh (`NavMeshAgent`) for player and guard movement
- Post Processing 3.2.2

## Key scripts

All gameplay scripts are in `Assets/The Great Fleece/Game/Scripts/`.

| Script | What it does |
| --- | --- |
| `Player.cs` | Click-to-move with a raycast and `NavMeshAgent`, the coin throw, and sending every guard to the coin |
| `GuardAI.cs` | Back-and-forth waypoint patrol with random pauses at each end, and the switch into coin-chasing |
| `Eyes.cs` | Guard vision trigger that starts the captured cutscene |
| `SecurityCameras.cs` | Camera view cone: turns red, stops the sweep, then starts the captured cutscene |
| `GrabKeyCardActivation.cs` | Plays the keycard cutscene and marks the card as collected |
| `WinStateActivation.cs` | Exit trigger that plays the win cutscene only if you have the keycard |
| `GameManager.cs` | Singleton that holds the keycard state and handles skipping the intro |
| `AudioManager.cs` / `VoiceOver.cs` | Plays voice lines from trigger zones, each one only once |
| `CameraTriggers.cs` / `LookAT.cs` | Switches between fixed camera angles and keeps the camera aimed at the player |
| `UIManager.cs` | Pause menu, restart, return to main menu, quit |
| `Menu/Main_Menu.cs` / `Menu/LoadLevel.cs` | Main menu buttons, and loading the level asynchronously behind a progress bar |

Cutscene timelines are in `Assets/The Great Fleece/Timeline/`.

## Running the project

1. Install [Git LFS](https://git-lfs.com) before cloning. The repo stores `*.asset` files (including everything in `ProjectSettings/`) in LFS, so cloning without it gives you placeholder files and the project won't open properly.
2. Clone the repo and add the folder in Unity Hub. Open it with **Unity 2019.4.40f1**.
3. Open `Assets/The Great Fleece/Game/_Scenes/Main_Menu.unity` and press Play.

The build order is `Main_Menu` → `LoadingScene` → `Main`. The level itself is in `Main.unity`.

## Author

Jan Ali Hassan · [Portfolio](https://janalihassan.dev) · [LinkedIn](https://www.linkedin.com/in/janalihassan) · [GitHub](https://github.com/janalihassan)
