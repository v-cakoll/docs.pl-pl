---
title: Instalowanie programu .NET Core w programie Ubuntu 20,04 Package Manager — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie Ubuntu 20,04 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 04/15/2020
ms.openlocfilehash: b99dcbab3305bffdcc9202bb2a09e3061abca95b
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82148381"
---
# <a name="ubuntu-2004-package-manager---install-net-core"></a><span data-ttu-id="23a45-103">Menedżer pakietów Ubuntu 20,04 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="23a45-103">Ubuntu 20.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="23a45-104">W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania programu .NET Core w systemie Ubuntu 20,04.</span><span class="sxs-lookup"><span data-stu-id="23a45-104">This article describes how to use a package manager to install .NET Core on Ubuntu 20.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="23a45-105">Dodaj klucz i źródło danych repozytorium Microsoft</span><span class="sxs-lookup"><span data-stu-id="23a45-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="23a45-106">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="23a45-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="23a45-107">Dodaj klucz podpisywania pakietu Microsoft do listy zaufanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="23a45-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="23a45-108">Dodaj repozytorium do Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="23a45-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="23a45-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="23a45-109">Install required dependencies.</span></span>

<span data-ttu-id="23a45-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="23a45-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="23a45-111">Otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="23a45-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="23a45-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="23a45-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="23a45-113">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="23a45-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="23a45-114">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="23a45-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="23a45-115">Jeśli zostanie wyświetlony komunikat o błędzie podobny do **nie można zlokalizować pakietu dotnet-SDK-3,1**, zobacz sekcję [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="23a45-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="23a45-116">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="23a45-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="23a45-117">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="23a45-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="23a45-118">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="23a45-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="23a45-119">Jeśli zostanie wyświetlony komunikat o błędzie podobny do sytuacji, w której **nie można znaleźć pakietu aspnetcore-Runtime-3,1**, zobacz sekcję [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="23a45-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="23a45-120">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="23a45-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="23a45-121">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="23a45-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="23a45-122">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="23a45-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="23a45-123">Jeśli zostanie wyświetlony komunikat o błędzie podobny do sytuacji, w której **nie można znaleźć pakietu dotnet-Runtime-3,1**, zobacz sekcję [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="23a45-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="23a45-124">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="23a45-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="23a45-125">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="23a45-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="23a45-126">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="23a45-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="23a45-127">Nie można zlokalizować</span><span class="sxs-lookup"><span data-stu-id="23a45-127">Unable to locate</span></span>

<span data-ttu-id="23a45-128">Jeśli zostanie wyświetlony komunikat o błędzie podobny do następującego: **nie można zlokalizować pakietu {pakiet .NET Core}**, uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="23a45-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="23a45-129">Jeśli to nie zadziała, można uruchomić instalację ręczną przy użyciu następujących poleceń.</span><span class="sxs-lookup"><span data-stu-id="23a45-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/20.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="23a45-130">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="23a45-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
