---
title: polecenie testu dotnet
description: Polecenie Test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 04/29/2020
ms.openlocfilehash: 22b27007d26c98cff40733ef8d449ce334f87848
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802681"
---
# <a name="dotnet-test"></a><span data-ttu-id="66b08-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="66b08-103">dotnet test</span></span>

<span data-ttu-id="66b08-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="66b08-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="66b08-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="66b08-105">Name</span></span>

<span data-ttu-id="66b08-106">`dotnet test`— Sterownik testowy .NET używany do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="66b08-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="66b08-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="66b08-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="66b08-108">Opis</span><span class="sxs-lookup"><span data-stu-id="66b08-108">Description</span></span>

<span data-ttu-id="66b08-109">`dotnet test`Polecenie służy do wykonywania testów jednostkowych w danym rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="66b08-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="66b08-110">`dotnet test`Polecenie kompiluje rozwiązanie i uruchamia test aplikacji hosta dla każdego projektu testowego w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="66b08-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="66b08-111">Host testowy wykonuje testy w danym projekcie przy użyciu struktury testowej, na przykład: MSTest, NUnit lub xUnit, i raportuje sukces lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="66b08-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="66b08-112">Jeśli wszystkie testy zakończą się pomyślnie, moduł uruchamiający testy zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca 1.</span><span class="sxs-lookup"><span data-stu-id="66b08-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="66b08-113">W przypadku projektów wielowymiarowych testy są uruchamiane dla każdej platformy dostosowanej.</span><span class="sxs-lookup"><span data-stu-id="66b08-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="66b08-114">Hosta testowego i struktury testów jednostkowych są spakowane jako pakiety NuGet i są przywracane jako zwykłe zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="66b08-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="66b08-115">Projekty testowe określają Test Runner przy użyciu zwykłego `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="66b08-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="66b08-116">Gdzie `Microsoft.NET.Test.Sdk` jest hostem testowym, `xunit` jest to Platforma testowa.</span><span class="sxs-lookup"><span data-stu-id="66b08-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="66b08-117">I `xunit.runner.visualstudio` jest adapterem testowym, który pozwala platformie xUnit na współdziałanie z hostem testowym.</span><span class="sxs-lookup"><span data-stu-id="66b08-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="66b08-118">Przywracanie niejawne</span><span class="sxs-lookup"><span data-stu-id="66b08-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="66b08-119">Argumenty</span><span class="sxs-lookup"><span data-stu-id="66b08-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="66b08-120">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="66b08-120">Path to the test project.</span></span>
  - <span data-ttu-id="66b08-121">Ścieżka do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="66b08-121">Path to the solution.</span></span>
  - <span data-ttu-id="66b08-122">Ścieżka do katalogu, który zawiera projekt lub rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="66b08-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="66b08-123">Ścieżka do pliku projektu testowego. *dll* .</span><span class="sxs-lookup"><span data-stu-id="66b08-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="66b08-124">Jeśli nie zostanie określony, wyszukuje projekt lub rozwiązanie w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="66b08-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="66b08-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="66b08-125">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="66b08-126">Ścieżka do katalogu, który ma być przeszukiwany dla dodatkowych adapterów testowych.</span><span class="sxs-lookup"><span data-stu-id="66b08-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="66b08-127">Sprawdzane są tylko pliki *. dll* z sufiksem `.TestAdapter.dll` .</span><span class="sxs-lookup"><span data-stu-id="66b08-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="66b08-128">Jeśli nie zostanie określony, zostanie przeszukany katalog test *. dll* .</span><span class="sxs-lookup"><span data-stu-id="66b08-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="66b08-129">Uruchamia testy w trybie polecenia Blame.</span><span class="sxs-lookup"><span data-stu-id="66b08-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="66b08-130">Ta opcja jest przydatna do izolowania problematycznych testów, które powodują awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="66b08-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="66b08-131">Gdy zostanie wykryta awaria, tworzy plik sekwencji w programie `TestResults/<Guid>/<Guid>_Sequence.xml` , który przechwytuje kolejność testów, które zostały uruchomione przed awarią.</span><span class="sxs-lookup"><span data-stu-id="66b08-131">When a crash is detected, it creates an sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="66b08-132">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="66b08-132">Defines the build configuration.</span></span> <span data-ttu-id="66b08-133">Wartość domyślna to `Debug` , ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="66b08-133">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="66b08-134">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="66b08-134">Enables data collector for the test run.</span></span> <span data-ttu-id="66b08-135">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="66b08-135">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="66b08-136">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku oraz do plików obok niego.</span><span class="sxs-lookup"><span data-stu-id="66b08-136">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="66b08-137">Proces rejestrowania komunikatów określa, które pliki są tworzone, takie jak `*.host_<date>.txt` Dziennik hosta testowego i `*.datacollector_<date>.txt` Dziennik modułu zbierającego dane.</span><span class="sxs-lookup"><span data-stu-id="66b08-137">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="66b08-138">Wymusza użycie `dotnet` lub .NET Framework hosta testowego dla plików binarnych testu.</span><span class="sxs-lookup"><span data-stu-id="66b08-138">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="66b08-139">Ta opcja określa tylko typ hosta, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="66b08-139">This option only determines which type of host to use.</span></span> <span data-ttu-id="66b08-140">Rzeczywista wersja platformy, która ma zostać użyta, jest określana przez *runtimeconfig. JSON* projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="66b08-140">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="66b08-141">Gdy nie zostanie określony, [atrybut zestawu TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) jest używany do określenia typu hosta.</span><span class="sxs-lookup"><span data-stu-id="66b08-141">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="66b08-142">Gdy ten atrybut jest usuwany z *biblioteki DLL*, używany jest host .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66b08-142">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="66b08-143">Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="66b08-143">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="66b08-144">Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="66b08-144">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="66b08-145">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="66b08-145">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="66b08-146">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="66b08-146">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="66b08-147">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="66b08-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="66b08-148">Na przykład, aby ukończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="66b08-148">For example, to complete authentication.</span></span> <span data-ttu-id="66b08-149">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="66b08-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="66b08-150">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="66b08-150">Specifies a logger for test results.</span></span> <span data-ttu-id="66b08-151">W przeciwieństwie do programu MSBuild, test dotnet nie akceptuje skrótów: zamiast `-l "console;v=d"` używać `-l "console;verbosity=detailed"` .</span><span class="sxs-lookup"><span data-stu-id="66b08-151">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="66b08-152">Nie kompiluje projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="66b08-152">Doesn't build the test project before running it.</span></span> <span data-ttu-id="66b08-153">Również niejawnie ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="66b08-153">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="66b08-154">Uruchom testy bez wyświetlania transparentu Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="66b08-154">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="66b08-155">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="66b08-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="66b08-156">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="66b08-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="66b08-157">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="66b08-157">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="66b08-158">Jeśli nie zostanie określony, ścieżka domyślna to `./bin/<configuration>/<framework>/` .</span><span class="sxs-lookup"><span data-stu-id="66b08-158">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="66b08-159">W przypadku projektów z wieloma platformami docelowymi (za pośrednictwem `TargetFrameworks` Właściwości) należy również zdefiniować, `--framework` kiedy należy określić tę opcję.</span><span class="sxs-lookup"><span data-stu-id="66b08-159">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="66b08-160">`dotnet test`zawsze uruchamia testy z katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="66b08-160">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="66b08-161">Można użyć <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> do korzystania z zasobów testowych w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="66b08-161">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="66b08-162">Katalog, w którym zostaną umieszczone wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="66b08-162">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="66b08-163">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="66b08-163">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="66b08-164">Wartość domyślna znajduje się `TestResults` w katalogu, który zawiera plik projektu.</span><span class="sxs-lookup"><span data-stu-id="66b08-164">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="66b08-165">Docelowy środowisko uruchomieniowe do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="66b08-165">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="66b08-166">`.runsettings`Plik, który ma być używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="66b08-166">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="66b08-167">Należy zauważyć, że `TargetPlatform` element (x86 | x64) nie ma wpływu na `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="66b08-167">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="66b08-168">Aby uruchomić testy, które są przeznaczone dla architektury x86, Zainstaluj wersję x86 programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="66b08-168">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="66b08-169">Liczba bitów programu *dotnet. exe* , która znajduje się na ścieżce, będzie używana do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="66b08-169">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="66b08-170">Więcej informacji zawierają następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="66b08-170">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="66b08-171">Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.</span><span class="sxs-lookup"><span data-stu-id="66b08-171">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="66b08-172">Konfigurowanie przebiegu testowego</span><span class="sxs-lookup"><span data-stu-id="66b08-172">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="66b08-173">Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="66b08-173">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="66b08-174">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="66b08-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="66b08-175">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="66b08-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="66b08-176">Wartość domyślna to `minimal`.</span><span class="sxs-lookup"><span data-stu-id="66b08-176">The default is `minimal`.</span></span> <span data-ttu-id="66b08-177">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="66b08-177">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="66b08-178">**`RunSettings`** argumentu</span><span class="sxs-lookup"><span data-stu-id="66b08-178">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="66b08-179">Wbudowane `RunSettings` są przekazane jako ostatni argument w wierszu polecenia po "--" (należy pamiętać, że spacja jest późniejsza niż--).</span><span class="sxs-lookup"><span data-stu-id="66b08-179">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="66b08-180">Wbudowane `RunSettings` są określone jako `[name]=[value]` pary.</span><span class="sxs-lookup"><span data-stu-id="66b08-180">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="66b08-181">Spacja jest używana do rozdzielania wielu `[name]=[value]` par.</span><span class="sxs-lookup"><span data-stu-id="66b08-181">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="66b08-182">Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="66b08-182">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="66b08-183">Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów runsettings przy użyciu wiersza polecenia](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="66b08-183">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="66b08-184">Przykłady</span><span class="sxs-lookup"><span data-stu-id="66b08-184">Examples</span></span>

- <span data-ttu-id="66b08-185">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="66b08-185">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="66b08-186">Uruchom testy w `test1` projekcie:</span><span class="sxs-lookup"><span data-stu-id="66b08-186">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="66b08-187">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testu w formacie TRX:</span><span class="sxs-lookup"><span data-stu-id="66b08-187">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="66b08-188">Uruchom testy w projekcie w bieżącym katalogu i zaloguj się ze szczegółowymi informacjami o konsoli programu:</span><span class="sxs-lookup"><span data-stu-id="66b08-188">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - <span data-ttu-id="66b08-189">Uruchom testy w projekcie w bieżącym katalogu i Raportuj testy, które były w toku w przypadku awarii hosta testowego:</span><span class="sxs-lookup"><span data-stu-id="66b08-189">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="66b08-190">Szczegóły opcji filtrowania</span><span class="sxs-lookup"><span data-stu-id="66b08-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="66b08-191">`<Expression>`ma format `<property><operator><value>[|&<Expression>]` .</span><span class="sxs-lookup"><span data-stu-id="66b08-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="66b08-192">`<property>`jest atrybutem klasy `Test Case` .</span><span class="sxs-lookup"><span data-stu-id="66b08-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="66b08-193">Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="66b08-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="66b08-194">Platforma testowa</span><span class="sxs-lookup"><span data-stu-id="66b08-194">Test Framework</span></span> | <span data-ttu-id="66b08-195">Obsługiwane właściwości</span><span class="sxs-lookup"><span data-stu-id="66b08-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="66b08-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="66b08-196">MSTest</span></span>         | <ul><li><span data-ttu-id="66b08-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="66b08-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="66b08-198">Nazwa</span><span class="sxs-lookup"><span data-stu-id="66b08-198">Name</span></span></li><li><span data-ttu-id="66b08-199">ClassName</span><span class="sxs-lookup"><span data-stu-id="66b08-199">ClassName</span></span></li><li><span data-ttu-id="66b08-200">Priorytet</span><span class="sxs-lookup"><span data-stu-id="66b08-200">Priority</span></span></li><li><span data-ttu-id="66b08-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="66b08-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="66b08-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="66b08-202">xUnit</span></span>          | <ul><li><span data-ttu-id="66b08-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="66b08-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="66b08-204">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="66b08-204">DisplayName</span></span></li><li><span data-ttu-id="66b08-205">Cech</span><span class="sxs-lookup"><span data-stu-id="66b08-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="66b08-206">`<operator>`Opisuje relację między właściwością a wartością:</span><span class="sxs-lookup"><span data-stu-id="66b08-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="66b08-207">Operator</span><span class="sxs-lookup"><span data-stu-id="66b08-207">Operator</span></span> | <span data-ttu-id="66b08-208">Funkcja</span><span class="sxs-lookup"><span data-stu-id="66b08-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="66b08-209">Pełna zgodność</span><span class="sxs-lookup"><span data-stu-id="66b08-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="66b08-210">Niedokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="66b08-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="66b08-211">Contains</span><span class="sxs-lookup"><span data-stu-id="66b08-211">Contains</span></span>        |
| `!~`     | <span data-ttu-id="66b08-212">Nie zawiera</span><span class="sxs-lookup"><span data-stu-id="66b08-212">Not contains</span></span>    |

<span data-ttu-id="66b08-213">`<value>`jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="66b08-213">`<value>` is a string.</span></span> <span data-ttu-id="66b08-214">Wszystkie wyszukiwania są rozróżniane wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="66b08-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="66b08-215">Wyrażenie bez elementu `<operator>` jest automatycznie uznawane za `contains` Właściwość on `FullyQualifiedName` (na przykład `dotnet test --filter xyz` jest takie samo jak `dotnet test --filter FullyQualifiedName~xyz` ).</span><span class="sxs-lookup"><span data-stu-id="66b08-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="66b08-216">Wyrażenia mogą być dołączane za pomocą operatorów warunkowych:</span><span class="sxs-lookup"><span data-stu-id="66b08-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="66b08-217">Operator</span><span class="sxs-lookup"><span data-stu-id="66b08-217">Operator</span></span>            | <span data-ttu-id="66b08-218">Funkcja</span><span class="sxs-lookup"><span data-stu-id="66b08-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="66b08-219">LUB</span><span class="sxs-lookup"><span data-stu-id="66b08-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="66b08-220">AND</span><span class="sxs-lookup"><span data-stu-id="66b08-220">AND</span></span>      |

<span data-ttu-id="66b08-221">Wyrażenia można ująć w nawiasy, gdy są używane operatory warunkowe (na przykład `(Name~TestMethod1) | (Name~TestMethod2)` ).</span><span class="sxs-lookup"><span data-stu-id="66b08-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="66b08-222">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="66b08-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66b08-223">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66b08-223">See also</span></span>

- [<span data-ttu-id="66b08-224">Struktury i elementy docelowe</span><span class="sxs-lookup"><span data-stu-id="66b08-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="66b08-225">Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="66b08-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="66b08-226">Przekazywanie argumentów runsettings za poorednictwem wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="66b08-226">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
