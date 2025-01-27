# Installing a Local AI Server w/ Ollama
In today's digital landscape, exploring Artificial Intelligence (AI) is more accessible than ever before! Whether you're a developer looking to experiment while keeping your data private or someone curious about using Large Language models w/o the overhead of cloud-based solutions, setting up a local AI server can prove to be very useful.
  
This guide walks you through installing an AI server hosted locally on your computer (use w/o wifi!) using Windows Subsystem for Linux (WSL), Docker, Ollama, & WebUI.

# Set up WSL
  1. Install WSL using
```
wsl --install
```
  3. Run
```
sudo apt update
```
```
sudo apt upgrade -y
```

# Download & Install Ollama
  1. Download & Install Ollama
```
curl -fsSL http://ollama.com/install.sh | sh
```
  3. Install Ollama3 or other LLM
```
ollama pull llama3
```
```
ollama pull deepseek-r1
```
```
sudo apt-get update 
```

# Set up Docker
  1. Update the system's package list and add Docker's GPG key
```
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc 
```

  2. Create a a new repository with Docker's signature and update
```
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

  3. Install Docker and its Related Tools
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

# Run Open WebUI Docker Container
```
docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

# Perfect!
  By following these steps, you should have successfully set up a local AI server! Forge ahead and experiment with these Language models w/o chat limits, wifi or having to pay a premium for chatGPT 👀. 
  You can download all kinds of different models available on Ollama to play around with but if you found this helpful, feel free to comment or contribute!
