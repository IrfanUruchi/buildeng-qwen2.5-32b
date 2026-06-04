# buildeng-qwen2.5-32b

BuildEng V8 32B is the main large-scale training branch of my BuildEng project, based on Qwen2.5-32B-Instruct.

This repository is focused on the training-side work around the project, including dataset generation, dataset preparation, validation, testing, and release preparation. The actual model weights are hosted separately on Hugging Face.

BuildEng is a domain-focused engineering language model project aimed mainly at civil engineering, structural reasoning, construction workflows, field diagnostics, and conservative engineering-assistant behavior. The goal is not to make a model that sounds confident in every answer, but one that handles engineering questions with more care when safety, inspections, uncertainty, or missing information are involved.

## BuildEng Philosophy

BuildEng is trained to be conservative by default. It should avoid unsupported structural approval, separate symptoms from diagnosis, request missing information, and recommend inspection or qualified engineering review when a condition may involve structural risk.

This is especially important for engineering tasks where a confident but wrong answer can be worse than no answer.

## Dataset

The model was trained using the BuildEng V8 final dataset.

Dataset repository:

```text
https://huggingface.co/datasets/Irfanuruchi/buildeng
```

The final dataset contains 145,117 validated engineering instruction samples.

The dataset was built around civil and structural engineering workflows, including beams, slabs, columns, footings, retaining walls, load paths, foundation settlement, soil reasoning, construction sequencing, temporary bracing, renovation unknowns, waterproofing failures, inspection workflows, uncertainty handling, contradiction handling, cause-versus-symptom separation, repair logic, multi-turn engineering diagnosis, and adversarial engineering prompts.

Some building systems topics are also included, such as HVAC airflow and duct reasoning, but the main direction of this branch is civil, structural, and construction engineering behavior.

## Training

The 32B model was fine-tuned from Qwen2.5-32B-Instruct using QLoRA.

Training setup:

```text
Base model: Qwen/Qwen2.5-32B-Instruct
Dataset size: 145,117 samples
Training method: QLoRA
LoRA rank: 32
LoRA alpha: 64
Sequence length: 4096
Precision: bf16
Hardware: NVIDIA A100 80GB
```

The training pipeline used vanilla Transformers, PEFT, TRL, and bitsandbytes.

The full 32B production training script used for the final BuildEng V8 training run is not included in this repository. This repository is intended to document the dataset and project workflow rather than provide a complete one-command reproduction of the final large-scale cloud training environment.

## Repository Contents

This repository is intended to contain the supporting code and documentation for the BuildEng 32B project, including dataset generation scripts, dataset formatting scripts, validation scripts, testing scripts, and merge/release preparation workflows.

The goal is to keep this repository as a clean engineering record of the project instead of a dump of temporary experiment files.

## Hugging Face Releases

Main merged model:

```text
https://huggingface.co/Irfanuruchi/qwen2.5-32b-buildeng
```

Dataset:

```text
https://huggingface.co/datasets/Irfanuruchi/buildeng
```

## Model Releases

Main merged model:

```text
https://huggingface.co/Irfanuruchi/qwen2.5-32b-buildeng
```

Dataset:

```text
https://huggingface.co/datasets/Irfanuruchi/buildeng
```

GGUF releases:

```text
Q4_K_M
https://huggingface.co/Irfanuruchi/qwen2.5-32b-buildeng-GGUF-Q4_K_M

Q5_K_M
https://huggingface.co/Irfanuruchi/qwen2.5-32b-buildeng-GGUF-Q5_K_M

Q6_K
https://huggingface.co/Irfanuruchi/qwen2.5-32b-buildeng-GGUF-Q6_K

Q8_0
https://huggingface.co/Irfanuruchi/qwen2.5-32b-buildeng-GGUF-Q8_0

F16
https://huggingface.co/Irfanuruchi/qwen2.5-32b-buildeng-GGUF-F16
```



## Dedication

This project is dedicated to my father for his birthday.

He is a civil and building engineer, and one of the main reasons I chose engineering myself. BuildEng connects my work in computer engineering and AI with the engineering world that inspired me growing up.

> “My father is the engineer I looked up to long before I understood what engineering really meant.”

## Important Notice

BuildEng is not a licensed engineer and must not be used as final engineering approval, design certification, construction sign-off, or replacement for professional review.

It is intended for research, education, drafting support, engineering-assistant workflows, and preliminary reasoning only.

## License

Apache-2.0
****
