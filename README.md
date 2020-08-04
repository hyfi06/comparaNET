# ComparaNET

## Install

### Virtual environment

Create environment

```bash
python3 -m venv venv
```

Initialization environment

```bash
source venv/bin/activate
```

### Install dependencies

```bash
pip3 install -r requirements.txt
```

### Crate Kernel ipython

```bash
ipython kernel install --user --name=comparaNET
```

### Install docker db

```bash
docker volume create dbmongo
docker run -d -p 27018:27017 --mount src=dbmongo,dst=/data/db --name db mongo
```

### Download data

Download data [here](https://datos.gob.mx/busca/dataset/concentrado-de-contrataciones-abiertas-de-la-apf-shcp/resource/aa36c461-a1d3-4373-bfb5-ca479ed86f26?inner_span=True).

Unzip `contratacionesabiertas_bulk.json`

### Load data in mongodb

```bash
mongoimport --host localhost --port 27018 --db comparanet --collection contrataciones --file contratacionesabiertas_bulk.json --jsonArray
```

## Run

```bash
jupyter-notebook &
```

Select _comparaNET_ kernel

```bash
docker run -d --name db mongo:comparaNET
```
