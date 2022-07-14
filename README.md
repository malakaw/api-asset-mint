# api-asset-mint



工程主要的作用提供页面提交接口，处理页面关于nft mint的各种参数，并保存到对应目录，后续定时任务去读取文件，然后调用cardano-cli去在cardano 链上生成nft.


### 环境



python 2.7

gunicorn 



### 配置

 这里唯一需要配置的就是接口接收的order需要生产nft的信息保存下来，这里保存到文件，文件配置在文件order.py

`base_path = "/XX/XX/order_jsons"`

启动文件

run.sh



### 文件说明

主要解释下order的文件目录结构参考下面

.....xxx../order_json/yyyy_m/address/yyyy_mm_dd_MM_SS_SS

实例：

```2022_7/addr_test1qra5v69zswvp09t76p3x57zr80g45sn7a024lx2utsczplhdf5f65ywwsaqzwkp939sxpa40afnezx8jf09ersmz526qdhfh0j/2022_07_14_15_44_38```

此目录下文件：2022_07_14_15_44_38.json

```json 
{
  "paid_date": "",
  "create_date": "2022_07_14_15_44_38",
  "to_address": "",
  "from_address": "addr_test1vrfkq33rrsczulhumfssfa4cqadwzp0clh85nyjvhl0eysglfdkvs",
  "modify_date": "",
  "nfts": [
    {
      "count": 1,
      "nft_name": "123",
      "describe": "ss",
      "name": "saddd",
      "ipfs": "QmNVjp1Gjtc8cWbucz1NRbY75A5bdQV1YGcpmktR6xq6z5"
    }
  ],
  "paid_ada_amount": 0,
  "has_paid": false
}
```



 此文件就是另外的定时任务需要处理的，定时任务用这个文件来mint nft,并判断发送给指定的 address



