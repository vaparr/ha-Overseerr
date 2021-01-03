---
title: Overseerr
description: Instructions on how to set up the Overseerr integration in Home Assistant.
ha_category:
  - Sensor
ha_domain: overseerr
---

The `Overseerr` integration monitors data from your [Overseerr](https://overseerr.dev) instance.

## Setup

This component needs to authenticate to your Overseerr instance with either a user `password` or an `api_key`.

To find your `api_key` open the Overseerr web interface. Navigate to **Settings**, you should then be able to see your `api_key`.


## Configuration

If you want to enable this sensor, add the following lines to your `configuration.yaml`:

```yaml
# Example configuration.yaml entry
overseerr:
  host: OVERSEERR_HOST
  username: OVERSEERR_USERNAME
  password: OVERSEERR_PASSWORD
```

{% configuration %}
host:
  description: The hostname or IP Address Overseerr is running on.
  required: true
  type: string
api_key:
  description: Your Overseerr API key. 
  required: true
  type: string
port:
  description: The port Overseerr is running on.
  required: false
  default: 5055
  type: integer
urlbase:
  description: The Base URL path of your Overseerr instance.
  required: false
  type: string
ssl:
  description: Whether or not to use SSL when connecting to Overseerr.
  required: false
  default: false
  type: boolean
{% endconfiguration %}

## Full example for the configuration

```yaml
# Example configuration.yaml entry
overseerr:
  host: 192.168.1.62
  port: 5055
  api_key: MTYwODIpppppppppppppppYzLTI0OqqqqqqqqqqqqzIwLeeeeeee==
```

## Services

### Submit request services

Available services: `submit_movie_request`, `submit_tv_request`

#### Service `submit_movie_request`

Searches and requests the closest matching movie.

| Service data attribute | Optional | Description                                      |
| ---------------------- | -------- | ------------------------------------------------ |
| `name`                 |      no  | Search parameter.                                |                          |

#### Service `submit_tv_request`

Searches and requests the closest matching TV show.

| Service data attribute | Optional | Description                                                                                   |
|------------------------|----------|-----------------------------------------------------------------------------------------------|
| `name`                 |       no | Search parameter.                                                                             |
| `season`               |      yes | Which season(s) to request. Must be one of `first`, `latest` or `all`. Defaults to latest.    |
