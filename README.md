# vLLM-Bento
BentoML deployment of vLLM served models

## Reference Repository
All codes from this repository are adapted from [Self-host Llama 3.1 3B Instruct with vLLM and BentoML example from BentoML](https://github.com/bentoml/BentoVLLM/tree/main/llama3.2-3b-instruct)

## To get started
Spin up a colab instance with a T4 GPU. 

Clone this repository: 
`git clone https://github.com/tituslhy/vLLM-Llama3.2-Bento.git`

Open a terminal and type:
`pip install -r requirements.txt`

Export your HuggingFace API key:
`EXPORT HUGGINGFACE_API_KEY=...`

In your terminal, run:
`python service.py`

In your colab notebook, run the following codes:
```
import os
from google.colab import userdata

ngrok_auth_token = userdata.get('NGROK_AUTH_TOKEN')
```

```
!ngrok config add-authtoken {ngrok_auth_token}
```

```
from pyngrok import ngrok
from IPython.display import display, Markdown

port = 3000
# Open a ngrok tunnel to the HTTP server
public_url = ngrok.connect(port).public_url
display(Markdown((f" * ngrok tunnel \"{public_url}\" -> \"http://127.0.0.1:{port}\"")))
```

Your vLLM is now accessible via the public_url.