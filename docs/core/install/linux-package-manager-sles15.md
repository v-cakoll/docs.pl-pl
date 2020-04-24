---
title: Zainstaluj .NET Core na SLES 15 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować pakiet .NET Core SDK i środowisko wykonawcze w sles 15.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 608229447ef8814130c2a42edfc1c11c35ca156c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645629"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="7a756-103">Menedżer pakietów SLES 15 — instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="7a756-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="7a756-104">W tym artykule opisano sposób instalowania programu .NET Core w sles 15 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="7a756-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="7a756-105">Dodawanie klucza repozytorium firmy Microsoft i kanału informacyjnego</span><span class="sxs-lookup"><span data-stu-id="7a756-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="7a756-106">Przed zainstalowaniem platformy .NET należy:</span><span class="sxs-lookup"><span data-stu-id="7a756-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="7a756-107">Dodaj klucz podpisywania pakietu firmy Microsoft do listy zaufanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="7a756-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="7a756-108">Dodaj repozytorium do menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="7a756-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="7a756-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="7a756-109">Install required dependencies.</span></span>

<span data-ttu-id="7a756-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="7a756-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="7a756-111">Otwórz terminal i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7a756-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="7a756-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="7a756-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="7a756-113">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7a756-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="7a756-114">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7a756-114">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="7a756-115">Instalowanie ASP.NET core środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="7a756-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="7a756-116">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="7a756-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="7a756-117">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7a756-117">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="7a756-118">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="7a756-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="7a756-119">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7a756-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="7a756-120">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7a756-120">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="7a756-121">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="7a756-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="7a756-122">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="7a756-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="7a756-123">Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="7a756-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="7a756-124">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="7a756-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-rpm.md)]
