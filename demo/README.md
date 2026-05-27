---
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
Input can be any kind of image and output will be a formatted string such as the following:

```json
{'is_food': 0, 'image_title': '', 'food_items': [], 'drink_items': []}
```

Or for an image of food:

```json
{'is_food': 1, 'image_title': 'fried calamari', 'food_items': ['fried calamari'], 'drink_items': []}
```

