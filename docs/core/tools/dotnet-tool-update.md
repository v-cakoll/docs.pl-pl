---
title: polecenie aktualizacji narzędzi DotNet
description: Polecenie aktualizacji narzędzi dotnet aktualizuje określonego narzędzia globalnej podstawowe w .NET na maszynie.
ms.date: 05/29/2018
ms.openlocfilehash: bc7edada013c118564d44cbe4542dacb76925692
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516646"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="8755c-103">Aktualizacja narzędzi DotNet</span><span class="sxs-lookup"><span data-stu-id="8755c-103">dotnet tool update</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="8755c-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8755c-104">Name</span></span>

<span data-ttu-id="8755c-105">`dotnet tool update` — Aktualizuje określony [narzędzia programu .NET Core globalnego](global-tools.md) na swojej maszynie.</span><span class="sxs-lookup"><span data-stu-id="8755c-105">`dotnet tool update` - Updates the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8755c-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="8755c-106">Synopsis</span></span>

```console
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="8755c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8755c-107">Description</span></span>

<span data-ttu-id="8755c-108">`dotnet tool update` Polecenia umożliwia aktualizacji narzędzia globalnej platformy .NET Core na urządzeniu do najnowszej stabilnej wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="8755c-108">The `dotnet tool update` command provides a way for you to update .NET Core Global Tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="8755c-109">Polecenie powoduje odinstalowanie i ponowne zainstalowanie narzędziem skutecznie aktualizowania.</span><span class="sxs-lookup"><span data-stu-id="8755c-109">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="8755c-110">Aby polecenie, albo musisz określić, czy chcesz zaktualizować narzędzie instalacji na poziomie użytkownika, w którym używana jest `--global` opcję lub określ ścieżkę do miejsca narzędzie jest instalowana za pomocą `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="8755c-110">To use the command, you either have to specify that you want to update a tool from a user-wide installation using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="8755c-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8755c-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="8755c-112">Nazwy/Identyfikatora pakietu NuGet, który zawiera narzędzie globalnego .NET Core można zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="8755c-112">Name/ID of the NuGet package that contains the .NET Core Global Tool to update.</span></span> <span data-ttu-id="8755c-113">Możesz znaleźć przy użyciu nazwy pakietu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="8755c-113">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="8755c-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="8755c-114">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="8755c-115">Dodaje dodatkowe źródła pakietu NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="8755c-115">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="8755c-116">Konfiguracja NuGet (*nuget.config*) plik do użycia.</span><span class="sxs-lookup"><span data-stu-id="8755c-116">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="8755c-117">Określa [platformę docelową](../../standard/frameworks.md) można zaktualizować tego narzędzia na potrzeby.</span><span class="sxs-lookup"><span data-stu-id="8755c-117">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

`-g|--global`

<span data-ttu-id="8755c-118">Określa, czy aktualizacja jest narzędziem użytkownika na poziomie.</span><span class="sxs-lookup"><span data-stu-id="8755c-118">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="8755c-119">Nie można połączyć z `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="8755c-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="8755c-120">Jeśli nie określisz tę opcję, należy określić `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="8755c-120">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="8755c-121">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="8755c-121">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="8755c-122">Określa lokalizację, w którym zainstalowano narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="8755c-122">Specifies the location where the Global Tool is installed.</span></span> <span data-ttu-id="8755c-123">ŚCIEŻKA może być bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="8755c-123">PATH can be absolute or relative.</span></span> <span data-ttu-id="8755c-124">Nie można połączyć z `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="8755c-124">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="8755c-125">Jeśli nie określisz tę opcję, należy określić `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="8755c-125">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="8755c-126">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="8755c-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8755c-127">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="8755c-127">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="8755c-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8755c-128">Examples</span></span>

<span data-ttu-id="8755c-129">Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:</span><span class="sxs-lookup"><span data-stu-id="8755c-129">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool update -g dotnetsay`

<span data-ttu-id="8755c-130">Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzia globalnych znajduje się w określonym folderze Windows:</span><span class="sxs-lookup"><span data-stu-id="8755c-130">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Windows folder:</span></span>

`dotnet tool update dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="8755c-131">Aktualizacje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzia globalnych znajduje się w określonym folderze Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="8755c-131">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Linux/macOS folder:</span></span>

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="8755c-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8755c-132">See also</span></span>

- [<span data-ttu-id="8755c-133">Narzędzia globalnej platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="8755c-133">.NET Core Global Tools</span></span>](global-tools.md)
