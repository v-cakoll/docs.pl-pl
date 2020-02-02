---
title: Instalowanie programu .NET Core w systemie Fedora 31 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie Fedora 31 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/17/2019
ms.openlocfilehash: 28bda3676f99037e565080e1ff3f9d89a67d0d69
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920782"
---
# <a name="fedora-31-package-manager---install-net-core"></a><span data-ttu-id="0493c-103">Menedżer pakietów Fedora 31 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="0493c-103">Fedora 31 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="0493c-104">W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania platformy .NET Core w systemie Fedora 31.</span><span class="sxs-lookup"><span data-stu-id="0493c-104">This article describes how to use a package manager to install .NET Core on Fedora 31.</span></span> <span data-ttu-id="0493c-105">Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0493c-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="0493c-106">Zarejestruj klucz i źródło danych firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="0493c-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="0493c-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="0493c-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="0493c-108">Zarejestruj klucz Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0493c-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="0493c-109">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="0493c-109">Register the product repository.</span></span>
- <span data-ttu-id="0493c-110">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="0493c-110">Install required dependencies.</span></span>

<span data-ttu-id="0493c-111">Należy to zrobić tylko raz dla każdego komputera.</span><span class="sxs-lookup"><span data-stu-id="0493c-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="0493c-112">Otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="0493c-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="0493c-113">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="0493c-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="0493c-114">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0493c-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="0493c-115">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="0493c-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="0493c-116">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0493c-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="0493c-117">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0493c-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="0493c-118">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="0493c-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="0493c-119">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="0493c-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="0493c-120">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0493c-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="0493c-121">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="0493c-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="0493c-122">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="0493c-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="0493c-123">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="0493c-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="0493c-124">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0493c-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="0493c-125">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="0493c-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
