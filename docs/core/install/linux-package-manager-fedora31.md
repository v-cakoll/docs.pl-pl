---
title: Instalowanie programu .NET Core w systemie Fedora 31 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie Fedora 31 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/17/2019
ms.openlocfilehash: 25c670694ed2d9e89fe37cedf0b06efd8bc93293
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116967"
---
# <a name="fedora-31-package-manager---install-net-core"></a>Menedżer pakietów Fedora 31 — Instalowanie programu .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania platformy .NET Core w systemie Fedora 31. Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.

## <a name="register-microsoft-key-and-feed"></a>Rejestrowanie klucza firmy Microsoft i źródła danych

Przed zainstalowaniem programu .NET należy:

- Zarejestruj klucz Microsoft.
- Zarejestruj repozytorium produktów.
- Zainstaluj wymagane zależności.

Te operacje należy wykonać tylko jeden raz na każdej maszynie.

Otwórz Terminal i uruchom następujące polecenia.

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a>Zainstaluj zestaw .NET Core SDK

Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK. W terminalu uruchom następujące polecenie.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Zainstaluj środowisko uruchomieniowe ASP.NET Core

Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET. W terminalu uruchom następujące polecenie.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalowanie środowiska uruchomieniowego platformy .NET Core

Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core. W terminalu uruchom następujące polecenie.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Jak zainstalować inne wersje

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
