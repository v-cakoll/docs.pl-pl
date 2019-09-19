---
title: polecenie instalacji narzędzia dotnet
description: Polecenie instalacji narzędzia dotnet służy do instalowania na komputerze określonego narzędzia globalnego platformy .NET Core.
ms.date: 05/29/2018
ms.openlocfilehash: d6f691117e93a39c9837b282dca19e452515c80a
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117463"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="3fafe-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="3fafe-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="3fafe-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3fafe-104">Name</span></span>

<span data-ttu-id="3fafe-105">`dotnet tool install`-Instaluje określone [Narzędzie globalne platformy .NET Core](global-tools.md) na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3fafe-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3fafe-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3fafe-106">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="3fafe-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3fafe-107">Description</span></span>

<span data-ttu-id="3fafe-108">`dotnet tool install` Polecenie umożliwia instalację narzędzi globalnych platformy .NET Core na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3fafe-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="3fafe-109">Aby użyć polecenia, musisz określić, że ma być używana instalacja obejmująca wiele użytkowników przy użyciu `--global` opcji, lub określić ścieżkę instalacji `--tool-path` przy użyciu opcji.</span><span class="sxs-lookup"><span data-stu-id="3fafe-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="3fafe-110">Narzędzia globalne są instalowane domyślnie w następujących katalogach po określeniu `-g` opcji (lub `--global`):</span><span class="sxs-lookup"><span data-stu-id="3fafe-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="3fafe-111">OS</span><span class="sxs-lookup"><span data-stu-id="3fafe-111">OS</span></span>          | <span data-ttu-id="3fafe-112">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="3fafe-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="3fafe-113">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="3fafe-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="3fafe-114">Windows</span><span class="sxs-lookup"><span data-stu-id="3fafe-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="3fafe-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3fafe-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="3fafe-116">Nazwa/identyfikator pakietu NuGet zawierającego narzędzie globalne programu .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="3fafe-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="3fafe-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="3fafe-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="3fafe-118">Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="3fafe-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="3fafe-119">Plik konfiguracji NuGet (*NuGet. config*) do użycia.</span><span class="sxs-lookup"><span data-stu-id="3fafe-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="3fafe-120">Określa [platformę docelową](../../standard/frameworks.md) do zainstalowania narzędzia dla programu.</span><span class="sxs-lookup"><span data-stu-id="3fafe-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="3fafe-121">Domyślnie zestaw .NET Core SDK próbuje wybrać najbardziej odpowiednią platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="3fafe-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="3fafe-122">Określa, że instalacja jest szeroka.</span><span class="sxs-lookup"><span data-stu-id="3fafe-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="3fafe-123">Nie można łączyć z `--tool-path` opcją.</span><span class="sxs-lookup"><span data-stu-id="3fafe-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="3fafe-124">Jeśli ta opcja nie zostanie określona, należy określić `--tool-path` opcję.</span><span class="sxs-lookup"><span data-stu-id="3fafe-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="3fafe-125">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3fafe-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="3fafe-126">Określa lokalizację, w której ma zostać zainstalowane narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="3fafe-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="3fafe-127">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="3fafe-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="3fafe-128">Jeśli ścieżka nie istnieje, polecenie próbuje ją utworzyć.</span><span class="sxs-lookup"><span data-stu-id="3fafe-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="3fafe-129">Nie można łączyć z `--global` opcją.</span><span class="sxs-lookup"><span data-stu-id="3fafe-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="3fafe-130">Jeśli ta opcja nie zostanie określona, należy określić `--global` opcję.</span><span class="sxs-lookup"><span data-stu-id="3fafe-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3fafe-131">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="3fafe-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3fafe-132">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="3fafe-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="3fafe-133">Wersja narzędzia do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="3fafe-133">The version of the tool to install.</span></span> <span data-ttu-id="3fafe-134">Domyślnie jest zainstalowana najnowsza stabilna wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="3fafe-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="3fafe-135">Użyj tej opcji, aby zainstalować Podgląd lub starsze wersje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="3fafe-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="3fafe-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3fafe-136">Examples</span></span>

<span data-ttu-id="3fafe-137">Instaluje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) w domyślnej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="3fafe-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="3fafe-138">Instaluje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) w określonym folderze systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="3fafe-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="3fafe-139">Instaluje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) w określonym folderze systemu Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="3fafe-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="3fafe-140">Instaluje wersję 2.0.0 narzędzia globalnego [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :</span><span class="sxs-lookup"><span data-stu-id="3fafe-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="3fafe-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fafe-141">See also</span></span>

- [<span data-ttu-id="3fafe-142">Narzędzia globalne platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="3fafe-142">.NET Core Global Tools</span></span>](global-tools.md)
