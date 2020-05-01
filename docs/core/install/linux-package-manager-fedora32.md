---
title: Instalowanie programu .NET Core w systemie Fedora 32 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie Fedora 32 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624967"
---
# <a name="fedora-32-package-manager---install-net-core"></a>Menedżer pakietów Fedora 32 — Instalowanie programu .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania programu .NET Core w systemie Fedora 32.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

Począwszy od Fedora 32, środowisko .NET Core 3,1 jest dostępne w domyślnych repozytoriach pakietów w Fedora.

## <a name="install-the-net-core-sdk"></a>Zainstalowany zestaw .NET Core SDK

Zainstaluj zestaw .NET Core SDK. W terminalu uruchom następujące polecenie.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Zainstaluj środowisko uruchomieniowe ASP.NET Core

Zainstaluj środowisko uruchomieniowe ASP.NET. W terminalu uruchom następujące polecenie.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalowanie środowiska uruchomieniowego platformy .NET Core

Zainstaluj środowisko uruchomieniowe programu .NET Core. W terminalu uruchom następujące polecenie.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Jak zainstalować inne wersje

Aby zainstalować inne wersje programu .NET Core, ręcznie zainstaluj [zestaw .NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) lub [środowisko uruchomieniowe programu .NET Core](runtime.md?pivots=os-linux#download-and-manually-install).
