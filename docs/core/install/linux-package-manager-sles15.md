---
title: Instalowanie programu .NET Core w systemie SLES 15 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe na SLES 15 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: be5a21db8c3942bfe8827dfbce41bcf88aec342a
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595664"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="7173b-103">SLES 15 Package Manager — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="7173b-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="7173b-104">W tym artykule opisano, jak za pomocą Menedżera pakietów zainstalować platformę .NET Core w systemie SLES 15.</span><span class="sxs-lookup"><span data-stu-id="7173b-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="7173b-105">Dodaj klucz i źródło danych repozytorium Microsoft</span><span class="sxs-lookup"><span data-stu-id="7173b-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="7173b-106">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="7173b-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="7173b-107">Dodaj klucz podpisywania pakietu Microsoft do listy zaufanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="7173b-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="7173b-108">Dodaj repozytorium do Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="7173b-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="7173b-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="7173b-109">Install required dependencies.</span></span>

<span data-ttu-id="7173b-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="7173b-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="7173b-111">Otwórz Terminal i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7173b-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="7173b-112">Obecnie pakiet instalacyjny usługi Microsoft Repository SLES 15 zainstaluje plik *Microsoft-prod.* Repository w niewłaściwym katalogu, uniemożliwiając użyciu narzędzia zypper znalezienie pakietów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7173b-112">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="7173b-113">Aby rozwiązać ten problem, Utwórz link symboliczny w poprawnym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7173b-113">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="7173b-114">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="7173b-114">Install the .NET Core SDK</span></span>

<span data-ttu-id="7173b-115">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="7173b-115">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="7173b-116">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7173b-116">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="7173b-117">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7173b-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="7173b-118">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7173b-118">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="7173b-119">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7173b-119">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="7173b-120">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="7173b-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="7173b-121">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7173b-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="7173b-122">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7173b-122">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="7173b-123">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="7173b-123">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="7173b-124">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="7173b-124">Troubleshoot the package manager</span></span>

<span data-ttu-id="7173b-125">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7173b-125">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="7173b-126">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="7173b-126">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-rpm.md)]
