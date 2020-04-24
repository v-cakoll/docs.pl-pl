---
title: Zainstaluj .NET Core na Debianie 10 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować .NET Core SDK i środowisko wykonawcze na Debianie 10.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: a312496ed9a26783198cdd038db7ffa2bdc7381e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645291"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="c47bd-103">Menedżer pakietów Debian 10 - Zainstaluj .NET Core</span><span class="sxs-lookup"><span data-stu-id="c47bd-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="c47bd-104">W tym artykule opisano, jak zainstalować program .NET Core w debianie 10 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="c47bd-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="c47bd-105">Dodawanie klucza repozytorium firmy Microsoft i kanału informacyjnego</span><span class="sxs-lookup"><span data-stu-id="c47bd-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="c47bd-106">Przed zainstalowaniem platformy .NET należy:</span><span class="sxs-lookup"><span data-stu-id="c47bd-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="c47bd-107">Dodaj klucz podpisywania pakietu firmy Microsoft do listy zaufanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="c47bd-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="c47bd-108">Dodaj repozytorium do menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="c47bd-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="c47bd-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="c47bd-109">Install required dependencies.</span></span>

<span data-ttu-id="c47bd-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="c47bd-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="c47bd-111">Otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="c47bd-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="c47bd-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c47bd-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="c47bd-113">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c47bd-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="c47bd-114">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="c47bd-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="c47bd-115">Instalowanie ASP.NET core środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c47bd-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="c47bd-116">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="c47bd-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="c47bd-117">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="c47bd-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="c47bd-118">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="c47bd-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="c47bd-119">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c47bd-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="c47bd-120">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="c47bd-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c47bd-121">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="c47bd-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="c47bd-122">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="c47bd-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="c47bd-123">Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="c47bd-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="c47bd-124">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="c47bd-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
