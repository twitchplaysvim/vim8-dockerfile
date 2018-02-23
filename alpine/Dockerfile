FROM alpine:3.7 as builder
LABEL maintainer="Peter Meehan <meehanp2@tcd.ie>"

RUN apk add --no-cache alpine-sdk git ncurses-dev

RUN git clone https://github.com/vim/vim.git

WORKDIR /vim

RUN make
RUN make install

########################################

FROM alpine:3.7
LABEL maintainer="Peter Meehan <meehanp2@tcd.ie>"

RUN apk add --no-cache ncurses-libs

WORKDIR /usr/local/bin
COPY --from=builder /usr/local/bin/vim .

WORKDIR /tmp

CMD ["vim"]
