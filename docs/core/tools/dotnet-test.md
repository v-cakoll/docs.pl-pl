---
title: polecenie testu dotnet
description: Polecenie Test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 05/29/2018
ms.openlocfilehash: 890d1fc3fd9d47f2bdcd63f2a25248c3edd705e4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626050"
---
# <a name="dotnet-test"></a><span data-ttu-id="ba8ff-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="ba8ff-103">dotnet test</span></span>

<span data-ttu-id="ba8ff-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="ba8ff-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ba8ff-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="ba8ff-105">Name</span></span>

<span data-ttu-id="ba8ff-106">`dotnet test` — sterownik testowy .NET używany do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ba8ff-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="ba8ff-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame]
    [-c|--configuration] [--collect] [-d|--diag] [-f|--framework]
    [--filter] [-l|--logger] [--no-build] [--no-restore]
    [-o|--output] [-r|--results-directory] [-s|--settings]
    [-t|--list-tests] [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="ba8ff-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ba8ff-108">Description</span></span>

<span data-ttu-id="ba8ff-109">Polecenie `dotnet test` służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="ba8ff-110">`dotnet test` polecenie uruchamia aplikację konsolową Test Runner określoną dla projektu.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="ba8ff-111">Moduł uruchamiający testy wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raportuje sukces lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="ba8ff-112">Jeśli wszystkie testy zakończą się pomyślnie, moduł uruchamiający testy zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca 1.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="ba8ff-113">Moduł uruchamiający testy i Biblioteka testów jednostkowych są spakowane jako pakiety NuGet i są przywracane jako zwykłe zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="ba8ff-114">Projekty testowe określają Test Runner przy użyciu zwykłego elementu `<PackageReference>`, jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="ba8ff-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="ba8ff-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ba8ff-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="ba8ff-116">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-116">Path to the test project.</span></span> <span data-ttu-id="ba8ff-117">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="ba8ff-118">Opcje</span><span class="sxs-lookup"><span data-stu-id="ba8ff-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="ba8ff-119">Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="ba8ff-120">Uruchamia testy w trybie polecenia Blame.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="ba8ff-121">Ta opcja jest przydatna do izolowania problematycznych testów, które powodują awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="ba8ff-122">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration {Debug|Release}`**

  <span data-ttu-id="ba8ff-123">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-123">Defines the build configuration.</span></span> <span data-ttu-id="ba8ff-124">Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="ba8ff-125">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-125">Enables data collector for the test run.</span></span> <span data-ttu-id="ba8ff-126">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="ba8ff-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="ba8ff-127">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ba8ff-128">Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ba8ff-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="ba8ff-129">Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ba8ff-130">Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="ba8ff-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ba8ff-131">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ba8ff-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="ba8ff-132">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-132">Prints out a short help for the command.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="ba8ff-133">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-133">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="ba8ff-134">Nie kompiluje projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-134">Doesn't build the test project before running it.</span></span> <span data-ttu-id="ba8ff-135">Również niejawnie ustawia flagę-`--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-135">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ba8ff-136">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-136">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="ba8ff-137">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-137">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="ba8ff-138">Katalog, w którym zostaną umieszczone wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-138">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="ba8ff-139">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-139">If the specified directory doesn't exist, it's created.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="ba8ff-140">Plik `.runsettings` używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-140">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="ba8ff-141">Skonfiguruj testy jednostkowe za pomocą pliku `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-141">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="ba8ff-142">Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-142">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="ba8ff-143">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ba8ff-144">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="ba8ff-145">`RunSettings` argumenty</span><span class="sxs-lookup"><span data-stu-id="ba8ff-145">`RunSettings` arguments</span></span>

  <span data-ttu-id="ba8ff-146">Argumenty są przekazane jako konfiguracje `RunSettings` dla testu.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-146">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="ba8ff-147">Argumenty są określane jako pary `[name]=[value]` po "--" (należy zwrócić uwagę na spację po--).</span><span class="sxs-lookup"><span data-stu-id="ba8ff-147">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="ba8ff-148">Spacja jest używana do rozdzielania wielu par `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-148">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="ba8ff-149">Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="ba8ff-149">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="ba8ff-150">Aby uzyskać więcej informacji, zobacz [VSTest. Console. exe: przekazywanie runsettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="ba8ff-150">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="ba8ff-151">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ba8ff-151">Examples</span></span>

- <span data-ttu-id="ba8ff-152">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ba8ff-152">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="ba8ff-153">Uruchom testy w `test1` projekcie:</span><span class="sxs-lookup"><span data-stu-id="ba8ff-153">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="ba8ff-154">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testu w formacie TRX:</span><span class="sxs-lookup"><span data-stu-id="ba8ff-154">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="ba8ff-155">Szczegóły opcji filtrowania</span><span class="sxs-lookup"><span data-stu-id="ba8ff-155">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ba8ff-156">`<Expression>` ma `<property><operator><value>[|&<Expression>]`format.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-156">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="ba8ff-157">`<property>` jest atrybutem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-157">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="ba8ff-158">Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="ba8ff-158">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="ba8ff-159">Struktury testowej</span><span class="sxs-lookup"><span data-stu-id="ba8ff-159">Test Framework</span></span> | <span data-ttu-id="ba8ff-160">Obsługiwane właściwości</span><span class="sxs-lookup"><span data-stu-id="ba8ff-160">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ba8ff-161">MSTest</span><span class="sxs-lookup"><span data-stu-id="ba8ff-161">MSTest</span></span>         | <ul><li><span data-ttu-id="ba8ff-162">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ba8ff-162">FullyQualifiedName</span></span></li><li><span data-ttu-id="ba8ff-163">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="ba8ff-163">Name</span></span></li><li><span data-ttu-id="ba8ff-164">Nazwą</span><span class="sxs-lookup"><span data-stu-id="ba8ff-164">ClassName</span></span></li><li><span data-ttu-id="ba8ff-165">Priorytet</span><span class="sxs-lookup"><span data-stu-id="ba8ff-165">Priority</span></span></li><li><span data-ttu-id="ba8ff-166">TestCategory</span><span class="sxs-lookup"><span data-stu-id="ba8ff-166">TestCategory</span></span></li></ul> |
| <span data-ttu-id="ba8ff-167">xUnit</span><span class="sxs-lookup"><span data-stu-id="ba8ff-167">xUnit</span></span>          | <ul><li><span data-ttu-id="ba8ff-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ba8ff-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="ba8ff-169">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ba8ff-169">DisplayName</span></span></li><li><span data-ttu-id="ba8ff-170">Cech</span><span class="sxs-lookup"><span data-stu-id="ba8ff-170">Traits</span></span></li></ul>                                   |

<span data-ttu-id="ba8ff-171">`<operator>` opisuje relację między właściwością a wartością:</span><span class="sxs-lookup"><span data-stu-id="ba8ff-171">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="ba8ff-172">Operator</span><span class="sxs-lookup"><span data-stu-id="ba8ff-172">Operator</span></span> | <span data-ttu-id="ba8ff-173">Funkcja</span><span class="sxs-lookup"><span data-stu-id="ba8ff-173">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="ba8ff-174">Dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="ba8ff-174">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="ba8ff-175">Niedokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="ba8ff-175">Not exact match</span></span> |
| `~`      | <span data-ttu-id="ba8ff-176">Contains</span><span class="sxs-lookup"><span data-stu-id="ba8ff-176">Contains</span></span>        |
| `!~`     | <span data-ttu-id="ba8ff-177">Nie zawiera</span><span class="sxs-lookup"><span data-stu-id="ba8ff-177">Not contains</span></span>    |

<span data-ttu-id="ba8ff-178">`<value>` jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-178">`<value>` is a string.</span></span> <span data-ttu-id="ba8ff-179">Wszystkie wyszukiwania są rozróżniane wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="ba8ff-179">All the lookups are case insensitive.</span></span>

<span data-ttu-id="ba8ff-180">Wyrażenie bez `<operator>` jest automatycznie uznawane za `contains` właściwości `FullyQualifiedName` (na przykład `dotnet test --filter xyz` jest taka sama jak `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="ba8ff-180">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="ba8ff-181">Wyrażenia mogą być dołączane za pomocą operatorów warunkowych:</span><span class="sxs-lookup"><span data-stu-id="ba8ff-181">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="ba8ff-182">Operator</span><span class="sxs-lookup"><span data-stu-id="ba8ff-182">Operator</span></span>            | <span data-ttu-id="ba8ff-183">Funkcja</span><span class="sxs-lookup"><span data-stu-id="ba8ff-183">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="ba8ff-184">LUB</span><span class="sxs-lookup"><span data-stu-id="ba8ff-184">OR</span></span>       |
| `&`                 | <span data-ttu-id="ba8ff-185">AND</span><span class="sxs-lookup"><span data-stu-id="ba8ff-185">AND</span></span>      |

<span data-ttu-id="ba8ff-186">Wyrażenia można ująć w nawiasy, gdy są używane operatory warunkowe (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="ba8ff-186">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="ba8ff-187">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ba8ff-187">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba8ff-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba8ff-188">See also</span></span>

- [<span data-ttu-id="ba8ff-189">Struktury i elementy docelowe</span><span class="sxs-lookup"><span data-stu-id="ba8ff-189">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="ba8ff-190">Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="ba8ff-190">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
