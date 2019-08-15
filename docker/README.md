# Docker folder for geohackweek misc

Build docker image:

```
docker build -t conda_ghw:latest .
```

For activating bob:

``` bash
docker run -it -u bob -w "/home/bob" --rm --name ghw_bob conda_ghw19:latest /bin/bash
```

Bob commands:
- `pip install pipenv`
- `mkdir geoproject`
- `cd geoproject`
- `vi requirements.txt`
  ```
  ipython
  requests
  fiona
  gdal
  netCDF4
  ```
- `cat requirements.txt`
- `pipenv install -r requirements.txt`

For activating sandy:

``` bash
docker run -it -u sandy -w "/home/sandy" --rm --name ghw_sandy conda_ghw19:latest /bin/bash
```

Sandy commands:
- `export PATH="$HOME/miniconda/bin:$PATH"`
- `conda --version`
- `mkdir geoproject`
- `cd geoproject`
- `vi environment.yml`
  ```
  name: geoproj
  channels:  
  - conda-forge
  dependencies:
  - python=3.6
  - ipython
  - requests
  - fiona
  - gdal
  - netCDF4
  ```
- `cat environment.yml`
- `conda env create -f environment.yml`
- `source activate geoproj`
- `gdalinfo --version`
- `ogr2ogr --version`
