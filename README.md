# eMudhra 弱中级密钥复现

## 前言
起因：eMudhra 在 2025 年 4 月 30 日生成了 8 组 ECDSA P-384 中间级 CA 密钥对，但这几对的密钥对的私钥...
？！😼4😼！？ 
随便我们回顾一下 `ECDSA P-384`加密
关于受影响的密钥：

| Intermediate key | Use | Private scalar `d` | SHA-256(SPKI) |
|---|---:|---:|---|
| `emSign DV TLS CA - G3B` | TLS | 156 | `ebed6475c2c2d80fcb199f3fe8dd6e6b3ce60b77eb15d4e42c3dec0c6f5b5105` |
| `emSign DV TLS CA - G3C` | TLS | 230 | `49dd353dc2b919a3770645117d0e60c16115e7d1bc259eefe734b00ea434fe5f` |
| `emSign EV TLS CA - G3B` | TLS | 115 | `e0254c7fcdc265e2f0f8a428dabb75ab4ae039b4872d62f5ee57f0877d5a8a41` |
| `emSign EV TLS CA - G3C` | TLS | 56 | `5c0660a2b164910d8ff589c18e14552e9e0ec237dcefe2cb736d41a4811f81a0` |
| `emSign OV TLS CA - G3B` | TLS | 155 | `43bffa19d6ef651451f6841e019931e96f6f2eaeff28ab4b6f1ce4576de2717b` |
| `emSign OV TLS CA - G3C` | TLS | 4 | `63ecefee431d49523bc1136c4e72d0206a477086caf606cd5cf025686c109cf8` |
| `emSign OV CodeSigning CA - G3B` | Code signing | 66 | `ec4ffa1ad0ac88081314b7aaffef6a91f97cd57291bb5ba686c5415f5eb4f6b6` |
| `emSign OV CodeSigning CA - G3C` | Code signing | 237 | `92c063d67e8f14db71d288e11266ffdaf69cbf115f7bab14f3bc2f68d25e0e30` |

## 危害原理

## 复现

先简单回顾，我们需要准备的
- 弱密钥
- 弱密钥颁发的证书
- caddy/nginx
- 内网网关的重定向

### 快速开始

```bash
git clone # eMudhra-ca-re
