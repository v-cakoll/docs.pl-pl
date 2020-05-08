---
title: dotnet VSTest — polecenie
description: Polecenie dotnet VSTest kompiluje projekt i wszystkie jego zależności.
ms.date: 02/27/2020
ms.openlocfilehash: f7db58f4aab59354b8c69ce0371324c23482dafe
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975397"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="10096-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="10096-103">dotnet vstest</span></span>

<span data-ttu-id="10096-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="10096-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10096-105">`dotnet vstest` Polecenie jest zastępowane przez `dotnet test`, co może być teraz używane do uruchamiania zestawów.</span><span class="sxs-lookup"><span data-stu-id="10096-105">The `dotnet vstest` command is superseded by `dotnet test`, which can now be used to run assemblies.</span></span> <span data-ttu-id="10096-106">Zobacz [`dotnet test`](dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="10096-106">See [`dotnet test`](dotnet-test.md).</span></span>

## <a name="name"></a><span data-ttu-id="10096-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="10096-107">Name</span></span>

<span data-ttu-id="10096-108">`dotnet-vstest`-Uruchamia testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="10096-108">`dotnet-vstest` - Runs tests from the specified assemblies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="10096-109">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="10096-109">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="10096-110">Opis</span><span class="sxs-lookup"><span data-stu-id="10096-110">Description</span></span>

<span data-ttu-id="10096-111">`dotnet-vstest` Polecenie uruchamia aplikację wiersza `VSTest.Console` polecenia w celu uruchomienia zautomatyzowanych testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="10096-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="10096-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="10096-112">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="10096-113">Uruchom testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="10096-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="10096-114">Oddziel wiele nazw zestawów testowych spacjami.</span><span class="sxs-lookup"><span data-stu-id="10096-114">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="10096-115">Symbole wieloznaczne są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="10096-115">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="10096-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="10096-116">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="10096-117">Uruchamia testy w trybie polecenia Blame.</span><span class="sxs-lookup"><span data-stu-id="10096-117">Runs the tests in blame mode.</span></span> <span data-ttu-id="10096-118">Ta opcja jest pomocna w odizolowaniu problematycznych testów powodujących awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="10096-118">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="10096-119">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="10096-119">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <PATH_TO_LOG_FILE>`**

  <span data-ttu-id="10096-120">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="10096-120">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="10096-121">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="10096-121">Logs are written to the provided file.</span></span>

- **`--Framework <FRAMEWORK>`**

  <span data-ttu-id="10096-122">Docelowa wersja .NET Framework używana do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="10096-122">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="10096-123">Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="10096-123">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="10096-124">Inne obsługiwane wartości to `Framework40`, `Framework45`, `FrameworkCore10`, i `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="10096-124">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="10096-125">Uruchamia testy w procesie izolowanym.</span><span class="sxs-lookup"><span data-stu-id="10096-125">Runs the tests in an isolated process.</span></span> <span data-ttu-id="10096-126">Powoduje to, że proces *VSTest. Console. exe* jest mniej prawdopodobnie zatrzymany w przypadku błędu w testach, ale testy mogą działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="10096-126">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <FILE_NAME>`**

  <span data-ttu-id="10096-127">Wyświetla wszystkie odnalezione testy z danego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="10096-127">Lists all discovered tests from the given test container.</span></span>

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="10096-128">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="10096-128">Specify a logger for test results.</span></span>

  - <span data-ttu-id="10096-129">Aby opublikować wyniki testów w Team Foundation Server, użyj dostawcy `TfsPublisher` rejestratora:</span><span class="sxs-lookup"><span data-stu-id="10096-129">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="10096-130">Aby zarejestrować wyniki do pliku Wyniki testów programu Visual Studio (TRX), użyj dostawcy `trx` rejestratora.</span><span class="sxs-lookup"><span data-stu-id="10096-130">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="10096-131">Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="10096-131">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="10096-132">Jeśli `LogFileName` nie zostanie podany, unikatowa nazwa pliku zostanie utworzona w celu przechowywania wyników testu.</span><span class="sxs-lookup"><span data-stu-id="10096-132">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="10096-133">Uruchom testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="10096-133">Run tests in parallel.</span></span> <span data-ttu-id="10096-134">Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="10096-134">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="10096-135">Określ jawną liczbę rdzeni przez ustawienie `MaxCpuCount` właściwości w `RunConfiguration` węźle w pliku *runsettings* .</span><span class="sxs-lookup"><span data-stu-id="10096-135">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <PROCESS_ID>`**

  <span data-ttu-id="10096-136">Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="10096-136">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <PLATFORM_TYPE>`**

  <span data-ttu-id="10096-137">Architektura platformy docelowej używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="10096-137">Target platform architecture used for test execution.</span></span> <span data-ttu-id="10096-138">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="10096-138">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <PORT>`**

  <span data-ttu-id="10096-139">Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="10096-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PATH>`**

  <span data-ttu-id="10096-140">Katalog wyników testu zostanie utworzony w określonej ścieżce, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="10096-140">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <SETTINGS_FILE>`**

  <span data-ttu-id="10096-141">Ustawienia do użycia podczas przeprowadzania testów.</span><span class="sxs-lookup"><span data-stu-id="10096-141">Settings to use when running tests.</span></span>

- **`--TestAdapterPath <PATH>`**

  <span data-ttu-id="10096-142">Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="10096-142">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <EXPRESSION>`**

  <span data-ttu-id="10096-143">Uruchom testy zgodne z podanym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="10096-143">Run tests that match the given expression.</span></span> <span data-ttu-id="10096-144">`<EXPRESSION>`ma format `<property>Operator<value>[|&<EXPRESSION>]`, gdzie operator jest jednym z `=`, `!=`lub. `~`</span><span class="sxs-lookup"><span data-stu-id="10096-144">`<EXPRESSION>` is of the format `<property>Operator<value>[|&<EXPRESSION>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="10096-145">Operator `~` ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, `DisplayName`takich jak.</span><span class="sxs-lookup"><span data-stu-id="10096-145">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="10096-146">`()` Nawiasy służą do grupowania podwyrażeń.</span><span class="sxs-lookup"><span data-stu-id="10096-146">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="10096-147">Aby uzyskać więcej informacji, zobacz [przypadku testowego Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="10096-147">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <TEST_NAMES>`**

  <span data-ttu-id="10096-148">Uruchom testy z nazwami, które pasują do podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="10096-148">Run tests with names that match the provided values.</span></span> <span data-ttu-id="10096-149">Użyj przecinków, aby oddzielić wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="10096-149">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="10096-150">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="10096-150">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="10096-151">Odczytuje plik odpowiedzi w celu uzyskania dodatkowych opcji.</span><span class="sxs-lookup"><span data-stu-id="10096-151">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="10096-152">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="10096-152">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="10096-153">Argumenty są określane jako pary nazwa-wartość formularza `<n>=<v>`, gdzie `<n>` jest nazwą argumentu i `<v>` jest wartością argumentu.</span><span class="sxs-lookup"><span data-stu-id="10096-153">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="10096-154">Użyj spacji, aby rozdzielić wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="10096-154">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="10096-155">Przykłady</span><span class="sxs-lookup"><span data-stu-id="10096-155">Examples</span></span>

<span data-ttu-id="10096-156">Uruchom testy w *mytestproject. dll*:</span><span class="sxs-lookup"><span data-stu-id="10096-156">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="10096-157">Uruchom testy w *mytestproject. dll*, eksportując do folderu niestandardowego z nazwą niestandardową:</span><span class="sxs-lookup"><span data-stu-id="10096-157">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="10096-158">Uruchom testy w *mytestproject. dll* i *myothertestproject. exe*:</span><span class="sxs-lookup"><span data-stu-id="10096-158">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="10096-159">Uruchom `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="10096-159">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="10096-160">Uruchom `TestMethod1` i `TestMethod2` testy:</span><span class="sxs-lookup"><span data-stu-id="10096-160">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="10096-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10096-161">See also</span></span>

- [<span data-ttu-id="10096-162">Opcje wiersza poleceń narzędzia VSTest.Console.exe</span><span class="sxs-lookup"><span data-stu-id="10096-162">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
