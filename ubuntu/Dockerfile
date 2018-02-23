FROM ubuntu:xenial as builder
LABEL maintainer="Peter Meehan <meehanp2@tcd.ie>"

RUN apt update -y
RUN apt install -y git make gcc libncurses5-dev

RUN git clone https://github.com/vim/vim.git

WORKDIR /vim

RUN make
RUN make install

########################################

FROM ubuntu:xenial
LABEL maintainer="Peter Meehan <meehanp2@tcd.ie>"

RUN apt update -y
RUN apt install -y libncurses5-dev

WORKDIR /usr/local/bin
COPY --from=builder /usr/local/bin/vim .

WORKDIR /tmp

CMD ["vim"]
