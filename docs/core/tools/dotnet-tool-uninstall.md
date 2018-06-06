---
title: polecenie - .NET Core interfejsu wiersza polecenia Odinstaluj narzędzi DotNet
description: Polecenie odinstalowania narzędzia dotnet odinstalowuje określonego .NET Core globalne narzędzia z komputera.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5cf80d1756dbf4e88bb52a8028d186d44978f440
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696945"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="3d4d5-103">Odinstaluj narzędzie DotNet</span><span class="sxs-lookup"><span data-stu-id="3d4d5-103">dotnet tool uninstall</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="3d4d5-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3d4d5-104">Name</span></span>

<span data-ttu-id="3d4d5-105">`dotnet tool uninstall` -Odinstalowuje określony [narzędzie globalne .NET Core](global-tools.md) z komputera.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-105">`dotnet tool uninstall` - Uninstalls the specified [.NET Core Global Tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3d4d5-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3d4d5-106">Synopsis</span></span>

```
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="3d4d5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3d4d5-107">Description</span></span>

<span data-ttu-id="3d4d5-108">`dotnet tool uninstall` Polecenie umożliwia można odinstalować .NET Core globalne narzędzia z komputera.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-108">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core Global Tools from your machine.</span></span> <span data-ttu-id="3d4d5-109">Polecenia, albo należy określić, czy chcesz usunąć użytkownika na poziomie narzędzia przy użyciu `--global` opcji lub określ ścieżkę, aby wskazywała narzędzie jest instalowana za pomocą `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-109">To use the command, you either have to specify that you want to remove a user-wide tool using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="3d4d5-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3d4d5-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="3d4d5-111">Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie globalne .NET Core do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-111">Name/ID of the NuGet package that contains the .NET Core Global Tool to uninstall.</span></span> <span data-ttu-id="3d4d5-112">Można znaleźć przy użyciu nazwy pakietu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-112">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="3d4d5-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="3d4d5-113">Options</span></span>

`-g|--global`

<span data-ttu-id="3d4d5-114">Określa, że narzędzie do usunięcia z instalacji na poziomie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-114">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="3d4d5-115">Nie można połączyć z `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-115">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="3d4d5-116">Jeśli nie określisz tej opcji, należy określić `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-116">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="3d4d5-117">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-117">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="3d4d5-118">Określa lokalizację, gdzie można odinstalować narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-118">Specifies the location where to uninstall the Global Tool.</span></span> <span data-ttu-id="3d4d5-119">ŚCIEŻKA może być bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-119">PATH can be absolute or relative.</span></span> <span data-ttu-id="3d4d5-120">Nie można połączyć z `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-120">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="3d4d5-121">Jeśli nie określisz tej opcji, należy określić `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-121">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="3d4d5-122">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3d4d5-122">Examples</span></span>

<span data-ttu-id="3d4d5-123">Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:</span><span class="sxs-lookup"><span data-stu-id="3d4d5-123">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool uninstall -g dotnetsay`

<span data-ttu-id="3d4d5-124">Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne z określonego folderu systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="3d4d5-124">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Windows folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="3d4d5-125">Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne z określonego folderu Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="3d4d5-125">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Linux/macOS folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="3d4d5-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d4d5-126">See also</span></span>

[<span data-ttu-id="3d4d5-127">Narzędzia globalne .NET core</span><span class="sxs-lookup"><span data-stu-id="3d4d5-127">.NET Core Global Tools</span></span>](global-tools.md)