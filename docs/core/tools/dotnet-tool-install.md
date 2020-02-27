---
title: polecenie instalacji narzędzia dotnet
description: Polecenie instalacji narzędzia dotnet służy do instalowania określonego narzędzia platformy .NET Core na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 837d12bc807ad95ccdbd9c0e087c7d45418c6e74
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626037"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="a987f-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="a987f-103">dotnet tool install</span></span>

<span data-ttu-id="a987f-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="a987f-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a987f-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="a987f-105">Name</span></span>

<span data-ttu-id="a987f-106">`dotnet tool install` — instaluje na komputerze określone [Narzędzie .NET Core](global-tools.md) .</span><span class="sxs-lookup"><span data-stu-id="a987f-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a987f-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a987f-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="a987f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a987f-108">Description</span></span>

<span data-ttu-id="a987f-109">Polecenie `dotnet tool install` zapewnia sposób instalowania narzędzi platformy .NET Core na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a987f-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="a987f-110">Aby użyć polecenia, należy określić jedną z następujących opcji instalacji:</span><span class="sxs-lookup"><span data-stu-id="a987f-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="a987f-111">Aby zainstalować narzędzie globalne w lokalizacji domyślnej, użyj opcji `--global`.</span><span class="sxs-lookup"><span data-stu-id="a987f-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="a987f-112">Aby zainstalować narzędzie globalne w niestandardowej lokalizacji, użyj opcji `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="a987f-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="a987f-113">Aby zainstalować narzędzie lokalne, Pomiń opcje `--global` i `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="a987f-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="a987f-114">**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="a987f-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="a987f-115">Narzędzia globalne są instalowane domyślnie w następujących katalogach po określeniu opcji `-g` lub `--global`:</span><span class="sxs-lookup"><span data-stu-id="a987f-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="a987f-116">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="a987f-116">OS</span></span>          | <span data-ttu-id="a987f-117">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="a987f-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="a987f-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="a987f-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="a987f-119">System Windows</span><span class="sxs-lookup"><span data-stu-id="a987f-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="a987f-120">Narzędzia lokalne są dodawane do pliku *manifest. JSON* w katalogu *. config* w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a987f-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="a987f-121">Jeśli plik manifestu jeszcze nie istnieje, utwórz go, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="a987f-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="a987f-122">Aby uzyskać więcej informacji, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="a987f-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="a987f-123">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a987f-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="a987f-124">Nazwa/identyfikator pakietu NuGet zawierającego narzędzie .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="a987f-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="a987f-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="a987f-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="a987f-126">Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="a987f-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="a987f-127">Plik konfiguracji NuGet (*NuGet. config*) do użycia.</span><span class="sxs-lookup"><span data-stu-id="a987f-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="a987f-128">Określa [platformę docelową](../../standard/frameworks.md) do zainstalowania narzędzia dla programu.</span><span class="sxs-lookup"><span data-stu-id="a987f-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="a987f-129">Domyślnie zestaw .NET Core SDK próbuje wybrać najbardziej odpowiednią platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="a987f-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="a987f-130">Określa, że instalacja jest szeroka.</span><span class="sxs-lookup"><span data-stu-id="a987f-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="a987f-131">Nie można łączyć z opcją `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="a987f-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="a987f-132">Pominięcie obu `--global` i `--tool-path` określa instalację narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a987f-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span> 

- **`-h|--help`**

  <span data-ttu-id="a987f-133">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a987f-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="a987f-134">Określa lokalizację, w której ma zostać zainstalowane narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="a987f-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="a987f-135">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="a987f-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="a987f-136">Jeśli ścieżka nie istnieje, polecenie próbuje ją utworzyć.</span><span class="sxs-lookup"><span data-stu-id="a987f-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="a987f-137">Pominięcie obu `--global` i `--tool-path` określa instalację narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a987f-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span> 

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a987f-138">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="a987f-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a987f-139">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a987f-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="a987f-140">Wersja narzędzia do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="a987f-140">The version of the tool to install.</span></span> <span data-ttu-id="a987f-141">Domyślnie jest zainstalowana najnowsza stabilna wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="a987f-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="a987f-142">Użyj tej opcji, aby zainstalować Podgląd lub starsze wersje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="a987f-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="a987f-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a987f-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="a987f-144">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w domyślnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="a987f-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="a987f-145">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a987f-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="a987f-146">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu systemu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="a987f-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="a987f-147">Instaluje wersję 2.0.0 programu [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="a987f-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="a987f-148">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie lokalne dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="a987f-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="a987f-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a987f-149">See also</span></span>

- [<span data-ttu-id="a987f-150">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="a987f-150">.NET Core tools</span></span>](global-tools.md)
