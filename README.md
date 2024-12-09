# websci25-image-types

This repository serves as a digital appendix to our WebSci'25 submission. We introduce 

1. A decision tree to improve human annotation quality
2. Prompting `gpt-4o` for computational classification of visual political communication on Instagram.



This `README` file contains a visualization of the Decision Tree, an overview of the Few-Shot-Examples used when prompting, and a code snippet highlighting how few-shot examples were provided in the prompt.

The `/data` folder contains `CSV` files with classification results for each prompting scenario. All files include a `Majority Human` column representing our Gold Standard derived from the Decision Tree. The folder also contains the file `Few-Shot-Example-Paths.txt`, which allows you to filter the few-shot examples during the evaluation. 

The `/Prompts` folder contains one folder per prompting approach. Each subfolder contains markdown files containing the prompts used in our experiments, the evaluation results, and API parameters.



### Decision Tree

![A visual overview of the Decision Tree.](images/decision_tree.png)



### Few-Shot Examples

The image below shows the pictures we used in our few-shot prompt. Examples were selected once using pandas' `sample()` function. Then, the same examples were used for every request. Each line represents a separate user message. The text to the left is the textual message part. Few-Shot images were sent using `detail=low` setting.

![Few-Shot Examples Plot](images/Image-Types-Few-Shot-Examples-ALL_2024-11-07-14-47_Prompt_V2.png)

## Code for Few-Shot Examples

```python
few_shot_prompt = []
few_shot_image_paths = {}
labels = eval_df['decision'].unique()
for label in labels:
  if label == "Review":
    continue

  few_shot_image_paths[label] = []

  few_shot_samples = eval_df[eval_df['decision'] == label].sample(n=3, random_state=4466) 

  few_shot_images = [{
      "type": "text",
      "text": f"{{ 'decision': '{label}' }}"
    }]
  for index, row in few_shot_samples.iterrows():
    image_base_64 = encode_image(row['image'])
    few_shot_image_paths[label].append(row['image'])

    few_shot_images.append({
        "type": "image_url",
        "image_url": {
            "url": f"data:image/jpeg;base64,{image_base_64}",
            "detail": "low"
        }
    })

  few_shot_prompt.append({
      "role": "user",
      "content": few_shot_images
  })
```

