---
title: dotnet VSTest — polecenie
description: Polecenie dotnet VSTest kompiluje projekt i wszystkie jego zależności.
ms.date: 05/30/2018
ms.openlocfilehash: c3838617ed539cf56f2840b826e9de58833820fd
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215310"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="70efe-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="70efe-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="70efe-104">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="70efe-104">Name</span></span>

<span data-ttu-id="70efe-105">`dotnet-vstest` — uruchamia testy z określonych plików.</span><span class="sxs-lookup"><span data-stu-id="70efe-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="70efe-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="70efe-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="70efe-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="70efe-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="70efe-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="70efe-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="70efe-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="70efe-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="70efe-110">Opis</span><span class="sxs-lookup"><span data-stu-id="70efe-110">Description</span></span>

<span data-ttu-id="70efe-111">Polecenie `dotnet-vstest` uruchamia `VSTest.Console` aplikację wiersza polecenia w celu uruchomienia zautomatyzowanych testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="70efe-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="70efe-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="70efe-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="70efe-113">Uruchom testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="70efe-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="70efe-114">Oddziel wiele nazw zestawów testowych spacjami.</span><span class="sxs-lookup"><span data-stu-id="70efe-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="70efe-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="70efe-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="70efe-116">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="70efe-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="70efe-117">Ustawienia do użycia podczas przeprowadzania testów.</span><span class="sxs-lookup"><span data-stu-id="70efe-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="70efe-118">Uruchom testy z nazwami, które pasują do podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="70efe-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="70efe-119">Rozdziel wiele wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="70efe-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="70efe-120">Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="70efe-121">Architektura platformy docelowej używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="70efe-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="70efe-122">Prawidłowe wartości to `x86`, `x64`i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="70efe-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="70efe-123">Docelowa wersja .NET Framework używana do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="70efe-124">Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="70efe-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="70efe-125">Inne obsługiwane wartości to `Framework40`, `Framework45`, `FrameworkCore10`i `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="70efe-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="70efe-126">Wykonaj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="70efe-126">Execute tests in parallel.</span></span> <span data-ttu-id="70efe-127">Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="70efe-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="70efe-128">Określ jawną liczbę rdzeni przez ustawienie właściwości MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="70efe-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="70efe-129">Uruchom testy zgodne z podanym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="70efe-129">Run tests that match the given expression.</span></span> <span data-ttu-id="70efe-130">`<Expression>` ma format `<property>Operator<value>[|&<Expression>]`, gdzie operator jest jednym z `=`, `!=`lub `~`.</span><span class="sxs-lookup"><span data-stu-id="70efe-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="70efe-131">`~` operatora ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="70efe-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="70efe-132">`()` nawiasów są używane do grupowania wyrażeń podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="70efe-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="70efe-133">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="70efe-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="70efe-134">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="70efe-135">Aby opublikować wyniki testów w Team Foundation Server, użyj dostawcy rejestratora `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="70efe-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="70efe-136">Aby zarejestrować wyniki do pliku Wyniki testów programu Visual Studio (TRX), użyj dostawcy rejestratora `trx`.</span><span class="sxs-lookup"><span data-stu-id="70efe-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="70efe-137">Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="70efe-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="70efe-138">Jeśli nie podano `LogFileName`, zostanie utworzona unikatowa nazwa pliku do przechowywania wyników testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="70efe-139">Wyświetla wszystkie odnalezione testy z danego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="70efe-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="70efe-140">Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="70efe-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="70efe-141">Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="70efe-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="70efe-142">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="70efe-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="70efe-143">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="70efe-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="70efe-144">Uruchamia testy w trybie polecenia Blame.</span><span class="sxs-lookup"><span data-stu-id="70efe-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="70efe-145">Ta opcja jest pomocna w odizolowaniu problematycznych testów powodujących awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="70efe-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="70efe-146">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="70efe-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="70efe-147">Uruchamia testy w procesie izolowanym.</span><span class="sxs-lookup"><span data-stu-id="70efe-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="70efe-148">Powoduje to, że proces *VSTest. Console. exe* jest mniej prawdopodobnie zatrzymany w przypadku błędu w testach, ale testy mogą działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="70efe-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="70efe-149">Odczytuje plik odpowiedzi w celu uzyskania dodatkowych opcji.</span><span class="sxs-lookup"><span data-stu-id="70efe-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="70efe-150">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="70efe-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="70efe-151">Argumenty są określane jako pary nazwa-wartość w formularzu `<n>=<v>`, gdzie `<n>` jest nazwą argumentu, a `<v>` to wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="70efe-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="70efe-152">Użyj spacji, aby rozdzielić wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="70efe-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="70efe-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="70efe-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="70efe-154">Ustawienia do użycia podczas przeprowadzania testów.</span><span class="sxs-lookup"><span data-stu-id="70efe-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="70efe-155">Uruchom testy z nazwami, które pasują do podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="70efe-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="70efe-156">Rozdziel wiele wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="70efe-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="70efe-157">Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="70efe-158">Architektura platformy docelowej używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="70efe-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="70efe-159">Prawidłowe wartości to `x86`, `x64`i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="70efe-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="70efe-160">Docelowa wersja .NET Framework używana do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="70efe-161">Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="70efe-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="70efe-162">Inne obsługiwane wartości to `Framework40`, `Framework45`i `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="70efe-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="70efe-163">Wykonaj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="70efe-163">Execute tests in parallel.</span></span> <span data-ttu-id="70efe-164">Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="70efe-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="70efe-165">Określ jawną liczbę rdzeni przez ustawienie właściwości MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="70efe-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="70efe-166">Uruchom testy zgodne z podanym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="70efe-166">Run tests that match the given expression.</span></span> <span data-ttu-id="70efe-167">`<Expression>` ma format `<property>Operator<value>[|&<Expression>]`, gdzie operator jest jednym z `=`, `!=`lub `~`.</span><span class="sxs-lookup"><span data-stu-id="70efe-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="70efe-168">`~` operatora ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="70efe-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="70efe-169">`()` nawiasów są używane do grupowania wyrażeń podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="70efe-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="70efe-170">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="70efe-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="70efe-171">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="70efe-172">Aby opublikować wyniki testów w Team Foundation Server, użyj dostawcy rejestratora `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="70efe-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="70efe-173">Aby zarejestrować wyniki do pliku Wyniki testów programu Visual Studio (TRX), użyj dostawcy rejestratora `trx`.</span><span class="sxs-lookup"><span data-stu-id="70efe-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="70efe-174">Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="70efe-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="70efe-175">Jeśli nie podano `LogFileName`, zostanie utworzona unikatowa nazwa pliku do przechowywania wyników testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="70efe-176">Wyświetla wszystkie odnalezione testy z danego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="70efe-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="70efe-177">Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="70efe-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="70efe-178">Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="70efe-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="70efe-179">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="70efe-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="70efe-180">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="70efe-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="70efe-181">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="70efe-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="70efe-182">Argumenty są określane jako pary nazwa-wartość w formularzu `<n>=<v>`, gdzie `<n>` jest nazwą argumentu, a `<v>` to wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="70efe-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="70efe-183">Użyj spacji, aby rozdzielić wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="70efe-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="70efe-184">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="70efe-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="70efe-185">Ustawienia do użycia podczas przeprowadzania testów.</span><span class="sxs-lookup"><span data-stu-id="70efe-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="70efe-186">Uruchom testy z nazwami, które pasują do podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="70efe-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="70efe-187">Rozdziel wiele wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="70efe-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="70efe-188">Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="70efe-189">Architektura platformy docelowej używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="70efe-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="70efe-190">Prawidłowe wartości to `x86`, `x64`i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="70efe-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="70efe-191">Docelowa wersja .NET Framework używana do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="70efe-192">Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="70efe-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="70efe-193">Inne obsługiwane wartości to `Framework40`, `Framework45`i `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="70efe-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="70efe-194">Wykonaj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="70efe-194">Execute tests in parallel.</span></span> <span data-ttu-id="70efe-195">Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="70efe-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="70efe-196">Określ jawną liczbę rdzeni przez ustawienie właściwości MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="70efe-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="70efe-197">Uruchom testy zgodne z podanym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="70efe-197">Run tests that match the given expression.</span></span> <span data-ttu-id="70efe-198">`<Expression>` ma format `<property>Operator<value>[|&<Expression>]`, gdzie operator jest jednym z `=`, `!=`lub `~`.</span><span class="sxs-lookup"><span data-stu-id="70efe-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="70efe-199">`~` operatora ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="70efe-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="70efe-200">`()` nawiasów są używane do grupowania wyrażeń podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="70efe-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="70efe-201">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="70efe-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="70efe-202">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="70efe-203">Aby opublikować wyniki testów w Team Foundation Server, użyj dostawcy rejestratora `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="70efe-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="70efe-204">Aby zarejestrować wyniki do pliku Wyniki testów programu Visual Studio (TRX), użyj dostawcy rejestratora `trx`.</span><span class="sxs-lookup"><span data-stu-id="70efe-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="70efe-205">Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="70efe-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="70efe-206">Jeśli nie podano `LogFileName`, zostanie utworzona unikatowa nazwa pliku do przechowywania wyników testu.</span><span class="sxs-lookup"><span data-stu-id="70efe-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="70efe-207">Wyświetla wszystkie odnalezione testy z danego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="70efe-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="70efe-208">Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="70efe-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="70efe-209">Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="70efe-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="70efe-210">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="70efe-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="70efe-211">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="70efe-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="70efe-212">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="70efe-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="70efe-213">Argumenty są określane jako pary nazwa-wartość w formularzu `<n>=<v>`, gdzie `<n>` jest nazwą argumentu, a `<v>` to wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="70efe-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="70efe-214">Użyj spacji, aby rozdzielić wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="70efe-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="70efe-215">Przykłady</span><span class="sxs-lookup"><span data-stu-id="70efe-215">Examples</span></span>

<span data-ttu-id="70efe-216">Uruchom testy w `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="70efe-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="70efe-217">Uruchom testy w `mytestproject.dll`, eksportując do folderu niestandardowego z nazwą niestandardową:</span><span class="sxs-lookup"><span data-stu-id="70efe-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="70efe-218">Uruchom testy w `mytestproject.dll` i `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="70efe-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="70efe-219">Uruchom testy `TestMethod1`:</span><span class="sxs-lookup"><span data-stu-id="70efe-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="70efe-220">Uruchom testy `TestMethod1` i `TestMethod2`:</span><span class="sxs-lookup"><span data-stu-id="70efe-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
