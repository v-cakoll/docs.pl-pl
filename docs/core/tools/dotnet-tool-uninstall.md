---
title: polecenie odinstalowania narzędzia DotNet
description: Polecenie odinstalowania narzędzia dotnet odinstalowuje określonego narzędzia globalnej podstawowych platformy .NET z poziomu Twojej maszyny.
ms.date: 05/29/2018
ms.openlocfilehash: 4d53d305131e3399ab5d9c19f9319f3ba3544c19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680926"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="e1e12-103">Odinstalowywanie narzędzia DotNet</span><span class="sxs-lookup"><span data-stu-id="e1e12-103">dotnet tool uninstall</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="e1e12-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e1e12-104">Name</span></span>

<span data-ttu-id="e1e12-105">`dotnet tool uninstall` -Odinstalowuje określony [narzędzia programu .NET Core globalnego](global-tools.md) z Twojego komputera.</span><span class="sxs-lookup"><span data-stu-id="e1e12-105">`dotnet tool uninstall` - Uninstalls the specified [.NET Core Global Tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e1e12-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e1e12-106">Synopsis</span></span>

```console
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="e1e12-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e1e12-107">Description</span></span>

<span data-ttu-id="e1e12-108">`dotnet tool uninstall` Polecenia umożliwia należy odinstalować narzędzia globalnej platformy .NET Core z poziomu Twojej maszyny.</span><span class="sxs-lookup"><span data-stu-id="e1e12-108">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core Global Tools from your machine.</span></span> <span data-ttu-id="e1e12-109">Można użyć polecenia, masz albo określić, czy chcesz usunąć, przy użyciu narzędzia użytkownika na poziomie `--global` opcję lub określ ścieżkę do miejsca narzędzie jest instalowana za pomocą `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="e1e12-109">To use the command, you either have to specify that you want to remove a user-wide tool using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="e1e12-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e1e12-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="e1e12-111">Nazwy/Identyfikatora pakietu NuGet, który zawiera .NET Core globalnego narzędzie, aby odinstalować.</span><span class="sxs-lookup"><span data-stu-id="e1e12-111">Name/ID of the NuGet package that contains the .NET Core Global Tool to uninstall.</span></span> <span data-ttu-id="e1e12-112">Możesz znaleźć przy użyciu nazwy pakietu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1e12-112">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="e1e12-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="e1e12-113">Options</span></span>

`-g|--global`

<span data-ttu-id="e1e12-114">Określa, że narzędzie ma zostać usunięty z instalacji na poziomie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e1e12-114">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="e1e12-115">Nie można połączyć z `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="e1e12-115">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="e1e12-116">Jeśli nie określisz tę opcję, należy określić `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="e1e12-116">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="e1e12-117">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1e12-117">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="e1e12-118">Określa lokalizację, gdzie można odinstalować narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="e1e12-118">Specifies the location where to uninstall the Global Tool.</span></span> <span data-ttu-id="e1e12-119">ŚCIEŻKA może być bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="e1e12-119">PATH can be absolute or relative.</span></span> <span data-ttu-id="e1e12-120">Nie można połączyć z `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="e1e12-120">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="e1e12-121">Jeśli nie określisz tę opcję, należy określić `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="e1e12-121">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="e1e12-122">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e1e12-122">Examples</span></span>

<span data-ttu-id="e1e12-123">Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:</span><span class="sxs-lookup"><span data-stu-id="e1e12-123">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool uninstall -g dotnetsay`

<span data-ttu-id="e1e12-124">Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne z określonego folderu Windows:</span><span class="sxs-lookup"><span data-stu-id="e1e12-124">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Windows folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="e1e12-125">Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne z określonego folderu w systemie Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="e1e12-125">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Linux/macOS folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="e1e12-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1e12-126">See also</span></span>

- [<span data-ttu-id="e1e12-127">Narzędzia globalnej platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="e1e12-127">.NET Core Global Tools</span></span>](global-tools.md)
