# NavBot-Helper-ZPS
Config file of key binds to help with NavBot with Zombie Panic: Source https://github.com/caxanga334/NavBot


# NavBot Helper Keybinds Table

| Key                 | Action                                | Description                                                                                    |
|---------------------|---------------------------------------|--------------------------------------------------------------------------------------------------|
| F1                  | Edit Connections                      | Cycle connection edit modes. Right Click: Mark nav area. Left Click: Connect/Disconnect.          |
| F2                  | Edit Area                             | Cycle area edit types. Right Click: Select/start area. Left Click: Perform action. |
| F3                  | Area Attributes                       | Cycle area attribute types. Right Click: Mark area. Left Click: Apply attribute. |
| F4                  | Ladder Editing                        | Cycle ladder editing modes. Right Click / Left Click: Ladder actions.                               |
| F5                  | Build / Test Nav Paths                | Cycle path-finding test modes. Right Click: Mark destination. Left Click: Start path test. |
| F6                  | Adjust Area Height                    | Cycle through area height options. Left / Right Click: Select area. Mouse Wheel: Raise / Lower height. |
| F7                  | Set Selection Mode                    | Cycle selection editing modes: Begin selection. Left Click: End selection.       |
| F9                  | Mark Walkable Areas                   | Toggle marking walkable areas. Left / Right Click: Mark walkable area or delete all walkable marks.        | 
| F10                 | Seed Walkable Spots                   | Seeds walkable spots for initial nav mesh generation.                                                         |
| F11                 | Generate Incremental Nav Mesh         | Run incremental nav mesh generation after seeding walkable spots.                                        |
| Keypad /            | Toggle Waypoint Edit                  | Toggle waypoint editing mode on/off.                                                                          |
| Keypad *            | Toggle NavMesh Edit                   | Toggle full nav mesh editing mode on/off.                                                                |
| Keypad Up Arrow     | Waypoint Radius                       | Cycle waypoint radius.                                                                                     |
| Keypad 5            | Waypoint Team                         | Cycle waypoint team.                                                                        |
| Keypad Down Arrow   | Waypoint Control Point Index          | Cycle waypoint control point Index.                                                   |
| Keypad Right Arrow  | Waypoint Attribute                    | Cycle waypoint attributes. Left Click: Apply attribute. |
| Keypad PLUS         | Add Waypoint                          | Adds a waypoint.                                                                                 |
| Keypad MINUS        | Delete Waypoint                       | Deletes the nearest waypoint.                                                                         |
| Keypad ENTER        | Nav Analyze                           | Save and Compress Nav mesh. |
| Insert              | Show Spawn Points                     | Displays spawn points (doesn’t include teleport-only spawns on some maps).                                     |
| Page Up             | Toggle NoClip                         | Enable / Disable noclip mode.                                                                                  |
| Page Down           | Toggle Gravity                        | Toggle gravity.                                                                      |
| Home                | Toggle Friendly Fire                  | Toggle friendly fire                                                                                       |
| Delete              | Cycle Bot Quota                       | Cycle bot quota                                                         |
| End                 | Remove All Bots                       | Kick all bots and reset bot quota to zero.                                                                 |



# New map process
- Copy .cfg file to \zps\cfg
- Add `-console` to Game startup
- Load map
- Press ESC and load keybinds by typing `exec navbot-helper-zps.cfg`
- Press "Page Up" to enable god mode
- Press "F10" to Seed Walkable spots
- Press "F11" to Generate Nav Mesh
- Press Enter to Save Nav Mesh
- Fly around map and look for walkable areas not covered with nav mesh if you find any
  - Press "F9" to enable Mark as Walkable. Left click to place marker
  - Press "F11" to generate the nav mesh
  - If these new areas are on top of already existing ones, use `sm_nav_delete_overlapping_from_selected_set` to remove them
  - Press "Enter" to save
  - Repeat process until all walkable areas have nav mesh
- Press "Insert" to show spawn points and make sure they have nav mesh
- Add ladders (to be added)
- Look for disconnected nav mesh and join them with "F1"
- Look for and remove nav mesh from non walkable areas (e.g places you don't want the bots going)

# Misc useful commands
- `sm_nav_snap_to_grid 1`
- `sm_navbot_tool_bots_go_to` makes bots come to your location
- `sm_navbot_debug_blind` bots can't see each other
- `sm_nav_merge_ladders <bottom ladder ID> <top ladder ID>` merge/join ladders that are close to each other
- `showtriggers_toggle` 

# Fix Errors
## Degenerate Navigation Area
Error Example:<br>
``L 12/31/2025 - 22:28:56: [NavBot] Degenerate Navigation Area #1320 at setpos 1962.5 975 704.031``<br>
Fix with:<br>
``sm_nav_add_to_selected_set_by_id 1320``<br>
``sm_nav_delete_marked``
