---
title: Zainstaluj .NET Core na Linux RHEL 7 package manager - .NET Core
description: Użyj menedżera pakietów, aby zainstalować pakiet .NET Core SDK i środowisko wykonawcze na RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: d1f1372b32c7b2471a96492d48aab5533dadb64a
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134203"
---
# <a name="rhel-7-package-manager---install-net-core"></a>RHEL 7 Package Manager - Zainstaluj .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

W tym artykule opisano, jak zainstalować program .NET Core na rhel 7 za pomocą menedżera pakietów.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Zarejestruj swoją subskrypcję Red Hat

Aby zainstalować program .NET Core z programu Red Hat w programie RHEL, należy najpierw zarejestrować się przy użyciu Menedżera subskrypcji Red Hat. Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zobacz [Dokumentację produktu Red Hat dla platformy .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Zainstalowany zestaw .NET Core SDK

Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączania pakietu .NET Core SDK. W terminalu uruchom następujące polecenia, aby włączyć kanał RHEL 7 dotnet i zainstalować.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Instalowanie ASP.NET Core Runtime

Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączania ASP.NET Core Runtime. W terminalu uruchom następujące polecenia.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a>Instalowanie środowiska wykonawczego .NET Core

Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączenia środowiska uruchomieniowego .NET Core. W terminalu uruchom następujące polecenia.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a>Zobacz też

- [Korzystanie z .NET Core 3.1 w red hat enterprise linux 7](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
