---
title: dotnet sln — polecenie
description: Polecenie dotnet-sln udostępnia wygodną opcję dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.
ms.date: 02/14/2020
ms.openlocfilehash: dc0e2f294076ea649f150b076ac279cdc5d224a0
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503591"
---
# <a name="dotnet-sln"></a><span data-ttu-id="9a5c3-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="9a5c3-103">dotnet sln</span></span>

<span data-ttu-id="9a5c3-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="9a5c3-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9a5c3-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="9a5c3-105">Name</span></span>

<span data-ttu-id="9a5c3-106">`dotnet sln` — modyfikuje plik rozwiązania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-106">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9a5c3-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9a5c3-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a><span data-ttu-id="9a5c3-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9a5c3-108">Description</span></span>

<span data-ttu-id="9a5c3-109">`dotnet sln` polecenie zapewnia wygodny sposób dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-109">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="9a5c3-110">Aby użyć polecenia `dotnet sln`, plik rozwiązania musi już istnieć.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="9a5c3-111">Jeśli trzeba ją utworzyć, użyj polecenia [dotnet New](dotnet-new.md) , tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9a5c3-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="9a5c3-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9a5c3-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="9a5c3-113">Plik rozwiązania, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-113">The solution file to use.</span></span> <span data-ttu-id="9a5c3-114">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-114">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="9a5c3-115">Jeśli w katalogu znajduje się wiele plików rozwiązania, należy określić jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-115">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="9a5c3-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="9a5c3-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="9a5c3-117">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-117">Prints out a short help for the command.</span></span>

## <a name="commands"></a><span data-ttu-id="9a5c3-118">Polecenia</span><span class="sxs-lookup"><span data-stu-id="9a5c3-118">Commands</span></span>

### `add`

<span data-ttu-id="9a5c3-119">Dodaje projekt lub wiele projektów do pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-119">Adds a project or multiple projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9a5c3-120">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9a5c3-120">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH>
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="9a5c3-121">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9a5c3-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="9a5c3-122">Plik rozwiązania, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-122">The solution file to use.</span></span> <span data-ttu-id="9a5c3-123">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="9a5c3-124">Jeśli w katalogu znajduje się wiele plików rozwiązania, należy określić jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-124">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="9a5c3-125">Ścieżka do projektu, który ma zostać dodany do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-125">The path to the project to add to the solution.</span></span> <span data-ttu-id="9a5c3-126">Dodaj wiele projektów, dodając je po innych rozdzielonych spacjami.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-126">Add multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="9a5c3-127">Rozszerzenia [wzorca obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) powłoki systemu UNIX/Linux są przetwarzane prawidłowo przez polecenie `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-127">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="9a5c3-128">Opcje</span><span class="sxs-lookup"><span data-stu-id="9a5c3-128">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="9a5c3-129">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-129">Prints out a short help for the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="9a5c3-130">Umieszcza projekty w katalogu głównym rozwiązania zamiast tworzenia folderu rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-130">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="9a5c3-131">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-131">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder`**

  <span data-ttu-id="9a5c3-132">Ścieżka folderu rozwiązania docelowego, do którego mają zostać dodane projekty.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-132">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="9a5c3-133">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-133">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="9a5c3-134">Usuwa projekt lub wiele projektów z pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-134">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9a5c3-135">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9a5c3-135">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH>
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="9a5c3-136">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9a5c3-136">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="9a5c3-137">Plik rozwiązania, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-137">The solution file to use.</span></span> <span data-ttu-id="9a5c3-138">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-138">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="9a5c3-139">Jeśli w katalogu znajduje się wiele plików rozwiązania, należy określić jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-139">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="9a5c3-140">Ścieżka do projektu, który ma zostać usunięty z rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-140">The path to the project to remove from the solution.</span></span> <span data-ttu-id="9a5c3-141">Usuń wiele projektów, dodając je po innych rozdzielonych spacjami.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-141">Remove multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="9a5c3-142">Rozszerzenia [wzorca obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) powłoki systemu UNIX/Linux są przetwarzane prawidłowo przez polecenie `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-142">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="9a5c3-143">Opcje</span><span class="sxs-lookup"><span data-stu-id="9a5c3-143">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="9a5c3-144">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-144">Prints out a short help for the command.</span></span>

### `list`

<span data-ttu-id="9a5c3-145">Wyświetla wszystkie projekty w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-145">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9a5c3-146">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9a5c3-146">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="9a5c3-147">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9a5c3-147">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="9a5c3-148">Plik rozwiązania, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-148">The solution file to use.</span></span> <span data-ttu-id="9a5c3-149">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-149">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="9a5c3-150">Jeśli w katalogu znajduje się wiele plików rozwiązania, należy określić jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-150">If there are multiple solution files in the directory, one must be specified.</span></span>

#### <a name="options"></a><span data-ttu-id="9a5c3-151">Opcje</span><span class="sxs-lookup"><span data-stu-id="9a5c3-151">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="9a5c3-152">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="9a5c3-152">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="9a5c3-153">Przykłady</span><span class="sxs-lookup"><span data-stu-id="9a5c3-153">Examples</span></span>

- <span data-ttu-id="9a5c3-154">Dodaj C# projekt do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="9a5c3-154">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="9a5c3-155">Usuń C# projekt z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="9a5c3-155">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="9a5c3-156">Dodaj wiele C# projektów do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="9a5c3-156">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="9a5c3-157">Usuń wiele C# projektów z rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="9a5c3-157">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="9a5c3-158">Dodawanie wielu C# projektów do rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych (tylko w systemie UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="9a5c3-158">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="9a5c3-159">Usuwanie wielu C# projektów z rozwiązania przy użyciu wzorca obsługi symboli wieloznacznych (tylko w systemie UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="9a5c3-159">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
