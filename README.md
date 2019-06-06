# Alexa Magento 2 Skill - C&M

> Alexa Magento 2 Skill for [Magento 2](https://magento.com/home-page) and
> [Amazon Alexa](https://developer.amazon.com/alexa).

`Alexa Magento 2 Skill` allows to send requests to a Magento 2 website and
 process reponses using an Amazon Alexa device (such as an Amazon Echo).

> User: "Alexa, demande à magento le nombre de clients connectés"\
> Alexa: "Le nombre de clients et visiteurs en ligne est de 10."

## Installation

### Get the skill

Clone or download this repository:

```
$ git clone git@github.com:ClickAndMortar/alexa-magento2-skill.git
```

### Configure the skill

Edit `skill.json` file to add 
[custom](https://developer.amazon.com/docs/smapi/skill-manifest.html#custom)
[endpoint](https://developer.amazon.com/docs/smapi/skill-manifest.html#endpoint-4)
uri (HTTPS URL of [Alexa Magento 2 Module](https://github.com/ClickAndMortar/magento2-module-alexa) route) and
[sslCertificateType](https://developer.amazon.com/docs/smapi/skill-manifest.html#sslCertificateType-enumeration).

#### Configure the skill with an exposed webserver

For a Magento 2 website available at `https://example.com`
with a certificate from a trusted certificate authority.

Edit `skill.json`:

```json
...
 "apis": {
      "custom": {
        "endpoint": {
          "uri": "https://example.com/alexa/v1.0",
          "sslCertificateType": "Trusted"
        }
      }
    },
...
```

#### Configure the skill with a local webserver

For a Magento 2 website available at `http://localhost:2380`.

Using [ngrok](https://ngrok.com/) for exposing a local webserver:

```bash
ngrok http -host-header=rewrite localhost:2380
```

Get URI to use:

```
Forwarding                    https://<id>.ngrok.io -> localhost:2380 
```

Edit `skill.json`:

```json
...
 "apis": {
      "custom": {
        "endpoint": {
          "uri": "https://<id>.ngrok.io/alexa/v1.0",
          "sslCertificateType": "Wildcard"
        }
      }
    },
...
```

### Deploy Alexa skill

Using [Alexa Skills Kit CLI](https://developer.amazon.com/docs/smapi/quick-start-alexa-skills-kit-command-line-interface.html):

```bash
ask deploy
```
### Install Magento 2 Module

In order to communicate with Alexa device, your Magento 2 must have [Alexa Magento 2 Module](https://github.com/ClickAndMortar/alexa-magento2-module#alexa-magento-2-module).
