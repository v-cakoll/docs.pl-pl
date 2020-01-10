---
title: Instalowanie programu .NET Core w systemie SLES 15 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe na SLES 15 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 18a0068e5494d6a25e9cd278ce88f5915e2000b8
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740646"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="9b3a5-103">SLES 15 Package Manager — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="9b3a5-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="9b3a5-104">W tym artykule opisano, jak za pomocą Menedżera pakietów zainstalować platformę .NET Core w systemie SLES 15.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span> <span data-ttu-id="9b3a5-105">Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="9b3a5-106">Rejestrowanie klucza firmy Microsoft i źródła danych</span><span class="sxs-lookup"><span data-stu-id="9b3a5-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="9b3a5-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="9b3a5-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="9b3a5-108">Zarejestruj klucz Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="9b3a5-109">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-109">Register the product repository.</span></span>
- <span data-ttu-id="9b3a5-110">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-110">Install required dependencies.</span></span>

<span data-ttu-id="9b3a5-111">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="9b3a5-112">Otwórz Terminal i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="9b3a5-113">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="9b3a5-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="9b3a5-114">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="9b3a5-115">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="9b3a5-116">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9b3a5-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="9b3a5-117">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="9b3a5-118">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="9b3a5-119">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="9b3a5-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="9b3a5-120">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="9b3a5-121">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="9b3a5-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="9b3a5-122">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="9b3a5-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
