---
title: Instalowanie programu .NET Core w systemie CentOS 7 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie CentOS 7 za pomocą Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 66e78aadf933d3e10b99e3d2c7258733e96164f6
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920853"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="30e7c-103">Menedżer pakietów CentOS 7 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="30e7c-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="30e7c-104">W tym artykule opisano, jak za pomocą Menedżera pakietów zainstalować platformę .NET Core w systemie CentOS 7.</span><span class="sxs-lookup"><span data-stu-id="30e7c-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span> <span data-ttu-id="30e7c-105">Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="30e7c-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="30e7c-106">Zarejestruj klucz i źródło danych firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="30e7c-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="30e7c-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="30e7c-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="30e7c-108">Zarejestruj klucz Microsoft.</span><span class="sxs-lookup"><span data-stu-id="30e7c-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="30e7c-109">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="30e7c-109">Register the product repository.</span></span>
- <span data-ttu-id="30e7c-110">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="30e7c-110">Install required dependencies.</span></span>

<span data-ttu-id="30e7c-111">Należy to zrobić tylko raz dla każdego komputera.</span><span class="sxs-lookup"><span data-stu-id="30e7c-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="30e7c-112">Otwórz Terminal i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="30e7c-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="30e7c-113">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="30e7c-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="30e7c-114">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="30e7c-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="30e7c-115">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="30e7c-115">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="30e7c-116">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="30e7c-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="30e7c-117">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="30e7c-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="30e7c-118">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="30e7c-118">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="30e7c-119">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="30e7c-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="30e7c-120">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30e7c-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="30e7c-121">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="30e7c-121">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="30e7c-122">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="30e7c-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="30e7c-123">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="30e7c-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="30e7c-124">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30e7c-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="30e7c-125">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="30e7c-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
