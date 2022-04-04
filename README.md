<h1 align="center">
  <br>
  <a href="https://www.energyweb.org/"><img src="https://www.energyweb.org/wp-content/uploads/2019/04/logo-brand.png" alt="EnergyWeb" width="150"></a>
  <br>
  EnergyWeb Rosetta API
  <br>
  <br>
</h1>

A Rosetta implementation for the [Energy Web Chain](https://energyweb.org)

# Overview
The Energy Web Chain (EW Chain) Rosetta API implementation allows you to quickly and easily launch a local EW Chain node and begin interacting with EW Chain using the standardized Rosetta API. This Rosetta implementation facilitates querying EW Chain (Data API) and generating and submitting blockchain transactions (Construction API).

## More on Rosetta:
* [Rosetta Overview](https://www.rosetta-api.org/)
* [Specifications](https://github.com/coinbase/rosetta-specifications)
* [Reference Go Implementation](https://github.com/coinbase/rosetta-sdk-go)
* [Rosetta CLI](https://github.com/coinbase/rosetta-cli)

# RPC endpoints

# Build / Run

Energyweb Rosetta API requires synchronized EWC (or Volta) archive node with tracing module enabled

## Local

Use template `.env.example.ewc` or `.env.example.volta` and rename it to `.env` 

```
yarn
yarn build
yarn start
```

## rosetta-cli validation

1. Volta

.env configuration

```shell
BLOCKCHAIN=ewc
NETWORK=volta
WEB3_PROVIDER_URL=<volta web3 archive node with tracing>
```

```shell
rosetta-cli check:data --configuration-file volta.json
rosetta-cli check:construction --configuration-file volta.json
```
2. EWC

.env configuration

```shell
BLOCKCHAIN=ewc
NETWORK=mainnet
WEB3_PROVIDER_URL=<mainnet web3 archive node with tracing>
```

```shell
rosetta-cli check:data --configuration-file mainnet.json
rosetta-cli check:construction --configuration-file mainnet.json
```

## Docker deployment example

1. Build container using Dockerfile

```shell
docker build -t nodeapi:1.0.0 -f Dockerfile .
```

2. Go to configs and use template `.env.example.ewc` or `.env.example.volta` and rename it to `.env`. 
3. Go to /configs/OE folder and use template `chainspec.json.ewc` or `chainspec.json.volta` and rename it to `chainspec.json`.

4. Use docker-compose to run both rosetta API and blockchain node. 

```shell
docker-compose up -d
```

5. Validate whether openethereum node and rosetta api are working correctly

```shell
docker-compose logs openethereum
docker-compose logs rosetta
```
