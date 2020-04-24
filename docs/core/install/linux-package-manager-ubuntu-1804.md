---
title: Zainstaluj .NET Core na Ubuntu 18.04 package manager - .NET Core
description: Użyj menedżera pakietów, aby zainstalować .NET Core SDK i środowisko uruchomieniowe na Ubuntu 18.04.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: ea01c324335c5e0eb120b72fd6384df640f0997e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645612"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a>Ubuntu 18.04 Package Manager - Zainstaluj .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

W tym artykule opisano, jak zainstalować program .NET Core na Ubuntu 18.04 za pomocą menedżera pakietów.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a>Dodawanie klucza repozytorium firmy Microsoft i kanału informacyjnego

Przed zainstalowaniem platformy .NET należy:

- Dodaj klucz podpisywania pakietu firmy Microsoft do listy zaufanych kluczy.
- Dodaj repozytorium do menedżera pakietów.
- Zainstaluj wymagane zależności.

Te operacje należy wykonać tylko jeden raz na każdej maszynie.

Otwórz terminal i uruchom następujące polecenia.

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>Zainstalowany zestaw .NET Core SDK

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core. W terminalu uruchom następujące polecenia.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować pakietu dotnet-sdk-3.1,** zobacz [sekcję Rozwiązywanie problemów z menedżerem pakietów.](#troubleshoot-the-package-manager)

## <a name="install-the-aspnet-core-runtime"></a>Instalowanie ASP.NET core środowiska uruchomieniowego

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET Core runtime. W terminalu uruchom następujące polecenia.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować aspnetcore-runtime-3.1,** zobacz [sekcję Rozwiązywanie problemów z menedżerem pakietów.](#troubleshoot-the-package-manager)

## <a name="install-the-net-core-runtime"></a>Instalowanie środowiska wykonawczego .NET Core

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core. W terminalu uruchom następujące polecenia.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować paczki dotnet-runtime-3.1,** zobacz [sekcję Rozwiązywanie problemów z menedżerem pakietów.](#troubleshoot-the-package-manager)

## <a name="how-to-install-other-versions"></a>Jak zainstalować inne wersje

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Rozwiązywanie problemów z menedżerem pakietów

Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.

### <a name="unable-to-locate"></a>Nie można zlokalizować

Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować pakietu {pakiet .NET Core}**, uruchom następujące polecenia.

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

Jeśli to nie zadziała, można uruchomić ręczną instalację za pomocą następujących poleceń.

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a>Nie można pobrać

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
