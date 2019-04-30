---
title: polecenie sln DotNet
description: Polecenia dotnet sln udostępnia wygodne możliwość dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.
ms.date: 06/13/2018
ms.openlocfilehash: a88e22c68f639f2a42e59f9a271e431f04e24a2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665003"
---
# <a name="dotnet-sln"></a><span data-ttu-id="0c025-103">DotNet sln</span><span class="sxs-lookup"><span data-stu-id="0c025-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0c025-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0c025-104">Name</span></span>

<span data-ttu-id="0c025-105">`dotnet sln` — Modyfikuje plik rozwiązania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0c025-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0c025-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="0c025-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="0c025-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0c025-107">Description</span></span>

<span data-ttu-id="0c025-108">`dotnet sln` Polecenie zapewnia wygodny sposób dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0c025-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="0c025-109">Aby użyć `dotnet sln` polecenia Plik rozwiązania musi już istnieć.</span><span class="sxs-lookup"><span data-stu-id="0c025-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="0c025-110">Jeśli musisz utworzyć jeden, użyj [dotnet nowe](dotnet-new.md) polecenia, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0c025-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="0c025-111">Polecenia</span><span class="sxs-lookup"><span data-stu-id="0c025-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="0c025-112">Dodaje projekt lub wielu projektów do pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0c025-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="0c025-113">[Wzorce obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminale systemu Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="0c025-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="0c025-114">Usuwa projekt lub wieloma projektami z pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0c025-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="0c025-115">[Wzorce obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminale systemu Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="0c025-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="0c025-116">Wyświetla listę wszystkich projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0c025-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="0c025-117">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0c025-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="0c025-118">Plik rozwiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="0c025-118">Solution file to use.</span></span> <span data-ttu-id="0c025-119">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="0c025-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="0c025-120">W przypadku wielu rozwiązań plików w katalogu, należy określić jedną.</span><span class="sxs-lookup"><span data-stu-id="0c025-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="0c025-121">Opcje</span><span class="sxs-lookup"><span data-stu-id="0c025-121">Options</span></span>

`-h|--help`

<span data-ttu-id="0c025-122">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="0c025-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="0c025-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="0c025-123">Examples</span></span>

<span data-ttu-id="0c025-124">Dodaj projekt C# do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="0c025-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="0c025-125">Usuń projekt C# za pomocą rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="0c025-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="0c025-126">Dodawanie wielu projektów języka C# do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="0c025-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="0c025-127">Usuń wiele projektów języka C# za pomocą rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="0c025-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="0c025-128">Dodawanie wielu projektów języka C# do rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych:</span><span class="sxs-lookup"><span data-stu-id="0c025-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="0c025-129">Za pomocą rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych, należy usunąć wielu projektów języka C#:</span><span class="sxs-lookup"><span data-stu-id="0c025-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> <span data-ttu-id="0c025-130">Symboli wieloznacznych nie jest funkcją interfejsu wiersza polecenia, ale raczej funkcja powłoki poleceń programu.</span><span class="sxs-lookup"><span data-stu-id="0c025-130">Globbing is not a CLI feature but rather a feature of the command shell.</span></span> <span data-ttu-id="0c025-131">Aby pomyślnie rozszerzyć plików, należy użyć powłoki, który obsługuje symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="0c025-131">To successfully expand the files, you must use a shell that supports globbing.</span></span> <span data-ttu-id="0c025-132">Aby uzyskać więcej informacji na temat obsługi symboli wieloznacznych, zobacz [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span><span class="sxs-lookup"><span data-stu-id="0c025-132">For more information about globbing, see [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span></span>
