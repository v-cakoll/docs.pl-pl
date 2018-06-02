---
title: polecenie - .NET Core interfejsu wiersza polecenia instalacji narzędzia DotNet
description: Narzędzie dotnet zainstalować instaluje polecenia określonego .NET Core globalne narzędzia na komputerze.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f3068848910d6672a10ecfb639bac8e18a72818d
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697290"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="b4508-103">Instalowanie narzędzi DotNet</span><span class="sxs-lookup"><span data-stu-id="b4508-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="b4508-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b4508-104">Name</span></span>

<span data-ttu-id="b4508-105">`dotnet tool install` -Instaluje określony [narzędzie globalne .NET Core](global-tools.md) na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b4508-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b4508-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="b4508-106">Synopsis</span></span>

```
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="b4508-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b4508-107">Description</span></span>

<span data-ttu-id="b4508-108">`dotnet tool install` Polecenie umożliwia do zainstalowania narzędzia globalne .NET Core na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b4508-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="b4508-109">Aby polecenie, albo należy określić, że instalacja na poziomie użytkownika przy użyciu `--global` opcji lub określ ścieżkę do zainstalowania go przy użyciu `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="b4508-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="b4508-110">Narzędzia globalny są instalowane w następujących katalogów domyślnie po określeniu `-g` (lub `--global`) opcja:</span><span class="sxs-lookup"><span data-stu-id="b4508-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="b4508-111">SYSTEM OPERACYJNY</span><span class="sxs-lookup"><span data-stu-id="b4508-111">OS</span></span>          | <span data-ttu-id="b4508-112">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="b4508-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="b4508-113">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="b4508-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="b4508-114">Windows</span><span class="sxs-lookup"><span data-stu-id="b4508-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="b4508-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b4508-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="b4508-116">Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie globalne .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="b4508-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="b4508-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="b4508-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="b4508-118">Dodaje dodatkowe źródła pakietów NuGet podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="b4508-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="b4508-119">Konfiguracja nuget projektu (*nuget.config*) pliku do użycia.</span><span class="sxs-lookup"><span data-stu-id="b4508-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="b4508-120">Określa [platformy docelowej](../../standard/frameworks.md) zainstalować za pomocą narzędzia.</span><span class="sxs-lookup"><span data-stu-id="b4508-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="b4508-121">Domyślnie program .NET Core SDK próbuje wybierz najbardziej odpowiednią platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="b4508-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="b4508-122">Określa, że instalacja jest szeroki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b4508-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="b4508-123">Nie można połączyć z `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="b4508-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="b4508-124">Jeśli nie określisz tej opcji, należy określić `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="b4508-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="b4508-125">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="b4508-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="b4508-126">Określa lokalizację, gdzie zainstalować narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="b4508-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="b4508-127">ŚCIEŻKA może być bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="b4508-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="b4508-128">Jeśli ŚCIEŻKA nie istnieje, polecenie próbuje je utworzyć.</span><span class="sxs-lookup"><span data-stu-id="b4508-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="b4508-129">Nie można połączyć z `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="b4508-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="b4508-130">Jeśli nie określisz tej opcji, należy określić `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="b4508-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b4508-131">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="b4508-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b4508-132">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b4508-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="b4508-133">Wersja narzędzia do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="b4508-133">The version of the tool to install.</span></span> <span data-ttu-id="b4508-134">Domyślnie jest zainstalowana najnowsza wersja stabilne wersje pakietów.</span><span class="sxs-lookup"><span data-stu-id="b4508-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="b4508-135">Ta opcja służy do instalowania wersji zapoznawczej lub starsze wersje tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="b4508-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="b4508-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b4508-136">Examples</span></span>

<span data-ttu-id="b4508-137">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w domyślnej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="b4508-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="b4508-138">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w określonym folderze systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="b4508-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="b4508-139">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w określonym folderze Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="b4508-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="b4508-140">Instaluje wersję 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:</span><span class="sxs-lookup"><span data-stu-id="b4508-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="b4508-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4508-141">See also</span></span>

[<span data-ttu-id="b4508-142">Narzędzia globalne .NET core</span><span class="sxs-lookup"><span data-stu-id="b4508-142">.NET Core Global Tools</span></span>](global-tools.md)