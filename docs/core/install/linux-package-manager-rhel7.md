---
title: Zainstaluj .NET Core na menedżerze pakietów Linux RHEL 7 - .NET Core
description: Użyj menedżera pakietów, aby zainstalować zestaw SDK .NET Core i program runtime w rhel 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 4f85ed3da8a434fcd5b6ee88491daf623c3c8b31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76980187"
---
# <a name="rhel-7-package-manager---install-net-core"></a>RHEL 7 Menedżer pakietów — instalowanie programu .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

W tym artykule opisano sposób instalowania programu .NET Core za pomocą menedżera pakietów w usłudze RHEL 7.

## <a name="register-your-red-hat-subscription"></a>Zarejestruj subskrypcję Red Hat

Aby zainstalować program .NET Core z red hat na rhel, należy najpierw zarejestrować się za pomocą Menedżera subskrypcji Red Hat. Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zapoznaj się z [dokumentacją produktu Red Hat dla .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Zainstalowany zestaw .NET Core SDK

Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączyć zestaw SDK .NET Core. W terminalu uruchom następujące polecenia, aby włączyć kanał RHEL 7 dotnet i zainstalować.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Instalowanie ASP.NET core runtime

Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączyć ASP.NET core runtime. W terminalu uruchom następujące polecenia.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a>Instalowanie programu runowego .NET Core

Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączyć program .NET Core Runtime. W terminalu uruchom następujące polecenia.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a>Zobacz też

- [Korzystanie z .NET Core 3.1 na Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
