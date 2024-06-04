# Sovereign Data-at-Rest (DAR) Sensor: Docker Compose-based Deployment

## Prerequisites

To deploy the Soveren DAR Sensor, you need the following:
* A working Docker Compose installation.
* A token for the sensor to authenticate and authorize it with Soveren Cloud. Here's how to create one: [Managing Sensors - Data at Rest (DAR)](https://docs.soveren.io/en/stable/administration/managing-sensors/#data-at-rest-dar).

## Configuration

You can configure the sensor either by setting the appropriate environment variables or by specifying them in the `.env` file. Below we describe how to use the `.env` file.

### Token

The Soveren Cloud will authenticate and authorize the sensor using the specific token assigned to it.
You configure the token value in the `SVRN_CRAWLER_STATSCLIENT_TOKEN` variable.

### Connecting to data sources 

You should configure the sensor to connect to the data sources by providing specific parameters.

#### S3

Available configuration parameters are described here: https://docs.soveren.io/en/stable/administration/configuring-sensor/#s3-buckets. If you want to enable S3 buckets scanning, provide all necessary options as a JSON string without line breaks.

A minimal example configuration is:

```dotenv
S3_CRAWL_STRING="[{\"accesskeyid\":\"\",\"secretaccesskey\":\"\"}]"
```

#### Kafka

Available configuration parameters are described here: https://docs.soveren.io/en/stable/administration/configuring-sensor/#kafka_1. If you want to enable Kafka scanning, provide all necessary options as a JSON string without line breaks.

A minimal example configuration is:

```dotenv
KAFKA_STRING="[[{\"instancename\":\"KAFKA INSTANCE NAME\", \"brokers\":[\"\"],\"tls\":\"false\",\"tlsconfig\":{\"insecureskipverify\":\"true\"},\"sasl\":\"false\"}]]"
```

#### Databases

Available configuration parameters are described here: https://docs.soveren.io/en/stable/administration/configuring-sensor/#databases. If you want to enable database scanning, provide all necessary options as a JSON string without line breaks.

An example configuration is:

```dotenv
DATABASE_POSTGRES_STRING="[{\"name\":\"DATABASE NAME\",\"connectionstring\":\"postgresql://user:password@netloc:port/dbname\"}]"
```

## Further reading

The detailed documentation on using Soveren is available here: https://docs.soveren.io/en/stable/user-guide/

The release notes for the Soveren DAR Sensor is available here: https://github.com/soverenio/helm-charts/blob/master/charts/soveren-dar-sensor/release-notes.md