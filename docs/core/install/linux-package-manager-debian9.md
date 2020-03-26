---
title: Zainstaluj .NET Core na Debianie 9 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować .NET Core SDK i środowisko wykonawcze na Debianie 9.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: cfe28d04edfac97938612537986498636c141be0
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134292"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="6cd45-103">Menedżer pakietów Debian 9 - Zainstaluj .NET Core</span><span class="sxs-lookup"><span data-stu-id="6cd45-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="6cd45-104">W tym artykule opisano, jak zainstalować program .NET Core w debianie 9 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="6cd45-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="6cd45-105">Rejestrowanie klucza firmy Microsoft i źródła danych</span><span class="sxs-lookup"><span data-stu-id="6cd45-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="6cd45-106">Przed zainstalowaniem platformy .NET należy:</span><span class="sxs-lookup"><span data-stu-id="6cd45-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="6cd45-107">Zarejestruj klucz firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6cd45-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="6cd45-108">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="6cd45-108">Register the product repository.</span></span>
- <span data-ttu-id="6cd45-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="6cd45-109">Install required dependencies.</span></span>

<span data-ttu-id="6cd45-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="6cd45-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="6cd45-111">Otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="6cd45-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="6cd45-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6cd45-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="6cd45-113">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cd45-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="6cd45-114">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="6cd45-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="6cd45-115">Instalowanie ASP.NET core środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6cd45-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="6cd45-116">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="6cd45-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="6cd45-117">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="6cd45-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="6cd45-118">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="6cd45-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="6cd45-119">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cd45-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="6cd45-120">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="6cd45-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="6cd45-121">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="6cd45-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="6cd45-122">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="6cd45-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="6cd45-123">Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="6cd45-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="6cd45-124">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="6cd45-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
