# Bifrost Integration

Integrate haptic feedback into your Unity XR project with Bifrost Integration. Realistic hand presence, haptics, and gestures. Easy and powerful.

The **Bifrost Integration** empowers developers to seamlessly integrate our haptic technology into their Unity projects. With our SDK, you can effortlessly capture and interpret hand movements, haptic feedback, and finger gestures. Whether you’re building immersive virtual reality experiences, training simulations, or interactive applications, Bifrost Integration unlocks a new level of realism and interaction. Elevate your project by adding lifelike hand presence and tactile sensations—**all with ease**.

_Note: This package is currently in beta._

# Technical Details

**Full Finger Tracking (Curl and Splay):** Our SDK provides precise finger tracking, capturing natural movements like curling and splaying. Developers can access individual finger data for lifelike interactions.

**Spatial Force Feedback:** Feel the virtual world! The Bifrost Pulse SDK offers spatial force feedback, allowing users to sense resistance, pressure, and touch in their virtual environment.

**Hardstop Feedback:** Experience realistic tactile sensations with hardstop feedback. Whether gripping a virtual object or colliding with a surface, users will feel the impact.

**Variable Force Feedback:** Fine-tune haptic responses. Adjust force levels dynamically based on context, enhancing immersion and responsiveness.

**Integration Made Easy:** Built on the SteamVR SDK, our solution streamlines setup. Our nearly drag-and-drop integration ensures a seamless experience for developers. Elevate your VR projects with Bifrost Integration—powerful, intuitive, and immersive!

**Requirements:**
- Windows 8.1 or later
- Bifrost driver (v0.2.5-beta or higher)
- SteamVR runtime

**Dependencies:**
- SteamVR Plugin

**Documentation:**
- See our [documentation](https://www.bifrostvr.com/pulse/docs) for tutorials and information on integrating Pulse into your projects.

# Setup Guide

**1)** Install and Set Up the [Unity SteamVR Plugin](https://assetstore.unity.com/packages/tools/integration/steamvr-plugin-32647):

**2)** Install **Bifrost Integration**.
- Simply drag and drop the Unity package into your project assets.

**3)** Set up Bindings
- SteamVR may or may not prompt you about **partial bindings**, ensure you select "Replace" instead of "Merge."
If you are not prompted, please copy all the files in `Bifrost/SteamVR_Bifrost/1` to `Streaming Assets/SteamVR`. If there are already files there, delete them.
To verify this was done correctly, check the Console. There should be no errors.

**4)** Ready Your Device:
- Ensure your device is powered on and calibrated to your hand. Refer to the [calibration instructions](https://www.bifrostvr.com/pulse/driver).

**6)** Load the Demo Scene:
- Open the Demo scene located at `Bifrost/scenes/Demo.unity`. This scene showcases various examples of haptics that can be simulated with Pulse.

**7)** Compile and Play:
- Compile your project and start playing. This action should automatically launch the SteamVR runtime and Bifrost UI.

8) Troubleshooting:
- If you encounter any issues, follow these steps:

	- Open the SteamVR Input window.
	- Click "Open Binding UI."
	- Select "Pulse" as the device.
	- Verify that it is using the official bindings for Bifrost Integration.
	- If the bindings are incorrect, it's likely that step 3 was not executed correctly.


# Implementing Haptics

**1)** Spatial Feedback:
Spatial feedback is designed for static objects within your virtual environment. It operates by applying a force to your fingers that is proportional to the force exerted by the in-game hand on the static object. This feedback creates a sensation of resistance, effectively pulling back your finger in space to simulate the presence and interaction with the object.

**To implement:**

- Replace the default SteamVR Player hands with Hand_Bifrost in the prefabs folder. Thats it! 
- By default, spatial feedback will be enabled on all colliders. This can be changed in the layermask.

**2)** Interactable Feedback:
Interactable feedback is tailored for objects that can be grabbed or interacted with directly. When these objects are grabbed, each finger can be assigned a specific feedback type:

- None: No haptic feedback is applied to the finger.
- Force: A force is applied to the finger, providing a tactile sensation of interaction.
- Hardstop: Prevents the finger from moving beyond a certain position, simulating a physical barrier or constraint.

**To implement:**

- Set up spatial feedback hands. 
- Create a throwable object using the SteamVR plugin.
- Add the SpatialFeedback script to the object.
- Set the SteamVR hover events to the SpatialFeedback grab and release methods.
- Configure the type and level of haptics for that object.
