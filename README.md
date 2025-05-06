# Chatbot-using-Custom-Dataset


📖 **Overview**

This project features a multilingual chatbot trained with data in Hindi, English, and Telugu. It is built using a small dataset of 3,000 question-answer pairs, and it's designed to respond accurately across these three languages. The model leverages advanced techniques like LoRA adapters (PEFT) and FP16 training for efficient fine-tuning. The full dataset is private, but a sample of 10 examples is included to showcase the structure and functionality.

⚙️ **Features**

- **Multilingual**: English, Hindi & Telugu
- **Rephrasings**: 5 variants per base question
- **Lightweight**: LoRA adapters for efficient fine‑tuning
- **Colab‑Ready**: End‑to‑end in a Google Colab notebook

## 🚀 Getting Started  
1. Open the Google Colab notebook using the following link:
   - [Chatbot Colab Notebook](https://colab.research.google.com/drive/1S48XvO5IoUBHUBLIv56x0AN-uZhVOauv?authuser=1#scrollTo=jLXdvwm4alel)
2. Install the required dependencies by running the cell in the first section of the notebook.
   *Note: The necessary packages are listed in the notebook itself in the first cell. You don't need to install anything manually unless you face an issue.*
3. Run all cells to preprocess the sample data, fine‑tune on the demo set, and execute tests.

## 🛠️ Data Configuration  
- **Private Dataset**: 3,000 examples (not included).  
- **Sample Dataset**: 10 examples in `sample_data/sample.jsonl` to showcase format.

## 🔄 Notebook Contents   
- **Training**: LoRA‑based fine‑tuning on the sample dataset (FP16, gradient checkpointing).  
- **Validation**: This repo does **not** include a validation split to simplify adapter tuning.  
- **Model Saving**: Exports LoRA adapter weights to your Colab Drive.  

## 🏋️‍♀️ Training & Zero‑Loss Explanation  
During Colab training you may observe repeated logged loss values of `0.000000`. This could be due to:

1. **FP16 rounding**: Very small loss values might be rounded to zero, especially in FP16 training.
2. **Data predictability**: The prompt/response pairs might be very similar or repetitive, causing fast convergence and very small loss values.

This does not indicate any issues with the model. For confirmation of its correct behavior, please refer to the final cell of the notebook, where you can see real sample outputs.

## 📝 Sample Execution  
The final cell in the Colab notebook demonstrates real‑time testing using questions from your college, with three tiers of handling to reduce hallucination and improve accuracy:

1. **Exact Match**: Direct lookup in the sample mapping.  
2. **Semantic Search**: Uses SentenceTransformer “all‑MiniLM‑L6‑v2” embeddings to find the closest existing question (similarity threshold configurable).  
3. **Fallback Generation**: T5 generation with beam search, repetition and length penalties to produce an answer if no match is found.

## 🤝 Contributing  
Contributions welcome! Feel free to fork, add more sample questions or evaluation metrics.

## 📄 License  
This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.  
