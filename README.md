# VicunaWithGUI
This project support a WEB UI with Vicuna13B (using llama-cpp-python, chatbot-ui)

# How to use it?
### Clone this repo
```bash
git clone https://github.com/blackcon/VicunaWithGUI.git
cd VicunaWithGUI
```
### Download model ([eachadea/ggml-vicuna-13b-4bit](https://huggingface.co/eachadea/ggml-vicuna-13b-4bit/tree/main))
```bash
mkdir models
cd models
wget https://huggingface.co/eachadea/ggml-vicuna-13b-4bit/resolve/main/ggml-vicuna-13b-4bit-rev1.bin
```
### Run API server ([llama-cpp-python](https://github.com/abetlen/llama-cpp-python))
```bash
# clone as submodule
cd VicunaWithGUI
git submodule add https://github.com/abetlen/llama-cpp-python.git
git clone https://github.com/ggerganov/llama.cpp.git llama-cpp-python/vendor/llama.cpp

# setup llama-cpp-python
cd llama-cpp-python
pip3 install scikit-build cmake
python3 setup.py develop

# Run
MODEL=`pwd`/../models/ggml-vicuna-13b-4bit-rev1.bin HOST=127.0.0.1 python3 -m llama_cpp.server
```
### Run chatbot-UI ([chatbot-ui](https://github.com/mckaywrigley/chatbot-ui))
```bash
cd VicunaWithGUI
git submodule add https://github.com/mckaywrigley/chatbot-ui.git

cd chatbot-ui
# install
npm i

# run
OPENAI_API_HOST=http://127.0.0.1:8000 npm run dev
```
