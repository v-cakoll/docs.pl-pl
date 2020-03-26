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
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="72395-103">RHEL 7 Package Manager - Zainstaluj .NET Core</span><span class="sxs-lookup"><span data-stu-id="72395-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="72395-104">W tym artykule opisano, jak zainstalować program .NET Core na rhel 7 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="72395-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="72395-105">Zarejestruj swoją subskrypcję Red Hat</span><span class="sxs-lookup"><span data-stu-id="72395-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="72395-106">Aby zainstalować program .NET Core z programu Red Hat w programie RHEL, należy najpierw zarejestrować się przy użyciu Menedżera subskrypcji Red Hat.</span><span class="sxs-lookup"><span data-stu-id="72395-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="72395-107">Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zobacz [Dokumentację produktu Red Hat dla platformy .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="72395-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="72395-108">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="72395-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="72395-109">Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączania pakietu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="72395-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="72395-110">W terminalu uruchom następujące polecenia, aby włączyć kanał RHEL 7 dotnet i zainstalować.</span><span class="sxs-lookup"><span data-stu-id="72395-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="72395-111">Instalowanie ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="72395-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="72395-112">Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączania ASP.NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="72395-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="72395-113">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="72395-113">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="72395-114">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="72395-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="72395-115">Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączenia środowiska uruchomieniowego .NET Core.</span><span class="sxs-lookup"><span data-stu-id="72395-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="72395-116">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="72395-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a><span data-ttu-id="72395-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72395-117">See also</span></span>

- [<span data-ttu-id="72395-118">Korzystanie z .NET Core 3.1 w red hat enterprise linux 7</span><span class="sxs-lookup"><span data-stu-id="72395-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
