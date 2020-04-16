---
title: Polecenie aktualizacji narzędzia dotnet
description: Polecenie aktualizacji narzędzia dotnet aktualizuje określone narzędzie .NET Core na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 6176846dbe8e2a91d9c6959dede15718d8f983b2
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463299"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="8b4ea-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="8b4ea-103">dotnet tool update</span></span>

<span data-ttu-id="8b4ea-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="8b4ea-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8b4ea-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8b4ea-105">Name</span></span>

<span data-ttu-id="8b4ea-106">`dotnet tool update`- Aktualizuje określone [narzędzie .NET Core](global-tools.md) na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8b4ea-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="8b4ea-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="8b4ea-108">Opis</span><span class="sxs-lookup"><span data-stu-id="8b4ea-108">Description</span></span>

<span data-ttu-id="8b4ea-109">Polecenie `dotnet tool update` umożliwia zaktualizowanie narzędzi .NET Core na komputerze do najnowszej stabilnej wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="8b4ea-110">Polecenie odinstalowuje i ponownie instaluje narzędzie, skutecznie aktualizując je.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="8b4ea-111">Aby użyć polecenia, należy określić jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="8b4ea-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="8b4ea-112">Aby zaktualizować narzędzie globalne zainstalowane w lokalizacji domyślnej, użyj `--global` tej opcji</span><span class="sxs-lookup"><span data-stu-id="8b4ea-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="8b4ea-113">Aby zaktualizować narzędzie globalne zainstalowane w lokalizacji niestandardowej, użyj `--tool-path` tej opcji.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="8b4ea-114">Aby zaktualizować narzędzie lokalne, `--global` pomiń opcje i `--tool-path` opcje.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="8b4ea-115">**Narzędzia lokalne są dostępne począwszy od .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="8b4ea-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="8b4ea-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8b4ea-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="8b4ea-117">Nazwa/identyfikator pakietu NuGet, który zawiera globalne narzędzie .NET Core do aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="8b4ea-118">Nazwę pakietu można znaleźć za pomocą polecenia [lista narzędzi dotnet.](dotnet-tool-list.md)</span><span class="sxs-lookup"><span data-stu-id="8b4ea-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="8b4ea-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="8b4ea-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="8b4ea-120">Dodaje dodatkowe źródło pakietu NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="8b4ea-121">Plik konfiguracji NuGet (*nuget.config*).</span><span class="sxs-lookup"><span data-stu-id="8b4ea-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="8b4ea-122">Określa [platformę docelową,](../../standard/frameworks.md) dla aby zaktualizować narzędzie.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="8b4ea-123">Określa, że aktualizacja jest dla narzędzia dla całego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="8b4ea-124">Nie można połączyć `--tool-path` z opcją.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="8b4ea-125">Pominięcie obu `--global` `--tool-path` i określa, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="8b4ea-126">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="8b4ea-127">Określa lokalizację, w której jest zainstalowane narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="8b4ea-128">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="8b4ea-129">Nie można połączyć `--global` z opcją.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="8b4ea-130">Pominięcie obu `--global` `--tool-path` i określa, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="8b4ea-131">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8b4ea-132">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="8b4ea-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="8b4ea-133">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8b4ea-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="8b4ea-134">Aktualizuje globalne narzędzie [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)</span><span class="sxs-lookup"><span data-stu-id="8b4ea-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="8b4ea-135">Aktualizuje globalne narzędzie [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="8b4ea-136">Aktualizuje globalne narzędzie [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="8b4ea-137">Aktualizuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) zainstalowane dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="8b4ea-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b4ea-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b4ea-138">See also</span></span>

- [<span data-ttu-id="8b4ea-139">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="8b4ea-139">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="8b4ea-140">Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu interfejsu wiersza polecenia .NET Core</span><span class="sxs-lookup"><span data-stu-id="8b4ea-140">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="8b4ea-141">Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core</span><span class="sxs-lookup"><span data-stu-id="8b4ea-141">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
