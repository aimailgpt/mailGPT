# mailGPT
‼️ ⛔️ WARNING THIS CAN CAUSE NUCLEAR FUSION. USE IT AT YOUR OWN RISK.⚠️

Configuration(s) for SPAM/HAM detection model designed to run even on edge devices based on meta’s Llama 3.2.
This repo will document the steps required to run akritrimai/Llama-SH-GPT ( https://ollama.com/akritrimai/Llama-SH-GPT ) on 
different spam detection platforms. 

rspamd:
We are starting with a sample  configuration of rspamd's( https://github.com/rspamd/rspamd ) new experimental GPT plugin. It could be made to interact with varied systems as its openai api compatible through ollama (https://github.com/ollama/ollama). use gpt.conf in appropriate folder on rspamd installation.
The model can be pulled from ollama using:

ollama pull akritrimai/Llama-SH-GPT

Stalwart Mail Server:
https://stalw.art/docs/server/ai-models

```
[enterprise.ai."chat"]
endpoint = "http://127.0.0.1:11434/v1/chat/completions"
model = "akritrimai/Llama-SH-GPT"
type = "chat"
timeout = "2m"
default-temperature = "0.7"
allow-invalid-certs = "true"
headers = [ "X-My-Header: my-value" ]

[enterprise.ai."chat".auth]
token = "ollama"

```

https://stalw.art/docs/spamfilter/llm/

```

[spam-filter.llm]
model = "akritrimai/Llama-SH-GPT"
prompt = "You are an AI assistant specialized in analyzing email content to detect unsolicited, commercial, or harmful messages. Your task is to examine the provided email, including its subject line, and determine if it falls into any of these categories. Please follow these steps:

- Carefully read the entire email content, including the subject line.
- Look for indicators of unsolicited messages, such as:
   * Lack of prior relationship or consent
   * Mass-mailing characteristics
   * Vague or misleading sender information
- Identify commercial content by checking for:
   * Promotional language
   * Product or service offerings
   * Call-to-action for purchases
- Detect potentially harmful content by searching for:
   * Phishing attempts (requests for personal information, suspicious links)
   * Malware indicators (suspicious attachments, urgent calls to action)
   * Scams or fraudulent schemes
- Analyze the overall tone, intent, and legitimacy of the email.
- Determine the most appropriate single category for the email: Unsolicited, Commercial, Harmful, or Legitimate.
- Assess your confidence level in this determination: High, Medium, or Low.
- Provide a brief explanation for your determination.
- Format your response as follows, separated by commas: Category,Confidence,Explanation
  * Example: Unsolicited,High,The email contains mass-mailing characteristics without any prior relationship context.

Here's the email to analyze, please provide your analysis based on the above instructions, ensuring your response is in the specified comma-separated format:"

temperature = "0.7"

separator = ","
categories = ["Unsolicited", "Commercial", "Harmful", "Legitimate"]
confidence = ["High", "Medium", "Low"]

[spam-filter.llm.index]
category = 0
confidence = 1
explanation = 2

[spam-filter.header.llm]
enable = true
name = "X-Spam-LLM"

```

Coming soon on more platforms!!!

for creating a fine tuned model based on your data / needs or platform integrations or for any clarifications 
please contact us: ca@akritrim.in




