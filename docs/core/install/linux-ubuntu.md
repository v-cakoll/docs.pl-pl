---
title: Instalowanie programu .NET Core w systemie Ubuntu — .NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core w systemie Ubuntu.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 7045d4d1c3585ba6d26c55ded4653775c9413841
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602958"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a>Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core w systemie Ubuntu

Platforma .NET Core jest obsługiwana w systemie Ubuntu. W tym artykule opisano sposób instalowania programu .NET Core w systemie Ubuntu. Gdy wersja Ubuntu nie jest objęta wsparciem, platforma .NET Core nie jest już obsługiwana w tej wersji. Te instrukcje mogą jednak ułatwić uzyskanie programu .NET Core działającego w tych wersjach, chociaż nie jest to obsługiwane.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Obsługiwane dystrybucje

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core oraz wersji Ubuntu, na których są obsługiwane. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec okresu obsłudze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja [Ubuntu osiągnie koniec cyklu życia](https://wiki.ubuntu.com/Releases).

- ✔️ wskazuje, że wersja programu Ubuntu lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja Ubuntu lub .NET Core nie jest obsługiwana w tej wersji Ubuntu.
- Gdy wersja Ubuntu i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| Ubuntu                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) (tylko instalacja ręczna) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20,04 (LTS)](#2004-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [19,10](#1910-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ❌[19,04](#1904-)       | ✔️ 2,1        | ✔️ 3,1        | ❌wersja zapoznawcza 5,0 |
| ❌[18,10](#1810-)       | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ✔️ [18,04 (LTS)](#1804-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ❌[17,10](#1710-)       | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ❌[17,04](#1704-)       | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ❌[16,10](#1610-)       | ❌2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ✔️ [16,04 (LTS)](#1604-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |

Następujące wersje programu .NET Core nie są już obsługiwane. Pliki do pobrania dla tych nadal są publikowane:

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>Jak zainstalować inne wersje

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a>20,04 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a>19,10 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a>19,04❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a>18,10❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a>18,04 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a>17,10❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a>17,04❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a>16,10❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a>16,04 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a>APT Update — zestaw SDK lub środowisko uruchomieniowe

Gdy dostępna jest nowa wersja poprawek dla programu .NET Core, można po prostu uaktualnić ją za pomocą APT za pomocą następujących poleceń:

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a>Rozwiązywanie problemów z APT

Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas instalowania programu .NET Core przy użyciu programu APT.

### <a name="unable-to-locate"></a>Nie można zlokalizować

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a>Nie można pobrać

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a>Przystawki

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Zależności

Po zainstalowaniu programu przy użyciu Menedżera pakietów te biblioteki są instalowane dla Ciebie. Jeśli jednak ręcznie zainstalujesz platformę .NET Core lub opublikujesz aplikację, musisz upewnić się, że te biblioteki są zainstalowane:

- liblttng-ust0
- libcurl3 (dla 14. x i 16. x)
- libcurl4 (dla 18. x)
- libssl 1.0.0
- libkrb5-3
- zlib1g
- libicu52 (dla 14. x)
- libicu55 (dla 16. x)
- libicu57 (dla 17. x)
- libicu60 (dla 18. x)

W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , wymagana jest również następująca zależność:

- libgdiplus (wersja 6.0.1 lub nowsza)

  > [!WARNING]
  > Aby zainstalować najnowszą wersję programu *libgdiplus* , można dodać do systemu repozytorium mono. Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.

## <a name="scripted-install"></a>Instalacja z skryptami

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Instalacja ręczna

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Następne kroki

- [Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code](../tutorials/with-visual-studio-code.md)
