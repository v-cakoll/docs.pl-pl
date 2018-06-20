---
title: polecenie sln DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie dotnet sln oferuje wygodny możliwość dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.
author: mairaw
ms.author: mairaw
ms.date: 06/13/2018
ms.openlocfilehash: 65ae402ef5519863886c8cf833598f5314b4bdad
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208336"
---
# <a name="dotnet-sln"></a><span data-ttu-id="cb154-103">DotNet sln</span><span class="sxs-lookup"><span data-stu-id="cb154-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cb154-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cb154-104">Name</span></span>

<span data-ttu-id="cb154-105">`dotnet sln` -Modyfikuje plik rozwiązania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb154-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cb154-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="cb154-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="cb154-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cb154-107">Description</span></span>

<span data-ttu-id="cb154-108">`dotnet sln` Polecenia oferuje wygodny sposób dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="cb154-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="cb154-109">Aby użyć `dotnet sln` polecenia, pliku rozwiązania musi już istnieć.</span><span class="sxs-lookup"><span data-stu-id="cb154-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="cb154-110">Aby go utworzyć, należy użyć [dotnet nowe](dotnet-new.md) polecenia, takich jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cb154-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="cb154-111">Polecenia</span><span class="sxs-lookup"><span data-stu-id="cb154-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="cb154-112">Dodaje projekt lub wielu projektach pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="cb154-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="cb154-113">[Wzorce globbing](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminali z systemem Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="cb154-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="cb154-114">Usuwa projekt lub wielu projektów z pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="cb154-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="cb154-115">[Wzorce globbing](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminali z systemem Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="cb154-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="cb154-116">Lista wszystkich projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="cb154-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="cb154-117">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cb154-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="cb154-118">Plik rozwiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="cb154-118">Solution file to use.</span></span> <span data-ttu-id="cb154-119">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="cb154-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="cb154-120">Jeśli istnieje wiele plików rozwiązania w katalogu, co jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="cb154-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="cb154-121">Opcje</span><span class="sxs-lookup"><span data-stu-id="cb154-121">Options</span></span>

`-h|--help`

<span data-ttu-id="cb154-122">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="cb154-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="cb154-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cb154-123">Examples</span></span>

<span data-ttu-id="cb154-124">Dodaj projekt C# do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="cb154-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="cb154-125">Usuwanie projektu C# z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="cb154-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="cb154-126">Dodawanie wielu projektów C# do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="cb154-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="cb154-127">Usuń wiele projektów C# z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="cb154-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="cb154-128">Dodawanie wielu projektów C# do rozwiązania przy użyciu wzorca globbing:</span><span class="sxs-lookup"><span data-stu-id="cb154-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="cb154-129">Usuń wiele projektów C# z rozwiązania przy użyciu wzorca globbing:</span><span class="sxs-lookup"><span data-stu-id="cb154-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`
