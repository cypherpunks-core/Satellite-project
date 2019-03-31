# Satellite Project 衛星計畫
***目標：在台灣發射比特幣交易到TELSTAR 18V衛星***
***Goal: Launch Bitcoin transactions in Taiwan to TELSTAR 18V satellite***
## 衛星計畫 材料
- [x] 筆電-一台裝有Linux筆電 ，最好有i5 ，硬碟要求 裝的下220GB全節點(最低要求3G修剪過的節點): https://amzn.to/2x6G86r
- [ ] 至少46公分（18英寸）衛星天線: https://amzn.to/2wBtPzK
- [ ] 軟體定義的無線電接口(Software Defined Radio Interface): https://amzn.to/2g8Nu2O
- [ ] Linear Polarization (線性極化) PLL LNB: https://amzn.to/2w0Zk4C
- [ ] LNB 安裝支架: https://amzn.to/2xgotXU
- [ ] LNB 電源: https://amzn.to/2KUGouq
- [ ] 同軸電纜: https://amzn.to/2w7N4xQ
- [ ] F連接器到SMA同軸適配器（F Connector to SMA Coax Adapter）: https://amzn.to/2gajpAh
- [x] 用於調整配件的螺絲起子和鉗子
- [ ] (選則)3英尺，衛星三腳架: https://amzn.to/2w81RZm

![](https://github.com/Blockstream/satellite/raw/master/doc/api_architecture.png?raw=true)

## 文章參考
* 材料說明：https://github.com/Blockstream/satellite/wiki/Hardware-Requirements
* 衛星覆蓋：https://blockstream.com/satellite/#satellite_network-coverage
* 衛星交易狀態：https://blockstream.com/satellite-queue/
* API 文件說明：https://github.com/Blockstream/satellite/tree/master/api
* Video-[使用SDR和GNU無線電降低區塊流量同步道衛星的成本](https://www.youtube.com/watch?v=o1N6zjOgmFA&t=158s)
* 快速互聯網比特幣中繼引擎（FIBER）是一種協議：http://bitcoinfibre.org/
* 自製教學
  * 硬體需求：[Building Your Own Bitcoin Satellite Node: Part 1 — Hardware Assembly](/article/building-your-own-bitcoin-satellite-node-part1.md)
  * 軟體需求：[Building Your Own Bitcoin Satellite Node: Part 2 — Software Installation](/article/building-your-own-bitcoin-satellite-node-part2.md)
  * 天線對齊：[Building Your Own Bitcoin Satellite Node: Part 3 — Dish Alignment](/article/building-your-own-bitcoin-satellite-node-part3.md)

### 衛星 閃電網路
> IMPORTANT The Blockstream Satellite API is currently operating in developer mode: utilizing Lightning Testnet for payment and without live satellite transmissions. We will transition the API to mainnet and live satellite broadcast on January 16th 2019.
> Subsequently, get the Lightning Invoice Number that was printed by the API data sender on the console and pay.


Blockstream衛星網路24小時不間斷地免費將比特幣區塊鏈廣播到全世界，保護網路不受干擾，讓世界上的每一個人都有機會使用比特幣。

## 為什麼使用衛星？
* 無需上網：
    Blockstream衛星將比特幣區塊鏈廣播至整個地球，減少比特幣對網路的依賴。現在世界上的每一個人都有機會使用比特幣。

* 大量成本節約：
    去除了成本這個障礙後，人們可以不花一分錢即可接收區塊，讓更多人能夠用上比特幣並參與到比特幣網路中來。

* 網路穩定性：
    Blockstream衛星提供了新的接收比特幣區塊鏈的方法，並且這個方法不會受連接故障的影響。這保護了用戶不受網路波動的影響，防止任何全節點被孤立或隔離。

## 工作原理
Blockstream衛星在地面的站點被稱為“基站（teleport）”，它們參與比特幣網路並將區塊傳送至地球同步衛星。

## 新聞蒐集
* [Bitcoin From Space: Blockstream CSO Explains Its Satellite Services](https://cointelegraph.com/news/bitcoin-from-space-blockstream-cso-explains-its-satellite-services)
* [Blockstream Launches 5th Satellite Streaming Bitcoin Blockchain From Space](https://cointelegraph.com/news/blockstream-launches-5th-satellite-streaming-bitcoin-blockchain-from-space)
* [How Satellites in Space Are Bringing Bitcoin to People Without Internet](https://blockexplorer.com/news/satellites-bring-bitcoin-to-people-without-internet/)
* [Blockstream Boosts Bitcoin Satellite Service With Lightning Payments](https://www.coindesk.com/blockstream-boosts-bitcoin-satellite-service-with-lightning-payments)