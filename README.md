<!-- markdownlint-disable MD028 MD033 MD045 -->

# reinstall

[![Codacy](https://img.shields.io/codacy/grade/dc679a17751448628fe6d8ac35e26eed?logo=Codacy&label=Codacy&style=flat-square)](https://app.codacy.com/gh/bin456789/reinstall/dashboard)
[![CodeFactor](https://img.shields.io/codefactor/grade/github/bin456789/reinstall?logo=CodeFactor&logoColor=white&label=CodeFactor&style=flat-square)](https://www.codefactor.io/repository/github/bin456789/reinstall)
[![Lines of Code](https://tokei.rs/b1/github/bin456789/reinstall?category=code&label=Lines%20of%20Code&style=flat-square)](https://github.com/XAMPPRocky/tokei)
[![Telegram Group](https://img.shields.io/badge/Telegram-2CA5E0?style=flat-square&logo=telegram&logoColor=white)](https://t.me/reinstall_os)
[![Github Sponsors](https://img.shields.io/badge/sponsor-30363D?style=flat-square&logo=GitHub-Sponsors&logoColor=#EA4AAA)](https://github.com/sponsors/bin456789)
<!-- [![Lines of Code](https://aschey.tech/tokei/github/bin456789/reinstall?category=code&label=Lines%20of%20Code&style=flat-square)](https://github.com/aschey/vercel-tokei) -->

一鍵重裝腳本 [English](README.en.md)

![捐贈者](https://raw.githubusercontent.com/bin456789/sponsors/refs/heads/master/sponsors.svg)

## 亮點

- 一鍵安裝 Linux，支持 17 種常見發行版本
- 一鍵安裝 Windows，使用官方 ISO 安裝而非自製鏡像，腳本會自動獲取 ISO 連結、自動安裝 Virtio 等驅動
- 支持任意方向重裝，即 `Linux to Linux`、`Linux to Windows`、`Windows to Windows`、`Windows to Linux`
- 無需填寫 IP 參數，自動識別動靜態，支援 `/32`、`/128`、`閘道不在子網範圍內`、`純 IPv6`、`雙網卡` 等特殊網路
- 專門適配低配小雞，比官方 netboot 需要更少的記憶體
- 全程用分區表 ID 識別硬碟，確保不會寫錯硬碟
- 支持 BIOS、EFI 引導，支持 ARM 伺服器
- 不含自製包，所有資源均即時從鏡像源獲得
- 有很多注釋

## 系統要求

原系統可以是表格中的任意系統

目標系統的配置要求如下：

| 目標系統                                                                                                                                                                                                                                                                                                                                                               | 版本                                  | 記憶體      | 硬碟         |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------- | --------- | ------------ |
| <img width="16" height="16" src="https://www.alpinelinux.org/alpine-logo.ico" /> Alpine                                                                                                                                                                                                                                                                                | 3.18, 3.19, 3.20, 3.21                | 256 MB    | 1 GB         |
| <img width="16" height="16" src="https://www.debian.org/favicon.ico" /> Debian                                                                                                                                                                                                                                                                                         | 9, 10, 11, 12                         | 256 MB    | 1 ~ 1.5 GB ^ |
| <img width="16" height="16" src="https://github.com/bin456789/reinstall/assets/7548515/f74b3d5b-085f-4df3-bcc9-8a9bd80bb16d" /> Kali                                                                                                                                                                                                                                   | 滾動                                  | 256 MB    | 1 ~ 1.5 GB ^ |
| <img width="16" height="16" src="https://canonical-subiquity.readthedocs-hosted.com/en/latest/_static/favicon.png" /> Ubuntu                                                                                                                                                                                                                                           | 16.04, 18.04, 20.04, 22.04, 24.04     | 512 MB \* | 2 GB         |
| <img width="16" height="16" src="https://img.alicdn.com/imgextra/i1/O1CN01oJnJZg1yK4RzI4Rx2_!!6000000006559-2-tps-118-118.png" /> Anolis                                                                                                                                                                                                                               | 7, 8                                  | 512 MB \* | 5 GB         |
| <img width="16" height="16" src="https://www.redhat.com/favicon.ico" /> RHEL &nbsp;<img width="16" height="16" src="https://almalinux.org/fav/favicon.ico" /> AlmaLinux &nbsp;<img width="16" height="16" src="https://rockylinux.org/favicon.png" /> Rocky &nbsp;<img width="16" height="16" src="https://www.oracle.com/asset/web/favicons/favicon-32.png" /> Oracle | 8, 9                                  | 512 MB \* | 5 GB         |
| <img width="16" height="16" src="https://opencloudos.org/qq.ico" /> OpenCloudOS                                                                                                                                                                                                                                                                                        | 8, 9                                  | 512 MB \* | 5 GB         |
| <img width="16" height="16" src="https://www.centos.org/assets/icons/favicon.svg" /> CentOS                                                                                                                                                                                                                                                                            | 9, 10                                 | 512 MB \* | 5 GB         |
| <img width="16" height="16" src="https://fedoraproject.org/favicon.ico" /> Fedora                                                                                                                                                                                                                                                                                      | 40, 41                                | 512 MB \* | 5 GB         |
| <img width="16" height="16" src="https://www.openeuler.org/favicon.ico" /> openEuler                                                                                                                                                                                                                                                                                   | 20.03, 22.03, 24.03                   | 512 MB \* | 5 GB         |
| <img width="16" height="16" src="https://static.opensuse.org/favicon.ico" /> openSUSE                                                                                                                                                                                                                                                                                  | 15.6, Tumbleweed (滾動)               | 512 MB \* | 5 GB         |
| <img width="16" height="16" src="https://github.com/user-attachments/assets/99a542b6-6482-4086-addf-f192c06fef73" /> NixOS                                                                                                                                                                                                                                             | 24.11                                 | 512 MB    | 5 GB         |
| <img width="16" height="16" src="https://archlinux.org/static/favicon.png" /> Arch                                                                                                                                                                                                                                                                                     | 滾動                                  | 512 MB    | 5 GB         |
| <img width="16" height="16" src="https://www.gentoo.org/assets/img/logo/gentoo-g.png" /> Gentoo                                                                                                                                                                                                                                                                        | 滾動                                  | 512 MB    | 5 GB         |
| <img width="16" height="16" src="https://blogs.windows.com/wp-content/uploads/prod/2022/09/cropped-Windows11IconTransparent512-32x32.png" /> Windows (DD)                                                                                                                                                                                                              | 任何                                  | 512 MB    | 取決於鏡像   |
| <img width="16" height="16" src="https://blogs.windows.com/wp-content/uploads/prod/2022/09/cropped-Windows11IconTransparent512-32x32.png" /> Windows (ISO)                                                                                                                                                                                                             | Vista, 7, 8.x (Server 2008 ~ 2012 R2) | 512 MB    | 25 GB        |
| <img width="16" height="16" src="https://blogs.windows.com/wp-content/uploads/prod/2022/09/cropped-Windows11IconTransparent512-32x32.png" /> Windows (ISO)                                                                                                                                                                                                             | 10, 11 (Server 2016 ~ 2025)           | 1 GB      | 25 GB        |

\* 表示使用雲鏡像安裝，非傳統網路安裝

^ 表示需要 256 MB 記憶體 + 1.5 GB 硬碟，或 512 MB 記憶體 + 1 GB 硬碟

> [!WARNING]
> ❌ 本腳本不支持 OpenVZ、LXC 虛擬機器
>
> 請改用 <https://github.com/LloydAsp/OsMutation>

## 下載（當前系統是 <img width="20" height="20" src="https://www.kernel.org/theme/images/logos/favicon.png" /> Linux）

國外伺服器：

```bash
curl -O https://raw.githubusercontent.com/bin456789/reinstall/main/reinstall.sh || wget -O reinstall.sh $_
```

國內伺服器：

```bash
curl -O https://jihulab.com/bin456789/reinstall/-/raw/main/reinstall.sh || wget -O reinstall.sh $_
```

## 下載（當前系統是 <img width="20" height="20" src="https://blogs.windows.com/wp-content/uploads/prod/2022/09/cropped-Windows11IconTransparent512-32x32.png" /> Windows）

> [!IMPORTANT]
> 請先關閉 `Windows Defender` 的 `即時保護` 功能。該功能會阻止 `certutil` 下載任何檔。

<details>

<summary>解決 Windows 7 下無法下載腳本</summary>

由於不支持 TLS 1.2、SHA-256、根證書沒有更新等原因，Vista，7 和 Server 2008 (R2) 可能無法自動下載腳本，因此需要手動下載，具體操作如下：

用 IE 下載 (先在 IE 高級設置裡啟用 TLS 1.2)，或者通過遠端桌面，將這兩個檔保存到同一個目錄

- <https://raw.githubusercontent.com/bin456789/reinstall/main/reinstall.bat>

- <https://www.cygwin.com/setup-x86.exe>

使用時運行下載的 `reinstall.bat`

</details>

國外伺服器：

```batch
certutil -urlcache -f -split https://raw.githubusercontent.com/bin456789/reinstall/main/reinstall.bat
```

國內伺服器：

```batch
certutil -urlcache -f -split https://jihulab.com/bin456789/reinstall/-/raw/main/reinstall.bat
```

## 使用

**所有功能** 都可在 Linux / Windows 下運行

- Linux 下運行 `bash reinstall.sh`
- Windows 下運行 `.\reinstall.bat`

### 功能 1: 安裝 <img width="16" height="16" src="https://www.kernel.org/theme/images/logos/favicon.png" /> Linux

- 用戶名 `root` 預設密碼 `123@@@`，首次開機可能要等幾分鐘才能成功登錄
- 安裝最新版可不輸入版本號
- 最大化利用磁碟空間：不含 boot 分區（Fedora 例外），不含 swap 分區
- 自動根據機器類型選擇不同的優化內核，例如 `Cloud`、`HWE` 內核
- 安裝 Red Hat 時需填寫 <https://access.redhat.com/downloads/content/rhel> 得到的 `qcow2` 鏡像連結，也可以安裝其它類 RHEL 系統，例如 `Alibaba Cloud Linux` 和 `TencentOS Server`
- 重裝後如需修改 SSH 埠或者改成金鑰登錄，注意還要修改 `/etc/ssh/sshd_config.d/` 裡面的文件

```bash
bash reinstall.sh anolis      7|8
                  rocky       8|9
                  redhat      8|9   --img='http://xxx.com/xxx.qcow2'
                  oracle      8|9
                  almalinux   8|9
                  opencloudos 8|9
                  centos      9|10
                  fedora      40|41
                  nixos       24.11
                  debian      9|10|11|12
                  opensuse    15.6|tumbleweed
                  openeuler   20.03|22.03|24.03
                  alpine      3.18|3.19|3.20|3.21
                  ubuntu      16.04|18.04|20.04|22.04|24.04 [--minimal]
                  kali
                  arch
                  gentoo
```

#### 可選參數

- `--password PASSWORD` 設置密碼
- `--ssh-port PORT` 修改 SSH 埠（安裝期間觀察日誌用，也用於新系統）
- `--web-port PORT` 修改 Web 埠（安裝期間觀察日誌用）
- `--hold 2` 安裝結束後不重啟，此時可以 SSH 登錄修改系統內容，系統掛載在 `/os` (此功能不支援 Debian/Kali)

> [!TIP]
> 安裝 Debian/Kali 時，x86 可通過後臺 VNC 查看安裝進度，ARM 可通過串列控制台查看安裝進度。
>
> 安裝其它系統時，可通過多種方式（SSH、HTTP 80 埠、後臺 VNC、串列控制台）查看安裝進度。
> <br />即使安裝過程出錯，也能通過 SSH 運行 `/trans.sh alpine` 安裝到 Alpine。

<details>

<summary>實驗性功能</summary>

雲鏡像安裝 Debian

- 適合於 CPU 較慢的機器

```bash
bash reinstall.sh debian --ci
```

ISO 安裝 CentOS, AlmaLinux, Rocky, Fedora

- 僅支援記憶體大於 2G 且為動態 IP 的機器
- 密碼 `123@@@`，SSH 埠 `22`，不支援用參數修改

```bash
bash reinstall.sh centos --installer
```

ISO 安裝 Ubuntu

- 僅支援記憶體大於 1G 且為動態 IP 的機器
- 密碼 `123@@@`，SSH 埠 `22`，不支援用參數修改

```bash
bash reinstall.sh ubuntu --installer
```

</details>

### 功能 2: DD

- 支援 `raw` `vhd` 格式的鏡像（未壓縮，或者壓縮成 `.gz` `.xz` `.zst` `.tar` `.tar.gz` `.tar.xz` `.tar.zst`）
- DD Windows 鏡像時，會自動擴展系統磁片，靜態 IP 的機器會配置好 IP，可能首次開機幾分鐘後才生效
- DD Linux 鏡像時，**不會**修改鏡像的任何內容

```bash
bash reinstall.sh dd --img https://example.com/xxx.xz
```

#### 可選參數

- `--allow-ping` 允許被 Ping (僅限 DD Windows)
- `--rdp-port PORT` 修改 RDP 埠 (僅限 DD Windows)
- `--ssh-port PORT` 修改 SSH 埠（安裝期間觀察日誌用）
- `--web-port PORT` 修改 Web 埠（安裝期間觀察日誌用）
- `--hold 2` DD 結束後不重啟，此時可以 SSH 登錄修改系統內容，Windows 系統會掛載在 `/os`，Linux 系統**不會**自動掛載

> [!TIP]
> 可通過多種方式（SSH、HTTP 80 埠、後臺 VNC、串列控制台）查看安裝進度。
> <br />即使安裝過程出錯，也能通過 SSH 運行 `/trans.sh alpine` 安裝到 Alpine。

### 功能 3: 重啟到 <img width="16" height="16" src="https://www.alpinelinux.org/alpine-logo.ico" /> Alpine Live OS（救援系統）

- 可用 ssh 連接，進行備份/恢復硬碟、手動 DD、修改分區、手動安裝 Alpine/Arch/Gentoo 等操作
- 用戶名 `root` 預設密碼 `123@@@`
- 如果手動操作沒有破壞原系統，再次重啟將回到原系統

```bash
bash reinstall.sh alpine --hold=1
```

#### 可選參數

- `--password PASSWORD` 設置密碼
- `--ssh-port PORT` 修改 SSH 埠

### 功能 4: 重啟到 <img width="16" height="16" src="https://netboot.xyz/img/favicon.ico" /> netboot.xyz

- 可使用商家後臺 VNC 手動安裝 [更多系統](https://github.com/netbootxyz/netboot.xyz?tab=readme-ov-file#what-operating-systems-are-currently-available-on-netbootxyz)
- 如果手動操作沒有破壞原系統，再次重啟將回到原系統

```bash
bash reinstall.sh netboot.xyz
```

![netboot.xyz](https://netboot.xyz/images/netboot.xyz.gif)

### 功能 5: 安裝 <img width="16" height="16" src="https://blogs.windows.com/wp-content/uploads/prod/2022/09/cropped-Windows11IconTransparent512-32x32.png" /> Windows ISO

![Windows 安裝介面](https://github.com/bin456789/reinstall/assets/7548515/07c1aea2-1ce3-4967-904f-aaf9d6eec3f7)

- 用戶名 `administrator` 預設密碼 `123@@@`
- 如果遠端登入失敗，可以嘗試使用用戶名 `.\administrator`
- 靜態機器會自動配置好 IP，可能首次開機幾分鐘後才生效
- 支援所有語言

#### 支援的系統

- Windows (Vista ~ 11)
- Windows Server (2008 ~ 2025)
  - Windows Server Essentials \*
  - Windows Server (Semi) Annual Channel \*
  - Hyper-V Server \*
  - Azure Stack HCI \*

#### 方法 1: 讓腳本自動查找 ISO （推薦）

- 通常情況下 Windows 每個月都會發佈新的官方 ISO，集成了最新的系統補丁，避免了剛安裝好系統就要下載一堆補丁
- 腳本會從 <https://massgrave.dev/genuine-installation-media> 查找 ISO，該網站收錄了每月發佈的 ISO，因此腳本查找到的 ISO 都是官方最新版
- 上面帶 \* 的系統不支援自動查找 ISO

```bash
bash reinstall.sh windows \
     --image-name 'Windows 11 Enterprise LTSC 2024' \
     --lang zh-cn
```

<details>
<summary>支援的語言</summary>

```text
ar-sa
bg-bg
cs-cz
da-dk
de-de
el-gr
en-gb
en-us
es-es
es-mx
et-ee
fi-fi
fr-ca
fr-fr
he-il
hr-hr
hu-hu
it-it
ja-jp
ko-kr
lt-lt
lv-lv
nb-no
nl-nl
pl-pl
pt-pt
pt-br
ro-ro
ru-ru
sk-sk
sl-si
sr-latn-rs
sv-se
th-th
tr-tr
uk-ua
zh-cn
zh-hk
zh-tw
```

</details>

#### 方法 2: 自行指定 ISO 連接

- 如果不知道 `--image-name`，可以隨便填，在重啟後連接 SSH，根據錯誤提示重新輸入正確的值

```bash
bash reinstall.sh windows \
     --image-name 'Windows 11 Enterprise LTSC 2024' \
     --iso 'https://drive.massgrave.dev/zh-cn_windows_11_enterprise_ltsc_2024_x64_dvd_cff9cd2d.iso'
```

<details>

<summary>以下網站可找到 ISO 連結</summary>

- <https://massgrave.dev/genuine-installation-media> (推薦，iso 來自官方，每月更新，包含最新補丁)
- <https://www.microsoft.com/software-download/windows10> (需用非 Windows User-Agent 打開)
- <https://www.microsoft.com/software-download/windows11>
- <https://www.microsoft.com/software-download/windowsinsiderpreviewiso> (預覽版)
- <https://www.microsoft.com/evalcenter/download-windows-10-enterprise>
- <https://www.microsoft.com/evalcenter/download-windows-11-enterprise>
- <https://www.microsoft.com/evalcenter/download-windows-11-iot-enterprise-ltsc-eval>
- <https://www.microsoft.com/evalcenter/download-windows-server-2012-r2>
- <https://www.microsoft.com/evalcenter/download-windows-server-2016>
- <https://www.microsoft.com/evalcenter/download-windows-server-2019>
- <https://www.microsoft.com/evalcenter/download-windows-server-2022>
- <https://www.microsoft.com/evalcenter/download-windows-server-2025>

</details>

#### 可選參數

- `--password PASSWORD` 設置密碼
- `--allow-ping` 允許被 Ping
- `--rdp-port PORT` 更改 RDP 埠
- `--ssh-port PORT` 修改 SSH 埠（安裝期間觀察日誌用）
- `--web-port PORT` 修改 Web 埠（安裝期間觀察日誌用）
- `--hold 2` 在進入 Windows 官方安裝程式之前，可以 SSH 登錄修改硬碟內容，硬碟掛載在 `/os`

#### 如何填寫映射名稱 `--image-name`

通常一個 ISO 會包含多個系統版本，例如家庭版、專業版。映射名稱 `--image-name` 就是用來指定要安裝的版本，填寫時不區分大小寫

可以用 DISM、DISM++、Wimlib 等工具查詢 ISO 包含的映射名稱

常用的映射名稱有：

```text
Windows 7 Ultimate
Windows 11 Pro
Windows 11 Enterprise LTSC 2024
Windows Server 2025 SERVERDATACENTER
```

#### 如何用 [DISM++](https://github.com/Chuyu-Team/Dism-Multi-language/releases) 查詢 ISO 包含的映射名稱

打開檔功能表 > 打開映射檔，選擇要安裝的 iso，即可得到映射名稱，所有映射名稱都可以安裝

![image-name](https://github.com/bin456789/reinstall/assets/7548515/5aae0a9b-61e2-4f66-bb98-d470a6beaac2)

#### 腳本會按需安裝以下驅動

- Virtio ([Virtio](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/)、[阿裡雲](https://www.alibabacloud.com/help/ecs/user-guide/update-red-hat-virtio-drivers-of-windows-instances))
- XEN ([XEN](https://xenproject.org/resources/downloads/)、[Citrix](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Upgrading_PV_drivers.html#win2008-citrix-upgrade)、[AWS](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/xen-drivers-overview.html))
- AWS ([ENA 網卡](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ena-driver-releases-windows.html)、[NVME 存儲控制器](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/nvme-driver-version-history.html))
- GCP ([gVNIC 網卡](https://cloud.google.com/compute/docs/networking/using-gvnic)、[GGA 顯卡](https://cloud.google.com/compute/docs/instances/enable-instance-virtual-display))
- Azure ([MANA 網卡](https://learn.microsoft.com/azure/virtual-network/accelerated-networking-mana-windows))
- Intel ([VMD 存儲控制器](https://www.intel.com/content/www/us/en/download/720755/intel-rapid-storage-technology-driver-installation-software-with-intel-optane-memory-11th-up-to-13th-gen-platforms.html))

> [!WARNING]
> Vista (Server 2008) 和 32 位元系統可能會缺少驅動

> [!WARNING]
> 未開啟 CSM 的 EFI 機器，無法安裝 Windows 7 (Server 2008 R2)
>
> Hyper-V (Azure) 需選擇合適的虛擬機器代系 <https://learn.microsoft.com/windows-server/virtualization/hyper-v/plan/should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v>

> [!WARNING]
> Windows 10 LTSC 2021 中文版鏡像 `zh-cn_windows_10_enterprise_ltsc_2021_x64_dvd_033b7312.iso` 的 `wsappx` 進程會長期佔用 CPU
>
> 解決方法是更新系統補丁，或者手動安裝 `VCLibs` 庫 <https://www.google.com/search?q=ltsc+wsappx>

#### ARM 安裝 Windows 的注意事項

大部分 ARM 機器都支持安裝 Windows 11 24H2

安裝過程可能會黑屏，串列控制台可能會顯示 `ConvertPages: failed to find range`，均不影響正常安裝

| 相容性 | 雲服務商 | 實例類型      | 問題                                                                         |
| ------ | -------- | ------------- | ---------------------------------------------------------------------------- |
| ✔️     | Azure    | B2pts_v2      |                                                                              |
| ✔️     | 阿裡雲   | g6r, c6r      |                                                                              |
| ✔️     | 阿裡雲   | g8y, c8y, r8y | 有幾率重啟時卡開機 Logo，強制重啟即可                                        |
| ✔️     | AWS      | T4g           |                                                                              |
| ✔️     | Scaleway | COPARM1       |                                                                              |
| ✔️     | Gcore    |               |                                                                              |
| ❔     | 甲骨文雲 | A1.Flex       | 不一定能安裝成功，越新創建的實例越容易成功<br />安裝後還需要手動載入顯卡驅動 |
| ❌     | 穀歌雲   | t2a           | 缺少網卡驅動                                                                 |

<details>

<summary>甲骨文雲載入顯卡驅動</summary>

使用遠端桌面登錄到伺服器，打開裝置管理員，找到顯卡，選擇更新驅動，在列表中選擇 `Red Hat VirtIO GPU DOD controller` 即可。不需要提前下載驅動。

![virtio-gpu-1](https://github.com/user-attachments/assets/503e1d82-4fa9-4486-917e-73326ad7c988)
![virtio-gpu-2](https://github.com/user-attachments/assets/bf3a9af6-13d8-4f93-9d6c-d3b2dbddb37d)
![virtio-gpu-3](https://github.com/user-attachments/assets/a9006a78-838f-45bf-a556-2dba193d3c03)

</details>

## 討論

[![GitHub Issues](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/bin456789/reinstall/issues)
[![Telegram Group](https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/reinstall_os)

## 如何修改腳本自用

1. Fork 本倉庫
2. 修改 `reinstall.sh` 和 `reinstall.bat` 開頭的 `confhome` 和 `confhome_cn`
3. 修改其它代碼

## 感謝

[![Github Sponsors](https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#EA4AAA)](https://github.com/sponsors/bin456789)

感謝以下商家提供白嫖機器

[![Oracle Cloud](https://github.com/bin456789/reinstall/assets/7548515/8b430ed4-8344-4f96-b4da-c2bda031cc90)](https://www.oracle.com/cloud/)
[![DartNode](https://github.com/bin456789/reinstall/assets/7548515/435d6740-bcdd-4f3a-a196-2f60ae397f17)](https://dartnode.com/)


