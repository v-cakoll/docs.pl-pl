---
title: polecenie instalacji narzędzia dotnet
description: Polecenie instalacji narzędzia dotnet instaluje określone narzędzie .NET Core na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 1e142773d1f981a8dc3b552d5a23d2864cdd82c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146466"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="b685b-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="b685b-103">dotnet tool install</span></span>

<span data-ttu-id="b685b-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="b685b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b685b-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b685b-105">Name</span></span>

<span data-ttu-id="b685b-106">`dotnet tool install`- Instaluje określone [narzędzie .NET Core](global-tools.md) na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b685b-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b685b-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="b685b-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME> <--tool-path>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="b685b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="b685b-108">Description</span></span>

<span data-ttu-id="b685b-109">Polecenie `dotnet tool install` umożliwia zainstalowanie narzędzi .NET Core na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b685b-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="b685b-110">Aby użyć polecenia, należy określić jedną z następujących opcji instalacji:</span><span class="sxs-lookup"><span data-stu-id="b685b-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="b685b-111">Aby zainstalować narzędzie globalne w lokalizacji `--global` domyślnej, użyj tej opcji.</span><span class="sxs-lookup"><span data-stu-id="b685b-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="b685b-112">Aby zainstalować narzędzie globalne w lokalizacji `--tool-path` niestandardowej, użyj tej opcji.</span><span class="sxs-lookup"><span data-stu-id="b685b-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="b685b-113">Aby zainstalować narzędzie lokalne, `--global` `--tool-path` pomiń te opcje.</span><span class="sxs-lookup"><span data-stu-id="b685b-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="b685b-114">**Lokalne narzędzia są dostępne począwszy od .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="b685b-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="b685b-115">Narzędzia globalne są domyślnie instalowane w `-g` następujących `--global` katalogach po określeniu lub opcji:</span><span class="sxs-lookup"><span data-stu-id="b685b-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="b685b-116">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="b685b-116">OS</span></span>          | <span data-ttu-id="b685b-117">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="b685b-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="b685b-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="b685b-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="b685b-119">Windows</span><span class="sxs-lookup"><span data-stu-id="b685b-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="b685b-120">Narzędzia lokalne są dodawane do pliku *tool-manifest.json* w katalogu *.config* w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b685b-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="b685b-121">Jeśli plik manifestu jeszcze nie istnieje, utwórz go, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b685b-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="b685b-122">Aby uzyskać więcej informacji, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="b685b-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="b685b-123">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b685b-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="b685b-124">Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="b685b-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="b685b-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="b685b-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="b685b-126">Dodaje dodatkowe źródło pakietu NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="b685b-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="b685b-127">Plik konfiguracji NuGet *(nuget.config)* do użycia.</span><span class="sxs-lookup"><span data-stu-id="b685b-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="b685b-128">Określa [platformę docelową,](../../standard/frameworks.md) dla dla za pomocą narzędzia.</span><span class="sxs-lookup"><span data-stu-id="b685b-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="b685b-129">Domyślnie zestaw SDK .NET Core próbuje wybrać najbardziej odpowiednią strukturę docelową.</span><span class="sxs-lookup"><span data-stu-id="b685b-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="b685b-130">Określa, że instalacja jest szeroka dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b685b-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="b685b-131">Nie można połączyć z `--tool-path` tą opcją.</span><span class="sxs-lookup"><span data-stu-id="b685b-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="b685b-132">Pominięcie obu `--global` `--tool-path` i określa instalację narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="b685b-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b685b-133">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="b685b-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="b685b-134">Określa lokalizację instalacji narzędzia globalnego.</span><span class="sxs-lookup"><span data-stu-id="b685b-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="b685b-135">PATH może być bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="b685b-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="b685b-136">Jeśli PATH nie istnieje, polecenie próbuje go utworzyć.</span><span class="sxs-lookup"><span data-stu-id="b685b-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="b685b-137">Pominięcie obu `--global` `--tool-path` i określa instalację narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="b685b-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="b685b-138">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="b685b-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b685b-139">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="b685b-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="b685b-140">Wersja narzędzia do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="b685b-140">The version of the tool to install.</span></span> <span data-ttu-id="b685b-141">Domyślnie zainstalowana jest najnowsza stabilna wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="b685b-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="b685b-142">Użyj tej opcji, aby zainstalować podgląd lub starsze wersje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="b685b-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="b685b-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b685b-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="b685b-144">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w lokalizacji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="b685b-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="b685b-145">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b685b-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="b685b-146">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu Linux / macOS.</span><span class="sxs-lookup"><span data-stu-id="b685b-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="b685b-147">Instaluje wersję 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="b685b-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="b685b-148">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie lokalne dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="b685b-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="b685b-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b685b-149">See also</span></span>

- [<span data-ttu-id="b685b-150">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="b685b-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="b685b-151">Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="b685b-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="b685b-152">Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="b685b-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
