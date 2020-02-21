---
title: dotnet sln — polecenie
description: Polecenie dotnet-sln udostępnia wygodną opcję dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543485"
---
# <a name="dotnet-sln"></a><span data-ttu-id="edf9a-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="edf9a-103">dotnet sln</span></span>

<span data-ttu-id="edf9a-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="edf9a-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="edf9a-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="edf9a-105">Name</span></span>

<span data-ttu-id="edf9a-106">`dotnet sln` — wyświetla lub modyfikuje projekty w pliku rozwiązania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="edf9a-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="edf9a-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="edf9a-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a><span data-ttu-id="edf9a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="edf9a-108">Description</span></span>

<span data-ttu-id="edf9a-109">`dotnet sln` polecenie zapewnia wygodny sposób wyświetlania i modyfikowania projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="edf9a-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="edf9a-110">Aby użyć polecenia `dotnet sln`, plik rozwiązania musi już istnieć.</span><span class="sxs-lookup"><span data-stu-id="edf9a-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="edf9a-111">Jeśli trzeba ją utworzyć, użyj polecenia [dotnet New](dotnet-new.md) , jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="edf9a-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="edf9a-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="edf9a-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="edf9a-113">Plik rozwiązania, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="edf9a-113">The solution file to use.</span></span> <span data-ttu-id="edf9a-114">Jeśli ten argument zostanie pominięty, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="edf9a-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="edf9a-115">Jeśli nie zostanie znaleziony żaden plik rozwiązania lub wiele plików rozwiązania, polecenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="edf9a-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="edf9a-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="edf9a-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="edf9a-117">Drukuje opis sposobu użycia polecenia.</span><span class="sxs-lookup"><span data-stu-id="edf9a-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="edf9a-118">Polecenia</span><span class="sxs-lookup"><span data-stu-id="edf9a-118">Commands</span></span>

### `list`

<span data-ttu-id="edf9a-119">Wyświetla wszystkie projekty w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="edf9a-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="edf9a-120">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="edf9a-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="edf9a-121">Argumenty</span><span class="sxs-lookup"><span data-stu-id="edf9a-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="edf9a-122">Plik rozwiązania, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="edf9a-122">The solution file to use.</span></span> <span data-ttu-id="edf9a-123">Jeśli ten argument zostanie pominięty, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="edf9a-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="edf9a-124">Jeśli nie zostanie znaleziony żaden plik rozwiązania lub wiele plików rozwiązania, polecenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="edf9a-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="edf9a-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="edf9a-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="edf9a-126">Drukuje opis sposobu użycia polecenia.</span><span class="sxs-lookup"><span data-stu-id="edf9a-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="edf9a-127">Dodaje jeden lub więcej projektów do pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="edf9a-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="edf9a-128">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="edf9a-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="edf9a-129">Argumenty</span><span class="sxs-lookup"><span data-stu-id="edf9a-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="edf9a-130">Plik rozwiązania, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="edf9a-130">The solution file to use.</span></span> <span data-ttu-id="edf9a-131">Jeśli nie jest określony, polecenie przeszukuje bieżący katalog dla jednego i kończy się niepowodzeniem, jeśli istnieje wiele plików rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="edf9a-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="edf9a-132">Ścieżka do projektu lub projektów, które mają zostać dodane do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="edf9a-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="edf9a-133">Rozszerzenia [wzorca obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) powłoki systemu UNIX/Linux są przetwarzane prawidłowo przez polecenie `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="edf9a-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="edf9a-134">Opcje</span><span class="sxs-lookup"><span data-stu-id="edf9a-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="edf9a-135">Drukuje opis sposobu użycia polecenia.</span><span class="sxs-lookup"><span data-stu-id="edf9a-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="edf9a-136">Umieszcza projekty w katalogu głównym rozwiązania zamiast tworzenia folderu rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="edf9a-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="edf9a-137">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="edf9a-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder`**

  <span data-ttu-id="edf9a-138">Ścieżka folderu rozwiązania docelowego, do którego mają zostać dodane projekty.</span><span class="sxs-lookup"><span data-stu-id="edf9a-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="edf9a-139">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="edf9a-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="edf9a-140">Usuwa projekt lub wiele projektów z pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="edf9a-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="edf9a-141">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="edf9a-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="edf9a-142">Argumenty</span><span class="sxs-lookup"><span data-stu-id="edf9a-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="edf9a-143">Plik rozwiązania, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="edf9a-143">The solution file to use.</span></span> <span data-ttu-id="edf9a-144">Jeśli pozostanie nieokreślony, polecenie przeszukuje bieżący katalog dla jednego i kończy się niepowodzeniem, jeśli istnieje wiele plików rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="edf9a-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="edf9a-145">Ścieżka do projektu lub projektów, które mają zostać dodane do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="edf9a-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="edf9a-146">Rozszerzenia [wzorca obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) powłoki systemu UNIX/Linux są przetwarzane prawidłowo przez polecenie `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="edf9a-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="edf9a-147">Opcje</span><span class="sxs-lookup"><span data-stu-id="edf9a-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="edf9a-148">Drukuje opis sposobu użycia polecenia.</span><span class="sxs-lookup"><span data-stu-id="edf9a-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="edf9a-149">Przykłady</span><span class="sxs-lookup"><span data-stu-id="edf9a-149">Examples</span></span>

- <span data-ttu-id="edf9a-150">Utwórz listę projektów w rozwiązaniu:</span><span class="sxs-lookup"><span data-stu-id="edf9a-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="edf9a-151">Dodaj C# projekt do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="edf9a-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="edf9a-152">Usuń C# projekt z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="edf9a-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="edf9a-153">Dodaj wiele C# projektów do katalogu głównego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="edf9a-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="edf9a-154">Dodaj wiele C# projektów do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="edf9a-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="edf9a-155">Usuń wiele C# projektów z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="edf9a-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="edf9a-156">Dodawanie wielu C# projektów do rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych (tylko w systemie UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="edf9a-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="edf9a-157">Usuwanie wielu C# projektów z rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych (tylko w systemie UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="edf9a-157">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
