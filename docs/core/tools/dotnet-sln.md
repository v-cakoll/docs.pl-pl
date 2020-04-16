---
title: dotnet sln, polecenie
description: Polecenie dotnet-sln zapewnia wygodną opcję dodawania, usuwania i listy projektów w pliku rozwiązania.
ms.date: 02/14/2020
ms.openlocfilehash: 231287477d986f9ec4a5404cc5278e76c297faa4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463396"
---
# <a name="dotnet-sln"></a><span data-ttu-id="37794-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="37794-103">dotnet sln</span></span>

<span data-ttu-id="37794-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="37794-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="37794-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="37794-105">Name</span></span>

<span data-ttu-id="37794-106">`dotnet sln`- Wyświetla lub modyfikuje projekty w pliku rozwiązania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="37794-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="37794-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="37794-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a><span data-ttu-id="37794-108">Opis</span><span class="sxs-lookup"><span data-stu-id="37794-108">Description</span></span>

<span data-ttu-id="37794-109">Polecenie `dotnet sln` zapewnia wygodny sposób listy i modyfikowania projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="37794-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="37794-110">Aby użyć `dotnet sln` polecenia, plik rozwiązania musi już istnieć.</span><span class="sxs-lookup"><span data-stu-id="37794-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="37794-111">Jeśli chcesz go utworzyć, użyj nowego polecenia [dotnet,](dotnet-new.md) jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="37794-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="37794-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="37794-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="37794-113">Plik rozwiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="37794-113">The solution file to use.</span></span> <span data-ttu-id="37794-114">Jeśli ten argument zostanie pominięty, polecenie przeszukuje bieżący katalog dla jednego.</span><span class="sxs-lookup"><span data-stu-id="37794-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="37794-115">Jeśli nie znajdzie żadnego pliku rozwiązania lub wielu plików rozwiązania, polecenie zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="37794-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="37794-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="37794-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="37794-117">Drukuje opis sposobu korzystania z polecenia.</span><span class="sxs-lookup"><span data-stu-id="37794-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="37794-118">Polecenia</span><span class="sxs-lookup"><span data-stu-id="37794-118">Commands</span></span>

### `list`

<span data-ttu-id="37794-119">Wyświetla listę wszystkich projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="37794-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="37794-120">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="37794-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="37794-121">Argumenty</span><span class="sxs-lookup"><span data-stu-id="37794-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="37794-122">Plik rozwiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="37794-122">The solution file to use.</span></span> <span data-ttu-id="37794-123">Jeśli ten argument zostanie pominięty, polecenie przeszukuje bieżący katalog dla jednego.</span><span class="sxs-lookup"><span data-stu-id="37794-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="37794-124">Jeśli nie znajdzie żadnego pliku rozwiązania lub wielu plików rozwiązania, polecenie zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="37794-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="37794-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="37794-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="37794-126">Drukuje opis sposobu korzystania z polecenia.</span><span class="sxs-lookup"><span data-stu-id="37794-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="37794-127">Dodaje jeden lub więcej projektów do pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="37794-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="37794-128">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="37794-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="37794-129">Argumenty</span><span class="sxs-lookup"><span data-stu-id="37794-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="37794-130">Plik rozwiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="37794-130">The solution file to use.</span></span> <span data-ttu-id="37794-131">Jeśli jest nieokreślony, polecenie przeszukuje bieżący katalog dla jednego i kończy się niepowodzeniem, jeśli istnieje wiele plików rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="37794-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="37794-132">Ścieżka do projektu lub projektów, aby dodać do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="37794-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="37794-133">Rozszerzenia [wzorca skorupy](https://en.wikipedia.org/wiki/Glob_(programming)) Uniksa/Linuksa są `dotnet sln` przetwarzane poprawnie przez polecenie.</span><span class="sxs-lookup"><span data-stu-id="37794-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="37794-134">Opcje</span><span class="sxs-lookup"><span data-stu-id="37794-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="37794-135">Drukuje opis sposobu korzystania z polecenia.</span><span class="sxs-lookup"><span data-stu-id="37794-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="37794-136">Umieszcza projekty w katalogu głównym rozwiązania, zamiast tworzyć folder rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="37794-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="37794-137">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="37794-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder <PATH>`**

  <span data-ttu-id="37794-138">Ścieżka folderu rozwiązania docelowego, do aby dodać projekty.</span><span class="sxs-lookup"><span data-stu-id="37794-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="37794-139">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="37794-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="37794-140">Usuwa projekt lub wiele projektów z pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="37794-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="37794-141">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="37794-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="37794-142">Argumenty</span><span class="sxs-lookup"><span data-stu-id="37794-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="37794-143">Plik rozwiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="37794-143">The solution file to use.</span></span> <span data-ttu-id="37794-144">Jeśli nie jest określony, polecenie przeszukuje bieżący katalog dla jednego i kończy się niepowodzeniem, jeśli istnieje wiele plików rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="37794-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="37794-145">Ścieżka do projektu lub projektów, aby dodać do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="37794-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="37794-146">Rozszerzenia [wzorca skorupy](https://en.wikipedia.org/wiki/Glob_(programming)) Uniksa/Linuksa są `dotnet sln` przetwarzane poprawnie przez polecenie.</span><span class="sxs-lookup"><span data-stu-id="37794-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="37794-147">Opcje</span><span class="sxs-lookup"><span data-stu-id="37794-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="37794-148">Drukuje opis sposobu korzystania z polecenia.</span><span class="sxs-lookup"><span data-stu-id="37794-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="37794-149">Przykłady</span><span class="sxs-lookup"><span data-stu-id="37794-149">Examples</span></span>

- <span data-ttu-id="37794-150">Wymień projekty w rozwiązaniu:</span><span class="sxs-lookup"><span data-stu-id="37794-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="37794-151">Dodaj projekt języka C# do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="37794-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="37794-152">Usuń projekt języka C# z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="37794-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="37794-153">Dodaj wiele projektów języka C# do katalogu głównego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="37794-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="37794-154">Dodaj wiele projektów języka C# do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="37794-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="37794-155">Usuń wiele projektów języka C# z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="37794-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="37794-156">Dodaj wiele projektów języka C# do rozwiązania przy użyciu wzorca globbingu (tylko Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="37794-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="37794-157">Dodaj wiele projektów języka C# do rozwiązania przy użyciu wzorca globbing (tylko program Windows PowerShell):</span><span class="sxs-lookup"><span data-stu-id="37794-157">Add multiple C# projects to a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add (ls **/*.csproj)
  ```

- <span data-ttu-id="37794-158">Usuń wiele projektów języka C# z rozwiązania przy użyciu wzorca globbingu (tylko Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="37794-158">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- <span data-ttu-id="37794-159">Usuń wiele projektów języka C# z rozwiązania przy użyciu wzorca globbing (tylko program Windows PowerShell):</span><span class="sxs-lookup"><span data-stu-id="37794-159">Remove multiple C# projects from a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove (ls **/*.csproj)
  ```
