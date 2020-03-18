---
title: Zainstaluj .NET Core na Menedżerze pakietów Ubuntu 18.04 - .NET Core
description: Użyj menedżera pakietów, aby zainstalować zestaw .NET Core SDK i czas uruchomieniowy na Ubuntu 18.04.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: e36116d357b8fcd5ced328a574e12c558dd9e2f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920688"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a><span data-ttu-id="38099-103">Menedżer pakietów Ubuntu 18.04 — instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="38099-103">Ubuntu 18.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="38099-104">W tym artykule opisano, jak zainstalować program .NET Core za pomocą menedżera pakietów w ubuntu 18.04.</span><span class="sxs-lookup"><span data-stu-id="38099-104">This article describes how to use a package manager to install .NET Core on Ubuntu 18.04.</span></span> <span data-ttu-id="38099-105">Jeśli instalujesz program runtime, zalecamy zainstalowanie [ASP.NET core runtime](#install-the-aspnet-core-runtime), ponieważ zawiera zarówno .NET Core, jak i ASP.NET core.</span><span class="sxs-lookup"><span data-stu-id="38099-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="38099-106">Rejestrowanie klucza firmy Microsoft i źródła danych</span><span class="sxs-lookup"><span data-stu-id="38099-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="38099-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="38099-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="38099-108">Zarejestruj klucz firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38099-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="38099-109">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="38099-109">Register the product repository.</span></span>
- <span data-ttu-id="38099-110">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="38099-110">Install required dependencies.</span></span>

<span data-ttu-id="38099-111">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="38099-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="38099-112">Otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="38099-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="38099-113">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="38099-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="38099-114">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="38099-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="38099-115">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="38099-115">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="38099-116">Jeśli zostanie wyświetlony komunikat o błędzie podobny do **Nie można zlokalizować pakietu dotnet-sdk-3.1**, zobacz [Sekcję Rozwiązywanie problemów z menedżerem pakietów.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="38099-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="38099-117">Instalowanie ASP.NET core</span><span class="sxs-lookup"><span data-stu-id="38099-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="38099-118">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET core.</span><span class="sxs-lookup"><span data-stu-id="38099-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="38099-119">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="38099-119">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="38099-120">Jeśli zostanie wyświetlony komunikat o błędzie podobny do **Nie można zlokalizować pakietu aspnetcore-runtime-3.1**, zobacz [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) sekcji.</span><span class="sxs-lookup"><span data-stu-id="38099-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="38099-121">Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="38099-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="38099-122">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38099-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="38099-123">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="38099-123">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="38099-124">Jeśli zostanie wyświetlony komunikat o błędzie podobny do **Nie można zlokalizować pakietu dotnet-runtime-3.1**, zobacz [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) sekcji.</span><span class="sxs-lookup"><span data-stu-id="38099-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="38099-125">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="38099-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="38099-126">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="38099-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="38099-127">Ta sekcja zawiera informacje o typowych błędach, które mogą pojawić się podczas instalowania programu .NET Core za pomocą Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="38099-127">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="38099-128">Nie można zlokalizować</span><span class="sxs-lookup"><span data-stu-id="38099-128">Unable to locate</span></span>

<span data-ttu-id="38099-129">Jeśli zostanie wyświetlony komunikat o błędzie podobny do **Nie można zlokalizować pakietu {pakiet .NET Core},** uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="38099-129">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="38099-130">Jeśli to nie zadziała, można uruchomić instalację ręczną za pomocą następujących poleceń.</span><span class="sxs-lookup"><span data-stu-id="38099-130">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="38099-131">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="38099-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
