# Purpose

We depend on the googleplay Go tool for our [research](https://github.com/the-ok-is-not-enough).
However, the tool and its dependency do change repository paths frequently.
Consequently it becomes hard to impossible onboarding people on the developed tooling and its dependencies.
This org is supposed to mitigate this problem and provide a persistent and working snapshot to build googleplay.

All glory goes to its actual developer. We are just librarians.


# Usage

We assume that you have a directory in which you clone both the `googleplay` and the `rosso` repository.

```
googleplay-persistent/
+---------------------googleplay/
+---------------------rosso/
```

1. go into `googleplay-persistent/googleplay/cmd/googleplay/` and run `go build`

```
$> go build
../../../rosso/tls/encoding.go:4:4: missing go.sum entry for module providing package github.com/refraction-networking/utls (imported by github.com/googleplay-persistent/rosso/tls); to add:
	go get github.com/googleplay-persistent/rosso/tls@v1.3.7
../../../rosso/protobuf/encoding.go:4:4: missing go.sum entry for module providing package google.golang.org/protobuf/encoding/protowire (imported by github.com/googleplay-persistent/rosso/protobuf); to add:
	go get github.com/googleplay-persistent/rosso/protobuf@v1.3.7
```

2. install the required dependencies

```
$> go get github.com/googleplay-persistent/rosso/tls@v1.3.7
go: downloading github.com/refraction-networking/utls v1.3.1
go: downloading golang.org/x/crypto v0.7.0
go: downloading github.com/andybalholm/brotli v1.0.5
go: downloading github.com/klauspost/compress v1.16.3
go: downloading golang.org/x/sys v0.6.0

$> go get github.com/googleplay-persistent/rosso/protobuf@v1.3.7
go: downloading google.golang.org/protobuf v1.30.0
```

3. run `go build` again

```
$> go build
// no output expected
```

4. test if the program works

```
$> ./googleplay 
Usage of ./googleplay:
  -d string
    	doc
  -device
    	create device
  -email string
    	your email
  -log int
    	log level (default 1)
  -p int
    	native platform
    	0: x86
    	1: armeabi-v7a
    	2: arm64-v8a
  -passwd string
    	password
  -purchase
    	purchase request
  -s	single APK
  -v uint
    	version code
```

You are now all set.
