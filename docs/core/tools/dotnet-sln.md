---
title: dotnet sln — polecenie
description: Polecenie dotnet-sln udostępnia wygodną opcję dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.
ms.date: 06/13/2018
ms.openlocfilehash: 3f18d6a2851d955d07cecc0cbc4c161cf0ec3e08
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202792"
---
# <a name="dotnet-sln"></a><span data-ttu-id="66d99-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="66d99-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="66d99-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="66d99-104">Name</span></span>

<span data-ttu-id="66d99-105">`dotnet sln`-Modyfikuje plik rozwiązania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="66d99-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="66d99-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="66d99-106">Synopsis</span></span>

```console
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="66d99-107">Opis</span><span class="sxs-lookup"><span data-stu-id="66d99-107">Description</span></span>

<span data-ttu-id="66d99-108">`dotnet sln` Polecenie zapewnia wygodny sposób dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="66d99-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="66d99-109">Aby użyć `dotnet sln` polecenia, plik rozwiązania musi już istnieć.</span><span class="sxs-lookup"><span data-stu-id="66d99-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="66d99-110">Jeśli trzeba ją utworzyć, użyj polecenia [dotnet New](dotnet-new.md) , tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="66d99-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```console
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="66d99-111">Polecenia</span><span class="sxs-lookup"><span data-stu-id="66d99-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="66d99-112">Dodaje projekt lub wiele projektów do pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="66d99-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="66d99-113">[Wzorce obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminalach opartych na systemie UNIX/Linux.</span><span class="sxs-lookup"><span data-stu-id="66d99-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="66d99-114">Usuwa projekt lub wiele projektów z pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="66d99-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="66d99-115">[Wzorce obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminalach opartych na systemie UNIX/Linux.</span><span class="sxs-lookup"><span data-stu-id="66d99-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="66d99-116">Wyświetla wszystkie projekty w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="66d99-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="66d99-117">Argumenty</span><span class="sxs-lookup"><span data-stu-id="66d99-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="66d99-118">Plik rozwiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="66d99-118">Solution file to use.</span></span> <span data-ttu-id="66d99-119">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="66d99-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="66d99-120">Jeśli w katalogu znajduje się wiele plików rozwiązania, należy określić jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="66d99-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="66d99-121">Opcje</span><span class="sxs-lookup"><span data-stu-id="66d99-121">Options</span></span>

`-h|--help`

<span data-ttu-id="66d99-122">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="66d99-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="66d99-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="66d99-123">Examples</span></span>

<span data-ttu-id="66d99-124">Dodaj C# projekt do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="66d99-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="66d99-125">Usuń C# projekt z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="66d99-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="66d99-126">Dodaj wiele C# projektów do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="66d99-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="66d99-127">Usuń wiele C# projektów z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="66d99-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="66d99-128">Dodawanie wielu C# projektów do rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych:</span><span class="sxs-lookup"><span data-stu-id="66d99-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="66d99-129">Usuwanie wielu C# projektów z rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych:</span><span class="sxs-lookup"><span data-stu-id="66d99-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> <span data-ttu-id="66d99-130">Obsługi symboli wieloznacznych nie jest funkcją interfejsu wiersza polecenia, ale raczej funkcją powłoki poleceń.</span><span class="sxs-lookup"><span data-stu-id="66d99-130">Globbing is not a CLI feature but rather a feature of the command shell.</span></span> <span data-ttu-id="66d99-131">Aby pomyślnie rozszerzyć pliki, należy użyć powłoki obsługującej obsługi symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="66d99-131">To successfully expand the files, you must use a shell that supports globbing.</span></span> <span data-ttu-id="66d99-132">Aby uzyskać więcej informacji na temat obsługi symboli wieloznacznych, zobacz [witrynę Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span><span class="sxs-lookup"><span data-stu-id="66d99-132">For more information about globbing, see [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span></span>
