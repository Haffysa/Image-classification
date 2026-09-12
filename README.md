# Packaging Material Image Classifier (Google Teachable Machine)

An image classification project built with Google Teachable Machine to recognise eight types of packaging materials and containers. The model uses visual features such as shape, texture, transparency and material appearance to sort objects — a task with real-world relevance to recycling systems, waste sorting and automated packaging recognition.

## Classes

- Clear Plastic Bottle
- Opaque Plastic Bottle
- Aluminium Beverage Can
- Steel Food Can
- Glass Bottle
- Glass Jar
- Cardboard Box
- Paper Cup

Several of these classes are visually similar (e.g. aluminium cans vs. steel cans, glass bottles vs. glass jars), which made this a genuinely challenging classification problem rather than a trivial one.

## Dataset

Images were sourced from Wikimedia, Google Images and personal iPhone photos, varying lighting, angle, background and arrangement to encourage generalisation. A fixed external test set of 80 images (10 per class) was kept separate from training data throughout.

| Version | Training images | Notes |
|---|---|---|
| V1 | 520 (65/class) | Baseline |
| V2 | 600 (75/class) | Added harder images per class |
| V3 | 630 | Added extra images to the three weakest classes (glass bottle, paper cup, aluminium beverage can) |

## Training Iterations

| Version | Epochs | Batch size | Learning rate |
|---|---|---|---|
| V1 | 45 | 32 | 0.005 |
| V2 | 70 | 16 | 0.001 |
| V3 | 100 | 16 | 0.0005 |

Each version reduced the learning rate and increased training epochs to encourage more stable, careful learning as the dataset grew and got harder.

## Results

**Overall performance on the external test set (80 images):**

| Version | Accuracy | Macro Precision | Macro Recall | Macro F1 |
|---|---|---|---|---|
| V1 | 77.50% | 0.8017 | 0.7750 | 0.7925 |
| V2 | 81.25% | 0.8354 | 0.8125 | 0.8009 |
| V3 | **88.75%** | **0.8982** | **0.8875** | **0.8933** |

**Per-class accuracy across versions:**

| Class | V1 | V2 | V3 |
|---|---|---|---|
| Clear Plastic Bottle | 67% | 80% | 83% |
| Opaque Plastic Bottle | 86% | 90% | 96% |
| Aluminium Beverage Can | 44% | 57% | 81% |
| Steel Food Can | 70% | 76% | 90% |
| Glass Bottle | 81% | 71% | 82% |
| Glass Jar | 66% | 70% | 75% |
| Cardboard Box | 87% | 82% | 88% |
| Paper Cup | 82% | 80% | 89% |

Version 3 was the strongest and most consistent model, with the biggest single improvement seen in Aluminium Beverage Can (44% → 81%).

## Key Findings

- Adding harder, more varied training images and lowering the learning rate over successive versions steadily improved accuracy and stability.
- The model's main confusion was between visually similar classes: clear vs. opaque plastic bottles, aluminium cans vs. steel cans, and glass bottles vs. glass jars.
- Transparent and reflective objects remained the hardest to classify reliably, even in the final version.

## Limitations & Future Work

- Some classes had more training images than others by the final version, which may have introduced a slight imbalance.
- Backgrounds in some images were relatively plain despite efforts to vary lighting and framing.
- Future improvements could include a larger and more diverse real-world image set, and techniques specifically aimed at distinguishing transparent or reflective materials.

## Tools

Google Teachable Machine

## Author

Hafsa Mohamed — Griffith University, Introduction to Artificial Intelligence
