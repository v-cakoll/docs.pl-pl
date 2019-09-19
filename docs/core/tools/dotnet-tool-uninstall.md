---
title: polecenie Narzędzia dotnet narzędzie do odinstalowywania
description: Polecenie Narzędzia dotnet narzędzie do odinstalowywania Odinstalowuje określone narzędzie globalne platformy .NET Core z maszyny.
ms.date: 05/29/2018
ms.openlocfilehash: 033753f44464e78b826e908e0b6cdf276da8a179
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117543"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="beb70-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="beb70-103">dotnet tool uninstall</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="beb70-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="beb70-104">Name</span></span>

<span data-ttu-id="beb70-105">`dotnet tool uninstall`-Odinstalowuje określone [Narzędzie globalne platformy .NET Core](global-tools.md) z komputera.</span><span class="sxs-lookup"><span data-stu-id="beb70-105">`dotnet tool uninstall` - Uninstalls the specified [.NET Core Global Tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="beb70-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="beb70-106">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="beb70-107">Opis</span><span class="sxs-lookup"><span data-stu-id="beb70-107">Description</span></span>

<span data-ttu-id="beb70-108">`dotnet tool uninstall` Polecenie umożliwia odinstalowanie narzędzi globalnych platformy .NET Core z komputera.</span><span class="sxs-lookup"><span data-stu-id="beb70-108">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core Global Tools from your machine.</span></span> <span data-ttu-id="beb70-109">Aby użyć polecenia, musisz określić, że chcesz usunąć narzędzie dostępne dla użytkownika przy użyciu `--global` opcji lub określić ścieżkę do lokalizacji, w której narzędzie zostanie zainstalowane `--tool-path` przy użyciu opcji.</span><span class="sxs-lookup"><span data-stu-id="beb70-109">To use the command, you either have to specify that you want to remove a user-wide tool using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="beb70-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="beb70-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="beb70-111">Nazwa/identyfikator pakietu NuGet zawierającego narzędzie globalne programu .NET Core do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="beb70-111">Name/ID of the NuGet package that contains the .NET Core Global Tool to uninstall.</span></span> <span data-ttu-id="beb70-112">Nazwę pakietu można znaleźć przy użyciu polecenia [listy narzędzi dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="beb70-112">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="beb70-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="beb70-113">Options</span></span>

`-g|--global`

<span data-ttu-id="beb70-114">Określa, że narzędzie ma zostać usunięte z instalacji na poziomie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="beb70-114">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="beb70-115">Nie można łączyć z `--tool-path` opcją.</span><span class="sxs-lookup"><span data-stu-id="beb70-115">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="beb70-116">Jeśli ta opcja nie zostanie określona, należy określić `--tool-path` opcję.</span><span class="sxs-lookup"><span data-stu-id="beb70-116">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="beb70-117">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="beb70-117">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="beb70-118">Określa lokalizację, w której ma zostać odinstalowane narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="beb70-118">Specifies the location where to uninstall the Global Tool.</span></span> <span data-ttu-id="beb70-119">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="beb70-119">PATH can be absolute or relative.</span></span> <span data-ttu-id="beb70-120">Nie można łączyć z `--global` opcją.</span><span class="sxs-lookup"><span data-stu-id="beb70-120">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="beb70-121">Jeśli ta opcja nie zostanie określona, należy określić `--global` opcję.</span><span class="sxs-lookup"><span data-stu-id="beb70-121">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="beb70-122">Przykłady</span><span class="sxs-lookup"><span data-stu-id="beb70-122">Examples</span></span>

<span data-ttu-id="beb70-123">Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :</span><span class="sxs-lookup"><span data-stu-id="beb70-123">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool uninstall -g dotnetsay`

<span data-ttu-id="beb70-124">Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego folderu systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="beb70-124">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Windows folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="beb70-125">Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego folderu Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="beb70-125">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Linux/macOS folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="beb70-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="beb70-126">See also</span></span>

- [<span data-ttu-id="beb70-127">Narzędzia globalne platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="beb70-127">.NET Core Global Tools</span></span>](global-tools.md)
