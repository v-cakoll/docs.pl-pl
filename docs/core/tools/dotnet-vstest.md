---
title: dotnet vstest, polecenie
description: Polecenie dotnet vstest tworzy projekt i wszystkie jego zależności.
ms.date: 02/27/2020
ms.openlocfilehash: e8fa94cf12ca2fe5fb99c6e3c1dcdb52185798c0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463283"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="2dd79-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="2dd79-103">dotnet vstest</span></span>

<span data-ttu-id="2dd79-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="2dd79-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2dd79-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="2dd79-105">Name</span></span>

<span data-ttu-id="2dd79-106">`dotnet-vstest`- Uruchamia testy z określonych plików.</span><span class="sxs-lookup"><span data-stu-id="2dd79-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2dd79-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="2dd79-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag <PATH_TO_LOG_FILE>]
    [--Framework <FRAMEWORK>] [--InIsolation] [-lt|--ListTests <FILE_NAME>]
    [--logger <LOGGER_URI/FRIENDLY_NAME>] [--Parallel]
    [--ParentProcessId <PROCESS_ID>] [--Platform] <PLATFORM_TYPE>
    [--Port <PORT>] [--ResultsDirectory<PATH>] [--Settings <SETTINGS_FILE>]
    [--TestAdapterPath <PATH>] [--TestCaseFilter <EXPRESSION>]
    [--Tests <TEST_NAMES>] [[--] <args>...]]

dotnet vstest -?|--Help
```

## <a name="description"></a><span data-ttu-id="2dd79-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2dd79-108">Description</span></span>

<span data-ttu-id="2dd79-109">Polecenie `dotnet-vstest` uruchamia `VSTest.Console` aplikację wiersza polecenia w celu uruchomienia automatycznych testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="2dd79-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="2dd79-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2dd79-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="2dd79-111">Uruchom testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="2dd79-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="2dd79-112">Oddziel wiele nazw zestawów testowych spacjami.</span><span class="sxs-lookup"><span data-stu-id="2dd79-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="2dd79-113">Obsługiwane są symbole wieloznaczne.</span><span class="sxs-lookup"><span data-stu-id="2dd79-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="2dd79-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="2dd79-114">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="2dd79-115">Uruchamia testy w trybie winy.</span><span class="sxs-lookup"><span data-stu-id="2dd79-115">Runs the tests in blame mode.</span></span> <span data-ttu-id="2dd79-116">Ta opcja jest przydatna w izolowaniu problematycznych testów powodujących awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="2dd79-116">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="2dd79-117">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml,* który przechwytuje kolejność wykonywania testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="2dd79-117">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <PATH_TO_LOG_FILE>`**

  <span data-ttu-id="2dd79-118">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="2dd79-118">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="2dd79-119">Dzienniki są zapisywane w podanym pliku.</span><span class="sxs-lookup"><span data-stu-id="2dd79-119">Logs are written to the provided file.</span></span>

- **`--Framework <FRAMEWORK>`**

  <span data-ttu-id="2dd79-120">Docelowa wersja programu .NET Framework używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="2dd79-120">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="2dd79-121">Przykładami prawidłowych `.NETFramework,Version=v4.6` wartości `.NETCoreApp,Version=v1.0`są lub .</span><span class="sxs-lookup"><span data-stu-id="2dd79-121">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="2dd79-122">Inne obsługiwane wartości `Framework40` `Framework45`to `FrameworkCore10`, `FrameworkUap10`, i .</span><span class="sxs-lookup"><span data-stu-id="2dd79-122">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="2dd79-123">Uruchamia testy w procesie izolowanym.</span><span class="sxs-lookup"><span data-stu-id="2dd79-123">Runs the tests in an isolated process.</span></span> <span data-ttu-id="2dd79-124">To sprawia, że proces *vstest.console.exe* jest mniej prawdopodobne, aby zatrzymać się na błąd w testach, ale testy mogą działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="2dd79-124">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <FILE_NAME>`**

  <span data-ttu-id="2dd79-125">Wyświetla listę wszystkich wykrytych testów z danego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="2dd79-125">Lists all discovered tests from the given test container.</span></span>

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="2dd79-126">Określ rejestrator dla wyników testów.</span><span class="sxs-lookup"><span data-stu-id="2dd79-126">Specify a logger for test results.</span></span>

  - <span data-ttu-id="2dd79-127">Aby opublikować wyniki testów na `TfsPublisher` serwerze Team Foundation Server, użyj dostawcy rejestratora:</span><span class="sxs-lookup"><span data-stu-id="2dd79-127">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="2dd79-128">Aby rejestrować wyniki w pliku wyników testów programu `trx` Visual Studio (TRX), należy użyć dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="2dd79-128">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="2dd79-129">Ten przełącznik tworzy plik w katalogu wyników testów o podanej nazwie pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="2dd79-129">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="2dd79-130">Jeśli `LogFileName` nie podano, zostanie utworzona unikatowa nazwa pliku w celu przechowywania wyników testów.</span><span class="sxs-lookup"><span data-stu-id="2dd79-130">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="2dd79-131">Uruchom testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="2dd79-131">Run tests in parallel.</span></span> <span data-ttu-id="2dd79-132">Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="2dd79-132">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="2dd79-133">Określ jawną liczbę rdzeni, `MaxCpuCount` ustawiając `RunConfiguration` właściwość pod węzłem w pliku *runsettings.*</span><span class="sxs-lookup"><span data-stu-id="2dd79-133">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <PROCESS_ID>`**

  <span data-ttu-id="2dd79-134">Identyfikator procesu nadrzędnego odpowiedzialnego za uruchomienie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="2dd79-134">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <PLATFORM_TYPE>`**

  <span data-ttu-id="2dd79-135">Architektura platformy docelowej używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="2dd79-135">Target platform architecture used for test execution.</span></span> <span data-ttu-id="2dd79-136">Prawidłowe `x86`wartości `x64`to `ARM`, i .</span><span class="sxs-lookup"><span data-stu-id="2dd79-136">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <PORT>`**

  <span data-ttu-id="2dd79-137">Określa port połączenia gniazda i odbieranie komunikatów o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="2dd79-137">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PATH>`**

  <span data-ttu-id="2dd79-138">Katalog wyników testów zostanie utworzony w określonej ścieżce, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="2dd79-138">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <SETTINGS_FILE>`**

  <span data-ttu-id="2dd79-139">Ustawienia, które mają być używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="2dd79-139">Settings to use when running tests.</span></span>

- **`--TestAdapterPath <PATH>`**

  <span data-ttu-id="2dd79-140">Użyj niestandardowych kart testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="2dd79-140">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <EXPRESSION>`**

  <span data-ttu-id="2dd79-141">Uruchom testy, które pasują do danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2dd79-141">Run tests that match the given expression.</span></span> <span data-ttu-id="2dd79-142">`<EXPRESSION>`ma format, `<property>Operator<value>[|&<EXPRESSION>]`w którym Operator `=` `!=`jest `~`jednym z , lub .</span><span class="sxs-lookup"><span data-stu-id="2dd79-142">`<EXPRESSION>` is of the format `<property>Operator<value>[|&<EXPRESSION>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="2dd79-143">Operator `~` ma "zawiera" semantykę i ma `DisplayName`zastosowanie do właściwości ciągu, takich jak .</span><span class="sxs-lookup"><span data-stu-id="2dd79-143">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="2dd79-144">Nawiasy `()` są używane do grupowanie podwyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2dd79-144">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="2dd79-145">Aby uzyskać więcej informacji, zobacz [Filtr Skrzynia testowa](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="2dd79-145">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <TEST_NAMES>`**

  <span data-ttu-id="2dd79-146">Uruchom testy z nazwami, które odpowiadają podanym wartościom.</span><span class="sxs-lookup"><span data-stu-id="2dd79-146">Run tests with names that match the provided values.</span></span> <span data-ttu-id="2dd79-147">Oddziel wiele wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="2dd79-147">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="2dd79-148">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="2dd79-148">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="2dd79-149">Odczytuje plik odpowiedzi, aby uzyskać więcej opcji.</span><span class="sxs-lookup"><span data-stu-id="2dd79-149">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="2dd79-150">Określa dodatkowe argumenty, które mają być przerzucene do karty.</span><span class="sxs-lookup"><span data-stu-id="2dd79-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="2dd79-151">Argumenty są określane jako pary nazwa-wartość `<n>=<v>` `<n>` formularza , gdzie `<v>` jest nazwą argumentu i jest wartością argumentu.</span><span class="sxs-lookup"><span data-stu-id="2dd79-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="2dd79-152">Użyj spacji, aby oddzielić wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="2dd79-152">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="2dd79-153">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2dd79-153">Examples</span></span>

<span data-ttu-id="2dd79-154">Uruchom testy w *mytestproject.dll*:</span><span class="sxs-lookup"><span data-stu-id="2dd79-154">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="2dd79-155">Uruchom testy w *pliku mytestproject.dll*, eksportując do folderu niestandardowego o niestandardowej nazwie:</span><span class="sxs-lookup"><span data-stu-id="2dd79-155">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="2dd79-156">Uruchom testy w *mytestproject.dll* i *myothertestproject.exe*:</span><span class="sxs-lookup"><span data-stu-id="2dd79-156">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="2dd79-157">Uruchom `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="2dd79-157">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="2dd79-158">`TestMethod1` Uruchamianie `TestMethod2` i testy:</span><span class="sxs-lookup"><span data-stu-id="2dd79-158">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="2dd79-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2dd79-159">See also</span></span>

- [<span data-ttu-id="2dd79-160">Opcje wiersza poleceń narzędzia VSTest.Console.exe</span><span class="sxs-lookup"><span data-stu-id="2dd79-160">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
