# bring_your_own_containers

## 不明なポイント
[ホスティングサービスでの独自の推論コードの使用](https://docs.aws.amazon.com/ja_jp/sagemaker/latest/dg/your-algorithms-inference-code.html) で、推論時には、
```
docker run image serve
```
で、コンテナを実行するって言ってる。
きっと、Dockerfileの`WORKINGDIR`に紐付いているはず。
```
WORKDIR /opt/program
```

一方で、
[エントリポイントを定義するために Amazon SageMaker コンテナによって使用される環境変数](https://docs.aws.amazon.com/ja_jp/sagemaker/latest/dg/docker-container-environmental-variables-entrypoint.html)
でエントリポイント設定するって言ってる。

- docker run image serve 実行するのか、 SAGEMAKER_SERVING_MODULE で指定したエントリポイントが実行されるのかどっち？
- SAGEMAKER_SERVING_MODULE の
## 参考
- [開始方法: Amazon SageMaker コンテナを使用して Python スクリプトを実行する](https://docs.aws.amazon.com/ja_jp/sagemaker/latest/dg/build-container-to-train-script-get-started.html)



