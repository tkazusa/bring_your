FROM tensorflow/tensorflow:2.0.0a0

RUN pip install sagemaker-containers

# 必要なパッケージをインストールします
# インストールによって生じる不要なファイルは削除します
RUN apt -y update && apt install -y --no-install-recommends \
    wget \
    nginx \
    ca-certificates \
    && apt clean
 
# pythonパッケージをインストールします
# キャッシュファイルは重たいので、削除しておきます
RUN pip install wheel numpy pandas flask gevent gunicorn && \
    rm -rf /root/.cache

# Copies the training code inside the container
COPY tf_codes /opt/ml/code

# Defines train.py as script entry point
ENV SAGEMAKER_PROGRAM train.py
ENV SAGEMAKER_SERVING_MODULE serve:start_server