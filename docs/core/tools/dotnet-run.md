---
title: polecenie dotnet run
description: Polecenie dotnet run zapewnia wygodną opcję uruchamiania aplikacji z kodu źródłowego.
ms.date: 02/19/2020
ms.openlocfilehash: e442ed56d676ffd189ef6d394d840cea671c2dc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157079"
---
# <a name="dotnet-run"></a><span data-ttu-id="d8d94-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d8d94-103">dotnet run</span></span>

<span data-ttu-id="d8d94-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="d8d94-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d8d94-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d8d94-105">Name</span></span>

<span data-ttu-id="d8d94-106">`dotnet run`- Uruchamia kod źródłowy bez żadnych jawnych poleceń kompilacji lub uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="d8d94-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d8d94-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d8d94-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile]
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project]
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a><span data-ttu-id="d8d94-108">Opis</span><span class="sxs-lookup"><span data-stu-id="d8d94-108">Description</span></span>

<span data-ttu-id="d8d94-109">Polecenie `dotnet run` zapewnia wygodną opcję uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8d94-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="d8d94-110">Jest to przydatne do szybkiego iteracyjnego rozwoju z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8d94-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="d8d94-111">Polecenie zależy od [`dotnet build`](dotnet-build.md) polecenia do utworzenia kodu.</span><span class="sxs-lookup"><span data-stu-id="d8d94-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="d8d94-112">Wszelkie wymagania dotyczące kompilacji, takie jak, że projekt `dotnet run` musi zostać przywrócony w pierwszej kolejności, stosuje się do, jak również.</span><span class="sxs-lookup"><span data-stu-id="d8d94-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="d8d94-113">Pliki wyjściowe są zapisywane w lokalizacji `bin/<configuration>/<target>`domyślnej, która jest .</span><span class="sxs-lookup"><span data-stu-id="d8d94-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="d8d94-114">Na przykład, jeśli `netcoreapp2.1` masz aplikację `dotnet run`i uruchomisz, dane wyjściowe są umieszczane w pliku `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="d8d94-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="d8d94-115">Pliki są zastępowane zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="d8d94-115">Files are overwritten as needed.</span></span> <span data-ttu-id="d8d94-116">Pliki tymczasowe są `obj` umieszczane w katalogu.</span><span class="sxs-lookup"><span data-stu-id="d8d94-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="d8d94-117">Jeśli projekt określa wiele struktur, `dotnet run` wykonywanie wyników w `-f|--framework <FRAMEWORK>` błąd, chyba że opcja jest używana do określenia struktury.</span><span class="sxs-lookup"><span data-stu-id="d8d94-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="d8d94-118">Polecenie `dotnet run` jest używane w kontekście projektów, a nie zestawy zbudowane.</span><span class="sxs-lookup"><span data-stu-id="d8d94-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="d8d94-119">Jeśli próbujesz uruchomić dll aplikacji zależnej od struktury, należy użyć [dotnet](dotnet.md) bez polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8d94-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="d8d94-120">Na przykład, `myapp.dll`aby uruchomić , należy użyć:</span><span class="sxs-lookup"><span data-stu-id="d8d94-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="d8d94-121">Aby uzyskać więcej `dotnet` informacji na temat sterownika, zobacz temat [.NET Core Command Line Tools (CLI).](index.md)</span><span class="sxs-lookup"><span data-stu-id="d8d94-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="d8d94-122">Aby uruchomić aplikację, `dotnet run` polecenie rozwiązuje zależności aplikacji, które znajdują się poza udostępnionym czasie wykonywania z pamięci podręcznej NuGet.</span><span class="sxs-lookup"><span data-stu-id="d8d94-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="d8d94-123">Ponieważ używa buforowanych zależności, nie jest zalecane `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="d8d94-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="d8d94-124">Zamiast tego należy utworzyć [`dotnet publish`](dotnet-publish.md) [wdrożenie](../deploying/index.md) przy użyciu polecenia i wdrożyć opublikowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="d8d94-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="d8d94-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="d8d94-125">Options</span></span>

- **`--`**

  <span data-ttu-id="d8d94-126">Rozgranicza `dotnet run` argumenty do argumentów dla uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8d94-126">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="d8d94-127">Wszystkie argumenty po tym ograniczniku są przekazywane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8d94-127">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="d8d94-128">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d8d94-128">Defines the build configuration.</span></span> <span data-ttu-id="d8d94-129">Wartość domyślna dla `Debug`większości projektów jest , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="d8d94-129">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d8d94-130">Tworzy i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d8d94-130">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d8d94-131">Struktura musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d8d94-131">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="d8d94-132">Wymusza rozwiązywanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d8d94-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d8d94-133">Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="d8d94-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d8d94-134">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8d94-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="d8d94-135">Umożliwia polecenie, aby zatrzymać i czekać na dane wejściowe użytkownika lub akcji (na przykład, aby zakończyć uwierzytelnianie).</span><span class="sxs-lookup"><span data-stu-id="d8d94-135">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="d8d94-136">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d8d94-136">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="d8d94-137">Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8d94-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="d8d94-138">Profile uruchamiania są zdefiniowane w pliku *launchSettings.json* `Development`i `Staging`są `Production`zwykle nazywane , i .</span><span class="sxs-lookup"><span data-stu-id="d8d94-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="d8d94-139">Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="d8d94-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="d8d94-140">Nie tworzy projektu przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="d8d94-140">Doesn't build the project before running.</span></span> <span data-ttu-id="d8d94-141">To również niejawne ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="d8d94-141">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="d8d94-142">Podczas przywracania projektu z odwołaniami do projektu (P2P) przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="d8d94-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="d8d94-143">Nie próbuje użyć *launchSettings.json* do skonfigurowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8d94-143">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d8d94-144">Nie wykonuje przywracania niejawnego podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8d94-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="d8d94-145">Określa ścieżkę pliku projektu do uruchomienia (nazwa folderu lub pełna ścieżka).</span><span class="sxs-lookup"><span data-stu-id="d8d94-145">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="d8d94-146">Jeśli nie zostanie określony, domyślnie jest to bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="d8d94-146">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="d8d94-147">Określa docelowy czas wykonywania, dla której ma zostać przywrócony pakiety.</span><span class="sxs-lookup"><span data-stu-id="d8d94-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="d8d94-148">Aby uzyskać listę identyfikatorów runtime (RID), zobacz [katalog RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d8d94-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d8d94-149">`-r`opcja krótka dostępna od czasu sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d8d94-149">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="d8d94-150">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8d94-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d8d94-151">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="d8d94-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d8d94-152">Wartością domyślną jest `m`.</span><span class="sxs-lookup"><span data-stu-id="d8d94-152">The default value is `m`.</span></span> <span data-ttu-id="d8d94-153">Dostępne od sdk .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="d8d94-153">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="d8d94-154">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d8d94-154">Examples</span></span>

- <span data-ttu-id="d8d94-155">Uruchom projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="d8d94-155">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="d8d94-156">Uruchom określony projekt:</span><span class="sxs-lookup"><span data-stu-id="d8d94-156">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="d8d94-157">Uruchom projekt w bieżącym katalogu `--help` (argument w tym przykładzie jest przekazywany do aplikacji, ponieważ używana jest opcja puste): `--`</span><span class="sxs-lookup"><span data-stu-id="d8d94-157">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="d8d94-158">Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu tylko z minimalnym wyjściem wyjściowym, a następnie uruchom projekt: (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="d8d94-158">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
