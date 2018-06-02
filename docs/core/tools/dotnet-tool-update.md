---
title: polecenie aktualizacji narzędzi DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie aktualizacji narzędzi dotnet aktualizuje określonego narzędzia globalne Core w .NET na tym komputerze.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 35a0bd0f85f0beed06d4250d8f195ce4fe4fcca4
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696692"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="b386f-103">Aktualizacja narzędzi DotNet</span><span class="sxs-lookup"><span data-stu-id="b386f-103">dotnet tool update</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="b386f-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b386f-104">Name</span></span>

<span data-ttu-id="b386f-105">`dotnet tool update` — Aktualizuje określony [narzędzie globalne .NET Core](global-tools.md) na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b386f-105">`dotnet tool update` - Updates the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b386f-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="b386f-106">Synopsis</span></span>

```
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="b386f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b386f-107">Description</span></span>

<span data-ttu-id="b386f-108">`dotnet tool update` Polecenie umożliwia aktualizacji na tym komputerze do najnowsza stabilna wersja pakietu narzędzia globalne .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b386f-108">The `dotnet tool update` command provides a way for you to update .NET Core Global Tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="b386f-109">Polecenie powoduje odinstalowanie i ponowne zainstalowanie narzędzia, efektywnie zaktualizowaniem go.</span><span class="sxs-lookup"><span data-stu-id="b386f-109">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="b386f-110">Polecenia, albo należy określić chcesz zaktualizować narzędzie instalacji na poziomie użytkownika używającego `--global` opcji lub określ ścieżkę, aby wskazywała narzędzie jest instalowana za pomocą `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="b386f-110">To use the command, you either have to specify that you want to update a tool from a user-wide installation using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="b386f-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b386f-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="b386f-112">Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie globalne .NET Core do aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="b386f-112">Name/ID of the NuGet package that contains the .NET Core Global Tool to update.</span></span> <span data-ttu-id="b386f-113">Można znaleźć przy użyciu nazwy pakietu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="b386f-113">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="b386f-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="b386f-114">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="b386f-115">Dodaje dodatkowe źródła pakietów NuGet podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="b386f-115">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="b386f-116">Konfiguracja nuget projektu (*nuget.config*) pliku do użycia.</span><span class="sxs-lookup"><span data-stu-id="b386f-116">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="b386f-117">Określa [platformy docelowej](../../standard/frameworks.md) można zaktualizować za pomocą narzędzia.</span><span class="sxs-lookup"><span data-stu-id="b386f-117">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

`-g|--global`

<span data-ttu-id="b386f-118">Określa, czy aktualizacja jest narzędziem użytkownika na poziomie.</span><span class="sxs-lookup"><span data-stu-id="b386f-118">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="b386f-119">Nie można połączyć z `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="b386f-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="b386f-120">Jeśli nie określisz tej opcji, należy określić `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="b386f-120">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="b386f-121">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="b386f-121">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="b386f-122">Określa lokalizację, w którym zainstalowano narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="b386f-122">Specifies the location where the Global Tool is installed.</span></span> <span data-ttu-id="b386f-123">ŚCIEŻKA może być bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="b386f-123">PATH can be absolute or relative.</span></span> <span data-ttu-id="b386f-124">Nie można połączyć z `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="b386f-124">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="b386f-125">Jeśli nie określisz tej opcji, należy określić `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="b386f-125">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b386f-126">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="b386f-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b386f-127">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b386f-127">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="b386f-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b386f-128">Examples</span></span>

<span data-ttu-id="b386f-129">Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:</span><span class="sxs-lookup"><span data-stu-id="b386f-129">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool update -g dotnetsay`

<span data-ttu-id="b386f-130">Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzia globalnych znajduje się w określonym folderze systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="b386f-130">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Windows folder:</span></span>

`dotnet tool update dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="b386f-131">Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzia globalnych znajduje się w określonym folderze Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="b386f-131">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Linux/macOS folder:</span></span>

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="b386f-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b386f-132">See also</span></span>

[<span data-ttu-id="b386f-133">Narzędzia globalne .NET core</span><span class="sxs-lookup"><span data-stu-id="b386f-133">.NET Core Global Tools</span></span>](global-tools.md)