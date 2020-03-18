---
title: polecenie dotnet tool update
description: Polecenie aktualizacji narzędzia dotnet aktualizuje określone narzędzie .NET Core na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 497b052a8b9cfa9dca8d80316075fe7565d6b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847823"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="33d81-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="33d81-103">dotnet tool update</span></span>

<span data-ttu-id="33d81-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="33d81-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="33d81-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="33d81-105">Name</span></span>

<span data-ttu-id="33d81-106">`dotnet tool update`- Aktualizuje określone [narzędzie .NET Core](global-tools.md) na komputerze.</span><span class="sxs-lookup"><span data-stu-id="33d81-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="33d81-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="33d81-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME> <--tool-path>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="33d81-108">Opis</span><span class="sxs-lookup"><span data-stu-id="33d81-108">Description</span></span>

<span data-ttu-id="33d81-109">Polecenie `dotnet tool update` umożliwia zaktualizowanie narzędzi .NET Core na komputerze do najnowszej stabilnej wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="33d81-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="33d81-110">Polecenie odinstalowuje i ponownie instaluje narzędzie, skutecznie je aktualizując.</span><span class="sxs-lookup"><span data-stu-id="33d81-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="33d81-111">Aby użyć polecenia, należy określić jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="33d81-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="33d81-112">Aby zaktualizować narzędzie globalne zainstalowane w lokalizacji `--global` domyślnej, użyj opcji</span><span class="sxs-lookup"><span data-stu-id="33d81-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="33d81-113">Aby zaktualizować narzędzie globalne, które zostało zainstalowane `--tool-path` w lokalizacji niestandardowej, użyj tej opcji.</span><span class="sxs-lookup"><span data-stu-id="33d81-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="33d81-114">Aby zaktualizować narzędzie lokalne, `--global` `--tool-path` pomiń te opcje.</span><span class="sxs-lookup"><span data-stu-id="33d81-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="33d81-115">**Lokalne narzędzia są dostępne począwszy od .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="33d81-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="33d81-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="33d81-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="33d81-117">Nazwa/identyfikator pakietu NuGet, który zawiera globalne narzędzie .NET Core do aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="33d81-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="33d81-118">Nazwę pakietu można znaleźć za pomocą polecenia [listy narzędzi dotnet.](dotnet-tool-list.md)</span><span class="sxs-lookup"><span data-stu-id="33d81-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="33d81-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="33d81-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="33d81-120">Dodaje dodatkowe źródło pakietu NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="33d81-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="33d81-121">Plik konfiguracji NuGet *(nuget.config)* do użycia.</span><span class="sxs-lookup"><span data-stu-id="33d81-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="33d81-122">Określa [platformę docelową,](../../standard/frameworks.md) dla dla za pomocą platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="33d81-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="33d81-123">Określa, że aktualizacja dotyczy narzędzia dla całego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="33d81-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="33d81-124">Nie można połączyć z `--tool-path` tą opcją.</span><span class="sxs-lookup"><span data-stu-id="33d81-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="33d81-125">Pominięcie obu `--global` `--tool-path` i określa, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="33d81-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="33d81-126">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="33d81-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="33d81-127">Określa lokalizację, w której jest zainstalowane narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="33d81-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="33d81-128">PATH może być bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="33d81-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="33d81-129">Nie można połączyć z `--global` tą opcją.</span><span class="sxs-lookup"><span data-stu-id="33d81-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="33d81-130">Pominięcie obu `--global` `--tool-path` i określa, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="33d81-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="33d81-131">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="33d81-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="33d81-132">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="33d81-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="33d81-133">Przykłady</span><span class="sxs-lookup"><span data-stu-id="33d81-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="33d81-134">Aktualizuje narzędzie globalne [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)</span><span class="sxs-lookup"><span data-stu-id="33d81-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="33d81-135">Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="33d81-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="33d81-136">Aktualizuje globalne narzędzie [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="33d81-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="33d81-137">Aktualizuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) zainstalowane dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="33d81-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="33d81-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33d81-138">See also</span></span>

- [<span data-ttu-id="33d81-139">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="33d81-139">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="33d81-140">Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="33d81-140">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="33d81-141">Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="33d81-141">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
