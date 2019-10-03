FROM tensorflow/tensorflow:2.0.0a0

RUN pip install sagemaker-containers

# 必要なパッケージをインストールします
# インストールによって生じる不要なファイルは削除します
RUN apt -y update && apt install -y --no-install-recommends \
    wget \
    python3-distutils \
    nginx \
    ca-certificates \
    && apt clean
 
# pythonパッケージをインストールします
# キャッシュファイルは重たいので、削除しておきます
RUN wget https://bootstrap.pypa.io/get-pip.py && python3 get-pip.py && \
    pip install wheel numpy scipy scikit-learn pandas lightgbm flask gevent gunicorn && \
    rm -rf /root/.cache

# Copies the training code inside the container
COPY tf_codes /opt/ml/code

# Defines train.py as script entry point
ENV SAGEMAKER_PROGRAM train.py
ENV SAGEMAKER_SERVING_MODULE serve.py