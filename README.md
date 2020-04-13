# newest-deno-in-docker-setup
While changes in deno are very frequent, this docker setup makes sure you are on the newest version

## Usage

To run your code in docker use

```
sudo docker-compose up --build
```

## Dont install deno every rebuild

If you want quicker build times or decide when a new version of deno should be installed, move the deno install section before copy like this:

```
From ubuntu:latest

# install software for deno installation
RUN apt-get update
RUN apt-get install unzip -y
RUN apt-get install curl -y

# install deno
RUN curl -fsSL https://deno.land/x/install/install.sh | sh
ENV DENO_INSTALL="/root/.deno"
ENV PATH="$DENO_INSTALL/bin:$PATH"

COPY . .

RUN deno cache ./mod.ts

CMD deno ./mod.ts
```

Now when you want to get a new deno installation you have to manually run:

```
sudo docker-compose build --no-cache deno 
```