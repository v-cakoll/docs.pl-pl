---
title: Instalowanie programu .NET Core w programie Ubuntu 18,04 Package Manager — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie Ubuntu 18,04 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 6929c7a91c131abb1170938fee010b077b1dbdc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450864"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a><span data-ttu-id="06964-103">Menedżer pakietów Ubuntu 18,04 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="06964-103">Ubuntu 18.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="06964-104">W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania programu .NET Core w systemie Ubuntu 18,04.</span><span class="sxs-lookup"><span data-stu-id="06964-104">This article describes how to use a package manager to install .NET Core on Ubuntu 18.04.</span></span> <span data-ttu-id="06964-105">Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="06964-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="06964-106">Zarejestruj klucz i źródło danych firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="06964-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="06964-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="06964-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="06964-108">Rejestrowanie klucza firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="06964-108">Register the Microsoft key</span></span>
- <span data-ttu-id="06964-109">Rejestrowanie repozytorium produktu</span><span class="sxs-lookup"><span data-stu-id="06964-109">register the product repository</span></span>
- <span data-ttu-id="06964-110">Instalowanie wymaganych zależności</span><span class="sxs-lookup"><span data-stu-id="06964-110">Install required dependencies</span></span>

<span data-ttu-id="06964-111">Należy to zrobić tylko raz dla każdego komputera.</span><span class="sxs-lookup"><span data-stu-id="06964-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="06964-112">Otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="06964-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="06964-113">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="06964-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="06964-114">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="06964-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="06964-115">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="06964-115">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.0
```

> [!IMPORTANT]
> <span data-ttu-id="06964-116">Jeśli zostanie wyświetlony komunikat o błędzie podobny do **nie można zlokalizować pakietu dotnet-SDK-3,0**, zobacz sekcję [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="06964-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="06964-117">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="06964-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="06964-118">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="06964-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="06964-119">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="06964-119">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.0
```

> [!IMPORTANT]
> <span data-ttu-id="06964-120">Jeśli zostanie wyświetlony komunikat o błędzie podobny do sytuacji, w której **nie można znaleźć pakietu aspnetcore-Runtime-3,0**, zobacz sekcję [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="06964-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="06964-121">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="06964-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="06964-122">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="06964-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="06964-123">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="06964-123">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.0
```

> [!IMPORTANT]
> <span data-ttu-id="06964-124">Jeśli zostanie wyświetlony komunikat o błędzie podobny do sytuacji, w której **nie można znaleźć pakietu dotnet-Runtime-3,0**, zobacz sekcję [Rozwiązywanie problemów z menedżerem pakietów](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="06964-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="06964-125">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="06964-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="06964-126">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="06964-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="06964-127">Jeśli zostanie wyświetlony komunikat o błędzie podobny do następującego: **nie można zlokalizować pakietu {pakiet .NET Core}** , uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="06964-127">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="06964-128">Jeśli to nie zadziała, można uruchomić instalację ręczną przy użyciu następujących poleceń.</span><span class="sxs-lookup"><span data-stu-id="06964-128">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```
