---
title: Zainstaluj .NET Core na Fedorze 29 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować .NET Core SDK i środowisko uruchomieniowe w Fedorze 29.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: d1cbe38f4f104a8e178d8bcfd1fa1bd6d7645261
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645314"
---
# <a name="fedora-29-package-manager---install-net-core"></a>Menedżer pakietów Fedory 29 - Zainstaluj .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

W tym artykule opisano, jak zainstalować program .NET Core w fedorze 29 za pomocą menedżera pakietów.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a>Dodawanie klucza repozytorium firmy Microsoft i kanału informacyjnego

Przed zainstalowaniem platformy .NET należy:

- Dodaj klucz podpisywania pakietu firmy Microsoft do listy zaufanych kluczy.
- Dodaj repozytorium do menedżera pakietów.
- Zainstaluj wymagane zależności.

Te operacje należy wykonać tylko jeden raz na każdej maszynie.

Otwórz terminal i uruchom następujące polecenia.

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
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
