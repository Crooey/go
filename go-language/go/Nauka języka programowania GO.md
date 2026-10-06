
1. Instalacja GO na linuxa

Pobieramy paczkę GO https://go.dev/dl/, następnie:
```
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.27.0.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
sudo tar zxvf go1.27.0.linux-386.tar.gz -C /usr/local/
export PATH=$PATH:/usr/local/go/bin
source zsh
export PATH="$PATH:$(go env GOPATH)/bin"
```


No i klasycznie tworzymy nasz pierwszy program Hello World! :)
https://go.dev/doc/tutorial/getting-started#prerequisites

```
mkdir hello
cd hello
```

W instrukcji GO jest uwzględnione, że warto zarządzać swoimi paczkami z modułami zwanymi go.mod, te paczki modułów są trzymane w repozytorium, które zainicjowaliśmy.

```
go mod init example/hello
```

![[Pasted image 20260828144152.png]]

Następnie tworzymy pliczek hello.go, któy będzie sercem naszej aplikacji.

```
nvim hello.go
```

i wklejamy poniższy kod:
```
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

This is your Go code. In this code, you:
- Declare a `main` package (a package is a way to group functions, and it's made up of all the files in the same directory).
- Import the popular [`fmt` package](https://pkg.go.dev/fmt/), which contains functions for formatting text, including printing to the console. This package is one of the [standard library](https://pkg.go.dev/std) packages you got when you installed Go.
- Implement a `main` function to print a message to the console. A `main` function executes by default when you run the `main` package.

Finalnie możemy uruchomić naszą aplikację:
```
go run .
```
![[Pasted image 20260828144552.png]]