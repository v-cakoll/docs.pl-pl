---
title: Instalowanie programu .NET Core w systemie openSUSE 15 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe na openSUSE 15 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: cba07bafc32cc71a1cdaec08902284e105af4776
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740669"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="4b597-103">openSUSE 15 Package Manager — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b597-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="4b597-104">W tym artykule opisano, jak za pomocą Menedżera pakietów zainstalować platformę .NET Core w systemie openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="4b597-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span> <span data-ttu-id="4b597-105">Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b597-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="4b597-106">Rejestrowanie klucza firmy Microsoft i źródła danych</span><span class="sxs-lookup"><span data-stu-id="4b597-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="4b597-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="4b597-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="4b597-108">Zarejestruj klucz Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4b597-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="4b597-109">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="4b597-109">Register the product repository.</span></span>
- <span data-ttu-id="4b597-110">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="4b597-110">Install required dependencies.</span></span>

<span data-ttu-id="4b597-111">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="4b597-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="4b597-112">Otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="4b597-112">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="dependency-error-with-net-core-31"></a><span data-ttu-id="4b597-113">Błąd zależności z platformą .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="4b597-113">Dependency error with .NET Core 3.1</span></span>

<span data-ttu-id="4b597-114">Kanał informacyjny pakietu programu .NET Core 3,1 dla openSUSE ma problem z zależnością **krb5** .</span><span class="sxs-lookup"><span data-stu-id="4b597-114">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="4b597-115">Użyj poniższego polecenia, aby zainstalować odpowiednie zależności przed zainstalowaniem programu .NET Core 3,1 lub ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4b597-115">Use the following command to install the correct dependencies prior to installing .NET Core 3.1 or ASP.NET Core 3.1.</span></span>

```bash
sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="4b597-116">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="4b597-116">Install the .NET Core SDK</span></span>

<span data-ttu-id="4b597-117">Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="4b597-117">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="4b597-118">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="4b597-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="4b597-119">Kanał informacyjny pakietu programu .NET Core 3,1 dla openSUSE ma problem z zależnością **krb5** .</span><span class="sxs-lookup"><span data-stu-id="4b597-119">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="4b597-120">Użyj poniższego polecenia, aby zainstalować odpowiednie zależności, a następnie Zainstaluj zestaw SDK platformy .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4b597-120">Use the following command to install the correct dependencies, then install the .NET Core 3.1 SDK.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="4b597-121">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4b597-121">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="4b597-122">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4b597-122">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="4b597-123">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="4b597-123">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="4b597-124">Kanał informacyjny pakietu programu .NET Core 3,1 dla openSUSE ma problem z zależnością **krb5** .</span><span class="sxs-lookup"><span data-stu-id="4b597-124">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="4b597-125">Użyj poniższego polecenia, aby zainstalować poprawne zależności, a następnie zainstaluj środowisko uruchomieniowe ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4b597-125">Use the following command to install the correct dependencies, then install the ASP.NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="4b597-126">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b597-126">Install the .NET Core runtime</span></span>

<span data-ttu-id="4b597-127">Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b597-127">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="4b597-128">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="4b597-128">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="4b597-129">Kanał informacyjny pakietu programu .NET Core 3,1 dla openSUSE ma problem z zależnością **krb5** .</span><span class="sxs-lookup"><span data-stu-id="4b597-129">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="4b597-130">Użyj poniższego polecenia, aby zainstalować poprawne zależności, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4b597-130">Use the following command to install the correct dependencies, then install the .NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="4b597-131">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="4b597-131">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
