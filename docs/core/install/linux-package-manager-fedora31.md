---
title: Zainstaluj .NET Core na Fedorze 31 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować .NET Core SDK i środowisko uruchomieniowe w Fedorze 31.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: e6ead528c441c37d089ebb33719494353de41433
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134248"
---
# <a name="fedora-31-package-manager---install-net-core"></a>Menedżer pakietów Fedory 31 - Zainstaluj .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

W tym artykule opisano, jak zainstalować program .NET Core w fedorze 31 za pomocą menedżera pakietów.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a>Rejestrowanie klucza firmy Microsoft i źródła danych

Przed zainstalowaniem platformy .NET należy:

- Zarejestruj klucz firmy Microsoft.
- Zarejestruj repozytorium produktów.
- Zainstaluj wymagane zależności.

Te operacje należy wykonać tylko jeden raz na każdej maszynie.

Otwórz terminal i uruchom następujące polecenia.

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a>Zainstalowany zestaw .NET Core SDK

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core. W terminalu uruchom następujące polecenie.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instalowanie ASP.NET core środowiska uruchomieniowego

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET środowisko wykonawcze. W terminalu uruchom następujące polecenie.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalowanie środowiska wykonawczego .NET Core

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core. W terminalu uruchom następujące polecenie.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Jak zainstalować inne wersje

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Rozwiązywanie problemów z menedżerem pakietów

Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.

### <a name="failed-to-fetch"></a>Nie można pobrać

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
