---
title: polecenie testu dotnet
description: Polecenie Test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 04/29/2020
ms.openlocfilehash: a8218b6596601069b89a60ad018adf89a1f47cf6
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624894"
---
# <a name="dotnet-test"></a><span data-ttu-id="f6f56-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="f6f56-103">dotnet test</span></span>

<span data-ttu-id="f6f56-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="f6f56-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f6f56-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f6f56-105">Name</span></span>

<span data-ttu-id="f6f56-106">`dotnet test`— Sterownik testowy .NET używany do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="f6f56-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f6f56-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="f6f56-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
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

## <a name="description"></a><span data-ttu-id="f6f56-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f6f56-108">Description</span></span>

<span data-ttu-id="f6f56-109">`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="f6f56-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="f6f56-110">`dotnet test` Polecenie uruchamia aplikację konsolową Test Runner określoną dla projektu.</span><span class="sxs-lookup"><span data-stu-id="f6f56-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="f6f56-111">Moduł uruchamiający testy wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raportuje sukces lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="f6f56-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="f6f56-112">Jeśli wszystkie testy zakończą się pomyślnie, moduł uruchamiający testy zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca 1.</span><span class="sxs-lookup"><span data-stu-id="f6f56-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="f6f56-113">W przypadku projektów wielowymiarowych testy są uruchamiane dla każdej platformy dostosowanej.</span><span class="sxs-lookup"><span data-stu-id="f6f56-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="f6f56-114">Moduł uruchamiający testy i Biblioteka testów jednostkowych są spakowane jako pakiety NuGet i są przywracane jako zwykłe zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="f6f56-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="f6f56-115">Projekty testowe określają Test Runner przy użyciu zwykłego `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="f6f56-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="f6f56-116">Przywracanie niejawne</span><span class="sxs-lookup"><span data-stu-id="f6f56-116">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="f6f56-117">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f6f56-117">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="f6f56-118">Ścieżka do projektu testowego lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f6f56-118">Path to the test project or solution.</span></span> <span data-ttu-id="f6f56-119">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="f6f56-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="f6f56-120">Opcje</span><span class="sxs-lookup"><span data-stu-id="f6f56-120">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="f6f56-121">Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="f6f56-121">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="f6f56-122">Uruchamia testy w trybie polecenia Blame.</span><span class="sxs-lookup"><span data-stu-id="f6f56-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="f6f56-123">Ta opcja jest przydatna do izolowania problematycznych testów, które powodują awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="f6f56-123">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="f6f56-124">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="f6f56-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="f6f56-125">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f6f56-125">Defines the build configuration.</span></span> <span data-ttu-id="f6f56-126">Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="f6f56-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="f6f56-127">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="f6f56-127">Enables data collector for the test run.</span></span> <span data-ttu-id="f6f56-128">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="f6f56-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="f6f56-129">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="f6f56-129">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f6f56-130">Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f6f56-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="f6f56-131">Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f6f56-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f6f56-132">Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="f6f56-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f6f56-133">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f6f56-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="f6f56-134">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="f6f56-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="f6f56-135">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="f6f56-135">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="f6f56-136">Na przykład, aby ukończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="f6f56-136">For example, to complete authentication.</span></span> <span data-ttu-id="f6f56-137">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f6f56-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="f6f56-138">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="f6f56-138">Specifies a logger for test results.</span></span> <span data-ttu-id="f6f56-139">W przeciwieństwie do programu MSBuild, test dotnet nie akceptuje skrótów: `-l "console;v=d"` zamiast `-l "console;verbosity=detailed"`używać.</span><span class="sxs-lookup"><span data-stu-id="f6f56-139">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="f6f56-140">Nie kompiluje projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="f6f56-140">Doesn't build the test project before running it.</span></span> <span data-ttu-id="f6f56-141">Również niejawnie ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="f6f56-141">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="f6f56-142">Uruchom testy bez wyświetlania transparentu Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="f6f56-142">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="f6f56-143">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f6f56-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f6f56-144">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="f6f56-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f6f56-145">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="f6f56-145">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="f6f56-146">Jeśli nie zostanie określony, ścieżka domyślna to `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="f6f56-146">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="f6f56-147">W przypadku projektów z wieloma platformami docelowymi ( `TargetFrameworks` za pośrednictwem właściwości) należy również zdefiniować `--framework` , kiedy należy określić tę opcję.</span><span class="sxs-lookup"><span data-stu-id="f6f56-147">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="f6f56-148">`dotnet test`Zawsze uruchamiaj testy z katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="f6f56-148">`dotnet test` always run tests from the output directory.</span></span> <span data-ttu-id="f6f56-149">Można użyć <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> do korzystania z zasobów testowych w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="f6f56-149">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="f6f56-150">Katalog, w którym zostaną umieszczone wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="f6f56-150">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="f6f56-151">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="f6f56-151">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="f6f56-152">Wartość domyślna znajduje `TestResults` się w katalogu, który zawiera plik projektu.</span><span class="sxs-lookup"><span data-stu-id="f6f56-152">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f6f56-153">Docelowy środowisko uruchomieniowe do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="f6f56-153">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="f6f56-154">Plik `.runsettings` , który ma być używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="f6f56-154">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="f6f56-155">Należy zauważyć, `TargetPlatform` że element (x86 | x64) nie ma wpływu `dotnet test`na.</span><span class="sxs-lookup"><span data-stu-id="f6f56-155">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="f6f56-156">Aby uruchomić testy, które są przeznaczone dla architektury x86, Zainstaluj wersję x86 programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f6f56-156">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="f6f56-157">Liczba bitów programu *dotnet. exe* , która znajduje się na ścieżce, będzie używana do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="f6f56-157">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="f6f56-158">Aby uzyskać więcej informacji, zobacz następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="f6f56-158">for more information, see the following resources:</span></span>

  - [<span data-ttu-id="f6f56-159">Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.</span><span class="sxs-lookup"><span data-stu-id="f6f56-159">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="f6f56-160">Konfigurowanie przebiegu testowego</span><span class="sxs-lookup"><span data-stu-id="f6f56-160">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="f6f56-161">Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="f6f56-161">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f6f56-162">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="f6f56-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f6f56-163">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f6f56-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f6f56-164">Wartość domyślna to `minimal`.</span><span class="sxs-lookup"><span data-stu-id="f6f56-164">The default is `minimal`.</span></span> <span data-ttu-id="f6f56-165">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="f6f56-165">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="f6f56-166">**`RunSettings`** argumentu</span><span class="sxs-lookup"><span data-stu-id="f6f56-166">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="f6f56-167">Argumenty są przekazane jako `RunSettings` konfiguracje dla testu.</span><span class="sxs-lookup"><span data-stu-id="f6f56-167">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="f6f56-168">Argumenty są określane jako `[name]=[value]` pary po "--" (należy zwrócić uwagę na spację po--).</span><span class="sxs-lookup"><span data-stu-id="f6f56-168">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="f6f56-169">Spacja jest używana do rozdzielania wielu `[name]=[value]` par.</span><span class="sxs-lookup"><span data-stu-id="f6f56-169">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="f6f56-170">Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="f6f56-170">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="f6f56-171">Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów runsettings przy użyciu wiersza polecenia](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="f6f56-171">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="f6f56-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f6f56-172">Examples</span></span>

- <span data-ttu-id="f6f56-173">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="f6f56-173">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="f6f56-174">Uruchom testy w `test1` projekcie:</span><span class="sxs-lookup"><span data-stu-id="f6f56-174">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="f6f56-175">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testu w formacie TRX:</span><span class="sxs-lookup"><span data-stu-id="f6f56-175">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="f6f56-176">Uruchom testy w projekcie w bieżącym katalogu i zaloguj się ze szczegółowymi informacjami o konsoli programu:</span><span class="sxs-lookup"><span data-stu-id="f6f56-176">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="f6f56-177">Szczegóły opcji filtrowania</span><span class="sxs-lookup"><span data-stu-id="f6f56-177">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f6f56-178">`<Expression>`ma format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="f6f56-178">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="f6f56-179">`<property>`jest atrybutem klasy `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="f6f56-179">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="f6f56-180">Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="f6f56-180">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="f6f56-181">Platforma testowa</span><span class="sxs-lookup"><span data-stu-id="f6f56-181">Test Framework</span></span> | <span data-ttu-id="f6f56-182">Obsługiwane właściwości</span><span class="sxs-lookup"><span data-stu-id="f6f56-182">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f6f56-183">MSTest</span><span class="sxs-lookup"><span data-stu-id="f6f56-183">MSTest</span></span>         | <ul><li><span data-ttu-id="f6f56-184">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f6f56-184">FullyQualifiedName</span></span></li><li><span data-ttu-id="f6f56-185">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f6f56-185">Name</span></span></li><li><span data-ttu-id="f6f56-186">ClassName</span><span class="sxs-lookup"><span data-stu-id="f6f56-186">ClassName</span></span></li><li><span data-ttu-id="f6f56-187">Priorytet</span><span class="sxs-lookup"><span data-stu-id="f6f56-187">Priority</span></span></li><li><span data-ttu-id="f6f56-188">TestCategory</span><span class="sxs-lookup"><span data-stu-id="f6f56-188">TestCategory</span></span></li></ul> |
| <span data-ttu-id="f6f56-189">xUnit</span><span class="sxs-lookup"><span data-stu-id="f6f56-189">xUnit</span></span>          | <ul><li><span data-ttu-id="f6f56-190">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f6f56-190">FullyQualifiedName</span></span></li><li><span data-ttu-id="f6f56-191">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="f6f56-191">DisplayName</span></span></li><li><span data-ttu-id="f6f56-192">Cech</span><span class="sxs-lookup"><span data-stu-id="f6f56-192">Traits</span></span></li></ul>                                   |

<span data-ttu-id="f6f56-193">`<operator>` Opisuje relację między właściwością a wartością:</span><span class="sxs-lookup"><span data-stu-id="f6f56-193">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="f6f56-194">Operator</span><span class="sxs-lookup"><span data-stu-id="f6f56-194">Operator</span></span> | <span data-ttu-id="f6f56-195">Funkcja</span><span class="sxs-lookup"><span data-stu-id="f6f56-195">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="f6f56-196">Pełna zgodność</span><span class="sxs-lookup"><span data-stu-id="f6f56-196">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="f6f56-197">Niedokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="f6f56-197">Not exact match</span></span> |
| `~`      | <span data-ttu-id="f6f56-198">Contains</span><span class="sxs-lookup"><span data-stu-id="f6f56-198">Contains</span></span>        |
| `!~`     | <span data-ttu-id="f6f56-199">Nie zawiera</span><span class="sxs-lookup"><span data-stu-id="f6f56-199">Not contains</span></span>    |

<span data-ttu-id="f6f56-200">`<value>`jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="f6f56-200">`<value>` is a string.</span></span> <span data-ttu-id="f6f56-201">Wszystkie wyszukiwania są rozróżniane wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="f6f56-201">All the lookups are case insensitive.</span></span>

<span data-ttu-id="f6f56-202">Wyrażenie bez `<operator>` elementu jest automatycznie uznawane za Właściwość `contains` on `FullyQualifiedName` (na przykład `dotnet test --filter xyz` jest takie samo jak `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="f6f56-202">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="f6f56-203">Wyrażenia mogą być dołączane za pomocą operatorów warunkowych:</span><span class="sxs-lookup"><span data-stu-id="f6f56-203">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="f6f56-204">Operator</span><span class="sxs-lookup"><span data-stu-id="f6f56-204">Operator</span></span>            | <span data-ttu-id="f6f56-205">Funkcja</span><span class="sxs-lookup"><span data-stu-id="f6f56-205">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="f6f56-206">LUB</span><span class="sxs-lookup"><span data-stu-id="f6f56-206">OR</span></span>       |
| `&`                 | <span data-ttu-id="f6f56-207">AND</span><span class="sxs-lookup"><span data-stu-id="f6f56-207">AND</span></span>      |

<span data-ttu-id="f6f56-208">Wyrażenia można ująć w nawiasy, gdy są używane operatory warunkowe (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="f6f56-208">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="f6f56-209">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f6f56-209">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6f56-210">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6f56-210">See also</span></span>

- [<span data-ttu-id="f6f56-211">Struktury i elementy docelowe</span><span class="sxs-lookup"><span data-stu-id="f6f56-211">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="f6f56-212">Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="f6f56-212">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="f6f56-213">Przekazywanie argumentów runsettings za poorednictwem wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="f6f56-213">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
