---
title: Zainstaluj .NET Core na Menedżerze pakietów Ubuntu 19.10 - .NET Core
description: Użyj menedżera pakietów, aby zainstalować zestaw .NET Core SDK i program runtime na Ubuntu 19.10.
author: thraka
ms.author: adegeo
ms.date: 01/16/2020
ms.openlocfilehash: b8fec2afa6f03e3dabbf1ff449431759087163ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920651"
---
# <a name="ubuntu-1910-package-manager---install-net-core"></a>Menedżer pakietów Ubuntu 19.10 — instalowanie programu .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

W tym artykule opisano, jak zainstalować program .NET Core za pomocą menedżera pakietów na stronie Ubuntu 19.10. Jeśli instalujesz program runtime, zalecamy zainstalowanie [ASP.NET core runtime](#install-the-aspnet-core-runtime), ponieważ zawiera zarówno .NET Core, jak i ASP.NET core.

## <a name="register-microsoft-key-and-feed"></a>Rejestrowanie klucza firmy Microsoft i źródła danych

Przed zainstalowaniem programu .NET należy:

- Zarejestruj klucz firmy Microsoft.
- Zarejestruj repozytorium produktów.
- Zainstaluj wymagane zależności.

Te operacje należy wykonać tylko jeden raz na każdej maszynie.

Otwórz terminal i uruchom następujące polecenia.

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>Zainstalowany zestaw .NET Core SDK

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw .NET Core SDK. W terminalu uruchom następujące polecenia.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> Jeśli zostanie wyświetlony komunikat o błędzie podobny do **Nie można zlokalizować pakietu dotnet-sdk-3.1**, zobacz [Sekcję Rozwiązywanie problemów z menedżerem pakietów.](#troubleshoot-the-package-manager)

## <a name="install-the-aspnet-core-runtime"></a>Instalowanie ASP.NET core

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET core. W terminalu uruchom następujące polecenia.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Jeśli zostanie wyświetlony komunikat o błędzie podobny do **Nie można zlokalizować pakietu aspnetcore-runtime-3.1**, zobacz [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) sekcji.

## <a name="install-the-net-core-runtime"></a>Instalowanie programu .NET Core

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj program .NET Core. W terminalu uruchom następujące polecenia.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> Jeśli zostanie wyświetlony komunikat o błędzie podobny do **Nie można zlokalizować pakietu dotnet-runtime-3.1**, zobacz [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) sekcji.

## <a name="how-to-install-other-versions"></a>Jak zainstalować inne wersje

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Rozwiązywanie problemów z menedżerem pakietów

Ta sekcja zawiera informacje o typowych błędach, które mogą pojawić się podczas instalowania programu .NET Core za pomocą Menedżera pakietów.

### <a name="unable-to-locate"></a>Nie można zlokalizować

Jeśli zostanie wyświetlony komunikat o błędzie podobny do **Nie można zlokalizować pakietu {pakiet .NET Core},** uruchom następujące polecenia.

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

Jeśli to nie zadziała, można uruchomić instalację ręczną za pomocą następujących poleceń.

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a>Nie można pobrać

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
