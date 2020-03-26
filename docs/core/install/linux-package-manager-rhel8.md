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
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="cf7a3-103">RHEL 8 Package Manager - Zainstaluj .NET Core</span><span class="sxs-lookup"><span data-stu-id="cf7a3-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="cf7a3-104">W tym artykule opisano, jak zainstalować program .NET Core na rhel 8 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-104">This article describes how to use a package manager to install .NET Core on RHEL 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="cf7a3-105">Zarejestruj swoją subskrypcję Red Hat</span><span class="sxs-lookup"><span data-stu-id="cf7a3-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="cf7a3-106">Aby zainstalować program .NET Core z programu Red Hat w programie RHEL, należy najpierw zarejestrować się przy użyciu Menedżera subskrypcji Red Hat.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="cf7a3-107">Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zobacz [Dokumentację produktu Red Hat dla platformy .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="cf7a3-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="cf7a3-108">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="cf7a3-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="cf7a3-109">Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączania pakietu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="cf7a3-110">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-110">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="cf7a3-111">Instalowanie ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="cf7a3-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="cf7a3-112">Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączania ASP.NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="cf7a3-113">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-113">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="cf7a3-114">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="cf7a3-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="cf7a3-115">Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączenia środowiska uruchomieniowego .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="cf7a3-116">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-116">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a><span data-ttu-id="cf7a3-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf7a3-117">See also</span></span>

- [<span data-ttu-id="cf7a3-118">Korzystanie z .NET Core 3.1 w red hat enterprise linux 8</span><span class="sxs-lookup"><span data-stu-id="cf7a3-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
