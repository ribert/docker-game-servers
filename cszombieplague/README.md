sudo docker build . --tag cszombieplague
sudo docker run -d -p 27013:27013/udp -p 27013:27013 cszombieplague
