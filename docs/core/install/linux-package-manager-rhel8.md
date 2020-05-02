---
title: Instalowanie programu .NET Core w systemie Linux RHEL 8 Package Manager — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w programie RHEL 8 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: 8829e842e920e6abd4184b5140f80bb016acace2
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728238"
---
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="5b789-103">Menedżer pakietów RHEL 8 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="5b789-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="5b789-104">W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania programu .NET Core w systemie Red Hat Enterprise Linux (RHEL) 8.</span><span class="sxs-lookup"><span data-stu-id="5b789-104">This article describes how to use a package manager to install .NET Core on Red Hat Enterprise Linux (RHEL) 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="5b789-105">Zarejestruj swoją subskrypcję Red Hat</span><span class="sxs-lookup"><span data-stu-id="5b789-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="5b789-106">Aby zainstalować platformę .NET Core z Red Hat na RHEL, należy najpierw zarejestrować się przy użyciu Menedżera subskrypcji Red Hat.</span><span class="sxs-lookup"><span data-stu-id="5b789-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="5b789-107">Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zapoznaj się z [dokumentacją produktu Red Hat dla platformy .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="5b789-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="5b789-108">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="5b789-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="5b789-109">Po zarejestrowaniu się w programie Subscription Manager można przystąpić do instalowania i włączania zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5b789-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="5b789-110">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="5b789-110">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="5b789-111">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5b789-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="5b789-112">Po zarejestrowaniu się w programie Subscription Manager można zainstalować i włączyć środowisko uruchomieniowe ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5b789-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="5b789-113">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="5b789-113">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="5b789-114">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="5b789-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="5b789-115">Po zarejestrowaniu się w programie Subscription Manager można rozpocząć instalację i włączenie środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5b789-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="5b789-116">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="5b789-116">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="5b789-117">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="5b789-117">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="see-also"></a><span data-ttu-id="5b789-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b789-118">See also</span></span>

- [<span data-ttu-id="5b789-119">Korzystanie z platformy .NET Core 3,1 w Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="5b789-119">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
