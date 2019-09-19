---
title: polecenie aktualizacji narzędzia dotnet
description: Polecenie aktualizacji narzędzia dotnet aktualizuje określone narzędzie globalne platformy .NET Core na komputerze.
ms.date: 05/29/2018
ms.openlocfilehash: b10ce39c8b9d4df23243bcf672454a455e34eec1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117533"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="ef7e0-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="ef7e0-103">dotnet tool update</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="ef7e0-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ef7e0-104">Name</span></span>

<span data-ttu-id="ef7e0-105">`dotnet tool update`-Aktualizuje określone [Narzędzie globalne platformy .NET Core](global-tools.md) na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-105">`dotnet tool update` - Updates the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ef7e0-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="ef7e0-106">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="ef7e0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ef7e0-107">Description</span></span>

<span data-ttu-id="ef7e0-108">`dotnet tool update` Polecenie umożliwia zaktualizowanie podstawowych narzędzi platformy .NET Core na komputerze do najnowszej stabilnej wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-108">The `dotnet tool update` command provides a way for you to update .NET Core Global Tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="ef7e0-109">Polecenie Odinstalowuje i ponownie instaluje narzędzie, co skutecznie aktualizuje go.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-109">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="ef7e0-110">Aby użyć polecenia, musisz określić, że chcesz zaktualizować narzędzie z instalacji na poziomie użytkownika przy użyciu `--global` opcji lub określić ścieżkę do miejsca instalacji narzędzia `--tool-path` przy użyciu opcji.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-110">To use the command, you either have to specify that you want to update a tool from a user-wide installation using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="ef7e0-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ef7e0-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="ef7e0-112">Nazwa/identyfikator pakietu NuGet zawierającego narzędzie globalne programu .NET Core do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-112">Name/ID of the NuGet package that contains the .NET Core Global Tool to update.</span></span> <span data-ttu-id="ef7e0-113">Nazwę pakietu można znaleźć przy użyciu polecenia [listy narzędzi dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="ef7e0-113">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="ef7e0-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="ef7e0-114">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="ef7e0-115">Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-115">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="ef7e0-116">Plik konfiguracji NuGet (*NuGet. config*) do użycia.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-116">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="ef7e0-117">Określa [platformę docelową](../../standard/frameworks.md) do zaktualizowania narzędzia dla programu.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-117">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

`-g|--global`

<span data-ttu-id="ef7e0-118">Określa, że aktualizacja dotyczy narzędzia dla całego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-118">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="ef7e0-119">Nie można łączyć z `--tool-path` opcją.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="ef7e0-120">Jeśli ta opcja nie zostanie określona, należy określić `--tool-path` opcję.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-120">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="ef7e0-121">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-121">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="ef7e0-122">Określa lokalizację, w której zainstalowano narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-122">Specifies the location where the Global Tool is installed.</span></span> <span data-ttu-id="ef7e0-123">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-123">PATH can be absolute or relative.</span></span> <span data-ttu-id="ef7e0-124">Nie można łączyć z `--global` opcją.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-124">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="ef7e0-125">Jeśli ta opcja nie zostanie określona, należy określić `--global` opcję.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-125">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ef7e0-126">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="ef7e0-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ef7e0-127">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="ef7e0-127">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="ef7e0-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ef7e0-128">Examples</span></span>

<span data-ttu-id="ef7e0-129">Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :</span><span class="sxs-lookup"><span data-stu-id="ef7e0-129">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool update -g dotnetsay`

<span data-ttu-id="ef7e0-130">Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym folderze systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="ef7e0-130">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Windows folder:</span></span>

`dotnet tool update dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="ef7e0-131">Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym folderze systemu Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="ef7e0-131">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Linux/macOS folder:</span></span>

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="ef7e0-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef7e0-132">See also</span></span>

- [<span data-ttu-id="ef7e0-133">Narzędzia globalne platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef7e0-133">.NET Core Global Tools</span></span>](global-tools.md)
