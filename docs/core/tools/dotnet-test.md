---
title: polecenie testu dotnet
description: Polecenie Test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 04/29/2020
ms.openlocfilehash: b427954fe0026e6ac96d3bbce2b70b5c44e884e0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005378"
---
# <a name="dotnet-test"></a><span data-ttu-id="c682f-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="c682f-103">dotnet test</span></span>

<span data-ttu-id="c682f-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="c682f-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c682f-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c682f-105">Name</span></span>

<span data-ttu-id="c682f-106">`dotnet test`— Sterownik testowy .NET używany do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="c682f-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c682f-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="c682f-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="c682f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c682f-108">Description</span></span>

<span data-ttu-id="c682f-109">`dotnet test`Polecenie służy do wykonywania testów jednostkowych w danym rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="c682f-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="c682f-110">`dotnet test`Polecenie kompiluje rozwiązanie i uruchamia test aplikacji hosta dla każdego projektu testowego w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="c682f-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="c682f-111">Host testowy wykonuje testy w danym projekcie przy użyciu struktury testowej, na przykład: MSTest, NUnit lub xUnit, i raportuje sukces lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="c682f-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="c682f-112">Jeśli wszystkie testy zakończą się pomyślnie, moduł uruchamiający testy zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca 1.</span><span class="sxs-lookup"><span data-stu-id="c682f-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="c682f-113">W przypadku projektów wielowymiarowych testy są uruchamiane dla każdej platformy dostosowanej.</span><span class="sxs-lookup"><span data-stu-id="c682f-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="c682f-114">Hosta testowego i struktury testów jednostkowych są spakowane jako pakiety NuGet i są przywracane jako zwykłe zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="c682f-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="c682f-115">Projekty testowe określają Test Runner przy użyciu zwykłego `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="c682f-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="c682f-116">Gdzie `Microsoft.NET.Test.Sdk` jest hostem testowym, `xunit` jest to Platforma testowa.</span><span class="sxs-lookup"><span data-stu-id="c682f-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="c682f-117">I `xunit.runner.visualstudio` jest adapterem testowym, który pozwala platformie xUnit na współdziałanie z hostem testowym.</span><span class="sxs-lookup"><span data-stu-id="c682f-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="c682f-118">Przywracanie niejawne</span><span class="sxs-lookup"><span data-stu-id="c682f-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="c682f-119">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c682f-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="c682f-120">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="c682f-120">Path to the test project.</span></span>
  - <span data-ttu-id="c682f-121">Ścieżka do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c682f-121">Path to the solution.</span></span>
  - <span data-ttu-id="c682f-122">Ścieżka do katalogu, który zawiera projekt lub rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="c682f-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="c682f-123">Ścieżka do pliku projektu testowego. *dll* .</span><span class="sxs-lookup"><span data-stu-id="c682f-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="c682f-124">Jeśli nie zostanie określony, wyszukuje projekt lub rozwiązanie w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c682f-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="c682f-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="c682f-125">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="c682f-126">Ścieżka do katalogu, który ma być przeszukiwany dla dodatkowych adapterów testowych.</span><span class="sxs-lookup"><span data-stu-id="c682f-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="c682f-127">Sprawdzane są tylko pliki *. dll* z sufiksem `.TestAdapter.dll` .</span><span class="sxs-lookup"><span data-stu-id="c682f-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="c682f-128">Jeśli nie zostanie określony, zostanie przeszukany katalog test *. dll* .</span><span class="sxs-lookup"><span data-stu-id="c682f-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="c682f-129">Uruchamia testy w trybie polecenia Blame.</span><span class="sxs-lookup"><span data-stu-id="c682f-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="c682f-130">Ta opcja jest przydatna do izolowania problematycznych testów, które powodują awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="c682f-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="c682f-131">Gdy zostanie wykryta awaria, tworzy plik sekwencji w programie `TestResults/<Guid>/<Guid>_Sequence.xml` , który przechwytuje kolejność testów, które zostały uruchomione przed awarią.</span><span class="sxs-lookup"><span data-stu-id="c682f-131">When a crash is detected, it creates an sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="c682f-132">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c682f-132">Defines the build configuration.</span></span> <span data-ttu-id="c682f-133">Wartość domyślna to `Debug` , ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="c682f-133">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="c682f-134">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="c682f-134">Enables data collector for the test run.</span></span> <span data-ttu-id="c682f-135">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="c682f-135">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="c682f-136">Aby zbierać pokrycie kodu na dowolnej platformie obsługiwanej przez platformę .NET Core, zainstaluj [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) i Użyj `--collect:"XPlat Code Coverage"` opcji.</span><span class="sxs-lookup"><span data-stu-id="c682f-136">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="c682f-137">W systemie Windows można zbierać pokrycie kodu przy użyciu `--collect "Code Coverage"` opcji.</span><span class="sxs-lookup"><span data-stu-id="c682f-137">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="c682f-138">Ta opcja generuje plik *. coverage* , który można otworzyć w programie Visual Studio 2019 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="c682f-138">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="c682f-139">Aby uzyskać więcej informacji, zobacz [Korzystanie z pokrycia kodu](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) i [Dostosowywanie analizy pokrycia kodu](/visualstudio/test/customizing-code-coverage-analysis).</span><span class="sxs-lookup"><span data-stu-id="c682f-139">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="c682f-140">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku oraz do plików obok niego.</span><span class="sxs-lookup"><span data-stu-id="c682f-140">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="c682f-141">Proces rejestrowania komunikatów określa, które pliki są tworzone, takie jak `*.host_<date>.txt` Dziennik hosta testowego i `*.datacollector_<date>.txt` Dziennik modułu zbierającego dane.</span><span class="sxs-lookup"><span data-stu-id="c682f-141">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c682f-142">Wymusza użycie `dotnet` lub .NET Framework hosta testowego dla plików binarnych testu.</span><span class="sxs-lookup"><span data-stu-id="c682f-142">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="c682f-143">Ta opcja określa tylko typ hosta, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="c682f-143">This option only determines which type of host to use.</span></span> <span data-ttu-id="c682f-144">Rzeczywista wersja platformy, która ma zostać użyta, jest określana przez *runtimeconfig. JSON* projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="c682f-144">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="c682f-145">Gdy nie zostanie określony, [atrybut zestawu TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) jest używany do określenia typu hosta.</span><span class="sxs-lookup"><span data-stu-id="c682f-145">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="c682f-146">Gdy ten atrybut jest usuwany z *biblioteki DLL*, używany jest host .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c682f-146">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="c682f-147">Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c682f-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="c682f-148">Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="c682f-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="c682f-149">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="c682f-149">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="c682f-150">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="c682f-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="c682f-151">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="c682f-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="c682f-152">Na przykład, aby ukończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="c682f-152">For example, to complete authentication.</span></span> <span data-ttu-id="c682f-153">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c682f-153">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="c682f-154">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="c682f-154">Specifies a logger for test results.</span></span> <span data-ttu-id="c682f-155">W przeciwieństwie do programu MSBuild, test dotnet nie akceptuje skrótów: zamiast `-l "console;v=d"` używać `-l "console;verbosity=detailed"` .</span><span class="sxs-lookup"><span data-stu-id="c682f-155">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="c682f-156">Nie kompiluje projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="c682f-156">Doesn't build the test project before running it.</span></span> <span data-ttu-id="c682f-157">Również niejawnie ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="c682f-157">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="c682f-158">Uruchom testy bez wyświetlania transparentu Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="c682f-158">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="c682f-159">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c682f-159">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c682f-160">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="c682f-160">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c682f-161">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="c682f-161">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="c682f-162">Jeśli nie zostanie określony, ścieżka domyślna to `./bin/<configuration>/<framework>/` .</span><span class="sxs-lookup"><span data-stu-id="c682f-162">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="c682f-163">W przypadku projektów z wieloma platformami docelowymi (za pośrednictwem `TargetFrameworks` Właściwości) należy również zdefiniować, `--framework` kiedy należy określić tę opcję.</span><span class="sxs-lookup"><span data-stu-id="c682f-163">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="c682f-164">`dotnet test`zawsze uruchamia testy z katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="c682f-164">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="c682f-165">Można użyć <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> do korzystania z zasobów testowych w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="c682f-165">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="c682f-166">Katalog, w którym zostaną umieszczone wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="c682f-166">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="c682f-167">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="c682f-167">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="c682f-168">Wartość domyślna znajduje się `TestResults` w katalogu, który zawiera plik projektu.</span><span class="sxs-lookup"><span data-stu-id="c682f-168">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="c682f-169">Docelowy środowisko uruchomieniowe do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="c682f-169">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="c682f-170">`.runsettings`Plik, który ma być używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="c682f-170">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="c682f-171">Należy zauważyć, że `TargetPlatform` element (x86 | x64) nie ma wpływu na `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="c682f-171">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="c682f-172">Aby uruchomić testy, które są przeznaczone dla architektury x86, Zainstaluj wersję x86 programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c682f-172">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="c682f-173">Liczba bitów programu *dotnet. exe* , która znajduje się na ścieżce, będzie używana do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="c682f-173">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="c682f-174">Więcej informacji zawierają następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="c682f-174">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="c682f-175">Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.</span><span class="sxs-lookup"><span data-stu-id="c682f-175">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="c682f-176">Konfigurowanie przebiegu testowego</span><span class="sxs-lookup"><span data-stu-id="c682f-176">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="c682f-177">Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="c682f-177">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c682f-178">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="c682f-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c682f-179">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="c682f-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="c682f-180">Wartość domyślna to `minimal`.</span><span class="sxs-lookup"><span data-stu-id="c682f-180">The default is `minimal`.</span></span> <span data-ttu-id="c682f-181">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="c682f-181">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="c682f-182">**`RunSettings`** argumentu</span><span class="sxs-lookup"><span data-stu-id="c682f-182">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="c682f-183">Wbudowane `RunSettings` są przekazane jako ostatni argument w wierszu polecenia po "--" (należy pamiętać, że spacja jest późniejsza niż--).</span><span class="sxs-lookup"><span data-stu-id="c682f-183">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="c682f-184">Wbudowane `RunSettings` są określone jako `[name]=[value]` pary.</span><span class="sxs-lookup"><span data-stu-id="c682f-184">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="c682f-185">Spacja jest używana do rozdzielania wielu `[name]=[value]` par.</span><span class="sxs-lookup"><span data-stu-id="c682f-185">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="c682f-186">Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="c682f-186">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="c682f-187">Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów runsettings przy użyciu wiersza polecenia](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="c682f-187">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="c682f-188">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c682f-188">Examples</span></span>

- <span data-ttu-id="c682f-189">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="c682f-189">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="c682f-190">Uruchom testy w `test1` projekcie:</span><span class="sxs-lookup"><span data-stu-id="c682f-190">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="c682f-191">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testu w formacie TRX:</span><span class="sxs-lookup"><span data-stu-id="c682f-191">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="c682f-192">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik pokrycia kodu (po zainstalowaniu [Coverlet](https://github.com/tonerdo/coverlet/blob/master/README.md)):</span><span class="sxs-lookup"><span data-stu-id="c682f-192">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/tonerdo/coverlet/blob/master/README.md)):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="c682f-193">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik pokrycia kodu (tylko system Windows):</span><span class="sxs-lookup"><span data-stu-id="c682f-193">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="c682f-194">Uruchom testy w projekcie w bieżącym katalogu i zaloguj się ze szczegółowymi informacjami o konsoli programu:</span><span class="sxs-lookup"><span data-stu-id="c682f-194">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - <span data-ttu-id="c682f-195">Uruchom testy w projekcie w bieżącym katalogu i Raportuj testy, które były w toku w przypadku awarii hosta testowego:</span><span class="sxs-lookup"><span data-stu-id="c682f-195">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="c682f-196">Szczegóły opcji filtrowania</span><span class="sxs-lookup"><span data-stu-id="c682f-196">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="c682f-197">`<Expression>`ma format `<property><operator><value>[|&<Expression>]` .</span><span class="sxs-lookup"><span data-stu-id="c682f-197">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="c682f-198">`<property>`jest atrybutem klasy `Test Case` .</span><span class="sxs-lookup"><span data-stu-id="c682f-198">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="c682f-199">Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="c682f-199">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="c682f-200">Platforma testowa</span><span class="sxs-lookup"><span data-stu-id="c682f-200">Test Framework</span></span> | <span data-ttu-id="c682f-201">Obsługiwane właściwości</span><span class="sxs-lookup"><span data-stu-id="c682f-201">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c682f-202">MSTest</span><span class="sxs-lookup"><span data-stu-id="c682f-202">MSTest</span></span>         | <ul><li><span data-ttu-id="c682f-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="c682f-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="c682f-204">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c682f-204">Name</span></span></li><li><span data-ttu-id="c682f-205">ClassName</span><span class="sxs-lookup"><span data-stu-id="c682f-205">ClassName</span></span></li><li><span data-ttu-id="c682f-206">Priorytet</span><span class="sxs-lookup"><span data-stu-id="c682f-206">Priority</span></span></li><li><span data-ttu-id="c682f-207">TestCategory</span><span class="sxs-lookup"><span data-stu-id="c682f-207">TestCategory</span></span></li></ul> |
| <span data-ttu-id="c682f-208">xUnit</span><span class="sxs-lookup"><span data-stu-id="c682f-208">xUnit</span></span>          | <ul><li><span data-ttu-id="c682f-209">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="c682f-209">FullyQualifiedName</span></span></li><li><span data-ttu-id="c682f-210">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="c682f-210">DisplayName</span></span></li><li><span data-ttu-id="c682f-211">Cech</span><span class="sxs-lookup"><span data-stu-id="c682f-211">Traits</span></span></li></ul>                                   |
| <span data-ttu-id="c682f-212">NUnit</span><span class="sxs-lookup"><span data-stu-id="c682f-212">NUnit</span></span>          | <ul><li><span data-ttu-id="c682f-213">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="c682f-213">FullyQualifiedName</span></span></li><li><span data-ttu-id="c682f-214">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c682f-214">Name</span></span></li><li><span data-ttu-id="c682f-215">TestCategory</span><span class="sxs-lookup"><span data-stu-id="c682f-215">TestCategory</span></span></li><li><span data-ttu-id="c682f-216">Priorytet</span><span class="sxs-lookup"><span data-stu-id="c682f-216">Priority</span></span></li></ul>                                   |

<span data-ttu-id="c682f-217">`<operator>`Opisuje relację między właściwością a wartością:</span><span class="sxs-lookup"><span data-stu-id="c682f-217">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="c682f-218">Operator</span><span class="sxs-lookup"><span data-stu-id="c682f-218">Operator</span></span> | <span data-ttu-id="c682f-219">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c682f-219">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="c682f-220">Pełna zgodność</span><span class="sxs-lookup"><span data-stu-id="c682f-220">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="c682f-221">Niedokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="c682f-221">Not exact match</span></span> |
| `~`      | <span data-ttu-id="c682f-222">Contains</span><span class="sxs-lookup"><span data-stu-id="c682f-222">Contains</span></span>        |
| `!~`     | <span data-ttu-id="c682f-223">Nie zawiera</span><span class="sxs-lookup"><span data-stu-id="c682f-223">Not contains</span></span>    |

<span data-ttu-id="c682f-224">`<value>`jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="c682f-224">`<value>` is a string.</span></span> <span data-ttu-id="c682f-225">Wszystkie wyszukiwania są rozróżniane wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="c682f-225">All the lookups are case insensitive.</span></span>

<span data-ttu-id="c682f-226">Wyrażenie bez elementu `<operator>` jest automatycznie uznawane za `contains` Właściwość on `FullyQualifiedName` (na przykład `dotnet test --filter xyz` jest takie samo jak `dotnet test --filter FullyQualifiedName~xyz` ).</span><span class="sxs-lookup"><span data-stu-id="c682f-226">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="c682f-227">Wyrażenia mogą być dołączane za pomocą operatorów warunkowych:</span><span class="sxs-lookup"><span data-stu-id="c682f-227">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="c682f-228">Operator</span><span class="sxs-lookup"><span data-stu-id="c682f-228">Operator</span></span>            | <span data-ttu-id="c682f-229">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c682f-229">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="c682f-230">LUB</span><span class="sxs-lookup"><span data-stu-id="c682f-230">OR</span></span>       |
| `&`                 | <span data-ttu-id="c682f-231">AND</span><span class="sxs-lookup"><span data-stu-id="c682f-231">AND</span></span>      |

<span data-ttu-id="c682f-232">Wyrażenia można ująć w nawiasy, gdy są używane operatory warunkowe (na przykład `(Name~TestMethod1) | (Name~TestMethod2)` ).</span><span class="sxs-lookup"><span data-stu-id="c682f-232">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="c682f-233">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="c682f-233">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c682f-234">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c682f-234">See also</span></span>

- [<span data-ttu-id="c682f-235">Struktury i elementy docelowe</span><span class="sxs-lookup"><span data-stu-id="c682f-235">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="c682f-236">Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="c682f-236">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="c682f-237">Przekazywanie argumentów runsettings za poorednictwem wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c682f-237">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
