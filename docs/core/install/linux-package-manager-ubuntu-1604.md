---
title: Zainstaluj .NET Core na Ubuntu 16.04 package manager - .NET Core
description: Użyj menedżera pakietów, aby zainstalować .NET Core SDK i środowisko uruchomieniowe na Ubuntu 16.04.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 9e99cd8649e907fbbf8ffac7bfc008610396a31c
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134170"
---
# <a name="ubuntu-1604-package-manager---install-net-core"></a><span data-ttu-id="8d79a-103">Ubuntu 16.04 Package Manager - Zainstaluj .NET Core</span><span class="sxs-lookup"><span data-stu-id="8d79a-103">Ubuntu 16.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="8d79a-104">W tym artykule opisano, jak zainstalować program .NET Core na Ubuntu 16.04 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="8d79a-104">This article describes how to use a package manager to install .NET Core on Ubuntu 16.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="8d79a-105">Rejestrowanie klucza firmy Microsoft i źródła danych</span><span class="sxs-lookup"><span data-stu-id="8d79a-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="8d79a-106">Przed zainstalowaniem platformy .NET należy:</span><span class="sxs-lookup"><span data-stu-id="8d79a-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="8d79a-107">Zarejestruj klucz firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8d79a-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="8d79a-108">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="8d79a-108">Register the product repository.</span></span>
- <span data-ttu-id="8d79a-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="8d79a-109">Install required dependencies.</span></span>

<span data-ttu-id="8d79a-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="8d79a-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="8d79a-111">Otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d79a-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="8d79a-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="8d79a-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="8d79a-113">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8d79a-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="8d79a-114">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d79a-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="8d79a-115">Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować pakietu dotnet-sdk-3.1,** zobacz [sekcję Rozwiązywanie problemów z menedżerem pakietów.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="8d79a-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="8d79a-116">Instalowanie ASP.NET core środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="8d79a-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="8d79a-117">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="8d79a-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="8d79a-118">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d79a-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="8d79a-119">Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować aspnetcore-runtime-3.1,** zobacz [sekcję Rozwiązywanie problemów z menedżerem pakietów.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="8d79a-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="8d79a-120">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="8d79a-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="8d79a-121">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8d79a-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="8d79a-122">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d79a-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="8d79a-123">Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować paczki dotnet-runtime-3.1,** zobacz [sekcję Rozwiązywanie problemów z menedżerem pakietów.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="8d79a-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="8d79a-124">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="8d79a-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="8d79a-125">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="8d79a-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="8d79a-126">Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="8d79a-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="8d79a-127">Nie można zlokalizować</span><span class="sxs-lookup"><span data-stu-id="8d79a-127">Unable to locate</span></span>

<span data-ttu-id="8d79a-128">Jeśli zostanie wyświetlony komunikat o błędzie podobny **do Nie można zlokalizować pakietu {pakiet .NET Core}**, uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d79a-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="8d79a-129">Jeśli to nie zadziała, można uruchomić ręczną instalację za pomocą następujących poleceń.</span><span class="sxs-lookup"><span data-stu-id="8d79a-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/16.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="8d79a-130">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="8d79a-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
