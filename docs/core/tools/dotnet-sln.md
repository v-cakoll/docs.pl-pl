---
title: polecenie sln DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie dotnet sln oferuje wygodny możliwość dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 837d47c38119f9a7aa75c74576ed75b8ef3813dd
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-sln"></a><span data-ttu-id="87ced-103">DotNet sln</span><span class="sxs-lookup"><span data-stu-id="87ced-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="87ced-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="87ced-104">Name</span></span>

<span data-ttu-id="87ced-105">`dotnet sln` -Modyfikuje plik rozwiązania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87ced-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="87ced-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="87ced-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="87ced-107">Opis</span><span class="sxs-lookup"><span data-stu-id="87ced-107">Description</span></span>

<span data-ttu-id="87ced-108">`dotnet sln` Polecenia oferuje wygodny sposób dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="87ced-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

## <a name="commands"></a><span data-ttu-id="87ced-109">Polecenia</span><span class="sxs-lookup"><span data-stu-id="87ced-109">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="87ced-110">Dodaje projekt lub wielu projektach pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="87ced-110">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="87ced-111">[Wzorce globbing](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminali z systemem Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="87ced-111">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="87ced-112">Usuwa projekt lub wielu projektów z pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="87ced-112">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="87ced-113">[Wzorce globbing](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminali z systemem Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="87ced-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="87ced-114">Lista wszystkich projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="87ced-114">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="87ced-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="87ced-115">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="87ced-116">Plik rozwiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="87ced-116">Solution file to use.</span></span> <span data-ttu-id="87ced-117">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="87ced-117">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="87ced-118">Jeśli istnieje wiele plików rozwiązania w katalogu, co jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="87ced-118">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="87ced-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="87ced-119">Options</span></span>

`-h|--help`

<span data-ttu-id="87ced-120">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="87ced-120">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="87ced-121">Przykłady</span><span class="sxs-lookup"><span data-stu-id="87ced-121">Examples</span></span>

<span data-ttu-id="87ced-122">Dodaj projekt C# do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="87ced-122">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="87ced-123">Usuwanie projektu C# z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="87ced-123">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="87ced-124">Dodawanie wielu projektów C# do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="87ced-124">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="87ced-125">Usuń wiele projektów C# z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="87ced-125">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="87ced-126">Dodawanie wielu projektów C# do rozwiązania przy użyciu wzorca globbing:</span><span class="sxs-lookup"><span data-stu-id="87ced-126">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="87ced-127">Usuń wiele projektów C# z rozwiązania przy użyciu wzorca globbing:</span><span class="sxs-lookup"><span data-stu-id="87ced-127">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`
