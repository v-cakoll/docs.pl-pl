---
title: Polecenie instalacji narzędzia dotnet
description: Polecenie instalacji narzędzia dotnet instaluje na komputerze określone narzędzie .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 723d25caa6009288dbb55d55f173b04d7b983450
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463365"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="7267e-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="7267e-103">dotnet tool install</span></span>

<span data-ttu-id="7267e-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="7267e-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7267e-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7267e-105">Name</span></span>

<span data-ttu-id="7267e-106">`dotnet tool install`- Instaluje określone [narzędzie .NET Core](global-tools.md) na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7267e-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7267e-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="7267e-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="7267e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="7267e-108">Description</span></span>

<span data-ttu-id="7267e-109">Polecenie `dotnet tool install` umożliwia zainstalowanie narzędzi .NET Core na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7267e-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="7267e-110">Aby użyć polecenia, należy określić jedną z następujących opcji instalacji:</span><span class="sxs-lookup"><span data-stu-id="7267e-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="7267e-111">Aby zainstalować narzędzie globalne w lokalizacji `--global` domyślnej, użyj tej opcji.</span><span class="sxs-lookup"><span data-stu-id="7267e-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="7267e-112">Aby zainstalować narzędzie globalne w lokalizacji `--tool-path` niestandardowej, użyj tej opcji.</span><span class="sxs-lookup"><span data-stu-id="7267e-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="7267e-113">Aby zainstalować narzędzie lokalne, `--global` pomiń opcje i `--tool-path` opcje.</span><span class="sxs-lookup"><span data-stu-id="7267e-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="7267e-114">**Narzędzia lokalne są dostępne począwszy od .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="7267e-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="7267e-115">Narzędzia globalne są domyślnie instalowane w `-g` następujących `--global` katalogach po określeniu lub opcji:</span><span class="sxs-lookup"><span data-stu-id="7267e-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="7267e-116">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="7267e-116">OS</span></span>          | <span data-ttu-id="7267e-117">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="7267e-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="7267e-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="7267e-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="7267e-119">Windows</span><span class="sxs-lookup"><span data-stu-id="7267e-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="7267e-120">Narzędzia lokalne są dodawane do pliku *tool-manifest.json* w katalogu *.config* w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7267e-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="7267e-121">Jeśli plik manifestu jeszcze nie istnieje, utwórz go, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="7267e-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="7267e-122">Aby uzyskać więcej informacji, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="7267e-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="7267e-123">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7267e-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="7267e-124">Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="7267e-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="7267e-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="7267e-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="7267e-126">Dodaje dodatkowe źródło pakietu NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="7267e-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="7267e-127">Plik konfiguracji NuGet (*nuget.config*).</span><span class="sxs-lookup"><span data-stu-id="7267e-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="7267e-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span><span class="sxs-lookup"><span data-stu-id="7267e-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="7267e-129">Domyślnie .NET Core SDK próbuje wybrać najbardziej odpowiednią platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="7267e-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="7267e-130">Określa, że instalacja jest ogólna.</span><span class="sxs-lookup"><span data-stu-id="7267e-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="7267e-131">Nie można połączyć `--tool-path` z opcją.</span><span class="sxs-lookup"><span data-stu-id="7267e-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="7267e-132">Pominięcie obu `--global` `--tool-path` i określa instalację narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7267e-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="7267e-133">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="7267e-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="7267e-134">Określa lokalizację, w której należy zainstalować narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="7267e-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="7267e-135">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="7267e-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="7267e-136">Jeśli PATH nie istnieje, polecenie próbuje go utworzyć.</span><span class="sxs-lookup"><span data-stu-id="7267e-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="7267e-137">Pominięcie obu `--global` `--tool-path` i określa instalację narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7267e-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="7267e-138">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="7267e-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7267e-139">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="7267e-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="7267e-140">Wersja narzędzia do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="7267e-140">The version of the tool to install.</span></span> <span data-ttu-id="7267e-141">Domyślnie jest zainstalowana najnowsza stabilna wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="7267e-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="7267e-142">Użyj tej opcji, aby zainstalować wersje zapoznawczą lub starsze.</span><span class="sxs-lookup"><span data-stu-id="7267e-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="7267e-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="7267e-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="7267e-144">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w lokalizacji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="7267e-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="7267e-145">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7267e-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="7267e-146">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="7267e-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="7267e-147">Instaluje wersję 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="7267e-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="7267e-148">Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie lokalne dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="7267e-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="7267e-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7267e-149">See also</span></span>

- [<span data-ttu-id="7267e-150">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="7267e-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="7267e-151">Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu interfejsu wiersza polecenia .NET Core</span><span class="sxs-lookup"><span data-stu-id="7267e-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="7267e-152">Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core</span><span class="sxs-lookup"><span data-stu-id="7267e-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
