# Changelog

## 1.0.0 - 2026-09-30

First public release for 3ds Max 2027.

The [User Guide](docs/SceneForge_User_Guide.pdf) describes the features up to the panel build
v133. The changes made after it are listed below.

### Added

- **Help menu** - SceneForge > About, Documentation, Report a bug..., Suggest a feature...
  and More plugins by the author; the same commands in the panel's Menu button (group Help)
  and in the command palette (Ctrl+P).
- **Report a bug...** copies the SceneForge and 3ds Max versions, Windows version, install
  folder, object count and the last lines of the panel log to the clipboard, then opens the
  GitHub bug form or your e-mail program. Nothing is sent automatically.
- **Create camera from view** - a camera matching the active viewport (position, target and
  field of view), created in the class of the current renderer: V-Ray Physical Camera,
  Corona Camera, FStorm Camera, or a Physical Camera for Arnold and the others.
- **Footer counters** for the selection and for the whole scene: objects, faces, triangles and
  vertices. The selection counter follows the selection made in 3ds Max and updates by itself.
- **Ctrl + drag** on the list selects the rows it passes over, with auto-scroll at the edges.
  A drag without Ctrl moves objects as before (parenting, layers, material headers).
- **Pivot** submenu in the row menu - the Hierarchy > Pivot one-shot commands plus: to the
  bottom / top of the object, to a bounding-box corner, to the world origin, to the parent's
  pivot, to the common centre of the selection, copy the pivot orientation.
- **Busy signal** - a wait cursor and a status-bar message during operations that take seconds
  on large scenes.
- The layer list can be turned off (bottom bar, palette, Preferences).
- Warning about an unnamed selection set (3ds Max does not remove it and some scripts fail on it).

### Changed

- Clicking the eye or the freeze icon on a **selected** row hides / freezes **every selected
  object** (the Scene Explorer rule); on an unselected row it acts on that row only. One undo step.
- After leaving isolation, unhiding or any refresh the list keeps its place and the selected
  object stays in view (centred when it moved), instead of jumping to the top.
- The list scrolls horizontally pixel by pixel instead of column by column.
- The vertical scroll bar stays at the visible edge of the panel, also when a floating Command
  Panel covers part of the dock.
- The named selection sets list updates by itself.
- English-only user interface.

### Fixed

- On heavy scenes the list sometimes stopped following added and deleted objects until
  Refresh was clicked - the scene listener was switched off after an import and is now also
  watched and restored automatically.
- Automatic rules no longer re-apply to objects that were already in the scene when importing;
  after a file is opened they run once per file.
- The undo warning no longer appears when nothing is wrong, and an undo block left open by
  another tool is closed automatically.
- Deleting many selected objects from the panel: from about 13 s for 300 objects (and far
  longer on 9 000) down to a single read of the selection.
- Home, End, Page Up and Page Down now work in the list (3ds Max used to swallow them).
- Errors raised inside 3ds Max callbacks are written to the panel log instead of disappearing.
- Scene reset, New, and merging a file refresh the panel fully.
- The panel log is capped at 1 MB.
