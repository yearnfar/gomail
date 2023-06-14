# Gomail
[![Code Coverage](http://gocover.io/_badge/github.com/yearnfar/gomail)](http://gocover.io/github.com/yearnfar/gomail) [![Documentation](https://godoc.org/github.com/yearnfar/gomail?status.svg)](https://godoc.org/github.com/yearnfar/gomail)

## Introduction

Gomail is a simple and efficient package to send emails. It is well tested and
documented.

Gomail can only send emails using an SMTP server. But the API is flexible and it
is easy to implement other methods for sending emails using a local Postfix, an
API, etc.

It requires Go 1.18 or newer.


## Features

Gomail supports:
- Attachments
- Embedded images
- HTML and text templates
- Automatic encoding of special characters
- SSL and TLS
- Sending multiple emails with the same SMTP connection


## Documentation

https://godoc.org/github.com/yearnfar/gomail


## Download

    go get github.com/yearnfar/gomail


## Examples

See the [examples in the documentation](https://godoc.org/github.com/yearnfar/gomail#example-package).


## FAQ

### x509: certificate signed by unknown authority

If you get this error it means the certificate used by the SMTP server is not
considered valid by the client running Gomail. As a quick workaround you can
bypass the verification of the server's certificate chain and host name by using
`SetTLSConfig`:

    package main

    import (
    	"crypto/tls"

    	"github.com/yearnfar/gomail"
    )

    func main() {
    	d := gomail.NewDialer("smtp.example.com", 587, "user", "123456")
    	d.TLSConfig = &tls.Config{InsecureSkipVerify: true}

        // Send emails using d.
    }

Note, however, that this is insecure and should not be used in production.



## License

[MIT](LICENSE)

