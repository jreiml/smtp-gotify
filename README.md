# SMTP to Gotify

[![MIT Licensed](https://img.shields.io/github/license/jreiml/smtp-gotify)](https://github.com/jreiml/smtp-gotify/blob/main/LICENSE)
[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/smtp-gotify)](https://artifacthub.io/packages/search?repo=smtp-gotify)

`smtp-gotify` is a small program which listens for SMTP and sends
all incoming Email messages to your Gotify server. It is an updated and maintained version of 
[scott-8/smtp-gotify](https://github.com/scott-8/smtp-gotify). 
The image is rebuilt every week and published to [quay.io](https://quay.io/repository/reiml/smtp-gotify).

Say you have a software which can send Email notifications via SMTP.
You may use `smtp-gotify` as an SMTP server so
the notification mail can be sent to a Gotify app.

## Getting started
You can use `smtp-gotify` with either Docker or Helm. 

### Helm
These [helm charts](https://github.com/jreiml/smtp-gotify-helm) can be used to deploy this on a Kubernetes cluster.

### Docker
Starting a docker container:

```
docker run \
    --name smtp-gotify \
    --restart=always
    -e GOTIFY_URL=<SERVER_URL> \
    -e GOTIFY_TOKEN=<APP_TOKEN1>,<APP_TOKEN2> \
    -p 2525:2525 \
    quay.io/reiml/smtp-gotify
```

The variable `GOTIFY_URL` should be in the form `http[s]://example.com[:port]/`.

A few other environmental variables that can be optionally specified:
`GOTIFY_PRIORITY`, `GOTIFY_TITLE_TEMPLATE`, and `GOTIFY_MESSAGE_TEMPLATE`.

Assuming that your Email-sending software is running in docker as well,
you may use `smtp-gotify:2525` as the target SMTP address.
No TLS or authentication is required.
