sudo docker build . --tag csvanilla
sudo docker run -d -p 27015:27015/udp -p 27015:27015 csvanilla
