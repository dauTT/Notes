# update

{% embed url="https://www.jajaldoang.com/post/how-to-update-golang/" %}

#### Remove existing go <a href="#remove-existing-go" id="remove-existing-go"></a>

First, you need to remove your existing golang.

```
sudo rm -rf /usr/local/go
```

If you don’t know where your golang is you can use `which`. It will show you where your `go` is located.

```
which go  
#in my case, it shows /usr/local/go/bin/go
```

You should remove the folder containing `/bin/go`. In my case, I removed `/usr/local/go`.

#### Download latest go version <a href="#download-latest-go-version" id="download-latest-go-version"></a>

Use curl to download the package. If you like to install another version, you can go to [https://golang.org/dl/](https://golang.org/dl/) .

We will download golang instalation package then extract it. It will be extracted to directory **`go`**. So if you already had directory named `go` in your currect directory, you should download it to another directory.\
For Linux:

```
curl -O https://dl.google.com/go/go1.17.1.linux-amd64.tar.gz
```

For Mac:

```
curl -O https://dl.google.com/go/go1.17.1.darwin-amd64.tar.gz
```

#### Extract the package <a href="#extract-the-package" id="extract-the-package"></a>

This will extract the package into folder go and move it to `/usr/local`

```
tar -xvf go1.17.1.linux-amd64.tar.gz
sudo mv go /usr/local
```

You need to update GOROOT if the installation folder is different from the previously installed go.

```
export GOROOT=/usr/local/go
```

#### Verify the installation <a href="#verify-the-installation" id="verify-the-installation"></a>

Use this command to verify that the installation is successful.

```
go version
```

\
