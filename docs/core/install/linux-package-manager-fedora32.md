---
title: Instalowanie programu .NET Core w systemie Fedora 32 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie Fedora 32 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624967"
---
# <a name="fedora-32-package-manager---install-net-core"></a><span data-ttu-id="f51dc-103">Menedżer pakietów Fedora 32 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="f51dc-103">Fedora 32 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="f51dc-104">W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania programu .NET Core w systemie Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="f51dc-104">This article describes how to use a package manager to install .NET Core on Fedora 32.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

<span data-ttu-id="f51dc-105">Począwszy od Fedora 32, środowisko .NET Core 3,1 jest dostępne w domyślnych repozytoriach pakietów w Fedora.</span><span class="sxs-lookup"><span data-stu-id="f51dc-105">Starting with Fedora 32, .NET Core 3.1 is available in the default package repositories in Fedora.</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="f51dc-106">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="f51dc-106">Install the .NET Core SDK</span></span>

<span data-ttu-id="f51dc-107">Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f51dc-107">Install the .NET Core SDK.</span></span> <span data-ttu-id="f51dc-108">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="f51dc-108">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="f51dc-109">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f51dc-109">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="f51dc-110">Zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f51dc-110">Install the ASP.NET runtime.</span></span> <span data-ttu-id="f51dc-111">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="f51dc-111">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="f51dc-112">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="f51dc-112">Install the .NET Core runtime</span></span>

<span data-ttu-id="f51dc-113">Zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f51dc-113">Install the .NET Core runtime.</span></span> <span data-ttu-id="f51dc-114">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="f51dc-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="f51dc-115">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="f51dc-115">How to install other versions</span></span>

<span data-ttu-id="f51dc-116">Aby zainstalować inne wersje programu .NET Core, ręcznie zainstaluj [zestaw .NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) lub [środowisko uruchomieniowe programu .NET Core](runtime.md?pivots=os-linux#download-and-manually-install).</span><span class="sxs-lookup"><span data-stu-id="f51dc-116">To install other versions of .NET Core, manually install [the .NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) or [the .NET Core Runtime](runtime.md?pivots=os-linux#download-and-manually-install).</span></span>
