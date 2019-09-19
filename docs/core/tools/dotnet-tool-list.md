---
title: polecenie listy narzędzi dotnet
description: Polecenie listy narzędzi dotnet zawiera listę określonego narzędzia globalnego platformy .NET Core z komputera.
ms.date: 05/29/2018
ms.openlocfilehash: 6d35b1dce0c6d57edb0c6dd5f9711f093bc804aa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117562"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="2ea9e-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="2ea9e-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="2ea9e-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="2ea9e-104">Name</span></span>

<span data-ttu-id="2ea9e-105">`dotnet tool list`-Wyświetla wszystkie [Narzędzia globalne .NET Core](global-tools.md) aktualnie zainstalowane w katalogu domyślnym na komputerze lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2ea9e-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="2ea9e-106">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="2ea9e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2ea9e-107">Description</span></span>

<span data-ttu-id="2ea9e-108">`dotnet tool list` Polecenie umożliwia wyświetlenie listy wszystkich narzędzi globalnych .NET Core zainstalowanych na komputerze (bieżący profil użytkownika) lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="2ea9e-109">Polecenie wyświetla nazwę pakietu, zainstalowaną wersję i polecenie Narzędzia globalne.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="2ea9e-110">Aby użyć polecenia list, musisz określić, że chcesz zobaczyć wszystkie narzędzia dostępne dla użytkownika przy użyciu `--global` opcji lub określić ścieżkę niestandardową `--tool-path` przy użyciu opcji.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="2ea9e-111">Opcje</span><span class="sxs-lookup"><span data-stu-id="2ea9e-111">Options</span></span>

`-g|--global`

<span data-ttu-id="2ea9e-112">Wyświetla narzędzia globalne dla całego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="2ea9e-113">Nie można łączyć z `--tool-path` opcją.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="2ea9e-114">Jeśli ta opcja nie zostanie określona, należy określić `--tool-path` opcję.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="2ea9e-115">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="2ea9e-116">Określa niestandardową lokalizację, w której mają zostać znalezione narzędzia globalne.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="2ea9e-117">ŚCIEŻKA może być bezwzględna lub względna.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="2ea9e-118">Nie można łączyć z `--global` opcją.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="2ea9e-119">Jeśli ta opcja nie zostanie określona, należy określić `--global` opcję.</span><span class="sxs-lookup"><span data-stu-id="2ea9e-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="2ea9e-120">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2ea9e-120">Examples</span></span>

<span data-ttu-id="2ea9e-121">Wyświetla listę wszystkich narzędzi globalnych zainstalowanych na komputerze użytkownika (bieżący profil użytkownika):</span><span class="sxs-lookup"><span data-stu-id="2ea9e-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="2ea9e-122">Wyświetla listę globalnych narzędzi z określonego folderu systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="2ea9e-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="2ea9e-123">Wyświetla listę globalnych narzędzi z określonego folderu Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="2ea9e-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="2ea9e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ea9e-124">See also</span></span>

- [<span data-ttu-id="2ea9e-125">Narzędzia globalne platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ea9e-125">.NET Core Global Tools</span></span>](global-tools.md)
