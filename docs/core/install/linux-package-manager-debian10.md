---
title: Instalowanie programu .NET Core w systemie Debian 10 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w systemie Debian 10 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 038f5579f99f700ce47dc67be2fd344f01cf800c
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595623"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="9c0dd-103">Menedżer pakietów Debian 10 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="9c0dd-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="9c0dd-104">W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania programu .NET Core w systemie Debian 10.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="9c0dd-105">Dodaj klucz i źródło danych repozytorium Microsoft</span><span class="sxs-lookup"><span data-stu-id="9c0dd-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="9c0dd-106">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="9c0dd-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="9c0dd-107">Dodaj klucz podpisywania pakietu Microsoft do listy zaufanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="9c0dd-108">Dodaj repozytorium do Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="9c0dd-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-109">Install required dependencies.</span></span>

<span data-ttu-id="9c0dd-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="9c0dd-111">Otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="9c0dd-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="9c0dd-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="9c0dd-113">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="9c0dd-114">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="9c0dd-115">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9c0dd-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="9c0dd-116">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="9c0dd-117">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="9c0dd-118">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="9c0dd-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="9c0dd-119">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="9c0dd-120">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="9c0dd-121">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="9c0dd-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="9c0dd-122">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="9c0dd-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="9c0dd-123">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="9c0dd-124">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="9c0dd-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
