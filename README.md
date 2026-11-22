# Cable management simulator

A 3D desk planner for working out where your cables will go before you buy clips, trays and cables. It shows each cable's messy path and its managed path, scores how clean the desk looks, and builds an install plan with real measurements.

## Opening it

Double-click `index.html`. It runs in your browser with no install, but it needs an internet connection because Three.js loads from a CDN (jsdelivr). Your setup saves itself in the browser as you work. The first time you open it, you get the example desk.

## Layout

- **Left panel:** desk size, the **Add device** palette, the device list, and the **Selected** inspector.
- **Middle:** the 3D view. Drag empty space to orbit, right-drag to pan, scroll to zoom.
- **Right panel:** cleanliness score, cables, and the install plan.
- **Top bar:** Before/After, views, display toggles, units, and file buttons.

## Building the desk

Set **Width**, **Depth**, **Height**, **Top** (desktop thickness), **Wall gap** (space between the desk's back edge and the wall) and **Finish**. Measure your real desk; every position and length in the plan depends on these numbers.

**Desk shape:** pick **Straight**, **L-shape** or **U-shape** at the top of the Desk panel.
- **Width** and **Depth** are the main desk, the part against the wall.
- An L-shape has one wing. Choose **Wing on left** or **Wing on right**.
- A U-shape has a wing on each side, and each wing has its own size. The ends are usually narrower than the main desk.
- A wing's **Width** is how wide it is side to side. Its **Length** is how far it comes forward past the front edge of the main desk. Wings sit flush with the outer sides of the main desk.

Devices can go anywhere on the wings. A cable from a device on a wing drops over the wing's outer edge and runs back under it, which keeps it out of view from the chair. The score and Auto-arrange both use the real shape.

## Devices

Click a button in **Add device**: monitor, PC tower, laptop, keyboard, mouse, speaker, speaker controller, subwoofer/amp, webcam, microphone, audio interface, USB hub/dock, lamp, power strip, wall outlet, cable tray, desk grommet, desk mat, or custom box. A webcam added while a monitor exists goes on top of it.

**Placement** (in the inspector) is one of **On desk**, **Under desk**, **Floor** or **Wall**. Each device type only offers the placements that make sense for it (a tray is under-desk only, an outlet is wall only).

**Moving a device:**
- Drag it in the 3D view. It slides on its own surface (desk top, underside, floor or wall).
- A monitor's screen may hang past the desk edge. Only its stand has to stay on the desk.
- Or use the inspector sliders: **Left–right**, **Back–front**, a height slider (**Raise**, **Gap below top** for under-desk items, **Height** on the wall) and **Rotate**.
- Left–right is measured from the desk's **left edge**, back–front from its **back edge**, so you can copy the numbers from a tape measure.

The inspector also has **Name**, **W / H / D** size, a **Needs a power cable** checkbox, **Duplicate** and **Delete**. A power strip's socket count comes from its width.

**Auto-arrange** (the button above the device list, or **A**) lays out everything on the desk top using each item's real size:
- Monitors form a centred row at the back. Two are both turned inward; with three, the middle one faces straight ahead and the sides turn inward.
- Speakers go either side of the screens, angled toward you. If there's no room, they move forward and a message tells you.
- The webcam sits on top of the main screen.
- The keyboard is front-centre. The mouse and speaker controller go to its right, the microphone to its left.
- Low boxes like the dock or audio interface go under the screens, next to the stand.
- Anything else goes to the nearest free spot toward the back corners, and the desk mat is centred under the keyboard and mouse.

Only desk-top items move, and locked items stay where they are. Ctrl+Z undoes it.

**Locking:** click **🔓 Lock** in the inspector or press **Shift+L** to pin a device in place. A locked device can't be dragged, nudged, rotated or moved with the sliders, and Auto-arrange leaves it alone. Locked items show 🔒 in the list and on their label. Auto-arrange works around them, and when you lock one monitor or speaker on one side, it puts the unlocked one in the mirror spot so the setup stays symmetric. Click **🔒 Locked** or press Shift+L again to unlock.

## Cables

- **Connect mode:** turn it on, click one device, then another. The cable kind is guessed (power for strips and outlets, DisplayPort monitor to PC, speaker wire for speakers, and so on). **Esc** leaves Connect mode.
- **The form:** pick From, To and a kind, then **Add cable**.
- **Auto power:** gives every device that needs power a cable to a power strip (an under-desk one if you have it), and adds a strip and wall outlet if they are missing.

Kinds: Power, DisplayPort, HDMI, USB-A, USB-C, 3.5mm audio, RCA, Speaker wire, Ethernet, XLR. Each has its own thickness.

Each cable in the list shows its route length, the length to buy, and any length still visible. Change its kind or route there, or delete it with ×. Route options:
- **Auto (grommet if any):** tucked under the desk, through the nearest grommet if there is one, otherwise over the back edge.
- **Over back edge:** always over the back edge, ignoring grommets.
- **Leave unmanaged:** the cable hangs loose even in After mode.

Hover a cable in the 3D view to see its name, kind and length. Click it to select it.

## Before vs After

**Before (messy)** draws cables as they would drape with no management. **After (managed)** draws them routed under the desk, along the tray if there is one, with clips and sleeves. Press **B** to switch.

## Views and display

- **3D**, **Chair** (your seated view), **Top**, **Under** (looking up at the underside, best for clip positions) and **Back**.
- **X-ray:** makes the desktop see-through.
- **Labels:** device names in the scene.
- **Clips:** show or hide clip and sleeve markers (orange marks under the desk).
- **Color-code:** colors cables by kind instead of their real colors.
- **cm / in:** units for every measurement.

## Cleanliness score

A 0–100 score with a grade (A to F) for the current mode, plus Before → After scores side by side. It takes points off for every length of cable that is:
- hanging in view at the front or sides of the desk (heaviest penalty),
- visible on the desk top,
- loose on the floor,
- dangling under the desk (Before mode only).

The panel lists each of these lengths, the total cable length, and the number of clip spots and sleeves.

## Install plan

- **Recommendations**, some with a button that applies them: mount the power strip under the desk (**Move strip under desk** / **Add under-desk strip**), add a cable tray of a given length (**Add this tray**), add a grommet at a given spot (**Add grommet here**). It also warns about a strip with too few sockets, long runs on the desk top or floor, cables hanging in view, and unmanaged cables, and tells you where sleeves go.
- **Under-desk clip positions** and **Desk-top clip positions:** tables of each clip's distance from the left edge and from the back edge, and how many cables it holds.
- **Shopping list:** adhesive clips (with 25% spare), the tray, braided sleeve length, and Velcro ties.
- **Cable lengths to buy:** each cable's route length and the next standard length up, with about 10% slack.

## Files

- **Export** saves the setup as `desk-setup.json`. **Import** loads one back.
- **New** clears to an empty desk. **Load example** replaces the setup with the example desk. Both ask first, so export before you use them if you want to keep your work.

## Keyboard shortcuts

Press **?** (or click **Shortcuts**) in the app to see this list.

| Action | Keys |
|---|---|
| Undo / redo | **Ctrl+Z** / **Ctrl+Y** or **Ctrl+Shift+Z** (also the Undo/Redo buttons) |
| Copy, cut, paste a device | **Ctrl+C**, **Ctrl+X**, **Ctrl+V** |
| Duplicate the selected device | **Ctrl+D** |
| Delete the selected cable or device | **Delete** or **Backspace** |
| Deselect, leave Connect mode, close help | **Esc** |
| Move the selected device 1 cm / 10 cm | **Arrow keys** / **Shift+Arrow keys** (up = toward the back; for a wall outlet, up = higher) |
| Rotate the selected device 15° | **R** / **Shift+R** |
| Select the next / previous device | **Tab** / **Shift+Tab** (when the 3D view has focus) |
| Before / After | **B** |
| Views: 3D, Chair, Top, Under, Back | **1** to **5** |
| Connect mode, Auto power | **C**, **P** |
| Auto-arrange the desk top | **A** |
| Lock / unlock the selected device | **Shift+L** |
| X-ray, Labels, Clips | **X**, **L**, **K** |
| Export / import the setup | **Ctrl+S** / **Ctrl+O** |

Undo covers every change to the desk, devices and cables (up to 150 steps), including New, Load example and Import. Repeated arrow-key moves or rotations within a second count as one step. View settings (Before/After, camera, units, toggles) are not part of undo. Shortcuts are ignored while you are typing in a text or number field.

## Typical workflow for real under-desk routing

1. Click **New** and enter your desk's real width, depth, height, top thickness and gap to the wall.
2. Add your devices, set their placement and type in their real **W / H / D**. Then either click **Auto-arrange** for a clean layout, or measure where each one really sits and type that into the sliders as distances from the left and back edges.
3. Add the wall outlet at its real height and position, and the power strip where it is now.
4. Connect the signal cables (Connect mode or the form), then click **Auto power**.
5. Press **B** to compare Before and After, and read the score breakdown to see which cables are still visible.
6. Work down the recommendations: usually move the strip under the desk first, then add the tray and any grommet. Move devices that still hang in view further back. Watch the score go up.
7. Switch to the **Under** view with **Clips** on to check the run.
8. Use the clip tables to mark clip positions on the underside of the desk, buy from the shopping list and the cable lengths list, and **Export** the setup so you can return to it.
