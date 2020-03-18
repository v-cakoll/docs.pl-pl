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
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="aaed8-103">RHEL 8 Menedżer pakietów — instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="aaed8-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="aaed8-104">W tym artykule opisano sposób instalowania programu .NET Core za pomocą menedżera pakietów w usłudze RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="aaed8-104">This article describes how to use a package manager to install .NET Core on RHEL 8.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="aaed8-105">Zarejestruj subskrypcję Red Hat</span><span class="sxs-lookup"><span data-stu-id="aaed8-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="aaed8-106">Aby zainstalować program .NET Core z red hat na rhel, należy najpierw zarejestrować się za pomocą Menedżera subskrypcji Red Hat.</span><span class="sxs-lookup"><span data-stu-id="aaed8-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="aaed8-107">Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zapoznaj się z [dokumentacją produktu Red Hat dla .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="aaed8-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="aaed8-108">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="aaed8-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="aaed8-109">Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączyć zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aaed8-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="aaed8-110">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="aaed8-110">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="aaed8-111">Instalowanie ASP.NET core runtime</span><span class="sxs-lookup"><span data-stu-id="aaed8-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="aaed8-112">Po zarejestrowaniu się w Menedżerze subskrypcji możesz przystąpić do instalacji i włączyć ASP.NET core runtime.</span><span class="sxs-lookup"><span data-stu-id="aaed8-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="aaed8-113">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="aaed8-113">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="aaed8-114">Instalowanie programu runowego .NET Core</span><span class="sxs-lookup"><span data-stu-id="aaed8-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="aaed8-115">Po zarejestrowaniu się w Menedżerze subskrypcji można przystąpić do instalacji i włączyć program .NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="aaed8-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="aaed8-116">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="aaed8-116">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a><span data-ttu-id="aaed8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aaed8-117">See also</span></span>

- [<span data-ttu-id="aaed8-118">Korzystanie z .NET Core 3.1 w red hat enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="aaed8-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
