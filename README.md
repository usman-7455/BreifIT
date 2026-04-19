# BriefIt — T5 Fine-Tuned Text Summarizer

> Paste long. Get short. Powered by a fine-tuned T5 model.

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://textsummarizer-a28sgatnbwcak775aapwts.streamlit.app/)

---

## What it does

BriefIt takes any long-form text — news articles, blog posts, research snippets — and generates a concise, readable summary using a fine-tuned T5-small model trained on the CNN/DailyMail dataset.

---

## Live Demo

**[Try it here →](https://textsummarizer-a28sgatnbwcak775aapwts.streamlit.app/)**

---

## Model Details

| Property | Value |
|---|---|
| Base Model | `t5-small` |
| Fine-tuned On | CNN/DailyMail 3.0.0 |
| Training Samples | 2,000 articles |
| Eval Samples | 500 articles |
| Epochs | 2 |
| Evaluation Metric | ROUGE (1, 2, L, Lsum) |
| HuggingFace Model | [`zentom/summary_generator_T5_Finetuned`](https://huggingface.co/zentom/summary_generator_T5_Finetuned) |

The model uses beam search (4 beams) with a repetition penalty for cleaner output. Input is prefixed with `summarize:` as required by T5's task-specific format.

---

## Features

- Adjustable summary length (min/max tokens via sliders)
- Compression ratio stats shown after each summary
- Clean Streamlit UI with model info expander
- GPU acceleration if available, CPU fallback otherwise

---

## Run Locally

```bash
git clone https://github.com/your-username/briefit
cd briefit
pip install -r requirements.txt
streamlit run app.py
```

**requirements.txt**
```
streamlit
transformers
torch
sentencepiece
```

---

## Project Structure

```
briefit/
├── app.py                        # Streamlit frontend
├── summarization_assignment.py   # Fine-tuning script
├── requirements.txt
└── README.md
```

---

## Fine-Tuning (Optional)

To retrain the model yourself, run:

```bash
python summarization_assignment.py
```

This will download the CNN/DailyMail dataset, fine-tune T5-small for 2 epochs, and save the model to `./t5-cnn-finetuned`. You can then push it to HuggingFace Hub and update the `model_name` in `app.py`.

---

## Built With

- [Hugging Face Transformers](https://huggingface.co/docs/transformers)
- [Streamlit](https://streamlit.io/)
- [CNN/DailyMail Dataset](https://huggingface.co/datasets/cnn_dailymail)
- [ROUGE Evaluation](https://huggingface.co/spaces/evaluate-metric/rouge)

---

## Author

Made by **Usman** — feel free to fork, star, or open issues.
