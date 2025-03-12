# DMIT VPS 使用全攻略：购买、系统重装、Root 密码设置、快照与流量计费详解

DMIT 目前采用全新的用户界面设计，其后台管理非常方便，包括重装系统、设置 Root 密码、上传密钥、查看流量计费以及取消续费等功能。本文将为您详细讲解 DMIT VPS 相关的使用教程和注意事项。

👉 [【推荐收藏】2025年 DMIT 最新优惠活动整理汇总 - 每日更新可用优惠套餐](https://bit.ly/dmit_coupon)

---

## VPS 购买教程

DMIT 的购买流程简单易懂，您可以参考以下教程完成购买：[DMIT VPS 购买教程](https://www.daniao.org/10982.html)。

---

## 流量计费策略详解

DMIT 针对部分套餐（包括 HKG.T1 和 SJC.T1）实施了单向取流量最大值的计费策略，这意味着只需计量流入（IN）和流出（OUT）的最大值即可。以下为具体说明：

- **计费规则**：
  - 系统仅计量 `MAX(IN, OUT)` 的单向最大值。
  - 流量统计 UI 界面会根据新规则更新展示，但并不会影响您可用的实际流量。
- **举例说明**：
  - **HKG.T1.STARTER 套餐**：单向流量计费，超量限速。
  - **LAX.sPro.CREATOR 套餐**：双向流量计费，超量后服务暂停。
  - **HKG.PRO 套餐**：同样是双向计费，超量暂停服务。

> 提示：不同套餐在流量计费上的规则可能略有差异，请登录后台确认具体详情。

---

## SSH 金钥与 Root 密码登录

### 使用 SSH 金钥登录
DMIT 支持通过配置密钥实现 SSH 登录，您可以参考以下教程：[如何配置密钥登录](https://www.daniao.org/15626.html)。

### 使用 Root 密码登录
DMIT 默认提供 Root 密码访问控制台功能，但如果需要通过 SSH 登录，请注意以下内容：

1. 进入系统后修改 SSH 配置允许 Root 密码登录。
2. 更改 Root 密码后，需要先关机再开机来使新密码生效。

#### Root 密码登录设置方法

**方法 1**：
bash
passwd  # 设置密码
sudo sed -i 's/^#\?PermitRootLogin.*/PermitRootLogin yes/g' /etc/ssh/sshd_config
sudo sed -i 's/^#\?PasswordAuthentication.*/PasswordAuthentication yes/g' /etc/ssh/sshd_config
sudo service sshd restart
reboot  # 重启服务器


**方法 2**：
bash
sudo -i  # 切换到 Root 身份（DMIT 默认以 Root 身份登录，此命令可忽略）
passwd  # 设置密码
nano /etc/ssh/sshd_config  # 修改配置文件
# 在文件中更改以下内容：
PermitRootLogin yes
PasswordAuthentication yes
reboot  # 重启服务器


> 注意：复制命令时请确保命令准确无误。如有疑问，可通过搜索获取更多帮助。

---

## 快照功能详解

DMIT 提供了免费的快照功能，用户可通过后台界面直接创建快照。这一功能非常实用，便于快速恢复系统状态。

---

## 重装系统的操作步骤

DMIT 提供多种可重装的操作系统，几乎能满足大多数用户的需求。您可以在后台界面选择合适的操作系统进行一键重装。

---

## 账单与续费管理

在续费管理界面，您可以方便地恢复到期账单的续费操作。只需按照后台指导步骤完成支付即可。

---

## 洛杉矶 PVM.LAX.Pro 套餐网络详情

针对洛杉矶 PVM.LAX.Pro 套餐，其网络配置如下：

- **线路**：洛杉矶 CN2 GIA。
- **电信**：
  - 去程 GIA（AS4809）。
  - 回程 GIA（AS4809）。
- **联通**：
  - 去程直连 AS4837。
  - 回程 GIA（AS4809）。
- **移动**：
  - 去程香港移动（AS58453）。
  - 回程 GIA（AS4809）。

---

以上就是 DMIT VPS 的主要使用说明。无论是购买、系统配置还是流量和网络管理，DMIT 都提供了强大的后台管理能力，确保用户无忧使用其服务。