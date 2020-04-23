---
title: polecenie dotnet run
description: Polecenie dotnet run zapewnia wygodną opcję uruchamiania aplikacji z kodu źródłowego.
ms.date: 02/19/2020
ms.openlocfilehash: 77282fd8615ef01b7867c1bf0f741c834b6ddb30
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102774"
---
# <a name="dotnet-run"></a><span data-ttu-id="a78a0-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a78a0-103">dotnet run</span></span>

<span data-ttu-id="a78a0-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="a78a0-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a78a0-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a78a0-105">Name</span></span>

<span data-ttu-id="a78a0-106">`dotnet run`- Uruchamia kod źródłowy bez żadnych jawnych poleceń kompilacji lub uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="a78a0-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a78a0-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a78a0-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a><span data-ttu-id="a78a0-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a78a0-108">Description</span></span>

<span data-ttu-id="a78a0-109">Polecenie `dotnet run` zapewnia wygodną opcję uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="a78a0-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="a78a0-110">Jest to przydatne do szybkiego rozwoju iteracyjnego z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="a78a0-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="a78a0-111">Polecenie zależy od [`dotnet build`](dotnet-build.md) polecenia do tworzenia kodu.</span><span class="sxs-lookup"><span data-stu-id="a78a0-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="a78a0-112">Wszelkie wymagania dotyczące kompilacji, takie jak, że projekt `dotnet run` musi zostać przywrócony w pierwszej kolejności, stosuje się również do.</span><span class="sxs-lookup"><span data-stu-id="a78a0-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="a78a0-113">Pliki wyjściowe są zapisywane w `bin/<configuration>/<target>`lokalizacji domyślnej, która jest .</span><span class="sxs-lookup"><span data-stu-id="a78a0-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="a78a0-114">Na przykład, jeśli `netcoreapp2.1` masz aplikację `dotnet run`i uruchomisz `bin/Debug/netcoreapp2.1`, dane wyjściowe są umieszczane w pliku .</span><span class="sxs-lookup"><span data-stu-id="a78a0-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="a78a0-115">Pliki są zastępowane w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="a78a0-115">Files are overwritten as needed.</span></span> <span data-ttu-id="a78a0-116">Pliki tymczasowe są `obj` umieszczane w katalogu.</span><span class="sxs-lookup"><span data-stu-id="a78a0-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="a78a0-117">Jeśli projekt określa wiele struktur, `dotnet run` wykonywanie powoduje błąd, `-f|--framework <FRAMEWORK>` chyba że opcja jest używana do określenia struktury.</span><span class="sxs-lookup"><span data-stu-id="a78a0-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="a78a0-118">Polecenie `dotnet run` jest używane w kontekście projektów, a nie zestawów.</span><span class="sxs-lookup"><span data-stu-id="a78a0-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="a78a0-119">Jeśli próbujesz uruchomić bibliotekę DLL aplikacji zależnej od struktury, należy użyć [dotnet](dotnet.md) bez polecenia.</span><span class="sxs-lookup"><span data-stu-id="a78a0-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="a78a0-120">Na przykład, `myapp.dll`aby uruchomić , użyj:</span><span class="sxs-lookup"><span data-stu-id="a78a0-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="a78a0-121">Aby uzyskać więcej `dotnet` informacji na temat sterownika, zobacz temat [.NET Core Command Line Tools (CLI).](index.md)</span><span class="sxs-lookup"><span data-stu-id="a78a0-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="a78a0-122">Aby uruchomić aplikację, `dotnet run` polecenie rozwiązuje zależności aplikacji, które znajdują się poza udostępnionym środowiskom run z pamięci podręcznej NuGet.</span><span class="sxs-lookup"><span data-stu-id="a78a0-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="a78a0-123">Ponieważ używa zależności w pamięci podręcznej, nie `dotnet run` jest zalecane do uruchamiania aplikacji w produkcji.</span><span class="sxs-lookup"><span data-stu-id="a78a0-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="a78a0-124">Zamiast tego [utwórz](../deploying/index.md) wdrożenie [`dotnet publish`](dotnet-publish.md) za pomocą polecenia i wdrożyć opublikowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="a78a0-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="a78a0-125">Niejawne przywracanie</span><span class="sxs-lookup"><span data-stu-id="a78a0-125">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="a78a0-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="a78a0-126">Options</span></span>

- **`--`**

  <span data-ttu-id="a78a0-127">Rozgranicza `dotnet run` argumenty na argumenty dla uruchamianą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a78a0-127">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="a78a0-128">Wszystkie argumenty po tym ogranicznik są przekazywane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a78a0-128">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="a78a0-129">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a78a0-129">Defines the build configuration.</span></span> <span data-ttu-id="a78a0-130">Wartość domyślna dla `Debug`większości projektów to , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="a78a0-130">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a78a0-131">Tworzy i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a78a0-131">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="a78a0-132">Struktura musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a78a0-132">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="a78a0-133">Wymusza wszystkie zależności do rozwiązania, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a78a0-133">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="a78a0-134">Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="a78a0-134">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a78a0-135">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a78a0-135">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="a78a0-136">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="a78a0-136">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="a78a0-137">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a78a0-137">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="a78a0-138">Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a78a0-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="a78a0-139">Profile uruchamiania są definiowane w pliku *launchSettings.json* i są zwykle nazywane `Development`, `Staging`i `Production`.</span><span class="sxs-lookup"><span data-stu-id="a78a0-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="a78a0-140">Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="a78a0-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="a78a0-141">Nie tworzy projektu przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="a78a0-141">Doesn't build the project before running.</span></span> <span data-ttu-id="a78a0-142">Również niejawne `--no-restore` ustawia flagę.</span><span class="sxs-lookup"><span data-stu-id="a78a0-142">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="a78a0-143">Podczas przywracania projektu z odwołaniami do projektu do projektu (P2P), przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="a78a0-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="a78a0-144">Nie próbuje użyć *launchSettings.json,* aby skonfigurować aplikację.</span><span class="sxs-lookup"><span data-stu-id="a78a0-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="a78a0-145">Nie wykonuje niejawnego przywracania podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="a78a0-145">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="a78a0-146">Określa ścieżkę pliku projektu do uruchomienia (nazwę folderu lub pełną ścieżkę).</span><span class="sxs-lookup"><span data-stu-id="a78a0-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="a78a0-147">Jeśli nie zostanie określony, domyślnie jest to bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="a78a0-147">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="a78a0-148">Określa docelowy czas wykonywania do przywrócenia pakietów dla.</span><span class="sxs-lookup"><span data-stu-id="a78a0-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="a78a0-149">Aby uzyskać listę identyfikatorów środowiska wykonawczego (RID), zobacz [katalog RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a78a0-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="a78a0-150">`-r`dostępna od momentu sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a78a0-150">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a78a0-151">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="a78a0-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a78a0-152">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="a78a0-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a78a0-153">Wartością domyślną jest `m`.</span><span class="sxs-lookup"><span data-stu-id="a78a0-153">The default value is `m`.</span></span> <span data-ttu-id="a78a0-154">Dostępne od .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="a78a0-154">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="a78a0-155">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a78a0-155">Examples</span></span>

- <span data-ttu-id="a78a0-156">Uruchom projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="a78a0-156">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="a78a0-157">Uruchom określony projekt:</span><span class="sxs-lookup"><span data-stu-id="a78a0-157">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="a78a0-158">Uruchom projekt w bieżącym katalogu `--help` (argument w tym przykładzie jest przekazywany do aplikacji, ponieważ używana jest pusta `--` opcja):</span><span class="sxs-lookup"><span data-stu-id="a78a0-158">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="a78a0-159">Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu tylko pokazując minimalne dane wyjściowe, a następnie uruchom projekt: (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="a78a0-159">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
