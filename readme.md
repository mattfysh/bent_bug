# description

when the XREADGROUP command fails, the benthos stream enters an infinite loop without a backoff. this causes a lot of pressure on the redis db.

while having this loop running in prod for ~3 hours, it managed to generate:

* nearly 1 million redis commands (XGROUP, XREADGROUP, HELLO, PING)
* ~4.3GB of data transfer

# reproduce

Run `docker compose up`
