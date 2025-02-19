# PEFT-Based Summarization Fine-Tuning

## Project Overview
This project fine-tunes a **dialogue summarization model** using **QLoRA with PEFT**.  
We applied **parameter-efficient fine-tuning (PEFT)** to improve the performance of a base model on summarizing dialogues.

| **Base Model Used** | `TinyLlama/TinyLlama-1.1B-Chat-v1.0` |
|---------------------|---------------------------------------------------|
| **Fine-Tuning Approach** | QLoRA (Quantized Low-Rank Adaptation) |
| **Dataset** | DialogSum a large-scale dialogue summarization dataset |
| **Frameworks** | Hugging Face `transformers`, `PEFT`, `datasets`, `evaluate` |

---

## Model Performance Comparison
| **Metric** | **Original Model** | **Fine-Tuned Model (PEFT)** | **Improvement** |
|------------|------------------|--------------------------|----------------|
| **ROUGE-1** | 0.2292 | **0.2975** | **+6.84%** |
| **ROUGE-2** | 0.0784 | **0.0867** | **+0.83%** |
| **ROUGE-L** | 0.1690 | **0.2603** | **+9.13%** |
| **ROUGE-Lsum** | 0.1899 | **0.2326** | **+4.27%** |

---

## Sample Outputs
| **Dialogue (Input)** | **Human Summary** | **Original Model Summary** | **Fine-Tuned Model Summary** |
|----------------------|------------------|------------------|------------------|
| "Hey! How are you?"<br> "I'm great, thanks!"<br> "Let's meet up later?" | "Two friends greet each other and plan to meet." | "Friends meet." | "Two friends talk and plan a meeting." |

**See the full sample outputs in [`images/`](image**)

---

## **Errors Encountered & Fixes**
| **Error** | **Cause** | **Fix** |
|-----------|----------|--------|
| `adapter_config.json` missing | LoRA adapter was not saved properly | had to change checkpoint to 500 from 1000 |
| `size mismatch in state_dict` | LoRA was trained on `LLaMA`, but `Phi-2` was used | Use the correct base model (`LLaMA`) |
| No training logs | `logging_steps` too high | Reduce `logging_steps=50` as given in assignment |
| GitHub authentication issues | No credential helper | Run `git config --global credential.helper store` |
| Version verification issues | rouge_score didn't have version attribute | Used metadata.version instead |

---

## Hugging Face Model Link
[PEFT Fine-Tuned Model](https://huggingface.co/marlis3)

---
