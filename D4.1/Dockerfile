FROM ubuntu:24.04

RUN apt update
RUN apt install -y pandoc python3 python3-venv python3-natsort texlive-luatex unzip wget
COPY install_quarto.sh /
RUN /install_quarto.sh
RUN quarto install chrome-headless-shell

WORKDIR /D4.1
