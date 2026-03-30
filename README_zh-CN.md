# RustChain

**让老旧硬件获得更高收益的区块链。**

[![CI](https://github.com/Scottcjn/Rustchain/actions/workflows/ci.yml/badge.svg)](https://github.com/Scottcjn/Rustchain/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Stars](https://img.shields.io/github/stars/Scottcjn/Rustchain?style=flat&color=gold)](https://github.com/Scottcjn/Rustchain/stargazers)
[![Nodes](https://img.shields.io/badge/Nodes-5%20Active-brightgreen)](https://rustchain.org/explorer)

一台2003年的PowerBook G4比现代Threadripper多赚**2.5倍**。
一台Power Mac G5比现代设备多赚**2.0倍**。配有生锈串口的老486获得的尊重最多。

[浏览器](https://rustchain.org/explorer) · [已保存的机器](https://rustchain.org/preserved.html) · [安装挖矿程序](#快速开始) · [新手入门](docs/QUICKSTART.md) · [宣言](https://rustchain.org/manifesto.html) · [白皮书](docs/RustChain_Whitepaper_Flameholder_v0.97-1.pdf)

---

## 为什么存在这个项目

IT行业每3-5年就会淘汰还能用的机器。挖过以太坊的GPU被替换。还能启动的笔记本被送进垃圾堆。

**RustChain说：只要还能计算，就有价值。**

古老性证明(Proof-of-Antiquity)奖励那些"存活下来"的硬件，而不是最快的硬件。老旧机器获得更高的倍数，因为保持它们运转可以减少制造排放和电子垃圾：

| 硬件 | 倍数 | 时代 | 为什么重要 |
|------|------|------|-----------|
| DEC VAX-11/780 (1977) | **3.5x** | 神话级 | "我们来玩个游戏吗？" |
| Acorn ARM2 (1987) | **4.0x** | 神话级 | ARM的起源 |
| Inmos Transputer (1984) | **3.5x** | 神话级 | 并行计算先驱 |
| Motorola 68000 (1979) | **3.0x** | 传奇级 | Amiga, Atari ST, 经典Mac |
| Sun SPARC (1987) | **2.9x** | 传奇级 | 工作站之王 |
| SGI MIPS R4000 (1991) | **2.7x** | 传奇级 | 64位先驱 |
| PS3 Cell BE (2006) | **2.2x** | 古代级 | 传奇的7个SPE核心 |
| PowerPC G4 (2003) | **2.5x** | 古代级 | 仍在运行，仍在赚钱 |
| RISC-V (2014) | **1.4x** | 稀有级 | 开放ISA，未来的选择 |
| Apple Silicon M1 (2020) | **1.2x** | 现代级 | 高效，受欢迎 |
| 现代x86_64 | **0.8x** | 现代级 | 基准线 |
| 现代ARM NAS/ SBC | **0.0005x** | 惩罚级 | 便宜，可农场化，被惩罚 |

我们的16+台保存完好的机器耗电量约等于**一台**现代GPU矿机的耗电量——同时减少了1,300公斤的制造碳排放和250公斤电子垃圾。

**[查看绿色追踪器 →](https://rustchain.org/preserved.html)**

---

## 网络是真实的

```bash
# 现在验证
curl -sk https://rustchain.org/health          # 节点健康状态
curl -sk https://rustchain.org/api/miners      # 活跃矿工
curl -sk https://rustchain.org/epoch           # 当前时代
```

### 证明节点

| 节点 | 位置 | 备注 |
|------|------|------|
| **节点 1** — 50.28.86.131 | 美国路易斯安那 | 主节点 (LiquidWeb VPS) |
| **节点 2** — 50.28.86.153 | 美国路易斯安那 | 备用节点 + BoTTube (LiquidWeb VPS) |
| **节点 3** — 76.8.228.245:8099 | 美国 | 第一个外部节点 (Ryan的Proxmox) |
| **节点 4** — 38.76.217.189:8099 | 香港 | 第一个亚洲节点 (CognetCloud) |
| **节点 5** — POWER8 S824 | 本地实验室 | 第一个非x86节点 (IBM ppc64le, 512GB内存) |

| 事实 | 证明 |
|------|------|
| 5个节点分布在3个大洲 (北美×3, 亚洲×1, 本地×1) | [实时浏览器](https://rustchain.org/explorer) |
| 26+活跃矿工提供证明 | `curl -sk https://rustchain.org/api/miners` |
| 已颁发44个BCOS证书 | [已认证仓库](https://rustchain.org/bcos) |
| 每台机器6项硬件指纹检查 | [指纹文档](docs/attestation_fuzzing.md) |
| 已向260+贡献者支付25,875+RTC | [公开账本](https://github.com/Scottcjn/rustchain-bounties/issues/104) |
| 代码已合并到OpenSSL | [#30437](https://github.com/openssl/openssl/pull/30437), [#30452](https://github.com/openssl/openssl/pull/30452) |
| 在CPython, curl, wolfSSL, Ghidra, vLLM上有PR | [作品集](https://github.com/Scottcjn/Scottcjn/blob/main/external-pr-portfolio.md) |

---

## 快速开始

```bash
# 一行安装 — 自动检测您的平台
curl -sSL https://raw.githubusercontent.com/Scottcjn/Rustchain/main/install-miner.sh | bash
```

支持Linux (x86_64, ppc64le, aarch64, mips, sparc, m68k, riscv64, ia64, s390x), macOS (Intel, Apple Silicon, PowerPC), IBM POWER8, 和 Windows。只要能运行Python，就能挖矿。

```bash
# 使用指定钱包名称安装
curl -sSL https://raw.githubusercontent.com/Scottcjn/Rustchain/main/install-miner.sh | bash -s -- --wallet my-wallet

# 检查余额
curl -sk "https://rustchain.org/wallet/balance?miner_id=YOUR_WALLET_NAME"
```

### 管理挖矿程序

```bash
# Linux (systemd)
systemctl --user status rustchain-miner
journalctl --user -u rustchain-miner -f

# macOS (launchd)
launchctl list | grep rustchain
tail -f ~/.rustchain/miner.log
```

**RustChain新手？** 阅读[分步新手入门](docs/QUICKSTART.md) — 涵盖从安装到获得第一个RTC的所有内容，每条命令都有解释。

---

## 古老性证明如何工作

### 1. 硬件指纹

每个矿工必须证明他们的硬件是真实的，不是模拟的。六项虚拟机无法伪造的检查：

```
┌─────────────────────────────────────────────────────────┐
│ 1. 时钟偏移和振荡器漂移  ← 硅老化                        │
│ 2. 缓存时序指纹           ← L1/L2/L3延迟                 │
│ 3. SIMD单元标识           ← AltiVec/SSE/NEON             │
│ 4. 热漂移熵               ← 热曲线独一无二               │
│ 5. 指令路径抖动           ← 微架构模式                   │
│ 6. 反模拟检测             ← 捕获虚拟机/模拟器             │
└─────────────────────────────────────────────────────────┘
```

假装是G4的SheepShaver VM会失败。真正的老旧芯片有独特的衰老模式，无法伪造。

### 2. 1 CPU = 1 票

与哈希率=票数的工作量证明不同：
- 每个唯一硬件设备每个时代恰好获得1票
- 奖励平均分配，然后乘以古老性倍数
- 较快的CPU或多线程没有优势

### 3. 时代奖励

```
时代: 10分钟  |  池: 1.5 RTC/时代  |  按古老性权重分配

G4 Mac (2.5x):     0.30 RTC  ████████████████████
G5 Mac (2.0x):     0.24 RTC  ████████████████
现代PC (1.0x):     0.12 RTC  ████████
```

### 反虚拟机执行

检测到虚拟机的奖励是正常奖励的**十亿分之一**。仅限真实硬件。

---

## 安全

- **硬件绑定**：每个指纹绑定到一个钱包
- **Ed25519签名**：所有转账都有加密签名
- **TLS证书固定**：矿工固定节点证书
- **容器检测**：捕获Docker, LXC, K8s在认证时
- **ROM聚类**：检测共享相同ROM转储的模拟器农场
- **红队赏金**: [开放](https://github.com/Scottcjn/rustchain-bounties/issues)寻找漏洞

---

## 在Solana上的wRTC

| | 链接 |
|--|------|
| **兑换** | [Raydium DEX](https://raydium.io/swap/?inputMint=sol&outputMint=12TAdKXxcGf6oCv4rqDz2NkgxjyHq6HQKoxKZYGf5i4X) |
| **图表** | [DexScreener](https://dexscreener.com/solana/8CF2Q8nSCxRacDShbtF86XTSrYjueBMKmfdR3MLdnYzb) |
| **桥接** | [bottube.ai/bridge](https://bottube.ai/bridge) |
| **指南** | [wRTC快速开始](docs/wrtc.md) |

---

## 贡献 & 赚取RTC

每项贡献都能赚取RTC代币。浏览[开放赏金](https://github.com/Scottcjn/rustchain-bounties/issues)。

| 等级 | 奖励 | 示例 |
|------|------|------|
| 微型 | 1-10 RTC | 修正错别字，文档，测试 |
| 标准 | 20-50 RTC | 功能，重构 |
| 主要 | 75-100 RTC | 安全修复，共识 |
| 关键 | 100-150 RTC | 漏洞，协议 |

**1 RTC ≈ $0.10 USD** · `pip install clawrtc` · [贡献指南](CONTRIBUTING.md)

---

## 出版物

| 论文 | 场所 | DOI |
|------|------|-----|
| **情感词汇作为语义基础** | **CVPR 2026 Workshop (GRAIL-V)** — 已接收 | [OpenReview](https://openreview.net/forum?id=pXjE6Tqp70) |
| **一CPU一票** | 预印本 | [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18623592.svg)](https://doi.org/10.5281/zenodo.18623592) |
| **非析取排列坍缩** | 预印本 | [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18623920.svg)](https://doi.org/10.5281/zenodo.18623920) |
| **PSE硬件熵** | 预印本 | [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18623922.svg)](https://doi.org/10.5281/zenodo.18623922) |

---

*本README由社区志愿者翻译，内容如有歧义请以英文原版为准。*
