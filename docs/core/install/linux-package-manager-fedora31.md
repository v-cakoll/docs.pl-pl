---
title: Zainstaluj .NET Core na Fedorze 31 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować .NET Core SDK i środowisko uruchomieniowe w Fedorze 31.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 56e5789132af2aa1171ea51698ae55d1eea5d457
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645311"
---
# <a name="fedora-31-package-manager---install-net-core"></a><span data-ttu-id="acae5-103">Menedżer pakietów Fedory 31 - Zainstaluj .NET Core</span><span class="sxs-lookup"><span data-stu-id="acae5-103">Fedora 31 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="acae5-104">W tym artykule opisano, jak zainstalować program .NET Core w fedorze 31 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="acae5-104">This article describes how to use a package manager to install .NET Core on Fedora 31.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="acae5-105">Dodawanie klucza repozytorium firmy Microsoft i kanału informacyjnego</span><span class="sxs-lookup"><span data-stu-id="acae5-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="acae5-106">Przed zainstalowaniem platformy .NET należy:</span><span class="sxs-lookup"><span data-stu-id="acae5-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="acae5-107">Dodaj klucz podpisywania pakietu firmy Microsoft do listy zaufanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="acae5-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="acae5-108">Dodaj repozytorium do menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="acae5-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="acae5-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="acae5-109">Install required dependencies.</span></span>

<span data-ttu-id="acae5-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="acae5-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="acae5-111">Otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="acae5-111">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="acae5-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="acae5-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="acae5-113">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="acae5-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="acae5-114">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="acae5-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="acae5-115">Instalowanie ASP.NET core środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="acae5-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="acae5-116">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="acae5-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="acae5-117">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="acae5-117">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="acae5-118">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="acae5-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="acae5-119">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="acae5-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="acae5-120">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="acae5-120">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="acae5-121">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="acae5-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="acae5-122">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="acae5-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="acae5-123">Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="acae5-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="acae5-124">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="acae5-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
