---
title: dotnet VSTest — polecenie
description: Polecenie dotnet VSTest kompiluje projekt i wszystkie jego zależności.
author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: da18fda6419cb9eaa1f488a3576161c3054b4426
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969815"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="fc0a7-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="fc0a7-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="fc0a7-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fc0a7-104">Name</span></span>

<span data-ttu-id="fc0a7-105">`dotnet-vstest`-Uruchamia testy z określonych plików.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fc0a7-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="fc0a7-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fc0a7-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fc0a7-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fc0a7-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fc0a7-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fc0a7-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fc0a7-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="fc0a7-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fc0a7-110">Description</span></span>

<span data-ttu-id="fc0a7-111">Polecenie uruchamia aplikację wiersza polecenia w celu uruchomienia zautomatyzowanych testów jednostkowych. `VSTest.Console` `dotnet-vstest`</span><span class="sxs-lookup"><span data-stu-id="fc0a7-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="fc0a7-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fc0a7-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="fc0a7-113">Uruchom testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="fc0a7-114">Oddziel wiele nazw zestawów testowych spacjami.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="fc0a7-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="fc0a7-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fc0a7-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fc0a7-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="fc0a7-117">Ustawienia do użycia podczas przeprowadzania testów.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="fc0a7-118">Uruchom testy z nazwami, które pasują do podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="fc0a7-119">Rozdziel wiele wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="fc0a7-120">Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="fc0a7-121">Architektura platformy docelowej używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="fc0a7-122">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="fc0a7-123">Docelowa wersja .NET Framework używana do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="fc0a7-124">Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="fc0a7-125">Inne obsługiwane wartości to `Framework40` `Framework45` `FrameworkCore10`,,, i. `FrameworkUap10`</span><span class="sxs-lookup"><span data-stu-id="fc0a7-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="fc0a7-126">Wykonaj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-126">Execute tests in parallel.</span></span> <span data-ttu-id="fc0a7-127">Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="fc0a7-128">Określ jawną liczbę rdzeni przez ustawienie właściwości MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="fc0a7-129">Uruchom testy zgodne z podanym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-129">Run tests that match the given expression.</span></span> <span data-ttu-id="fc0a7-130">`<Expression>`ma format `<property>Operator<value>[|&<Expression>]`, gdzie operator jest jednym z `=`, `!=`lub `~`.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="fc0a7-131">Operator `~` ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, `DisplayName`takich jak.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="fc0a7-132">Nawiasy `()` są używane do grupowania wyrażeń podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="fc0a7-133">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="fc0a7-134">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="fc0a7-135">Aby opublikować wyniki testów w Team Foundation Server, użyj `TfsPublisher` dostawcy rejestratora:</span><span class="sxs-lookup"><span data-stu-id="fc0a7-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="fc0a7-136">Aby zarejestrować wyniki do pliku wyniki testów programu Visual Studio (TRX), użyj `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="fc0a7-137">Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="fc0a7-138">Jeśli `LogFileName` nie zostanie podany, unikatowa nazwa pliku zostanie utworzona w celu przechowywania wyników testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="fc0a7-139">Wyświetla wszystkie odnalezione testy z danego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="fc0a7-140">Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="fc0a7-141">Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="fc0a7-142">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="fc0a7-143">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="fc0a7-144">Uruchamia testy w trybie polecenia Blame.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="fc0a7-145">Ta opcja jest pomocna w odizolowaniu problematycznych testów powodujących awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="fc0a7-146">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="fc0a7-147">Uruchamia testy w procesie izolowanym.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="fc0a7-148">Powoduje to, że proces *VSTest. Console. exe* jest mniej prawdopodobnie zatrzymany w przypadku błędu w testach, ale testy mogą działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="fc0a7-149">Odczytuje plik odpowiedzi w celu uzyskania dodatkowych opcji.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="fc0a7-150">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="fc0a7-151">Argumenty są określane jako pary nazwa-wartość formularza `<n>=<v>`, gdzie `<n>` jest nazwą argumentu i `<v>` jest wartością argumentu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="fc0a7-152">Użyj spacji, aby rozdzielić wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fc0a7-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fc0a7-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="fc0a7-154">Ustawienia do użycia podczas przeprowadzania testów.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="fc0a7-155">Uruchom testy z nazwami, które pasują do podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="fc0a7-156">Rozdziel wiele wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="fc0a7-157">Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="fc0a7-158">Architektura platformy docelowej używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="fc0a7-159">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="fc0a7-160">Docelowa wersja .NET Framework używana do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="fc0a7-161">Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="fc0a7-162">Inne obsługiwane wartości to `Framework40`, `Framework45`, i `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="fc0a7-163">Wykonaj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-163">Execute tests in parallel.</span></span> <span data-ttu-id="fc0a7-164">Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="fc0a7-165">Określ jawną liczbę rdzeni przez ustawienie właściwości MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="fc0a7-166">Uruchom testy zgodne z podanym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-166">Run tests that match the given expression.</span></span> <span data-ttu-id="fc0a7-167">`<Expression>`ma format `<property>Operator<value>[|&<Expression>]`, gdzie operator jest jednym z `=`, `!=`lub `~`.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="fc0a7-168">Operator `~` ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, `DisplayName`takich jak.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="fc0a7-169">Nawiasy `()` są używane do grupowania wyrażeń podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="fc0a7-170">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="fc0a7-171">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="fc0a7-172">Aby opublikować wyniki testów w Team Foundation Server, użyj `TfsPublisher` dostawcy rejestratora:</span><span class="sxs-lookup"><span data-stu-id="fc0a7-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="fc0a7-173">Aby zarejestrować wyniki do pliku wyniki testów programu Visual Studio (TRX), użyj `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="fc0a7-174">Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="fc0a7-175">Jeśli `LogFileName` nie zostanie podany, unikatowa nazwa pliku zostanie utworzona w celu przechowywania wyników testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="fc0a7-176">Wyświetla wszystkie odnalezione testy z danego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="fc0a7-177">Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="fc0a7-178">Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="fc0a7-179">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="fc0a7-180">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="fc0a7-181">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="fc0a7-182">Argumenty są określane jako pary nazwa-wartość formularza `<n>=<v>`, gdzie `<n>` jest nazwą argumentu i `<v>` jest wartością argumentu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="fc0a7-183">Użyj spacji, aby rozdzielić wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fc0a7-184">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fc0a7-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="fc0a7-185">Ustawienia do użycia podczas przeprowadzania testów.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="fc0a7-186">Uruchom testy z nazwami, które pasują do podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="fc0a7-187">Rozdziel wiele wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="fc0a7-188">Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="fc0a7-189">Architektura platformy docelowej używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="fc0a7-190">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="fc0a7-191">Docelowa wersja .NET Framework używana do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="fc0a7-192">Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="fc0a7-193">Inne obsługiwane wartości to `Framework40`, `Framework45`, i `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="fc0a7-194">Wykonaj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-194">Execute tests in parallel.</span></span> <span data-ttu-id="fc0a7-195">Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="fc0a7-196">Określ jawną liczbę rdzeni przez ustawienie właściwości MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="fc0a7-197">Uruchom testy zgodne z podanym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-197">Run tests that match the given expression.</span></span> <span data-ttu-id="fc0a7-198">`<Expression>`ma format `<property>Operator<value>[|&<Expression>]`, gdzie operator jest jednym z `=`, `!=`lub `~`.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="fc0a7-199">Operator `~` ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, `DisplayName`takich jak.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="fc0a7-200">Nawiasy `()` są używane do grupowania wyrażeń podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="fc0a7-201">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="fc0a7-202">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="fc0a7-203">Aby opublikować wyniki testów w Team Foundation Server, użyj `TfsPublisher` dostawcy rejestratora:</span><span class="sxs-lookup"><span data-stu-id="fc0a7-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="fc0a7-204">Aby zarejestrować wyniki do pliku wyniki testów programu Visual Studio (TRX), użyj `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="fc0a7-205">Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="fc0a7-206">Jeśli `LogFileName` nie zostanie podany, unikatowa nazwa pliku zostanie utworzona w celu przechowywania wyników testu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="fc0a7-207">Wyświetla wszystkie odnalezione testy z danego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="fc0a7-208">Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="fc0a7-209">Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="fc0a7-210">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="fc0a7-211">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="fc0a7-212">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="fc0a7-213">Argumenty są określane jako pary nazwa-wartość formularza `<n>=<v>`, gdzie `<n>` jest nazwą argumentu i `<v>` jest wartością argumentu.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="fc0a7-214">Użyj spacji, aby rozdzielić wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="fc0a7-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="fc0a7-215">Przykłady</span><span class="sxs-lookup"><span data-stu-id="fc0a7-215">Examples</span></span>

<span data-ttu-id="fc0a7-216">Uruchom testy w `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="fc0a7-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="fc0a7-217">Uruchom testy w `mytestproject.dll`, Eksportuj do folderu niestandardowego z nazwą niestandardową:</span><span class="sxs-lookup"><span data-stu-id="fc0a7-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="fc0a7-218">Uruchom testy w `mytestproject.dll` i `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="fc0a7-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="fc0a7-219">Uruchom `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="fc0a7-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="fc0a7-220">Uruchom `TestMethod1` i`TestMethod2` testy:</span><span class="sxs-lookup"><span data-stu-id="fc0a7-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
