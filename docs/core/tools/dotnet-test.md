---
title: polecenie testu dotnet
description: Polecenie Test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 04/29/2020
ms.openlocfilehash: 9b1e190579902dda71547b01f31dd5adcc22fe9c
ms.sourcegitcommit: c8c3e1c63a00b7d27f76f5e50ee6469e6bdc8987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251195"
---
# <a name="dotnet-test"></a><span data-ttu-id="079a4-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="079a4-103">dotnet test</span></span>

<span data-ttu-id="079a4-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="079a4-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="079a4-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="079a4-105">Name</span></span>

<span data-ttu-id="079a4-106">`dotnet test`— Sterownik testowy .NET używany do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="079a4-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="079a4-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="079a4-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="079a4-108">Opis</span><span class="sxs-lookup"><span data-stu-id="079a4-108">Description</span></span>

<span data-ttu-id="079a4-109">`dotnet test`Polecenie służy do wykonywania testów jednostkowych w danym rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="079a4-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="079a4-110">`dotnet test`Polecenie kompiluje rozwiązanie i uruchamia test aplikacji hosta dla każdego projektu testowego w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="079a4-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="079a4-111">Host testowy wykonuje testy w danym projekcie przy użyciu struktury testowej, na przykład: MSTest, NUnit lub xUnit, i raportuje sukces lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="079a4-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="079a4-112">Jeśli wszystkie testy zakończą się pomyślnie, moduł uruchamiający testy zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca 1.</span><span class="sxs-lookup"><span data-stu-id="079a4-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="079a4-113">W przypadku projektów wielowymiarowych testy są uruchamiane dla każdej platformy dostosowanej.</span><span class="sxs-lookup"><span data-stu-id="079a4-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="079a4-114">Hosta testowego i struktury testów jednostkowych są spakowane jako pakiety NuGet i są przywracane jako zwykłe zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="079a4-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="079a4-115">Projekty testowe określają Test Runner przy użyciu zwykłego `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="079a4-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="079a4-116">Gdzie `Microsoft.NET.Test.Sdk` jest hostem testowym, `xunit` jest to Platforma testowa.</span><span class="sxs-lookup"><span data-stu-id="079a4-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="079a4-117">I `xunit.runner.visualstudio` jest adapterem testowym, który pozwala platformie xUnit na współdziałanie z hostem testowym.</span><span class="sxs-lookup"><span data-stu-id="079a4-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="079a4-118">Przywracanie niejawne</span><span class="sxs-lookup"><span data-stu-id="079a4-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="079a4-119">Argumenty</span><span class="sxs-lookup"><span data-stu-id="079a4-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="079a4-120">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="079a4-120">Path to the test project.</span></span>
  - <span data-ttu-id="079a4-121">Ścieżka do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="079a4-121">Path to the solution.</span></span>
  - <span data-ttu-id="079a4-122">Ścieżka do katalogu, który zawiera projekt lub rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="079a4-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="079a4-123">Ścieżka do pliku projektu testowego. *dll* .</span><span class="sxs-lookup"><span data-stu-id="079a4-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="079a4-124">Jeśli nie zostanie określony, wyszukuje projekt lub rozwiązanie w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="079a4-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="079a4-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="079a4-125">Options</span></span>

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  <span data-ttu-id="079a4-126">Ścieżka do katalogu, który ma być przeszukiwany dla dodatkowych adapterów testowych.</span><span class="sxs-lookup"><span data-stu-id="079a4-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="079a4-127">Sprawdzane są tylko pliki *. dll* z sufiksem `.TestAdapter.dll` .</span><span class="sxs-lookup"><span data-stu-id="079a4-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="079a4-128">Jeśli nie zostanie określony, zostanie przeszukany katalog test *. dll* .</span><span class="sxs-lookup"><span data-stu-id="079a4-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="079a4-129">Uruchamia testy w trybie polecenia Blame.</span><span class="sxs-lookup"><span data-stu-id="079a4-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="079a4-130">Ta opcja jest przydatna do izolowania problematycznych testów, które powodują awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="079a4-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="079a4-131">Gdy zostanie wykryta awaria, tworzy plik sekwencji w programie `TestResults/<Guid>/<Guid>_Sequence.xml` , który przechwytuje kolejność testów, które zostały uruchomione przed awarią.</span><span class="sxs-lookup"><span data-stu-id="079a4-131">When a crash is detected, it creates a sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- <span data-ttu-id="079a4-132">**`--blame-crash`**(Dostępne od wersji .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="079a4-132">**`--blame-crash`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="079a4-133">Uruchamia testy w trybie polecenia Blame i zbiera zrzut awaryjny, gdy host testowy zostanie nieoczekiwanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="079a4-133">Runs the tests in blame mode and collects a crash dump when the test host exits unexpectedly.</span></span> <span data-ttu-id="079a4-134">Ta opcja jest obsługiwana tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="079a4-134">This option is only supported on Windows.</span></span> <span data-ttu-id="079a4-135">Katalog zawierający *procdump.exe* i *procdump64.exe* musi znajdować się w zmiennej środowiskowej PATH lub PROCDUMP_PATH.</span><span class="sxs-lookup"><span data-stu-id="079a4-135">A directory that contains *procdump.exe* and *procdump64.exe* must be in the PATH or PROCDUMP_PATH environment variable.</span></span> <span data-ttu-id="079a4-136">[Pobierz narzędzia](https://docs.microsoft.com/sysinternals/downloads/procdump).</span><span class="sxs-lookup"><span data-stu-id="079a4-136">[Download the tools](https://docs.microsoft.com/sysinternals/downloads/procdump).</span></span> <span data-ttu-id="079a4-137">Oznacza `--blame` .</span><span class="sxs-lookup"><span data-stu-id="079a4-137">Implies `--blame`.</span></span>

- <span data-ttu-id="079a4-138">**`--blame-crash-dump-type <DUMP_TYPE>`**(Dostępne od wersji .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="079a4-138">**`--blame-crash-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="079a4-139">Typ zrzutu awaryjnego do zebrania.</span><span class="sxs-lookup"><span data-stu-id="079a4-139">The type of crash dump to be collected.</span></span> <span data-ttu-id="079a4-140">Oznacza `--blame-crash` .</span><span class="sxs-lookup"><span data-stu-id="079a4-140">Implies `--blame-crash`.</span></span>

- <span data-ttu-id="079a4-141">**`--blame-crash-collect-always`**(Dostępne od wersji .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="079a4-141">**`--blame-crash-collect-always`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="079a4-142">Zbiera dane zrzutu awaryjnego w oczekiwany sposób, jak również nieoczekiwane wyjście hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="079a4-142">Collects a crash dump on expected as well as unexpected test host exit.</span></span>

- <span data-ttu-id="079a4-143">**`--blame-hang`**(Dostępne od wersji .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="079a4-143">**`--blame-hang`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="079a4-144">Uruchom testy w trybie polecenia Blame i zbiera zrzut zawieszenia, gdy test przekroczy określony limit czasu.</span><span class="sxs-lookup"><span data-stu-id="079a4-144">Run the tests in blame mode and collects a hang dump when a test exceeds the given timeout.</span></span>

- <span data-ttu-id="079a4-145">**`--blame-hang-dump-type <DUMP_TYPE>`**(Dostępne od wersji .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="079a4-145">**`--blame-hang-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="079a4-146">Typ zrzutu awaryjnego do zebrania.</span><span class="sxs-lookup"><span data-stu-id="079a4-146">The type of crash dump to be collected.</span></span> <span data-ttu-id="079a4-147">Powinien być `full` , `mini` lub `none` .</span><span class="sxs-lookup"><span data-stu-id="079a4-147">It should be `full`, `mini`, or `none`.</span></span> <span data-ttu-id="079a4-148">Gdy `none` jest określony, Host testowy zostaje zakończony po upływie limitu czasu, ale nie jest zbierany żaden zrzut.</span><span class="sxs-lookup"><span data-stu-id="079a4-148">When `none` is specified, test host is terminated on timeout, but no dump is collected.</span></span> <span data-ttu-id="079a4-149">Oznacza `--blame-hang` .</span><span class="sxs-lookup"><span data-stu-id="079a4-149">Implies `--blame-hang`.</span></span>

- <span data-ttu-id="079a4-150">**`--blame-hang-timeout <TIMESPAN>`**(Dostępne od wersji .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="079a4-150">**`--blame-hang-timeout <TIMESPAN>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="079a4-151">Limit czasu dla testu, po którym zostanie wyzwolony zrzut zawieszenia i proces hosta testowego zostanie przerwany.</span><span class="sxs-lookup"><span data-stu-id="079a4-151">Per-test timeout, after which a hang dump is triggered and the test host process is terminated.</span></span> <span data-ttu-id="079a4-152">Wartość limitu czasu jest określona w jednym z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="079a4-152">The timeout value is specified in one of the following formats:</span></span>
  
  - <span data-ttu-id="079a4-153">1,5 h</span><span class="sxs-lookup"><span data-stu-id="079a4-153">1.5h</span></span>
  - <span data-ttu-id="079a4-154">90m</span><span class="sxs-lookup"><span data-stu-id="079a4-154">90m</span></span>
  - <span data-ttu-id="079a4-155">5400</span><span class="sxs-lookup"><span data-stu-id="079a4-155">5400s</span></span>
  - <span data-ttu-id="079a4-156">5400000ms</span><span class="sxs-lookup"><span data-stu-id="079a4-156">5400000ms</span></span>

  <span data-ttu-id="079a4-157">Gdy nie jest używana żadna jednostka (na przykład 5400000), przyjmuje się, że wartość jest w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="079a4-157">When no unit is used (for example, 5400000), the value is assumed to be in milliseconds.</span></span> <span data-ttu-id="079a4-158">W przypadku użycia razem z testami opartymi na danych, zachowanie limitu czasu zależy od używanej karty testowej.</span><span class="sxs-lookup"><span data-stu-id="079a4-158">When used together with data driven tests, the timeout behavior depends on the test adapter used.</span></span> <span data-ttu-id="079a4-159">Dla xUnit i NUnit limit czasu jest odnawiany po każdym przypadku testowym.</span><span class="sxs-lookup"><span data-stu-id="079a4-159">For xUnit and NUnit the timeout is renewed after every test case.</span></span> <span data-ttu-id="079a4-160">W przypadku MSTest limit czasu jest używany dla wszystkich).</span><span class="sxs-lookup"><span data-stu-id="079a4-160">For MSTest, the timeout is used for all testcases.</span></span> <span data-ttu-id="079a4-161">Ta opcja jest obsługiwana w systemie Windows z systemem netcoreapp 2.1 lub nowszym oraz w systemie Linux z netcoreapp 3.1 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="079a4-161">This option is supported on Windows with netcoreapp2.1 and later, and on Linux with netcoreapp3.1 and later.</span></span> <span data-ttu-id="079a4-162">macOS nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="079a4-162">macOS is not supported.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="079a4-163">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="079a4-163">Defines the build configuration.</span></span> <span data-ttu-id="079a4-164">Wartość domyślna to `Debug` , ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="079a4-164">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_NAME>`**

  <span data-ttu-id="079a4-165">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="079a4-165">Enables data collector for the test run.</span></span> <span data-ttu-id="079a4-166">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="079a4-166">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="079a4-167">Aby zbierać pokrycie kodu na dowolnej platformie obsługiwanej przez platformę .NET Core, zainstaluj [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) i Użyj `--collect:"XPlat Code Coverage"` opcji.</span><span class="sxs-lookup"><span data-stu-id="079a4-167">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="079a4-168">W systemie Windows można zbierać pokrycie kodu przy użyciu `--collect "Code Coverage"` opcji.</span><span class="sxs-lookup"><span data-stu-id="079a4-168">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="079a4-169">Ta opcja generuje plik *. coverage* , który można otworzyć w programie Visual Studio 2019 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="079a4-169">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="079a4-170">Aby uzyskać więcej informacji, zobacz [Korzystanie z pokrycia kodu](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) i [Dostosowywanie analizy pokrycia kodu](/visualstudio/test/customizing-code-coverage-analysis).</span><span class="sxs-lookup"><span data-stu-id="079a4-170">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <LOG_FILE>`**

  <span data-ttu-id="079a4-171">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku oraz do plików obok niego.</span><span class="sxs-lookup"><span data-stu-id="079a4-171">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="079a4-172">Proces rejestrowania komunikatów określa, które pliki są tworzone, takie jak `*.host_<date>.txt` Dziennik hosta testowego i `*.datacollector_<date>.txt` Dziennik modułu zbierającego dane.</span><span class="sxs-lookup"><span data-stu-id="079a4-172">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="079a4-173">Wymusza użycie `dotnet` lub .NET Framework hosta testowego dla plików binarnych testu.</span><span class="sxs-lookup"><span data-stu-id="079a4-173">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="079a4-174">Ta opcja określa tylko typ hosta, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="079a4-174">This option only determines which type of host to use.</span></span> <span data-ttu-id="079a4-175">Rzeczywista wersja platformy, która ma zostać użyta, jest określana na podstawie *runtimeconfig.jsw* projekcie testowym.</span><span class="sxs-lookup"><span data-stu-id="079a4-175">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="079a4-176">Gdy nie zostanie określony, [atrybut zestawu TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) jest używany do określenia typu hosta.</span><span class="sxs-lookup"><span data-stu-id="079a4-176">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="079a4-177">Gdy ten atrybut jest usuwany z *biblioteki DLL*, używany jest host .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="079a4-177">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="079a4-178">Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="079a4-178">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="079a4-179">Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="079a4-179">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="079a4-180">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="079a4-180">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="079a4-181">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="079a4-181">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="079a4-182">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="079a4-182">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="079a4-183">Na przykład, aby ukończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="079a4-183">For example, to complete authentication.</span></span> <span data-ttu-id="079a4-184">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="079a4-184">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER>`**

  <span data-ttu-id="079a4-185">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="079a4-185">Specifies a logger for test results.</span></span> <span data-ttu-id="079a4-186">W przeciwieństwie do programu MSBuild, test dotnet nie akceptuje skrótów: zamiast `-l "console;v=d"` używać `-l "console;verbosity=detailed"` .</span><span class="sxs-lookup"><span data-stu-id="079a4-186">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="079a4-187">Nie kompiluje projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="079a4-187">Doesn't build the test project before running it.</span></span> <span data-ttu-id="079a4-188">Również niejawnie ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="079a4-188">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="079a4-189">Uruchom testy bez wyświetlania transparentu Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="079a4-189">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="079a4-190">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="079a4-190">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="079a4-191">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="079a4-191">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="079a4-192">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="079a4-192">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="079a4-193">Jeśli nie zostanie określony, ścieżka domyślna to `./bin/<configuration>/<framework>/` .</span><span class="sxs-lookup"><span data-stu-id="079a4-193">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="079a4-194">W przypadku projektów z wieloma platformami docelowymi (za pośrednictwem `TargetFrameworks` Właściwości) należy również zdefiniować, `--framework` kiedy należy określić tę opcję.</span><span class="sxs-lookup"><span data-stu-id="079a4-194">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="079a4-195">`dotnet test`zawsze uruchamia testy z katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="079a4-195">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="079a4-196">Można użyć <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> do korzystania z zasobów testowych w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="079a4-196">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <RESULTS_DIR>`**

  <span data-ttu-id="079a4-197">Katalog, w którym zostaną umieszczone wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="079a4-197">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="079a4-198">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="079a4-198">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="079a4-199">Wartość domyślna znajduje się `TestResults` w katalogu, który zawiera plik projektu.</span><span class="sxs-lookup"><span data-stu-id="079a4-199">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="079a4-200">Docelowy środowisko uruchomieniowe do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="079a4-200">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="079a4-201">`.runsettings`Plik, który ma być używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="079a4-201">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="079a4-202">`TargetPlatform`Element (x86 | x64) nie ma wpływu na `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="079a4-202">The `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="079a4-203">Aby uruchomić testy, które są przeznaczone dla architektury x86, Zainstaluj wersję x86 programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="079a4-203">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="079a4-204">Liczba bitów *dotnet.exe* , która znajduje się na ścieżce, będzie używana do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="079a4-204">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="079a4-205">Więcej informacji można znaleźć w następujących zasobach:</span><span class="sxs-lookup"><span data-stu-id="079a4-205">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="079a4-206">Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.</span><span class="sxs-lookup"><span data-stu-id="079a4-206">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="079a4-207">Konfigurowanie przebiegu testowego</span><span class="sxs-lookup"><span data-stu-id="079a4-207">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="079a4-208">Wyświetl listę odnalezionych testów zamiast uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="079a4-208">List the discovered tests instead of running the tests.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="079a4-209">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="079a4-209">Sets the verbosity level of the command.</span></span> <span data-ttu-id="079a4-210">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="079a4-210">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="079a4-211">Wartość domyślna to `minimal`.</span><span class="sxs-lookup"><span data-stu-id="079a4-211">The default is `minimal`.</span></span> <span data-ttu-id="079a4-212">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="079a4-212">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="079a4-213">**`RunSettings`** argumentu</span><span class="sxs-lookup"><span data-stu-id="079a4-213">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="079a4-214">Wbudowane `RunSettings` są przekazane jako ostatni argument w wierszu polecenia po "--" (należy pamiętać, że spacja jest późniejsza niż--).</span><span class="sxs-lookup"><span data-stu-id="079a4-214">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="079a4-215">Wbudowane `RunSettings` są określone jako `[name]=[value]` pary.</span><span class="sxs-lookup"><span data-stu-id="079a4-215">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="079a4-216">Spacja jest używana do rozdzielania wielu `[name]=[value]` par.</span><span class="sxs-lookup"><span data-stu-id="079a4-216">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="079a4-217">Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="079a4-217">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="079a4-218">Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów runsettings przy użyciu wiersza polecenia](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="079a4-218">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="079a4-219">Przykłady</span><span class="sxs-lookup"><span data-stu-id="079a4-219">Examples</span></span>

- <span data-ttu-id="079a4-220">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="079a4-220">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="079a4-221">Uruchom testy w `test1` projekcie:</span><span class="sxs-lookup"><span data-stu-id="079a4-221">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="079a4-222">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testu w formacie TRX:</span><span class="sxs-lookup"><span data-stu-id="079a4-222">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="079a4-223">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik pokrycia kodu (po zainstalowaniu integracji modułów zbierających [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) ):</span><span class="sxs-lookup"><span data-stu-id="079a4-223">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) collectors integration):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="079a4-224">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik pokrycia kodu (tylko system Windows):</span><span class="sxs-lookup"><span data-stu-id="079a4-224">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="079a4-225">Uruchom testy w projekcie w bieżącym katalogu i zaloguj się ze szczegółowymi informacjami o konsoli programu:</span><span class="sxs-lookup"><span data-stu-id="079a4-225">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- <span data-ttu-id="079a4-226">Uruchom testy w projekcie w bieżącym katalogu i Raportuj testy, które były w toku w przypadku awarii hosta testowego:</span><span class="sxs-lookup"><span data-stu-id="079a4-226">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="079a4-227">Szczegóły opcji filtrowania</span><span class="sxs-lookup"><span data-stu-id="079a4-227">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="079a4-228">`<Expression>`ma format `<property><operator><value>[|&<Expression>]` .</span><span class="sxs-lookup"><span data-stu-id="079a4-228">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="079a4-229">`<property>`jest atrybutem klasy `Test Case` .</span><span class="sxs-lookup"><span data-stu-id="079a4-229">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="079a4-230">Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="079a4-230">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="079a4-231">Platforma testowa</span><span class="sxs-lookup"><span data-stu-id="079a4-231">Test Framework</span></span> | <span data-ttu-id="079a4-232">Obsługiwane właściwości</span><span class="sxs-lookup"><span data-stu-id="079a4-232">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="079a4-233">MSTest</span><span class="sxs-lookup"><span data-stu-id="079a4-233">MSTest</span></span>         | <ul><li><span data-ttu-id="079a4-234">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="079a4-234">FullyQualifiedName</span></span></li><li><span data-ttu-id="079a4-235">Nazwa</span><span class="sxs-lookup"><span data-stu-id="079a4-235">Name</span></span></li><li><span data-ttu-id="079a4-236">ClassName</span><span class="sxs-lookup"><span data-stu-id="079a4-236">ClassName</span></span></li><li><span data-ttu-id="079a4-237">Priorytet</span><span class="sxs-lookup"><span data-stu-id="079a4-237">Priority</span></span></li><li><span data-ttu-id="079a4-238">TestCategory</span><span class="sxs-lookup"><span data-stu-id="079a4-238">TestCategory</span></span></li></ul> |
| <span data-ttu-id="079a4-239">xUnit</span><span class="sxs-lookup"><span data-stu-id="079a4-239">xUnit</span></span>          | <ul><li><span data-ttu-id="079a4-240">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="079a4-240">FullyQualifiedName</span></span></li><li><span data-ttu-id="079a4-241">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="079a4-241">DisplayName</span></span></li><li><span data-ttu-id="079a4-242">Cech</span><span class="sxs-lookup"><span data-stu-id="079a4-242">Traits</span></span></li></ul>                                   |
| <span data-ttu-id="079a4-243">NUnit</span><span class="sxs-lookup"><span data-stu-id="079a4-243">NUnit</span></span>          | <ul><li><span data-ttu-id="079a4-244">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="079a4-244">FullyQualifiedName</span></span></li><li><span data-ttu-id="079a4-245">Nazwa</span><span class="sxs-lookup"><span data-stu-id="079a4-245">Name</span></span></li><li><span data-ttu-id="079a4-246">TestCategory</span><span class="sxs-lookup"><span data-stu-id="079a4-246">TestCategory</span></span></li><li><span data-ttu-id="079a4-247">Priorytet</span><span class="sxs-lookup"><span data-stu-id="079a4-247">Priority</span></span></li></ul>                                   |

<span data-ttu-id="079a4-248">`<operator>`Opisuje relację między właściwością a wartością:</span><span class="sxs-lookup"><span data-stu-id="079a4-248">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="079a4-249">Operator</span><span class="sxs-lookup"><span data-stu-id="079a4-249">Operator</span></span> | <span data-ttu-id="079a4-250">Funkcja</span><span class="sxs-lookup"><span data-stu-id="079a4-250">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="079a4-251">Pełna zgodność</span><span class="sxs-lookup"><span data-stu-id="079a4-251">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="079a4-252">Niedokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="079a4-252">Not exact match</span></span> |
| `~`      | <span data-ttu-id="079a4-253">Contains</span><span class="sxs-lookup"><span data-stu-id="079a4-253">Contains</span></span>        |
| `!~`     | <span data-ttu-id="079a4-254">Nie zawiera</span><span class="sxs-lookup"><span data-stu-id="079a4-254">Not contains</span></span>    |

<span data-ttu-id="079a4-255">`<value>`jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="079a4-255">`<value>` is a string.</span></span> <span data-ttu-id="079a4-256">Wszystkie wyszukiwania są rozróżniane wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="079a4-256">All the lookups are case insensitive.</span></span>

<span data-ttu-id="079a4-257">Wyrażenie bez elementu `<operator>` jest automatycznie uznawane za `contains` Właściwość on `FullyQualifiedName` (na przykład `dotnet test --filter xyz` jest takie samo jak `dotnet test --filter FullyQualifiedName~xyz` ).</span><span class="sxs-lookup"><span data-stu-id="079a4-257">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="079a4-258">Wyrażenia mogą być dołączane za pomocą operatorów warunkowych:</span><span class="sxs-lookup"><span data-stu-id="079a4-258">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="079a4-259">Operator</span><span class="sxs-lookup"><span data-stu-id="079a4-259">Operator</span></span>            | <span data-ttu-id="079a4-260">Funkcja</span><span class="sxs-lookup"><span data-stu-id="079a4-260">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="079a4-261">LUB</span><span class="sxs-lookup"><span data-stu-id="079a4-261">OR</span></span>       |
| `&`                 | <span data-ttu-id="079a4-262">AND</span><span class="sxs-lookup"><span data-stu-id="079a4-262">AND</span></span>      |

<span data-ttu-id="079a4-263">Wyrażenia można ująć w nawiasy, gdy są używane operatory warunkowe (na przykład `(Name~TestMethod1) | (Name~TestMethod2)` ).</span><span class="sxs-lookup"><span data-stu-id="079a4-263">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="079a4-264">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="079a4-264">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="079a4-265">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="079a4-265">See also</span></span>

- [<span data-ttu-id="079a4-266">Struktury i elementy docelowe</span><span class="sxs-lookup"><span data-stu-id="079a4-266">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="079a4-267">Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="079a4-267">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="079a4-268">Przekazywanie argumentów runsettings za poorednictwem wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="079a4-268">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
