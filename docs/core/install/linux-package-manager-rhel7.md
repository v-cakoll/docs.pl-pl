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
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="61f6f-103">Menedżer pakietów RHEL 7 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="61f6f-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="61f6f-104">W tym artykule opisano, jak za pomocą Menedżera pakietów zainstalować platformę .NET Core w systemie RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="61f6f-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span> <span data-ttu-id="61f6f-105">Platforma .NET Core 3,1 nie jest jeszcze dostępna dla RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="61f6f-105">.NET Core 3.1 is not yet available for RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="61f6f-106">Zarejestruj swoją subskrypcję Red Hat</span><span class="sxs-lookup"><span data-stu-id="61f6f-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="61f6f-107">Aby zainstalować platformę .NET Core z Red Hat na RHEL, należy najpierw zarejestrować się przy użyciu Menedżera subskrypcji Red Hat.</span><span class="sxs-lookup"><span data-stu-id="61f6f-107">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="61f6f-108">Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zapoznaj się z [dokumentacją produktu Red Hat dla platformy .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="61f6f-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="61f6f-109">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="61f6f-109">Install the .NET Core SDK</span></span>

<span data-ttu-id="61f6f-110">Po zarejestrowaniu się w programie Subscription Manager można przystąpić do instalowania i włączania zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="61f6f-110">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="61f6f-111">W terminalu uruchom następujące polecenia, aby włączyć kanał dotnet RHEL 7 i zainstalować.</span><span class="sxs-lookup"><span data-stu-id="61f6f-111">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="61f6f-112">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="61f6f-112">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="61f6f-113">Po zarejestrowaniu się w programie Subscription Manager można zainstalować i włączyć środowisko uruchomieniowe ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="61f6f-113">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="61f6f-114">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="61f6f-114">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="61f6f-115">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="61f6f-115">Install the .NET Core Runtime</span></span>

<span data-ttu-id="61f6f-116">Po zarejestrowaniu się w programie Subscription Manager można rozpocząć instalację i włączenie środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="61f6f-116">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="61f6f-117">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="61f6f-117">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a><span data-ttu-id="61f6f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61f6f-118">See also</span></span>

- [<span data-ttu-id="61f6f-119">Korzystanie z platformy .NET Core 3,0 w Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="61f6f-119">Using .NET Core 3.0 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)
