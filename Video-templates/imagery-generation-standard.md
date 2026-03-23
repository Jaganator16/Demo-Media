# Guide: Asset, Image, and Video Generation for Demo Content

## Purpose

This guide defines the standard approach for creating visual assets, still images, and AI-generated video clips for product demo videos.

The goal is to improve consistency, reduce visual glitches, and build scenes that are easier to edit, reuse, and refine.

This is especially important for:
- user stories
- diagram-style explainer segments
- product visuals
- simple animated scenes

---

## Core principle

When including user stories, visual storytelling is essential.

The viewer should be able to understand what is happening from the visuals alone, even before the voiceover explains it.

This means:
- scenes must be clear
- movement must be intentional
- composition must support the script
- visuals must favour control over complexity

---

## Recommended tools

### Image generation
Use:
- ChatGPT image generation
- Nano Banana

### Video generation
Through ElevenLabs video generation, use:
- Veo 3.1 Fast
- Veo 3.1

These models work best when given:
- a clear start frame
- a clear end frame
- a well-written prompt

---

## Standard approach

Do **not** rely on generating two completely separate full images and asking the video model to interpolate between them.

This often causes:
- background flicker
- object distortion
- inconsistent shapes
- visual noise
- strange movement between frames

This happens because video generation models analyse images at the pixel level and predict intermediate motion, often without understanding scene logic.

Instead, build scenes from controlled assets.

---

## Image generation workflow

### 1. Create the scene concept
Decide:
- what the scene needs to communicate
- what must move
- what must remain static
- whether camera movement is necessary

Default rule:
- keep movement minimal
- avoid camera movement unless absolutely necessary

---

### 2. Create the start frame
Generate a full start frame that you are happy with.

This frame should define:
- composition
- lighting
- style
- object placement
- overall look of the scene

Do not move on until the start frame is strong.

---

### 3. Split the frame into assets
Once the start frame is approved, break it into layers.

Generate:

  - the background only  
  - no foreground objects
  - no characters
  - no moving elements

- each foreground object separately as transparent PNG assets  
  Examples:
  - people
  - doors
  - laptops
  - props
  - cabinet panels
  - icons
  - signal arms

You can:
- generate each asset in its own file, or
- generate multiple assets in one transparent image with spacing between them for later cropping

---

### 4. Create alternate asset states if needed
If parts of the scene change between start and end frames, generate those state changes as separate assets.

Examples:
- door closed / door open
- arm down / arm raised
- laptop shut / laptop open
- hand position A / hand position B
- object in left hand / object in right hand

This gives control over movement without asking the video model to invent it.

---

### 5. Build the final start and end frames manually
Use a photo editing tool such as:
- Pixelmator
- Canva
- other layer-based editor

Recreate the scene using:
- the static background
- the foreground assets
- start-state asset positions
- end-state asset positions

This gives you:
- a controlled start frame
- a controlled end frame
- consistent background and object design

---

## Video generation workflow

### 1. Use the manually built start and end frames
Insert the finished start and end frames into the video generation model.

This is far more stable than using two separately generated full images.

---

### 2. Write the prompt carefully
Write a prompt describing:
- what should move
- what should remain static
- the intended action
- the style and pacing

Before using the prompt, feed it into an LLM to:
- review it
- simplify it
- clarify movement instructions
- tailor it for the target video model

---

### 3. Keep motion simple
AI video generation works best when:
- only a few elements move
- movement is large enough to read clearly
- the scene is static apart from key actions
- camera is locked off

Avoid:
- complex choreography
- overlapping movements
- fine mechanical motion
- unnecessary background activity

---

## Important generation rules

### Rule 1: AI video takes the path of least resistance
Video generation will often ignore logic, physics, or continuity if there is an easier visual shortcut.

Example:
- A character holds a briefcase in the left hand
- The door handle is also on the left side
- Instead of using the right hand to open the door, the model may:
  - make the briefcase disappear
  - use the left hand to open the door
  - then make the briefcase reappear

This can happen even if prompts explicitly say not to.

### Practical response
Think through likely conflict points before generating assets.

Design scenes to reduce ambiguity.

Example:
- put the briefcase in the right hand instead
- keep the left hand free
- avoid actions that require complicated cross-body interaction

---

### Rule 2: Static objects should stay truly static
If the background is regenerated between frames, small distortions will often appear.

Examples:
- walls shifting
- cabinets changing shape
- trees flickering
- device proportions drifting

### Practical response
Always use:
- one consistent background
- manually positioned foreground assets
- separate motion elements

---

### Rule 3: Small mechanical movements are unreliable
AI video models struggle with precise, small, timed motion.

Example:
- a signal arm rotating exactly 30 degrees clockwise
- a switch moving into a specific locked position
- a tiny LED changing at an exact moment

### Practical response
If movement is:
- small
- precise
- timed
- mechanically important

animate it by hand in editing software instead.

Where possible:
- separate the moving object from the rest of the scene
- animate it in DaVinci, After Effects, or similar

Example:
- generate signal pole as one asset
- generate signal arm as a second asset
- rotate the arm manually in post

---

## Asset design rules

### Keep assets modular
Create assets so they can be reused across:
- multiple videos
- alternate story versions
- different customer segments
- positive and negative user stories

Examples:
- cabinet open / closed
- laptop closed / open
- same technician in multiple poses
- same UI in multiple states
- same background with different foregrounds

---

### Separate reusable from custom
Build reusable assets first.

Only generate custom assets when necessary for:
- a specific customer
- a specific device
- a specific scenario
- a one-off diagram

---

### Preserve editable backgrounds
Where possible, create a clean version of the scene background without text or overlays.

This makes it easier to:
- edit later
- swap copy
- localise content
- build multiple versions

---
 
## Quick review check

Before approving any asset or clip, check:

- Is the scene clear and easy to understand?
- Do static elements remain consistent?
- Does movement look intentional and believable?
- Does it match the script and support editing?
- Can this be reused or adapted later?

---

## Standard production approach

Default pipeline:

1. Write the scene goal  
2. Generate the best possible start frame  
3. Split the scene into reusable assets  
4. Generate alternate object states if needed  
5. Rebuild start and end frames manually  
6. Use those frames in video generation  
7. Polish the prompt with an LLM  
8. Generate the clip  
9. Fix precise movements manually in editing  
10. Save clean reusable assets for future projects

---

## Key principle to remember

AI image and video generation should be used to create the **look** of a scene.

Editing tools should be used to control the **logic** of a scene.

When precision matters, do not ask the model to guess.
