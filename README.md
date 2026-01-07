# AI_Tool
Adding extra ai tool in visual studio
You are inside a Docker container (root@2ebfa7037481) — NOT your Ubuntu host system.

Inside a Docker container:

❌ systemctl does NOT exist
❌ nano is usually NOT installed
❌ usermod is not needed
❌ You should NOT install Docker inside Docker



✅ Important: Install & Run Ollama on the HOST Ubuntu — NOT inside a container

Your prompt shows:

root@2ebfa7037481:/home/cidocker/share#

That means you are already inside another Docker container.

👉 Exit the container first

Run:

exit

Now your prompt should look like:

csg@csg-global:~$

If you see this → you are on actual Ubuntu host.



✅ After exiting, do these steps ON THE HOST:

1️⃣ Create Ollama docker folder

mkdir ~/ollama-docker
cd ~/ollama-docker

2️⃣ Install nano (if missing)

sudo apt install nano -y

3️⃣ Create compose file

nano docker-compose.yml

Paste:

version: "3.9"

services:
  ollama:
    image: ollama/ollama:latest
    container_name: ollama
    ports:
      - "11434:11434"
    volumes:
      - ollama_data:/root/.ollama
    restart: unless-stopped

volumes:
  ollama_data:



❗ Why this error happened?

Because:

You were inside a running Docker container
systemctl doesn’t exist inside containers
nano wasn’t installed
usermod commands don’t work normally



✅ Do this now:

Please run this on your machine and send me the output:

whoami
pwd

When you see:

csg@csg-global

then you are in the correct place to install Ollama.

I will guide you from there.








docker compose up -d
 
docker ps
 
ollama list
 
docker exec -it ollama ollama pull deepseek-coder-v2

 
docker exec -it ollama ollama run deepseek-coder-v2

 
docker exec -it ollama ollama list

 
if u want to delete
ollama rm deepseek-r1
 





