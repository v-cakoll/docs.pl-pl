---
title: Instalowanie programu .NET Core w systemie Linux RHEL 7 Package Manager — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie RHEL 7 za pomocą Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: bcc41bfcd7c6d03038952e3faaf07952c3deb69d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715537"
---
# <a name="rhel-7-package-manager---install-net-core"></a>Menedżer pakietów RHEL 7 — Instalowanie programu .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

W tym artykule opisano, jak za pomocą Menedżera pakietów zainstalować platformę .NET Core w systemie RHEL 7. Platforma .NET Core 3,1 nie jest jeszcze dostępna dla RHEL 7.

## <a name="register-your-red-hat-subscription"></a>Zarejestruj swoją subskrypcję Red Hat

Aby zainstalować platformę .NET Core z Red Hat na RHEL, należy najpierw zarejestrować się przy użyciu Menedżera subskrypcji Red Hat. Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zapoznaj się z [dokumentacją produktu Red Hat dla platformy .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Zainstaluj zestaw .NET Core SDK

Po zarejestrowaniu się w programie Subscription Manager można przystąpić do instalowania i włączania zestaw .NET Core SDK. W terminalu uruchom następujące polecenia, aby włączyć kanał dotnet RHEL 7 i zainstalować.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Zainstaluj środowisko uruchomieniowe ASP.NET Core

Po zarejestrowaniu się w programie Subscription Manager można zainstalować i włączyć środowisko uruchomieniowe ASP.NET Core. W terminalu uruchom następujące polecenia.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a>Instalowanie środowiska uruchomieniowego platformy .NET Core

Po zarejestrowaniu się w programie Subscription Manager można rozpocząć instalację i włączenie środowiska uruchomieniowego platformy .NET Core. W terminalu uruchom następujące polecenia.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a>Zobacz także

- [Korzystanie z platformy .NET Core 3,0 w Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)
