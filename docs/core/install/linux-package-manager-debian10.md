---
title: Zainstaluj .NET Core na Debianie 10 - menedżerze pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować .NET Core SDK i runtime w Debianie 10.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 94bcb493536bdee71ba83053d9e671d529226ac3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920835"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="a296f-103">Menedżer pakietów Debian 10 — zainstaluj program .NET Core</span><span class="sxs-lookup"><span data-stu-id="a296f-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="a296f-104">W tym artykule opisano, jak zainstalować program .NET Core na Debianie 10 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="a296f-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span> <span data-ttu-id="a296f-105">Jeśli instalujesz program runtime, zalecamy zainstalowanie [ASP.NET core runtime](#install-the-aspnet-core-runtime), ponieważ zawiera zarówno .NET Core, jak i ASP.NET core.</span><span class="sxs-lookup"><span data-stu-id="a296f-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="a296f-106">Rejestrowanie klucza firmy Microsoft i źródła danych</span><span class="sxs-lookup"><span data-stu-id="a296f-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="a296f-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="a296f-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="a296f-108">Zarejestruj klucz firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a296f-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="a296f-109">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="a296f-109">Register the product repository.</span></span>
- <span data-ttu-id="a296f-110">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="a296f-110">Install required dependencies.</span></span>

<span data-ttu-id="a296f-111">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="a296f-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="a296f-112">Otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="a296f-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="a296f-113">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a296f-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="a296f-114">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a296f-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="a296f-115">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="a296f-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="a296f-116">Instalowanie ASP.NET core</span><span class="sxs-lookup"><span data-stu-id="a296f-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="a296f-117">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a296f-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="a296f-118">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="a296f-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="a296f-119">Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="a296f-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="a296f-120">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a296f-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="a296f-121">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="a296f-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="a296f-122">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="a296f-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="a296f-123">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="a296f-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="a296f-124">Ta sekcja zawiera informacje o typowych błędach, które mogą pojawić się podczas instalowania programu .NET Core za pomocą Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="a296f-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="a296f-125">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="a296f-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
