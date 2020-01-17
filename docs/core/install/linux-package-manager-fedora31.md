---
title: Instalowanie programu .NET Core w systemie Fedora 31 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie Fedora 31 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/17/2019
ms.openlocfilehash: 25c670694ed2d9e89fe37cedf0b06efd8bc93293
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116967"
---
# <a name="fedora-31-package-manager---install-net-core"></a><span data-ttu-id="2f84f-103">Menedżer pakietów Fedora 31 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="2f84f-103">Fedora 31 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="2f84f-104">W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania platformy .NET Core w systemie Fedora 31.</span><span class="sxs-lookup"><span data-stu-id="2f84f-104">This article describes how to use a package manager to install .NET Core on Fedora 31.</span></span> <span data-ttu-id="2f84f-105">Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f84f-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="2f84f-106">Rejestrowanie klucza firmy Microsoft i źródła danych</span><span class="sxs-lookup"><span data-stu-id="2f84f-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="2f84f-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="2f84f-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="2f84f-108">Zarejestruj klucz Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2f84f-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="2f84f-109">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="2f84f-109">Register the product repository.</span></span>
- <span data-ttu-id="2f84f-110">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="2f84f-110">Install required dependencies.</span></span>

<span data-ttu-id="2f84f-111">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="2f84f-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="2f84f-112">Otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="2f84f-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="2f84f-113">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="2f84f-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="2f84f-114">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="2f84f-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="2f84f-115">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="2f84f-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="2f84f-116">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2f84f-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="2f84f-117">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2f84f-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="2f84f-118">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="2f84f-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="2f84f-119">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="2f84f-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="2f84f-120">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f84f-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="2f84f-121">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="2f84f-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="2f84f-122">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="2f84f-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
