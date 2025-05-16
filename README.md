<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  
</head>
<body>

  <h1>Arabic Text-to-SQL Using LoRA Fine-Tuning</h1>

  <p><strong>Author:</strong> Mahmoud Aymann</p>

  <p>
    This project demonstrates how to translate Arabic natural language questions into executable SQL queries using a fine-tuned Transformer-based model. The training process includes parsing a custom dataset, formatting data for instruction tuning, and applying parameter-efficient LoRA fine-tuning to a pretrained language model like Mistral-7B.
  </p>

  <h2>🔗 Dataset</h2>
  <p>
    You can access the Arabic Text-to-SQL dataset used in this project from the following Google Drive link:<br>
    <a href="https://drive.google.com/drive/folders/1FlxJI3wPp9W5V_Bl8vc8-wdkfi9pS-qt?usp=sharing" target="_blank">
      Arabic Text-to-SQL Dataset
    </a>
  </p>

  <h2>📁 Project Structure</h2>
  <ul>
    <li><strong>Data Loading:</strong> Loads `.jsonl` files with Arabic questions and SQL queries.</li>
    <li><strong>Schema Extraction:</strong> Reads SQLite databases to extract table-column structures for each `db_id`.</li>
    <li><strong>Preprocessing:</strong> Converts data to chat-style format suitable for instruction tuning.</li>
    <li><strong>Training:</strong> Fine-tunes a base LLM (e.g., Mistral) using LoRA and Hugging Face’s `trl` library.</li>
    <li><strong>Inference:</strong> Accepts Arabic prompts and generates corresponding SQL queries.</li>
  </ul>

  <h2>🛠️ Technologies Used</h2>
  <ul>
    <li>Python, pandas, sklearn</li>
    <li>SQLite3</li>
    <li>Hugging Face Transformers and Datasets</li>
    <li>PEFT and LoRA (parameter-efficient fine-tuning)</li>
    <li>Transformers Reinforcement Learning (trl) library</li>
  </ul>

  <h2>⚙️ Model Loading (Example)</h2>
  <pre><code>
from transformers import AutoModelForCausalLM, AutoTokenizer
model_name = "mistralai/Mistral-7B-v0.1"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForCausalLM.from_pretrained(model_name, device_map="auto", load_in_4bit=True)
  </code></pre>

  <h2>💡 Example Usage</h2>
  <pre><code>
Arabic: كم عدد رؤساء الأقسام الذين تزيد أعمارهم عن 56 سنة؟
Generated SQL: SELECT COUNT(*) FROM heads WHERE age &gt; 56;
  </code></pre>

  <h2>📦 Output</h2>
  <ul>
    <li>train.jsonl</li>
    <li>val.jsonl</li>
    <li>Fine-tuned model saved at: <code>/kaggle/working/mistral-finetuned-ar2sql</code></li>
  </ul>

  <h2>📌 Notes</h2>
  <ul>
    <li>Ensure you mount or access the appropriate SQLite database files when evaluating generated SQL queries.</li>
    <li>This project is a proof-of-concept for Arabic natural language interfaces to databases.</li>
  </ul>

  <h2>📜 License</h2>
  <p>MIT License or any preferred open license you choose.</p>

</body>
</html>
