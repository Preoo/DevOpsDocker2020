FROM ubuntu
RUN apt-get update && apt-get -y install curl;
COPY website_fetch.sh .
CMD ["bash", "website_fetch.sh"]
