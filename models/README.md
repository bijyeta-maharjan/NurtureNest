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
Llama 3 8B Instruct hosted on Tune Studio, guided with few-shot infant-care conversation
examples in [`training/llm_prompt_examples/`](../training/llm_prompt_examples/).
The app calls it through the Tune Studio API (`TUNE_MODEL_ID` in `.env`).
