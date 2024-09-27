# Implementation Code for "Leveraging Prior Experience: An Expandable Auxiliary Knowledge Base for Text-to-SQL"

## Repository Overview

The `result` folder contains all experimental results. Each subfolder may include the following files:

- **`knowledge_base`**: The knowledge base generated by running LPE-SQL on the full dev set, which includes a correct notebook and a mistake notebook.
- **`train_know.txt`**: Results using the training set with accumulation.
- **`train_noknow.txt`**: Results using the training set without accumulation.
- **`notrain_know.txt`**: Results obtained without using the training set through accumulation.
- **`common_4-shot.txt`**: A fixed set of four handwritten examples.

The `RQ4_result` contain experimental results obtained using Llama-3.1-70B on the dev subset, along with the initial knowledge base files and the dev subset used in the experiments.


## Download BIRD Dataset
First, download the [BIRD dataset](https://drive.google.com/drive/folders/1zcoVq3SZItFaTIc6HA7AR_eMdZqKVjpL?usp=sharing) and save it to the following directory:  
`/LPE-SQL/data/`

## Run Inference
To run inference, you need to add your OpenAI API key in the `gpt_request.py` file. Update the following variables:

```python
api_key = "your_api_key"
base_url = "your_base_url"
```

Then, execute the command below. The predicted SQL queries will be saved to a file named predict_dev.json located in `/LPE-SQL/result/engine (Llama-3.1-70B)`. Additionally, the results will be saved in result.txt found in 
`/LPE-SQL/src/knowledge_base/results/engine (Llama-3.1-70B)`:

```bash
sh run.sh
```

## Run Evaluation
To evaluate the results, use the following command:
```bash
python evaluation_ex.py --path /LPE-SQL/src/knowledge_base/results/engine/result.txt 
```
