# UnrealDemo of Yugen: 

Showing of the Technologies which was used during the showing of Yugen

<img src="imagesForReadme/TitelImage.jpg" alt="Titelimage" style="max-height:200px;">


## What is Yugen:
Yugen is a showing created by [Christine Bonansea](https://www.cbcdance.com/) & [Chris Ziegler](http://www.movingimages.de/) during the EU dance and technology initiative MODINA. During their residence they got development and tech-support from [MIREVI](https://mirevi.de/). Music and Sound was produced by [Hugo Paquete](https://hugopaquete.com/).

The act was about a human dancer wearing a motion-capture-suit, and a virtual avatar, showing off interactions between them.

The showing was split in three different parts:
1. PreShow with virtual Ipad-Camera
2. Dancer on Stage with projection-mapping on top of her
3. Dancer on Stage with background-projection

---

## Limitations of the demo:

- Due to third-party-licenses, technological complexity and very specific hardware requirements, this demo is only showing the third and longest part.
- Due to privacy rights a different virtual avatar is used, and the animations were replaced with freely available animations from [mixamo](https://www.mixamo.com/#/).

---

## What does the demo show:

- Cameraswitching between static and moving cameras
- Animationblending between different prerecorded animationclips
- Animationblending between prerecorded and livestreamed animations
- Changing visual styles
- Timedilation
- Mapping Livestreamed data from Rokoko and LiveLinkFace to Metahuman

During the show this was controlled via a Streamdeck and Keyboard Inputs. The demonstrator uses UI-elements for a better usability and easier interaction.

---

## Requirements:
- [Unreal 5.2](https://www.unrealengine.com/download)
- [Rokoko Plugin](https://www.fab.com/listings/b1019dc6-bb36-4f94-bc85-aec9dc67a48c) installed

---

## How to use:

1. Open the Unreal-Project and open the Mainlevel.
2. Press "Play"
3. UI appears in the Gameview

<img src="imagesForReadme/howToUse.jpg" alt="howToUse" style="max-height:100px;">


#### The UI is split into three sections:

- CameraManager -> Upper left corner
- RenderManager -> lower left corner
- AnimationManager -> right side

---

#### CameraManager:
The CameraManager-UI is made of buttons, which let you control what camera is used to render the scene.
- Camera 1-3 are static cameras placed in the scene similar to position which were used during the showing
- Camera 4 is mounted to the head of the virtual avatar (with a bit of smoothing applied)
- Camera 5 is a movable camera, controllable via WASD or ArrowKeys and rotated by holding down the left mouse button and moving it around inside the view.

<img src="imagesForReadme/DifferentCameras.jpg" alt="DifferentCameras" style="max-height:100px;">

Underneath there are FadeOut/FadeIn buttons, which can be used to fade the view to black and reverse it over a duration of 5 seconds

During the show this was used to control the visuals on the backprojection.

---
#### RenderManager:

The RenderManager-UI is five buttons, each changing the view to a different rendermode/visual.
- Normal: The normal rendering, which is active by default
- Wireframe: Displays only the mesh topology
- Unlit: Removes all lighting calculations
- Detail: Shows lighting without base color textures
- ShaderComplexity: Shows how complex the shadercalculations are for what part of the image

<img src="imagesForReadme/DifferentVisuals.jpg" alt="DifferentVisuals" style="max-height:100px;">

These are the modes you are also capable to switch in between when using Unreal by pressing F1-F5 when play is active.

During the show this was used to change the visual style, especially in preshow and the end sequence.
___

#### AnimationManager:

The AnimationManager controls anything which has to do with the animation on the virtual character:

<table>
  <tr>
    <td valign="top">
      <ul>
        <li>Set which animation is playing</li>
        <li>Blend between pre-recorded animations</li>
        <li>Blend between pre-recorded and livestreamed animations</li>
        <li>Toggle between pre-recorded and livestreamed faceanimations</li>
        <li>Reset characterposition</li>
      </ul>
    </td>
    <td>
      <img src="imagesForReadme/AnimationManager.jpg" height="175">
    </td>
  </tr>
</table>

##### Animations:

To set an animation select one of the eight buttons. There are two selectionslots (blue/red). By pressing a button the oldest selection gets replaced.
Right now the animations are:
1. HipHop1
2. HipHop2
3. Rumba
4. Samba
5. SillyDance
6. Brookly Uprock
7. Angry
8. Capoeira

These animations can be replaced to any animation based on a metahuman by selecting the animationmanager in the Outliner and swapping out the animations in the Details-panel.

<img src="imagesForReadme/ChangeAnimation.jpg" alt="ChangeAnimations" style="max-height:300px;">

Replacing them with animation not based on a metahuman, a retargeting is necessary. This can be done by importing the animation into Unreal and following this guide:

[Unreal Animation Retargeting](https://dev.epicgames.com/documentation/unreal-engine/retargeting-bipeds-with-ik-rig-in-unreal-engine)

The prepared Metahuman-IK-Rig can be found in Content/MetaHumans/Metahuman_IKRig.

During the show different animations were used based on the story and triggered at specific timings. 

##### AnimationBlending:

To blend between the two selected animations move the slider underneath the 8 buttons. 
At the most left position only the blue animation, on the most right position only the red is playing. 
In-between both animations are blended, depending on how far the slider is moved towards a side.

During the showing the animation-blending was used to swap between animations or to insert glitch-effects into the animation.

##### TimeDilation:

With the second slider the speed of the animation on the character can be set. 
- 1 -> normal speed
- 0.1 - 0.9 -> slower animation
- 1.1 - 2-0 -> faster animation
- 0 -> paused

During the showing the time dilation was used to set focus on specific virtual movements (slow-motion) and to support the glitching effect in the end (fast-forward)

##### MocapBlending

The third slider is for blending between the prerecorded animation set with the buttons, and a livestreamed animation via Rokoko-LiveLink-Plugin.

To stream body-mocap-data from Rokoko to Unreal follow this guide from [25] onwards: 

[Start Streaming Rokoko-Unreal](https://support.rokoko.com/hc/en-us/articles/15165002022929-Unreal-Engine-5-3-and-prior-Livestream-to-Default-Metahumans)

Additionally, select BP_Lexi in the Outliner and change the LiveLinkBodySubject to the correct name:

<img src="imagesForReadme/LiveLinkName.jpg" alt="LiveLinkName" style="max-height:100px;">

To stream face-mocap-data from iPhone to Unreal follow this guide until the phone shows up in LiveLink (Stop at "Software Setup"): 

[Start Streaming with LiveLinkFace](https://dev.epicgames.com/community/learning/tutorials/lEYe/unreal-engine-facial-capture-with-live-link)

Additionally, select BP_Lexi in the Outliner and change the ARKitFaceSubject to the correct name:

<img src="imagesForReadme/LiveLinkNameFace.jpg" alt="LiveLinkNameFace" style="max-height:100px;">

As a substitute, a LiveLinkRecording can be found under Content/Cinematics/Scene_1_08 in case Rokoko and/or an Iphone is not available.
Double click it to open the Sequencer and press play on the bottom left to start the animation. Two LiveLinkSources should appear in Unreal-LiveLink.

<img src="imagesForReadme/PreRecordedLiveLink.jpg" alt="PreRecordedLiveLink" style="max-height:300px;">

With the button "Toggle Facetracking" the facial-animations can be changed between pre-recorded and livestreamed facial-animations.

During the show this was used to sync up the real dancer with the virtual avatar, based on how close the dancer was to the screen. 
- If the dancer was next to the screen, both movements were identically.
- When the dancer moved away, the animation blended towards a prerecorded and the dancers unsynced.

This can be simulated inside the white square underneath the mocap-slider by moving the blue dot around.

<img src="imagesForReadme/MocapBlendingSpace.jpg" alt="MocapBlendingSpace" style="max-height:300px;">

Left: Fully synced ||
Middle: mixed ||
Right Fully asynced

Underneath there are two reset-buttons in case the animations leads the character too far offstage.
Both reset the virtual avatars position back to the center. Soft reset does this over a time span of 3 seconds, the other instantly.

<img src="imagesForReadme/Reset.jpg" alt="Reset" style="max-height:300px;">