title: FoodExtract-Vision Fine-tuned VLM Structued Data Extractor
emoji: 🍟➡️📝
colorFrom: green
colorTo: blue
sdk: gradio
app_file: app.py
pinned: false
license: apache-2.0
---

Fine-tuned SmolVLM2-500M to extract food and drink items from images. This is a follow-along from [LearnHuggingface](https://www.learnhuggingface.com/notebooks/hugging_face_vlm_fine_tune_tutorial) and [YT Video](https://www.youtube.com/watch?v=_EMfJSmLSKE)
For additional info :
[Github Repo](github.com/mrdbourke/learn-huggingface)

**Base model:** https://huggingface.co/HuggingFaceTB/SmolVLM-500M-Instruct
* **Fine-tuning dataset:** https://huggingface.co/datasets/mrdbourke/FoodExtract-1k-Vision (1k food images and 500 not food images)
* **Fine-tuned model:** https://huggingface.co/chanifrusydi/FoodExtract-Vision-SmolVLM2-500M-fine-tune-v1-VIDEO

## Overview

Extract food and drink items in a structured way from images.

The original model outputs fail to capture the desired structure. But the fine-tuned model sticks to the output structure quite well.

However, the fine-tuned model could definitely be improved with respects to its ability to extract the right food/drink items.

Both models use the input prompt:

````
Classify the given input image into food or not and if edible food or drink items are present, extract those to a list. If no food/drink items are visible, return empty lists.

Only return valid JSON in the following form:

```json
{
  'is_food': 0, # int - 0 or 1 based on whether food/drinks are present (0 = no foods visible, 1 = foods visible)
  'image_title': '', # str - short food-related title for what foods/drinks are visible in the image, leave blank if no foods present
  'food_items': [], # list[str] - list of visible edible food item nouns
  'drink_items': [] # list[str] - list of visible edible drink item nouns
}
```
````

Except one model has been fine-tuned on the structured data whereas the other hasn't.

Notable next steps would be:
* **Remove the input prompt:** Just train the model to go straight from image -> text (no text prompt on input), this would save on inference tokens.
* **Fine-tune on more real-world data:** Right now the model is only trained on 1k food images (from Food101) and 500 not food (random internet images), training on real world data would likely significantly improve performance.
* **Fix the repetitive generation:** The model can sometimes get stuck in a repetitive generation pattern, e.g. "onions", "onions", "onions", etc. We could look into patterns to help reduce this.