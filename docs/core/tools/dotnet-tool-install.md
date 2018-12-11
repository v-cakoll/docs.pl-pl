---
title: polecenia instalacji narzędzia DotNet
description: Narzędzia dotnet zainstalować polecenie instaluje określonego narzędzia globalnej podstawowych platformy .NET na maszynie.
ms.date: 05/29/2018
ms.openlocfilehash: 251e7b04be96ac2340727fa03dbaa2d548110fa9
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168718"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="838f0-103">Instalowanie narzędzi DotNet</span><span class="sxs-lookup"><span data-stu-id="838f0-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="838f0-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="838f0-104">Name</span></span>

<span data-ttu-id="838f0-105">`dotnet tool install` -Instaluje określony [narzędzia programu .NET Core globalnego](global-tools.md) na swojej maszynie.</span><span class="sxs-lookup"><span data-stu-id="838f0-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="838f0-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="838f0-106">Synopsis</span></span>

```console
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="838f0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="838f0-107">Description</span></span>

<span data-ttu-id="838f0-108">`dotnet tool install` Polecenie umożliwia zainstalowanie narzędzia globalnej platformy .NET Core na swojej maszynie.</span><span class="sxs-lookup"><span data-stu-id="838f0-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="838f0-109">Można użyć polecenia, to należy określić ma użytkownika całej instalacji przy użyciu `--global` opcji lub możesz określić ścieżkę do je zainstalować za pomocą `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="838f0-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="838f0-110">Globalne narzędzia są instalowane w następujących katalogach domyślnie po określeniu `-g` (lub `--global`) opcja:</span><span class="sxs-lookup"><span data-stu-id="838f0-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="838f0-111">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="838f0-111">OS</span></span>          | <span data-ttu-id="838f0-112">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="838f0-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="838f0-113">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="838f0-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="838f0-114">Windows</span><span class="sxs-lookup"><span data-stu-id="838f0-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="838f0-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="838f0-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="838f0-116">Nazwy/Identyfikatora pakietu NuGet, który zawiera narzędzie globalnego .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="838f0-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="838f0-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="838f0-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="838f0-118">Dodaje dodatkowe źródła pakietu NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="838f0-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="838f0-119">Konfiguracja NuGet (*nuget.config*) plik do użycia.</span><span class="sxs-lookup"><span data-stu-id="838f0-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="838f0-120">Określa [platformę docelową](../../standard/frameworks.md) do zainstalowania tego narzędzia na potrzeby.</span><span class="sxs-lookup"><span data-stu-id="838f0-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="838f0-121">Domyślnie program .NET Core SDK próbuje wybierz najbardziej odpowiednią platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="838f0-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="838f0-122">Określa, czy instalacja się szerokie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="838f0-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="838f0-123">Nie można połączyć z `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="838f0-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="838f0-124">Jeśli nie określisz tę opcję, należy określić `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="838f0-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="838f0-125">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="838f0-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="838f0-126">Określa lokalizację, gdzie zainstalować narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="838f0-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="838f0-127">ŚCIEŻKA może być bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="838f0-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="838f0-128">Jeśli ŚCIEŻKA nie istnieje, polecenie próbuje je utworzyć.</span><span class="sxs-lookup"><span data-stu-id="838f0-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="838f0-129">Nie można połączyć z `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="838f0-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="838f0-130">Jeśli nie określisz tę opcję, należy określić `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="838f0-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="838f0-131">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="838f0-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="838f0-132">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="838f0-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="838f0-133">Wersja narzędzia do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="838f0-133">The version of the tool to install.</span></span> <span data-ttu-id="838f0-134">Domyślnie jest zainstalowana najnowsza wersja stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="838f0-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="838f0-135">Użyj tej opcji do zainstalowania wersji zapoznawczej lub starsze wersje tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="838f0-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="838f0-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="838f0-136">Examples</span></span>

<span data-ttu-id="838f0-137">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w domyślnej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="838f0-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="838f0-138">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w określonym folderze Windows:</span><span class="sxs-lookup"><span data-stu-id="838f0-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="838f0-139">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne w określonym folderze Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="838f0-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="838f0-140">Instaluje wersję 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:</span><span class="sxs-lookup"><span data-stu-id="838f0-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="838f0-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="838f0-141">See also</span></span>

* [<span data-ttu-id="838f0-142">Narzędzia globalnej platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="838f0-142">.NET Core Global Tools</span></span>](global-tools.md)