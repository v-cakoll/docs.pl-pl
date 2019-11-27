---
title: Instalowanie programu .NET Core w systemie Linux RHEL 8,1 Package Manager — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie RHEL 8,1 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 5b658fe4c56b945210534872fe3cc502eb31a763
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450976"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="337a0-103">Menedżer pakietów RHEL 8,1 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="337a0-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="337a0-104">W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania programu .NET Core w systemie RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="337a0-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="337a0-105">Zarejestruj swoją subskrypcję Red Hat</span><span class="sxs-lookup"><span data-stu-id="337a0-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="337a0-106">Aby zainstalować platformę .NET Core z Red Hat na RHEL, należy najpierw zarejestrować się przy użyciu Menedżera subskrypcji Red Hat.</span><span class="sxs-lookup"><span data-stu-id="337a0-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="337a0-107">Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zapoznaj się z [dokumentacją produktu Red Hat dla platformy .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="337a0-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="337a0-108">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="337a0-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="337a0-109">Po zarejestrowaniu się w programie Subscription Manager można przystąpić do instalowania i włączania zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="337a0-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="337a0-110">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="337a0-110">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="337a0-111">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="337a0-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="337a0-112">Po zarejestrowaniu się w programie Subscription Manager można zainstalować i włączyć środowisko uruchomieniowe ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="337a0-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="337a0-113">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="337a0-113">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="337a0-114">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="337a0-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="337a0-115">Po zarejestrowaniu się w programie Subscription Manager można rozpocząć instalację i włączenie środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="337a0-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="337a0-116">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="337a0-116">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```
