---
title: polecenia DotNet do listy narzędzie — interfejs wiersza polecenia platformy .NET Core
description: Polecenie listy narzędzi dotnet Wyświetla określonego narzędzia globalnej podstawowe w .NET z poziomu Twojej maszyny.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: e2bea974207d3098ed67b69ed16a72a03c44cd8b
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841245"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="1dbfc-103">Lista narzędzi DotNet</span><span class="sxs-lookup"><span data-stu-id="1dbfc-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="1dbfc-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1dbfc-104">Name</span></span>

<span data-ttu-id="1dbfc-105">`dotnet tool list` — Wyświetla listę wszystkich [narzędzia globalnej platformy .NET Core](global-tools.md) aktualnie zainstalowane w domyślnym katalogu na komputerze lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1dbfc-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="1dbfc-106">Synopsis</span></span>

```console
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="1dbfc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1dbfc-107">Description</span></span>

<span data-ttu-id="1dbfc-108">`dotnet tool list` Polecenie dostarcza sposób do tworzenia listy wszystkich narzędzi globalnego .NET Core zainstalowane całej użytkownika na komputerze (bieżący profil użytkownika) lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="1dbfc-109">Polecenie wyświetla nazwę pakietu, zainstalowaną wersję i polecenia narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="1dbfc-110">Aby korzystać z polecenia list, masz albo określić, czy chcesz zobaczyć wszystkie narzędzia całej użytkownika przy użyciu `--global` opcji lub określić niestandardową ścieżkę, w którym używana jest `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="1dbfc-111">Opcje</span><span class="sxs-lookup"><span data-stu-id="1dbfc-111">Options</span></span>

`-g|--global`

<span data-ttu-id="1dbfc-112">Wyświetla globalne narzędzia na poziomie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="1dbfc-113">Nie można połączyć z `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="1dbfc-114">Jeśli nie określisz tę opcję, należy określić `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="1dbfc-115">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="1dbfc-116">Określa niestandardową lokalizację gdzie można znaleźć narzędzia globalnej.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="1dbfc-117">ŚCIEŻKA może być bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="1dbfc-118">Nie można połączyć z `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="1dbfc-119">Jeśli nie określisz tę opcję, należy określić `--global` opcji.</span><span class="sxs-lookup"><span data-stu-id="1dbfc-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="1dbfc-120">Przykłady</span><span class="sxs-lookup"><span data-stu-id="1dbfc-120">Examples</span></span>

<span data-ttu-id="1dbfc-121">Wyświetla wszystkie zainstalowane narzędzia globalnej użytkownika całej na komputerze (bieżący profil użytkownika):</span><span class="sxs-lookup"><span data-stu-id="1dbfc-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="1dbfc-122">Listy globalne narzędzia z określonego folderu Windows:</span><span class="sxs-lookup"><span data-stu-id="1dbfc-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="1dbfc-123">Listy globalne narzędzi z określonego folderu w systemie Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="1dbfc-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="1dbfc-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dbfc-124">See also</span></span>

* [<span data-ttu-id="1dbfc-125">Narzędzia globalnej platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="1dbfc-125">.NET Core Global Tools</span></span>](global-tools.md)