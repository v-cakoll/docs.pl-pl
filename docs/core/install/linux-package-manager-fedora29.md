---
title: Instalowanie programu .NET Core w programie Fedora 29-Package Manager — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w programie Fedora 29 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 1507687359adaca41465c82541a079f8eac465df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451004"
---
# <a name="fedora-29-package-manager---install-net-core"></a><span data-ttu-id="e0fae-103">Fedora 29 Package Manager — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0fae-103">Fedora 29 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="e0fae-104">W tym artykule opisano, jak za pomocą Menedżera pakietów zainstalować platformę .NET Core w systemie Fedora 29.</span><span class="sxs-lookup"><span data-stu-id="e0fae-104">This article describes how to use a package manager to install .NET Core on Fedora 29.</span></span> <span data-ttu-id="e0fae-105">Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0fae-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="e0fae-106">Zarejestruj klucz i źródło danych firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="e0fae-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="e0fae-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="e0fae-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="e0fae-108">Rejestrowanie klucza firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="e0fae-108">Register the Microsoft key</span></span>
- <span data-ttu-id="e0fae-109">Rejestrowanie repozytorium produktu</span><span class="sxs-lookup"><span data-stu-id="e0fae-109">register the product repository</span></span>
- <span data-ttu-id="e0fae-110">Instalowanie wymaganych zależności</span><span class="sxs-lookup"><span data-stu-id="e0fae-110">Install required dependencies</span></span>

<span data-ttu-id="e0fae-111">Należy to zrobić tylko raz dla każdego komputera.</span><span class="sxs-lookup"><span data-stu-id="e0fae-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="e0fae-112">Otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="e0fae-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="e0fae-113">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e0fae-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="e0fae-114">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e0fae-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="e0fae-115">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="e0fae-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="e0fae-116">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e0fae-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="e0fae-117">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e0fae-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="e0fae-118">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="e0fae-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="e0fae-119">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0fae-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="e0fae-120">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0fae-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="e0fae-121">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="e0fae-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e0fae-122">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="e0fae-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
