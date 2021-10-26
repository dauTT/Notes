# Debugging

dlv

```
go get github.com/go-delve/delve/cmd/dlv
```





tutorial

[https://golang.cafe/blog/golang-debugging-with-delve.html](https://golang.cafe/blog/golang-debugging-with-delve.html)

example:

```
dlv exec valink cosigner start /home/dau/workspace/dauTT/tendermint-mpc-validator/test/fixture/config_template/mpc/mpx/config.toml

```

Increase print string lenght:

```
# https://stackoverflow.com/questions/52416263/how-do-i-print-the-full-value-of-a-string-variable-in-delve
(dlv) config -list
(dlv) config max-string-len 1000


```
