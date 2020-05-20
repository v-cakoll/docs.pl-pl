---
title: polecenie instalacji narzędzia dotnet
description: Polecenie instalacji narzędzia dotnet służy do instalowania określonego narzędzia platformy .NET Core na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 067f90124833da537370a36934ff212aba7577f3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702815"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="85bed-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="85bed-103">dotnet tool install</span></span>

<span data-ttu-id="85bed-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="85bed-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="85bed-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="85bed-105">Name</span></span>

<span data-ttu-id="85bed-106">`dotnet tool install`-Instaluje określone [Narzędzie .NET Core](global-tools.md) na komputerze.</span><span class="sxs-lookup"><span data-stu-id="85bed-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="85bed-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="85bed-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a><span data-ttu-id="85bed-108">Opis</span><span class="sxs-lookup"><span data-stu-id="85bed-108">Description</span></span>

<span data-ttu-id="85bed-109">`dotnet tool install`Polecenie umożliwia Instalowanie narzędzi platformy .NET Core na komputerze.</span><span class="sxs-lookup"><span data-stu-id="85bed-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="85bed-110">Aby użyć polecenia, należy określić jedną z następujących opcji instalacji:</span><span class="sxs-lookup"><span data-stu-id="85bed-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="85bed-111">Aby zainstalować narzędzie globalne w lokalizacji domyślnej, użyj `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="85bed-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="85bed-112">Aby zainstalować narzędzie globalne w niestandardowej lokalizacji, użyj `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="85bed-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="85bed-113">Aby zainstalować narzędzie lokalne, należy pominąć `--global` Opcje i `--tool-path` .</span><span class="sxs-lookup"><span data-stu-id="85bed-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="85bed-114">**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="85bed-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="85bed-115">Narzędzia globalne są instalowane domyślnie w następujących katalogach po określeniu `-g` `--global` opcji lub:</span><span class="sxs-lookup"><span data-stu-id="85bed-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="85bed-116">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="85bed-116">OS</span></span>          | <span data-ttu-id="85bed-117">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="85bed-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="85bed-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="85bed-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="85bed-119">Windows</span><span class="sxs-lookup"><span data-stu-id="85bed-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="85bed-120">Narzędzia lokalne są dodawane do pliku *dotnet-Tools. JSON* w katalogu *. config* w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="85bed-120">Local tools are added to a *dotnet-tools.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="85bed-121">Jeśli plik manifestu jeszcze nie istnieje, utwórz go, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="85bed-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="85bed-122">Aby uzyskać więcej informacji, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="85bed-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="85bed-123">Argumenty</span><span class="sxs-lookup"><span data-stu-id="85bed-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="85bed-124">Nazwa/identyfikator pakietu NuGet zawierającego narzędzie .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="85bed-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="85bed-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="85bed-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="85bed-126">Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="85bed-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="85bed-127">Plik konfiguracji NuGet (*NuGet. config*) do użycia.</span><span class="sxs-lookup"><span data-stu-id="85bed-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="85bed-128">Określa [platformę docelową](../../standard/frameworks.md) do zainstalowania narzędzia dla programu.</span><span class="sxs-lookup"><span data-stu-id="85bed-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="85bed-129">Domyślnie zestaw .NET Core SDK próbuje wybrać najbardziej odpowiednią platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="85bed-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="85bed-130">Określa, że instalacja jest szeroka.</span><span class="sxs-lookup"><span data-stu-id="85bed-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="85bed-131">Nie można łączyć z `--tool-path` opcją.</span><span class="sxs-lookup"><span data-stu-id="85bed-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="85bed-132">Pomijanie obu `--global` i `--tool-path` określa instalację narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="85bed-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="85bed-133">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="85bed-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="85bed-134">Określa lokalizację, w której ma zostać zainstalowane narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="85bed-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="85bed-135">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="85bed-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="85bed-136">Jeśli ścieżka nie istnieje, polecenie próbuje ją utworzyć.</span><span class="sxs-lookup"><span data-stu-id="85bed-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="85bed-137">Pomijanie obu `--global` i `--tool-path` określa instalację narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="85bed-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="85bed-138">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="85bed-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="85bed-139">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="85bed-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="85bed-140">Wersja narzędzia do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="85bed-140">The version of the tool to install.</span></span> <span data-ttu-id="85bed-141">Domyślnie jest zainstalowana najnowsza stabilna wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="85bed-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="85bed-142">Użyj tej opcji, aby zainstalować Podgląd lub starsze wersje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="85bed-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="85bed-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="85bed-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="85bed-144">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w domyślnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="85bed-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="85bed-145">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="85bed-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="85bed-146">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu systemu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="85bed-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="85bed-147">Instaluje wersję 2.0.0 programu [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="85bed-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="85bed-148">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie lokalne dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="85bed-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="85bed-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85bed-149">See also</span></span>

- [<span data-ttu-id="85bed-150">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="85bed-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="85bed-151">Samouczek: Instalowanie i używanie narzędzia globalnego platformy .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="85bed-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="85bed-152">Samouczek: Instalowanie lokalnego narzędzia .NET Core i używanie go przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="85bed-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
