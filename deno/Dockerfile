From ubuntu:latest

# install software for deno installation
RUN apt-get update
RUN apt-get install unzip -y
RUN apt-get install curl -y

COPY . .

# install deno
RUN curl -fsSL https://deno.land/x/install/install.sh | sh
ENV DENO_INSTALL="/root/.deno"
ENV PATH="$DENO_INSTALL/bin:$PATH"

RUN deno cache ./mod.ts

CMD deno ./mod.ts

