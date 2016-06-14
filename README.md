lpc-atelier-go-2016
===================

`lpc-atelier-go-2016` is a simple repository holding sources for the `Go`
hands-on session of the Atelier `Go`.

## Bootstrapping the work environment

### Installing the `Go` toolchain

The `Go` hands-on session obviously needs for you to install the `Go`
toolchain.

There are 3 ways to do so:
- install `Go` via your favorite package manager (`yum`, `apt-get`,
  `fink`, ...)
- install `Go` via `docker`
- install `Go` manually.

While all 3 methods are valid ones, to reduce the complexity of the
debugging/configuration/OS matrix, we'll only recommend the last one.

#### Installing `Go` manually

This is best explained on the official page:
https://golang.org/doc/install

On linux-64b, it would perhaps look like:

```sh
$ mkdir -p $HOME/atelier-go/root
$ cd $HOME/atelier-go/root
$ curl -O -L https://golang.org/dl/go1.6.2.linux-amd64.tar.gz
$ tar zxf go1.6.2.linux-amd64.tar.gz
$ export GOROOT=$HOME/atelier-go/root/go
$ export PATH=$GOROOT/bin:$PATH

$ which go
${HOME}/atelier-go/root/go/bin/go

$ go version
go version go1.6.2 linux/amd64

$ which godoc
${HOME}/atelier-go/root/go/bin/godoc
```

### Setting up the work environment

Like `python` and its `$PYTHONPATH` environment variable, `Go` uses
`$GOPATH` to locate packages' source trees.
You can choose whatever you like (obviously a directory under which
you have read/write access, though.)
In the following, we'll assume you chose `$HOME/atelier-go/work`:

```sh
$ mkdir -p $HOME/atelier-go/work
$ export GOPATH=$HOME/atelier-go/work
$ export PATH=$GOPATH/bin:$PATH
```

Make sure the `go` tool is correctly setup:

```sh
$ go env
GOARCH="amd64"
GOBIN=""
GOCHAR="6"
GOEXE=""
GOHOSTARCH="amd64"
GOHOSTOS="linux"
GOOS="linux"
GOPATH="$HOME/atelier-go/work"
GORACE=""
GOROOT="$HOME/atelier-go/root/go"
GOTOOLDIR="$HOME/atelier-go/root/go/pkg/tool/linux_amd64"
CC="gcc"
GOGCCFLAGS="-fPIC -m64 -pthread -fmessage-length=0"
CXX="g++"
CGO_ENABLED="1"
```

(on other platforms/architectures, the output might differ
slightly. The important env.vars. are `GOPATH` and `GOROOT`.)

### Testing `go get`

Now that the `go` tool is correctly setup, let's try to fetch some
code.
For this part, you'll need the following tools installed to actually retrieve the code from the repositories:
- `git`

Without further ado:

```sh
$ go get -u -v github.com/sbinet/lpc-atelier-go-2016/cmd/lpc-hello
```

`go get` downloaded (cloned, in `git` speak) the whole
`github.com/sbinet/lpc-atelier-go-2016` repository (under `$GOPATH/src`) and
compiled the `lpc-hello` command.
As the compilation was successful, it also installed the `lpc-hello`
command under `$GOPATH/bin`.

The `lpc-hello` command is now available from your shell:

```sh
$ lpc-hello
Hello LPC-Atelier-Go-2016!

$ lpc-hello you
Hello you!
```

## Setting up your favorite editor

Extensive documentation on how to setup your editor (for code
highlighting, code completion, ...) is available here:

 https://github.com/golang/go/wiki/IDEsAndTextEditorPlugins
 
At the very least, you should try to install and setup `goimports` as
explained here:

 https://godoc.org/golang.org/x/tools/cmd/goimports

`goimports` provides automatic code formating as well as automated
insertion/deletion of used/unused packages (in your `import` package
statements.)

## Documentation

The `Go` programming language is quite new (released in 2009) but
ships already with quite a fair amount of documentation.
Here are a few pointers:

- http://golang.org/doc/code.html
- http://tour.golang.org
- http://golang.org/doc/effective_go.html
- http://dave.cheney.net/resources-for-new-go-programmers
- http://gobyexample.com

For more advanced topics:

- http://talks.golang.org
- http://blog.golang.org
- https://groups.google.com/d/forum/golang-nuts (`Go` community forum)
- the internets. typical queries are `go something` or `golang something`
