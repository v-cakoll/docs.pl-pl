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
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="8a155-103">RHEL 7 Menedżer pakietów — instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="8a155-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="8a155-104">W tym artykule opisano sposób instalowania programu .NET Core za pomocą menedżera pakietów w usłudze RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="8a155-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="8a155-105">Zarejestruj subskrypcję Red Hat</span><span class="sxs-lookup"><span data-stu-id="8a155-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="8a155-106">Aby zainstalować program .NET Core z red hat na rhel, należy najpierw zarejestrować się za pomocą Menedżera subskrypcji Red Hat.</span><span class="sxs-lookup"><span data-stu-id="8a155-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="8a155-107">Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zapoznaj się z [dokumentacją produktu Red Hat dla .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="8a155-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="8a155-108">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="8a155-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="8a155-109">Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączyć zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8a155-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="8a155-110">W terminalu uruchom następujące polecenia, aby włączyć kanał RHEL 7 dotnet i zainstalować.</span><span class="sxs-lookup"><span data-stu-id="8a155-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="8a155-111">Instalowanie ASP.NET core runtime</span><span class="sxs-lookup"><span data-stu-id="8a155-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="8a155-112">Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączyć ASP.NET core runtime.</span><span class="sxs-lookup"><span data-stu-id="8a155-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="8a155-113">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="8a155-113">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="8a155-114">Instalowanie programu runowego .NET Core</span><span class="sxs-lookup"><span data-stu-id="8a155-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="8a155-115">Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączyć program .NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="8a155-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="8a155-116">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="8a155-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a><span data-ttu-id="8a155-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a155-117">See also</span></span>

- [<span data-ttu-id="8a155-118">Korzystanie z .NET Core 3.1 na Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="8a155-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
