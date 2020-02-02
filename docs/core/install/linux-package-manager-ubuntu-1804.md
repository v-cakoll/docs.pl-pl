---
title: Instalowanie programu .NET Core w programie Ubuntu 18,04 Package Manager — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie Ubuntu 18,04 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: e36116d357b8fcd5ced328a574e12c558dd9e2f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920688"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a>Menedżer pakietów Ubuntu 18,04 — Instalowanie programu .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania programu .NET Core w systemie Ubuntu 18,04. Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.

## <a name="register-microsoft-key-and-feed"></a>Zarejestruj klucz i źródło danych firmy Microsoft

Przed zainstalowaniem programu .NET należy:

- Zarejestruj klucz Microsoft.
- Zarejestruj repozytorium produktów.
- Zainstaluj wymagane zależności.

Należy to zrobić tylko raz dla każdego komputera.

Otwórz Terminal i uruchom następujące polecenia.

```bash
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>Zainstaluj zestaw .NET Core SDK

Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK. W terminalu uruchom następujące polecenia.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> Jeśli zostanie wyświetlony komunikat o błędzie podobny do **nie można zlokalizować pakietu dotnet-SDK-3,1**, zobacz sekcję [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) .

## <a name="install-the-aspnet-core-runtime"></a>Zainstaluj środowisko uruchomieniowe ASP.NET Core

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe ASP.NET Core. W terminalu uruchom następujące polecenia.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Jeśli zostanie wyświetlony komunikat o błędzie podobny do sytuacji, w której **nie można znaleźć pakietu aspnetcore-Runtime-3,1**, zobacz sekcję [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) .

## <a name="install-the-net-core-runtime"></a>Instalowanie środowiska uruchomieniowego platformy .NET Core

Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core. W terminalu uruchom następujące polecenia.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> Jeśli zostanie wyświetlony komunikat o błędzie podobny do sytuacji, w której **nie można znaleźć pakietu dotnet-Runtime-3,1**, zobacz sekcję [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) .

## <a name="how-to-install-other-versions"></a>Jak zainstalować inne wersje

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Rozwiązywanie problemów z menedżerem pakietów

Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.

### <a name="unable-to-locate"></a>Nie można zlokalizować

Jeśli zostanie wyświetlony komunikat o błędzie podobny do następującego: **nie można zlokalizować pakietu {pakiet .NET Core}** , uruchom następujące polecenia.

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

Jeśli to nie zadziała, można uruchomić instalację ręczną przy użyciu następujących poleceń.

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a>Nie można pobrać

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
