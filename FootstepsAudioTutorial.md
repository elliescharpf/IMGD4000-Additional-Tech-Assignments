# Tutorial: Creating Footstep Sounds in Unreal Engine

Footstep sounds are a small detail that make a huge difference in immersion. In this tutorial, I’ll walk through how I implemented footsteps in our project, explaining how to do it and why each step matters.

---

## Step 1: Import Your Footstep Audio
- **How:** Start by opening your Content Browser in Unreal and create a **SoundFX** folder to keep all of your sound files organized.  
- Once you have your footstep sound file downloaded, drag it into the SoundFX folder. (I love the website freesound.org and usually get all of my sound files from there.)  
- ![Import Audio](https://github.com/user-attachments/assets/6a56dd69-2404-4d2e-b1f7-b933c60ceea3)

---

## Step 2: Edit Your Footstep Audio
- After you have your sound file in the Content Browser, duplicate it either by the number of footsteps in the audio or about 5–8 times. These duplicates will be used to cut the audio into separate files, each containing the sound of a single step.  
- Once you have all duplicate audio files, go to **Edit** and then **Plugins** in the top bar:   
  ![Plugins](https://github.com/user-attachments/assets/e4b73c46-1f4d-4c12-83c5-1946c6d0cfa1)  
  Add the **Waveform Editor** and restart Unreal:  
  ![Waveform Editor](https://github.com/user-attachments/assets/c0b80743-1c79-4118-8bb0-992de174ba0e)  
- Once the Waveform Editor is installed, right‑click your footstep audio file and select **Edit Waveform**:  
  ![Edit Waveform](https://github.com/user-attachments/assets/85453dab-f1e5-457e-9f80-5c761c69873d)  
- Zoom in, listen, and crop the audio so the clip only contains one step. To trim the audio, click the **Toggle fade in transformation** and **Toggle fade out transformation** buttons on the top bar:  
  ![Fade Buttons](https://github.com/user-attachments/assets/ec3ae51f-f66e-484b-bf5e-2f6fc477772a)  
  Then grab the green (beginning trim) or red (end trim) lines and pull them to either side of the footstep sound. Adjust the fade bars (white curved lines) so they’re just barely off the green and red trim bars:  
  ![Trim Lines](https://github.com/user-attachments/assets/9f900e2e-0f42-401e-85e1-31b405485e2d)  

For this part, you really want to make sure there is minimal silence before and after the step sound. Otherwise, the sounds will be delayed since they start with silence. Also, make sure the footstep is loud enough (you can change the volume for each footstep in the **Details** panel under **Sound > Volume**). Footsteps should be short, punchy, and consistent. Editing ensures each sound is clear and doesn’t overpower other audio elements like dialogue or ambient effects.  

Repeat this process until you have 5–8 single‑step sounds. I named mine **ConcreteFootsteps‑00X**.

---

## Step 3: Create a Sound Cue
- Once you have all your step audio files, right‑click in the Content Browser inside your SoundFX folder and select **Audio > Sound Cue**:  
  ![Sound Cue](https://github.com/user-attachments/assets/ea9c73bb-e1cf-4dd2-8a92-5a99fcdafd05)  
- I named mine **SC_ConcreteFootsteps**.  
- Open the Sound Cue, click on the Content Drawer, and drag in your footstep sound waves:  
  ![Content Drawer](https://github.com/user-attachments/assets/6c6ed126-2788-4585-9d01-c28602416420)  
- Right‑click and add a **Random** Sound Node. Keep clicking **Add Input** until you have as many inputs as footstep sounds. Connect each WavePlayer footstep sound into the Random node, then connect the Random node’s output to the Output node. It should look like this:  
  ![Random Node](https://github.com/user-attachments/assets/c1bcc0ce-9742-4c7e-9418-45ff90b5adee)  
- Once this is set up, click **Play Cue** in the top bar to listen to the footstep sounds.  

We do this randomization because repetition quickly breaks immersion. By having multiple variations, footsteps feel more natural and less robotic. It prevents the player from hearing the same sound repeatedly, making movement feel dynamic and realistic.

---

## Step 4: Connect Footsteps to Animation
- **How:** Open your character’s animation sequence (e.g., walk or run). Right‑click and navigate to **Add Notify... > Play Sound**:  
  ![Add Notify](https://github.com/user-attachments/assets/5afb0473-87e4-490e-a140-7991db790a6e)  
- Click on the Play Sound Notify you just placed. In the **Details** panel under **Anim Notify**, where it says **Sound** with a dropdown that currently says “None,” select your footstep sound cue (**SC_ConcreteFootsteps**).  
- Slow down your animation and watch when the character’s foot hits the ground. Pause and move the Animation Notify to this spot. For the next times the character’s foot touches the ground, right‑click the Notify and select **Copy**, then right‑click the next spot and select **Paste**. It should end up looking like this (you may have more step sounds depending on how fast your character’s animation is set up):  
  ![Animation Notify](https://github.com/user-attachments/assets/18e93aef-485f-43ec-ac0b-cd1d21749442)  

We line up the sounds to the exact moment the character’s foot touches the ground because timing is crucial for realism and immersion. By syncing audio to animation, footsteps match the character’s movement visually and physically, enhancing the player’s experience.

---

## Step 5: Test and Adjust
- **How:** Play the animation in‑engine and listen for timing, volume, and variation. Adjust notify placement or audio levels as needed.  
- **Why:** Iteration ensures the footsteps feel natural in context. Testing in‑game is the only way to confirm that the audio matches the player’s perception of movement.  

---
