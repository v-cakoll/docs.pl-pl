---
title: polecenie listy narzędzi DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie listy narzędzi dotnet Wyświetla określony .NET Core globalne narzędzia z komputera.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5f4793cd37c3a8df06eb6930ad9f381ac70d4e67
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696728"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="a2a74-103">Lista narzędzi DotNet</span><span class="sxs-lookup"><span data-stu-id="a2a74-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="a2a74-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a2a74-104">Name</span></span>

<span data-ttu-id="a2a74-105">`dotnet tool list` — Wyświetla listę wszystkich [.NET Core globalne narzędzia](global-tools.md) aktualnie zainstalowany domyślny katalog na komputerze lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="a2a74-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a2a74-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a2a74-106">Synopsis</span></span>

```
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="a2a74-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a2a74-107">Description</span></span>

<span data-ttu-id="a2a74-108">`dotnet tool list` Polecenie udostępnia sposób na liście wszystkie narzędzia globalne .NET Core zainstalowane na poziomie użytkownika na komputerze (bieżący profil użytkownika) lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="a2a74-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="a2a74-109">Polecenie wyświetla nazwę pakietu, wersji i polecenia narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="a2a74-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="a2a74-110">Polecenia listy albo należy określić, czy chcesz wyświetlić wszystkie narzędzia całej użytkownika przy użyciu `--global` opcji lub Określ niestandardową ścieżkę za pomocą `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="a2a74-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="a2a74-111">Opcje</span><span class="sxs-lookup"><span data-stu-id="a2a74-111">Options</span></span>

`-g|--global`

<span data-ttu-id="a2a74-112">Wyświetla globalne narzędzia na poziomie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a2a74-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="a2a74-113">Nie można połączyć z `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="a2a74-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="a2a74-114">Jeśli nie określisz tej opcji, należy określić `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="a2a74-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="a2a74-115">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a2a74-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="a2a74-116">Określa niestandardową lokalizację gdzie można znaleźć narzędzia globalnego.</span><span class="sxs-lookup"><span data-stu-id="a2a74-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="a2a74-117">ŚCIEŻKA może być bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="a2a74-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="a2a74-118">Nie można połączyć z `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="a2a74-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="a2a74-119">Jeśli nie określisz tej opcji, należy określić `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="a2a74-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="a2a74-120">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a2a74-120">Examples</span></span>

<span data-ttu-id="a2a74-121">Wyświetla listę wszystkich globalnych zainstalowano narzędzia użytkownika całej na tym komputerze (bieżący profil użytkownika):</span><span class="sxs-lookup"><span data-stu-id="a2a74-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="a2a74-122">Listy globalne narzędzi w określonym folderze systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="a2a74-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="a2a74-123">Listy globalne narzędzi z określonego folderu Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="a2a74-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="a2a74-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2a74-124">See also</span></span>

[<span data-ttu-id="a2a74-125">Narzędzia globalne .NET core</span><span class="sxs-lookup"><span data-stu-id="a2a74-125">.NET Core Global Tools</span></span>](global-tools.md)