---
title: Zainstaluj .NET Core na Linux RHEL 8 package manager - .NET Core
description: Użyj menedżera pakietów, aby zainstalować pakiet .NET Core SDK i środowisko wykonawcze na RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: b564a386eb67b6e414a832ad3bca10d3d09022bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134194"
---
# <a name="rhel-8-package-manager---install-net-core"></a>RHEL 8 Package Manager - Zainstaluj .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

W tym artykule opisano, jak zainstalować program .NET Core na rhel 8 za pomocą menedżera pakietów.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Zarejestruj swoją subskrypcję Red Hat

Aby zainstalować program .NET Core z programu Red Hat w programie RHEL, należy najpierw zarejestrować się przy użyciu Menedżera subskrypcji Red Hat. Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zobacz [Dokumentację produktu Red Hat dla platformy .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Zainstalowany zestaw .NET Core SDK

Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączania pakietu .NET Core SDK. W terminalu uruchom następujące polecenia.

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instalowanie ASP.NET Core Runtime

Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączania ASP.NET Core Runtime. W terminalu uruchom następujące polecenia.

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalowanie środowiska wykonawczego .NET Core

Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączenia środowiska uruchomieniowego .NET Core. W terminalu uruchom następujące polecenia.

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a>Zobacz też

- [Korzystanie z .NET Core 3.1 w red hat enterprise linux 8](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
