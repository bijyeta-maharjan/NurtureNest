# Models

## `cry-classifier/`
A `facebook/wav2vec2-base` model fine-tuned for 5-class infant cry classification
(belly pain, burping, discomfort, hungry, tired) on the [Donate-a-Cry corpus](../data/donateacry/).

This folder contains the model and processor configuration. The weights file
(`model.safetensors` / `pytorch_model.bin`, ~360 MB) is too large for the repository.
To recreate it, run from the repository root:

```bash
python training/train_cry_classifier.py
```

This saves the weights into `models/cry-classifier/`, where the app loads them.

Label order (alphabetical, from the dataset folder names):
`0 belly_pain · 1 burping · 2 discomfort · 3 hungry · 4 tired`

## Parenting-advice LLM
Llama 3 8B Instruct, fine-tuned on the conversation examples in
[`training/llm_finetune_data/`](../training/llm_finetune_data/) and hosted on Tune Studio.
The app calls it through the Tune Studio API (`TUNE_MODEL_ID` in `.env`).
