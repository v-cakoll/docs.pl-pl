---
title: Instalowanie programu .NET Core w systemie SLES 12 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie SLES 12 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a6c10c6b11bc57ae4bbe814c66c563b85ce3c22b
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920731"
---
# <a name="sles-12-package-manager---install-net-core"></a><span data-ttu-id="55be8-103">SLES 12 — Menedżer pakietów — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="55be8-103">SLES 12 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="55be8-104">W tym artykule opisano, jak za pomocą Menedżera pakietów zainstalować platformę .NET Core w systemie SLES 12.</span><span class="sxs-lookup"><span data-stu-id="55be8-104">This article describes how to use a package manager to install .NET Core on SLES 12.</span></span> <span data-ttu-id="55be8-105">Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="55be8-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="55be8-106">Zarejestruj klucz i źródło danych firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="55be8-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="55be8-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="55be8-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="55be8-108">Zarejestruj klucz Microsoft.</span><span class="sxs-lookup"><span data-stu-id="55be8-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="55be8-109">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="55be8-109">Register the product repository.</span></span>
- <span data-ttu-id="55be8-110">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="55be8-110">Install required dependencies.</span></span>

<span data-ttu-id="55be8-111">Należy to zrobić tylko raz dla każdego komputera.</span><span class="sxs-lookup"><span data-stu-id="55be8-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="55be8-112">Otwórz Terminal i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="55be8-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="55be8-113">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="55be8-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="55be8-114">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="55be8-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="55be8-115">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="55be8-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="55be8-116">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="55be8-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="55be8-117">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="55be8-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="55be8-118">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="55be8-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="55be8-119">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="55be8-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="55be8-120">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55be8-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="55be8-121">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="55be8-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="55be8-122">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="55be8-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="55be8-123">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="55be8-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="55be8-124">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55be8-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="55be8-125">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="55be8-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
