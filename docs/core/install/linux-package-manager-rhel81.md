---
title: Instalowanie programu .NET Core w systemie Linux RHEL 8,1 Package Manager — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie RHEL 8,1 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 20fb3e9e517858b9cc5d6e9c1bd97bf949558843
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800740"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="7aabb-103">Menedżer pakietów RHEL 8,1 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="7aabb-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="7aabb-104">W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania programu .NET Core w systemie RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="7aabb-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="7aabb-105">RHEL 8,0 nie obejmuje .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="7aabb-105">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="7aabb-106">Użyj polecenia `yum upgrade`, aby zaktualizować program do RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="7aabb-106">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="7aabb-107">Zarejestruj swoją subskrypcję Red Hat</span><span class="sxs-lookup"><span data-stu-id="7aabb-107">Register your Red Hat subscription</span></span>

<span data-ttu-id="7aabb-108">Aby zainstalować platformę .NET Core z Red Hat na RHEL, należy najpierw zarejestrować się przy użyciu Menedżera subskrypcji Red Hat.</span><span class="sxs-lookup"><span data-stu-id="7aabb-108">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="7aabb-109">Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zapoznaj się z [dokumentacją produktu Red Hat dla platformy .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="7aabb-109">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="7aabb-110">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="7aabb-110">Install the .NET Core SDK</span></span>

<span data-ttu-id="7aabb-111">Po zarejestrowaniu się w programie Subscription Manager można przystąpić do instalowania i włączania zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="7aabb-111">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="7aabb-112">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="7aabb-112">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="7aabb-113">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7aabb-113">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="7aabb-114">Po zarejestrowaniu się w programie Subscription Manager można zainstalować i włączyć środowisko uruchomieniowe ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7aabb-114">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="7aabb-115">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="7aabb-115">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="7aabb-116">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="7aabb-116">Install the .NET Core Runtime</span></span>

<span data-ttu-id="7aabb-117">Po zarejestrowaniu się w programie Subscription Manager można rozpocząć instalację i włączenie środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7aabb-117">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="7aabb-118">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="7aabb-118">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a><span data-ttu-id="7aabb-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7aabb-119">See also</span></span>

- [<span data-ttu-id="7aabb-120">Korzystanie z platformy .NET Core 3,0 w Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="7aabb-120">Using .NET Core 3.0 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
