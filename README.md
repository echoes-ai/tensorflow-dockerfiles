# tensorflow-dockerfiles

Prebuild docker images with TensorFlow

- [tensorflow-cuda-py3.7](/tensorflow-cuda-py3.7)
  
	Packed with `CUDA`, `TensorFlow` GPU version and `Python3.7`.

- [tensorflow-py3.7](/tensorflow-py3.7)

	Based on `python:3.7.3-stretch` with `TensorFlow` pre-installed.


### Install

```sh
$ docker pull echoesai/tensorflow-py3.7:latest 
```

For GPU version

```sh
$ docker pull echoesai/tensorflow-py3.7:latest-gpu
```

### License

[Apache2](/LICENSE)
