---
title: polecenie aktualizacji narzędzia dotnet
description: Polecenie aktualizacji narzędzia dotnet umożliwia zaktualizowanie określonego narzędzia .NET Core na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 50bb366fedfb0ea69b8b6007ff89e366b4f689de
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543420"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="04d7f-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="04d7f-103">dotnet tool update</span></span>

<span data-ttu-id="04d7f-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="04d7f-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="04d7f-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="04d7f-105">Name</span></span>

<span data-ttu-id="04d7f-106">`dotnet tool update` — aktualizuje określone [Narzędzie .NET Core](global-tools.md) na komputerze.</span><span class="sxs-lookup"><span data-stu-id="04d7f-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="04d7f-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="04d7f-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="04d7f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="04d7f-108">Description</span></span>

<span data-ttu-id="04d7f-109">`dotnet tool update` polecenie umożliwia zaktualizowanie narzędzi platformy .NET Core na komputerze do najnowszej stabilnej wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="04d7f-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="04d7f-110">Polecenie Odinstalowuje i ponownie instaluje narzędzie, co skutecznie aktualizuje go.</span><span class="sxs-lookup"><span data-stu-id="04d7f-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="04d7f-111">Aby użyć polecenia, należy określić jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="04d7f-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="04d7f-112">Aby zaktualizować narzędzie globalne, które zostało zainstalowane w lokalizacji domyślnej, użyj opcji `--global`</span><span class="sxs-lookup"><span data-stu-id="04d7f-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="04d7f-113">Aby zaktualizować narzędzie globalne, które zostało zainstalowane w niestandardowej lokalizacji, użyj opcji `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="04d7f-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="04d7f-114">Aby zaktualizować narzędzie lokalne, Pomiń opcje `--global` i `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="04d7f-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="04d7f-115">**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="04d7f-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="04d7f-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="04d7f-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="04d7f-117">Nazwa/identyfikator pakietu NuGet zawierającego narzędzie globalne programu .NET Core do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="04d7f-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="04d7f-118">Nazwę pakietu można znaleźć przy użyciu polecenia [listy narzędzi dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="04d7f-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="04d7f-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="04d7f-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="04d7f-120">Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="04d7f-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="04d7f-121">Plik konfiguracji NuGet (*NuGet. config*) do użycia.</span><span class="sxs-lookup"><span data-stu-id="04d7f-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="04d7f-122">Określa [platformę docelową](../../standard/frameworks.md) do zaktualizowania narzędzia dla programu.</span><span class="sxs-lookup"><span data-stu-id="04d7f-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="04d7f-123">Określa, że aktualizacja dotyczy narzędzia dla całego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="04d7f-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="04d7f-124">Nie można łączyć z opcją `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="04d7f-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="04d7f-125">Pominięcie obu `--global` i `--tool-path` oznacza, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="04d7f-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span> 

- **`-h|--help`**

  <span data-ttu-id="04d7f-126">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="04d7f-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="04d7f-127">Określa lokalizację, w której zainstalowano narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="04d7f-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="04d7f-128">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="04d7f-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="04d7f-129">Nie można łączyć z opcją `--global`.</span><span class="sxs-lookup"><span data-stu-id="04d7f-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="04d7f-130">Pominięcie obu `--global` i `--tool-path` oznacza, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="04d7f-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span> 

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="04d7f-131">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="04d7f-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="04d7f-132">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="04d7f-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="04d7f-133">Przykłady</span><span class="sxs-lookup"><span data-stu-id="04d7f-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="04d7f-134">Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .</span><span class="sxs-lookup"><span data-stu-id="04d7f-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="04d7f-135">Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="04d7f-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="04d7f-136">Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="04d7f-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="04d7f-137">Aktualizuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) zainstalowane dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="04d7f-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="04d7f-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04d7f-138">See also</span></span>

- [<span data-ttu-id="04d7f-139">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="04d7f-139">.NET Core tools</span></span>](global-tools.md)
