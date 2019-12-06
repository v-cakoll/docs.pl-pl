---
title: Instalowanie programu .NET Core w systemie Debian 9 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w programie Debian 9 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: b8b6a3039efcc2fbd15e0c3948984086c619bd44
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836935"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="87283-103">Menedżer pakietów Debian 9 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="87283-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="87283-104">W tym artykule opisano, jak za pomocą Menedżera pakietów zainstalować platformę .NET Core w systemie Debian 9.</span><span class="sxs-lookup"><span data-stu-id="87283-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span> <span data-ttu-id="87283-105">Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="87283-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="87283-106">Rejestrowanie klucza firmy Microsoft i kanału informacyjnego</span><span class="sxs-lookup"><span data-stu-id="87283-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="87283-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="87283-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="87283-108">Rejestrowanie klucza firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="87283-108">Register the Microsoft key</span></span>
- <span data-ttu-id="87283-109">Rejestrowanie repozytorium produktu</span><span class="sxs-lookup"><span data-stu-id="87283-109">register the product repository</span></span>
- <span data-ttu-id="87283-110">Instalowanie wymaganych zależności</span><span class="sxs-lookup"><span data-stu-id="87283-110">Install required dependencies</span></span>

<span data-ttu-id="87283-111">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="87283-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="87283-112">Otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="87283-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="87283-113">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="87283-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="87283-114">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="87283-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="87283-115">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="87283-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="87283-116">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="87283-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="87283-117">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="87283-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="87283-118">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="87283-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="87283-119">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="87283-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="87283-120">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87283-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="87283-121">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="87283-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="87283-122">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="87283-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
