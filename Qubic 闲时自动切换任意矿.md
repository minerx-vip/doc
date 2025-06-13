

## Qubic 显示切换任意其他飞行表

#### 1.功能说明

- 在 Qubic 空闲时间切换任意其他飞行表，并且两个每个飞行表可以指定自己的超频模板



#### 2.注意事项

需要将 minerX 客户端升级到  v0.8.8 以上版本



#### 3.使用说明：

- 如果 IDLE 飞行表算力显示1K：表示是 Qubic 空闲时间
- 如果 IDLE 飞行表算力显示2K：表示是 Qubic 时间



同时执行本飞行表、和其他任意两个需要切换的飞行表即可

- 关于钱包：创建一个币种和名称和钱包地址全部为 IDLE 的空钱包

- 其他配置中设置需要切换的两个飞行表：

  - qubic_name = Qubic 时间需要运行的飞行表名称
  - target_name = Qubic 空闲时间需要运行的飞行表名称
  - **飞行表名称一定要指定正确**

  ```ini
  qubic_name=qubic_GPU
  target_name=Tari_luckypool
  ```



#### 4.飞行表

```json
{
    "flightName": "qubic_auto",
    "descMsg": "qubic_auto 闲时切换 Tari",
    "digitalCash": "IDLE",
    "miningPool": "1",
    "miningConfig": "Custom",
    "disableFaultCard": false,
    "customConfig": {
        "customMiner": "qubic_auto",
        "customInstallUrl": "https://minerx-download.oss-cn-shanghai.aliyuncs.com/qubic/qubic_auto-1.0.9.tar.gz",
        "customAlgo": "---",
        "customTemplate": "%WORKER_NAME%",
        "customUrl": "",
        "customPass": "",
        "customUserConfig": "qubic_name=qubic_GPU\ntarget_name=Tari_luckypool",
        "useGpus": ""
    }
}
```



