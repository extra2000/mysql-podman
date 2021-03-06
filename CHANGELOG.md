# Changelog

## [2.0.0](https://github.com/extra2000/mysql-podman/compare/v1.0.1...v2.0.0) (2022-06-22)


### ⚠ BREAKING CHANGES

* **pod:** MySQL image has changed from `docker.io/mysql:8.0` to `docker.io/mysql/mysql-server:8.0`

### Code Refactoring

* **pod:** change image to `docker.io/mysql/mysql-server:8.0` ([fbc545f](https://github.com/extra2000/mysql-podman/commit/fbc545fe73a5179170a986caa897ab6c7d991987))


### Documentations

* **config:** disable X protocol by default ([64b705d](https://github.com/extra2000/mysql-podman/commit/64b705d4df99b1c11522e9770f8bd0a4bd6aec44))
* **deployment:** add workaround for Raspberry Pi ([fe5213f](https://github.com/extra2000/mysql-podman/commit/fe5213f3c684636a863ea188d67bd32cee3fa524))

### [1.0.1](https://github.com/extra2000/mysql-podman/compare/v1.0.0...v1.0.1) (2022-03-07)


### Documentations

* **custom.cnf:** disable `performance_schema` to reduce RAM usage ([c33b328](https://github.com/extra2000/mysql-podman/commit/c33b328ab3be5ba22473ceb5d6610dd07bf0a6bd))
* **custom.cnf:** minimize MySQL RAM as possible ([53f03d1](https://github.com/extra2000/mysql-podman/commit/53f03d135fb84854b9b5d04d0e6235175c799bb7))
* **deployments:** fix permission for `custom.cnf` ([684e64e](https://github.com/extra2000/mysql-podman/commit/684e64e3a04ab194800ef20e6e2ae3b4cda1d14d))

## 1.0.0 (2022-02-23)


### Features

* initial implementations ([33a1d20](https://github.com/extra2000/mysql-podman/commit/33a1d205f24f17dfa8dfb98895541e4363d8763e))


### Documentations

* **README:** update `README.md` ([5d5ad58](https://github.com/extra2000/mysql-podman/commit/5d5ad5841edfb4cfac3a915e7bce68f4a6a948f3))


### Continuous Integrations

* add AppVeyor with `semantic-release` ([50693d2](https://github.com/extra2000/mysql-podman/commit/50693d295a96098d62051b4d274cefadbc9e5b30))
