---
title: Instalowanie programu .NET Core w systemie SLES 15 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe na SLES 15 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 5551ce8cffa92d4efb6bbe9db2a4887f4b26cd6e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836914"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="6fbbb-103">SLES 15 Package Manager — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="6fbbb-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="6fbbb-104">W tym artykule opisano, jak za pomocą Menedżera pakietów zainstalować platformę .NET Core w systemie SLES 15.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span> <span data-ttu-id="6fbbb-105">Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="6fbbb-106">Rejestrowanie klucza firmy Microsoft i kanału informacyjnego</span><span class="sxs-lookup"><span data-stu-id="6fbbb-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="6fbbb-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="6fbbb-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="6fbbb-108">Rejestrowanie klucza firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="6fbbb-108">Register the Microsoft key</span></span>
- <span data-ttu-id="6fbbb-109">Rejestrowanie repozytorium produktu</span><span class="sxs-lookup"><span data-stu-id="6fbbb-109">register the product repository</span></span>
- <span data-ttu-id="6fbbb-110">Instalowanie wymaganych zależności</span><span class="sxs-lookup"><span data-stu-id="6fbbb-110">Install required dependencies</span></span>

<span data-ttu-id="6fbbb-111">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="6fbbb-112">Otwórz Terminal i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="6fbbb-113">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6fbbb-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="6fbbb-114">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="6fbbb-115">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="6fbbb-116">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6fbbb-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="6fbbb-117">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="6fbbb-118">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="6fbbb-119">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="6fbbb-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="6fbbb-120">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="6fbbb-121">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="6fbbb-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="6fbbb-122">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="6fbbb-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
