---
title: Zainstaluj .NET Core na serwerze Linux RHEL 8 package manager - .NET Core
description: Użyj menedżera pakietów, aby zainstalować zestaw SDK .NET Core i program runtime w usłudze RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 054494a9b77e1c7803e42c947e067d3eb290f73c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78849811"
---
# <a name="rhel-8-package-manager---install-net-core"></a>RHEL 8 Menedżer pakietów — instalowanie programu .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

W tym artykule opisano sposób instalowania programu .NET Core za pomocą menedżera pakietów w usłudze RHEL 8.

## <a name="register-your-red-hat-subscription"></a>Zarejestruj subskrypcję Red Hat

Aby zainstalować program .NET Core z red hat na rhel, należy najpierw zarejestrować się za pomocą Menedżera subskrypcji Red Hat. Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zapoznaj się z [dokumentacją produktu Red Hat dla .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Zainstalowany zestaw .NET Core SDK

Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączyć zestaw SDK .NET Core. W terminalu uruchom następujące polecenia.

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instalowanie ASP.NET core runtime

Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączyć ASP.NET core runtime. W terminalu uruchom następujące polecenia.

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalowanie programu runowego .NET Core

Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączyć program .NET Core Runtime. W terminalu uruchom następujące polecenia.

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a>Zobacz też

- [Korzystanie z .NET Core 3.1 w red hat enterprise Linux 8](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
