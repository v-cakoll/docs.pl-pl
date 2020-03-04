---
title: polecenie dotnet Run
description: Polecenie dotnet Run udostępnia wygodną opcję uruchamiania aplikacji z kodu źródłowego.
ms.date: 02/19/2020
ms.openlocfilehash: e442ed56d676ffd189ef6d394d840cea671c2dc6
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157079"
---
# <a name="dotnet-run"></a><span data-ttu-id="805d2-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="805d2-103">dotnet run</span></span>

<span data-ttu-id="805d2-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="805d2-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="805d2-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="805d2-105">Name</span></span>

<span data-ttu-id="805d2-106">`dotnet run` — uruchamia kod źródłowy bez żadnych jawnych poleceń kompilacji lub uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="805d2-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="805d2-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="805d2-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile]
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project]
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a><span data-ttu-id="805d2-108">Opis</span><span class="sxs-lookup"><span data-stu-id="805d2-108">Description</span></span>

<span data-ttu-id="805d2-109">Polecenie `dotnet run` udostępnia wygodną opcję uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="805d2-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="805d2-110">Jest to przydatne w przypadku szybkiego iteracyjnego programowania z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="805d2-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="805d2-111">Polecenie jest zależne od polecenia [`dotnet build`](dotnet-build.md) do kompilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="805d2-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="805d2-112">Wszelkie wymagania dotyczące kompilacji, takie jak najpierw należy przywrócić projekt, należy zastosować również do `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="805d2-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="805d2-113">Pliki wyjściowe są zapisywane w domyślnej lokalizacji, która jest `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="805d2-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="805d2-114">Na przykład jeśli masz aplikację `netcoreapp2.1` i uruchomisz `dotnet run`, dane wyjściowe są umieszczane w `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="805d2-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="805d2-115">Pliki są zastępowane w razie konieczności.</span><span class="sxs-lookup"><span data-stu-id="805d2-115">Files are overwritten as needed.</span></span> <span data-ttu-id="805d2-116">Pliki tymczasowe są umieszczane w katalogu `obj`.</span><span class="sxs-lookup"><span data-stu-id="805d2-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="805d2-117">Jeśli projekt określa wiele struktur, wykonywanie `dotnet run` powoduje błąd, chyba że zostanie użyta opcja `-f|--framework <FRAMEWORK>` do określenia struktury.</span><span class="sxs-lookup"><span data-stu-id="805d2-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="805d2-118">Polecenie `dotnet run` jest używane w kontekście projektów, nieskompilowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="805d2-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="805d2-119">Jeśli próbujesz uruchomić bibliotekę DLL aplikacji zależnej od platformy, musisz użyć [dotnet](dotnet.md) bez polecenia.</span><span class="sxs-lookup"><span data-stu-id="805d2-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="805d2-120">Na przykład aby uruchomić `myapp.dll`, użyj:</span><span class="sxs-lookup"><span data-stu-id="805d2-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="805d2-121">Aby uzyskać więcej informacji na temat sterownika `dotnet`, zobacz temat [narzędzia wiersza polecenia (CLI) platformy .NET Core](index.md) .</span><span class="sxs-lookup"><span data-stu-id="805d2-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="805d2-122">Aby uruchomić aplikację, polecenie `dotnet run` rozwiązuje zależności aplikacji, które są poza udostępnionym środowiskiem uruchomieniowym z pamięci podręcznej NuGet.</span><span class="sxs-lookup"><span data-stu-id="805d2-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="805d2-123">Ponieważ używa ona zależności buforowanych, nie zaleca się używania `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="805d2-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="805d2-124">Zamiast tego [Utwórz wdrożenie](../deploying/index.md) przy użyciu [`dotnet publish`](dotnet-publish.md) polecenia i Wdróż opublikowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="805d2-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="805d2-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="805d2-125">Options</span></span>

- **`--`**

  <span data-ttu-id="805d2-126">Ogranicza argumenty do `dotnet run` z argumentów dla uruchamianej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="805d2-126">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="805d2-127">Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="805d2-127">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="805d2-128">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="805d2-128">Defines the build configuration.</span></span> <span data-ttu-id="805d2-129">Wartość domyślna dla większości projektów jest `Debug`, ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="805d2-129">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="805d2-130">Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="805d2-130">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="805d2-131">Struktura musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="805d2-131">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="805d2-132">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="805d2-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="805d2-133">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="805d2-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="805d2-134">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="805d2-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="805d2-135">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="805d2-135">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="805d2-136">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="805d2-136">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="805d2-137">Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="805d2-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="805d2-138">Profile uruchamiania są zdefiniowane w pliku *profilu launchsettings. JSON* i są zwykle nazywane `Development`, `Staging`i `Production`.</span><span class="sxs-lookup"><span data-stu-id="805d2-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="805d2-139">Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="805d2-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="805d2-140">Nie kompiluje projektu przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="805d2-140">Doesn't build the project before running.</span></span> <span data-ttu-id="805d2-141">Również niejawne ustawia flagę `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="805d2-141">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="805d2-142">W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="805d2-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="805d2-143">Nie próbuje skonfigurować aplikacji przy użyciu pliku *profilu launchsettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="805d2-143">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="805d2-144">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="805d2-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="805d2-145">Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełna ścieżka).</span><span class="sxs-lookup"><span data-stu-id="805d2-145">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="805d2-146">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="805d2-146">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="805d2-147">Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety.</span><span class="sxs-lookup"><span data-stu-id="805d2-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="805d2-148">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="805d2-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="805d2-149">`-r` krótka opcja dostępna od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="805d2-149">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="805d2-150">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="805d2-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="805d2-151">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="805d2-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="805d2-152">Wartością domyślną jest `m`.</span><span class="sxs-lookup"><span data-stu-id="805d2-152">The default value is `m`.</span></span> <span data-ttu-id="805d2-153">Dostępne od wersji .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="805d2-153">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="805d2-154">Przykłady</span><span class="sxs-lookup"><span data-stu-id="805d2-154">Examples</span></span>

- <span data-ttu-id="805d2-155">Uruchom projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="805d2-155">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="805d2-156">Uruchom określony projekt:</span><span class="sxs-lookup"><span data-stu-id="805d2-156">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="805d2-157">Uruchom projekt w bieżącym katalogu (`--help` argument w tym przykładzie jest przesyłany do aplikacji, ponieważ jest używana opcja pustej `--`):</span><span class="sxs-lookup"><span data-stu-id="805d2-157">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="805d2-158">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu, wyświetlając tylko minimalne dane wyjściowe, a następnie Uruchom projekt: (zestaw .NET Core SDK 2,0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="805d2-158">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
