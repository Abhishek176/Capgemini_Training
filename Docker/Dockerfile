FROM ubuntu
RUN apt update -y && apt install git -y
Label name = "myappimage"
ENV DB_USER=admin
ENV DB_HOST=192.168.0.0
WORKDIR /demo
#COPY demo.tar .
ADD demo.tar .
RUN useradd test
USER test
EXPOSE <port_no>

FROM busybox
#CMD ["sh"]
ENTRYPOINT ["sh"]




