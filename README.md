# mailGPT
rspamd configuration for SPAM/HAM detection model designed to run even on edge devices based on meta’s Llama 3.2
gpt {
  enabled = true; # Enable the plugin
  type = "openai";
  api_key = "your_api_key_here";
  model = "gpt-3.5-turbo";
  max_tokens = 500;
  temperature = 0.6;
  top_p = 0.8;
  timeout = 15s;
}
