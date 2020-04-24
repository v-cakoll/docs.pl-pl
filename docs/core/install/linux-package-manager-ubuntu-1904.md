---
title: Zainstaluj .NET Core na Ubuntu 19.04 package manager - .NET Core
description: Użyj menedżera pakietów, aby zainstalować .NET Core SDK i środowisko uruchomieniowe na Ubuntu 19.04.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 3f338832185ed626289141f48cec88c1bf2e3a33
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645601"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a><span data-ttu-id="62120-103">Ubuntu 19.04 Package Manager - Zainstaluj .NET Core</span><span class="sxs-lookup"><span data-stu-id="62120-103">Ubuntu 19.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="62120-104">W tym artykule opisano, jak zainstalować program .NET Core na Ubuntu 19.04 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="62120-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="62120-105">Dodawanie klucza repozytorium firmy Microsoft i kanału informacyjnego</span><span class="sxs-lookup"><span data-stu-id="62120-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="62120-106">Przed zainstalowaniem platformy .NET należy:</span><span class="sxs-lookup"><span data-stu-id="62120-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="62120-107">Dodaj klucz podpisywania pakietu firmy Microsoft do listy zaufanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="62120-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="62120-108">Dodaj repozytorium do menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="62120-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="62120-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="62120-109">Install required dependencies.</span></span>

<span data-ttu-id="62120-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="62120-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="62120-111">Otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="62120-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="62120-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="62120-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="62120-113">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="62120-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="62120-114">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="62120-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="62120-115">Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować pakietu dotnet-sdk-3.1,** zobacz [sekcję Rozwiązywanie problemów z menedżerem pakietów.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="62120-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="62120-116">Instalowanie ASP.NET core środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="62120-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="62120-117">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="62120-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="62120-118">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="62120-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="62120-119">Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować aspnetcore-runtime-3.1,** zobacz [sekcję Rozwiązywanie problemów z menedżerem pakietów.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="62120-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="62120-120">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="62120-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="62120-121">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="62120-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="62120-122">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="62120-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="62120-123">Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować paczki dotnet-runtime-3.1,** zobacz [sekcję Rozwiązywanie problemów z menedżerem pakietów.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="62120-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="62120-124">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="62120-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="62120-125">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="62120-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="62120-126">Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="62120-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="62120-127">Nie można zlokalizować</span><span class="sxs-lookup"><span data-stu-id="62120-127">Unable to locate</span></span>

<span data-ttu-id="62120-128">Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować pakietu {pakiet .NET Core}**, uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="62120-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="62120-129">Jeśli to nie zadziała, można uruchomić ręczną instalację za pomocą następujących poleceń.</span><span class="sxs-lookup"><span data-stu-id="62120-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="62120-130">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="62120-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
