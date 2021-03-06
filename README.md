# From Keras to Production

## Daten

https://www.kaggle.com/moltean/fruits

## Notebooks
https://github.com/codecentric/from-keras-to-production-workshop.git

## Images pullen
- docker pull codecentric/from-keras-to-production-baseimage
- docker pull codecentric/tensorflow-serving-baseimage
- docker pull codecentric/jenkins-python-image

## Jupyterlab starten
```bash
docker run -p 8888:8888 --mount type=bind,source=$(pwd)/notebooks,target=/keras2production/notebooks codecentric/from-keras-to-production-baseimage
```

## Jenkins starten
```bash
docker run -p 8080:8080 -p 50000:50000 codecentric/jenkins-python-image
```

## TensorFlow Serving starten
```bash
docker run -p 8501:8501 -p 8500:8500 --mount type=bind,source=$(pwd)/notebooks/6-models/fruits/,target=/models/fruits -e MODEL_NAME=fruits -t tensorflow/serving:1.12.0
```

## Run slides
```bash
pip install -r requirements.txt
cd slides
jupyter nbconvert end2end_ds.ipynb --to slides --post serve --reveal-prefix=reveal.js
```
