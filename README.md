# VicunaWithGUI
This project support a WEB UI with Vicuna13B (using [llama-cpp-python](https://github.com/abetlen/llama-cpp-python), [chatbot-ui](https://github.com/mckaywrigley/chatbot-ui))

# 1. Preview
## 1) Chat-UI (url: `http://localhost:3000/en`)
<img width="1159" alt="image" src="https://user-images.githubusercontent.com/6852711/230879947-3348f405-e529-44b6-88db-49d488467bd4.png">

## 2) 🦙 llama.cpp Python API (url: `http://localhost:8000/docs`)
<img width="1159" alt="image" src="https://user-images.githubusercontent.com/6852711/230880175-cb3710f9-41b5-4df7-9b7c-177d5db136c9.png">

# 2. How to use it?
### 1) Clone this repo
```bash
git clone https://github.com/blackcon/VicunaWithGUI.git
cd VicunaWithGUI
```
### 2) Download model ([eachadea/ggml-vicuna-13b-4bit](https://huggingface.co/eachadea/ggml-vicuna-13b-4bit/tree/main))
```bash
mkdir models
cd models
wget https://huggingface.co/eachadea/ggml-vicuna-13b-4bit/resolve/main/ggml-vicuna-13b-4bit-rev1.bin
```
### 3) Run API server ([llama-cpp-python](https://github.com/abetlen/llama-cpp-python))
```bash
# clone as submodule
cd VicunaWithGUI
git submodule add https://github.com/abetlen/llama-cpp-python.git
git clone https://github.com/ggerganov/llama.cpp.git llama-cpp-python/vendor/llama.cpp

# change head
cd llama-cpp-python/vendor/llama.cpp
git checkout 1d78fecdab4087028a38517e86ed129f077174d8

# setup llama-cpp-python
cd llama-cpp-python
pip3 install scikit-build cmake
pip3 install fastapi sse_starlette uvicorn
python3 setup.py develop

# Run
MODEL=`pwd`/../models/ggml-vicuna-13b-4bit-rev1.bin HOST=127.0.0.1 python3 -m llama_cpp.server
```
### 4) Run chatbot-UI ([chatbot-ui](https://github.com/mckaywrigley/chatbot-ui))
```bash
cd VicunaWithGUI
git submodule add https://github.com/mckaywrigley/chatbot-ui.git

cd chatbot-ui
# install
npm i

# build
npm run build

# run as dev
OPENAI_API_HOST=http://127.0.0.1:8000 OPENAI_API_KEY=blah npm run dev
```

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=blackcon/VicunaWithGUI&type=Date)](https://star-history.com/#blackcon/VicunaWithGUI&Date)
