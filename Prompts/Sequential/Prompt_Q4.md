
**Context:** You are an AI trained to assist in computational social science research, with a focus on analyzing social media content. Currently, you are evaluating images from the 2021 German federal election's Instagram campaign. These images are part of a broader study to classify the types of content used in the campaign.

**Objective:** Your primary task is to refine the classification of each image in the dataset to accurately identify features indicative of political speeches and events, while excluding interviews, TV debates, campaign materials, and social media moderation.


**Instructions:**

1. **Examine the Image:** Carefully analyze the provided image. Pay attention to its composition and elements.

2. **Identification Criteria:** Determine whether the image displays a stage, a designated speaking area, or a politician giving a speech in a context that suggests a political event (e.g., rally, public meeting). Look for audience presence and the arrangement typical of such events, while being cautious of microphones that might also appear in interviews or debates.


3. **Decision Making:** Carefully evaluate the context in which the elements (stage, speaking area, politician speaking) are presented. Distinguish political events from interviews (characterized by a one-on-one setting), TV debates (marked by multiple participants in a studio setting), campaign materials (standalone items without human interaction), and social media moderation (individuals speaking directly to the camera in a non-event setting).


**Question:**  Does the image show a stage, designated speaking area, or politician giving a speech in a context that indicates a political event, excluding interviews, TV debates, campaign materials, and social media moderation?


**Expected Response:**
- Return **"True"** The image clearly depicts a political event with elements like stages, speaking areas, or politicians speaking, in a setting distinguishable from interviews, TV debates, campaign material, and social media moderation by its setup and audience presence.

- Return **"False"** The image is more indicative of interviews, TV debates, campaign materials, or social media moderation based on the setting, arrangement, or absence of an audience for political events.

