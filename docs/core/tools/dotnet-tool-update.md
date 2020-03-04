---
title: polecenie aktualizacji narzędzia dotnet
description: Polecenie aktualizacji narzędzia dotnet umożliwia zaktualizowanie określonego narzędzia .NET Core na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 80e807a0fc06ad762334f888e701f6d9c448369a
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156949"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="79209-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="79209-103">dotnet tool update</span></span>

<span data-ttu-id="79209-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="79209-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="79209-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="79209-105">Name</span></span>

<span data-ttu-id="79209-106">`dotnet tool update` — aktualizuje określone [Narzędzie .NET Core](global-tools.md) na komputerze.</span><span class="sxs-lookup"><span data-stu-id="79209-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="79209-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="79209-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="79209-108">Opis</span><span class="sxs-lookup"><span data-stu-id="79209-108">Description</span></span>

<span data-ttu-id="79209-109">`dotnet tool update` polecenie umożliwia zaktualizowanie narzędzi platformy .NET Core na komputerze do najnowszej stabilnej wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="79209-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="79209-110">Polecenie Odinstalowuje i ponownie instaluje narzędzie, co skutecznie aktualizuje go.</span><span class="sxs-lookup"><span data-stu-id="79209-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="79209-111">Aby użyć polecenia, należy określić jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="79209-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="79209-112">Aby zaktualizować narzędzie globalne, które zostało zainstalowane w lokalizacji domyślnej, użyj opcji `--global`</span><span class="sxs-lookup"><span data-stu-id="79209-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="79209-113">Aby zaktualizować narzędzie globalne, które zostało zainstalowane w niestandardowej lokalizacji, użyj opcji `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="79209-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="79209-114">Aby zaktualizować narzędzie lokalne, Pomiń opcje `--global` i `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="79209-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="79209-115">**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="79209-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="79209-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="79209-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="79209-117">Nazwa/identyfikator pakietu NuGet zawierającego narzędzie globalne programu .NET Core do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="79209-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="79209-118">Nazwę pakietu można znaleźć przy użyciu polecenia [listy narzędzi dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="79209-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="79209-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="79209-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="79209-120">Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="79209-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="79209-121">Plik konfiguracji NuGet (*NuGet. config*) do użycia.</span><span class="sxs-lookup"><span data-stu-id="79209-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="79209-122">Określa [platformę docelową](../../standard/frameworks.md) do zaktualizowania narzędzia dla programu.</span><span class="sxs-lookup"><span data-stu-id="79209-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="79209-123">Określa, że aktualizacja dotyczy narzędzia dla całego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="79209-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="79209-124">Nie można łączyć z opcją `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="79209-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="79209-125">Pominięcie obu `--global` i `--tool-path` oznacza, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="79209-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="79209-126">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="79209-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="79209-127">Określa lokalizację, w której zainstalowano narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="79209-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="79209-128">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="79209-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="79209-129">Nie można łączyć z opcją `--global`.</span><span class="sxs-lookup"><span data-stu-id="79209-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="79209-130">Pominięcie obu `--global` i `--tool-path` oznacza, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="79209-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="79209-131">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="79209-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="79209-132">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="79209-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="79209-133">Przykłady</span><span class="sxs-lookup"><span data-stu-id="79209-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="79209-134">Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .</span><span class="sxs-lookup"><span data-stu-id="79209-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="79209-135">Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="79209-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="79209-136">Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="79209-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="79209-137">Aktualizuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) zainstalowane dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="79209-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="79209-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79209-138">See also</span></span>

- [<span data-ttu-id="79209-139">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="79209-139">.NET Core tools</span></span>](global-tools.md)
