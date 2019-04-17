---
title: polecenie vstest DotNet
description: Polecenia dotnet vstest kompiluje projekt i wszystkie jego zależności.
author: guardrex
ms.date: 05/30/2018
ms.openlocfilehash: dcf17a59fea1f58757f39721c5dd5947ed30df0f
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613463"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="434eb-103">DotNet vstest</span><span class="sxs-lookup"><span data-stu-id="434eb-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="434eb-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="434eb-104">Name</span></span>

<span data-ttu-id="434eb-105">`dotnet-vstest` -Uruchamia testy z określonych plików.</span><span class="sxs-lookup"><span data-stu-id="434eb-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="434eb-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="434eb-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="434eb-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="434eb-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="434eb-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="434eb-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="434eb-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="434eb-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="434eb-110">Opis</span><span class="sxs-lookup"><span data-stu-id="434eb-110">Description</span></span>

<span data-ttu-id="434eb-111">`dotnet-vstest` Polecenia `VSTest.Console` aplikacji wiersza polecenia, aby uruchomić automatyczne testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="434eb-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="434eb-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="434eb-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="434eb-113">Uruchom testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="434eb-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="434eb-114">Oddziel wiele nazw zestawów testowych spacjami.</span><span class="sxs-lookup"><span data-stu-id="434eb-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="434eb-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="434eb-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="434eb-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="434eb-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="434eb-117">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="434eb-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="434eb-118">Uruchom testy o nazwach odpowiadających podanej wartości.</span><span class="sxs-lookup"><span data-stu-id="434eb-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="434eb-119">Wiele wartości należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="434eb-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="434eb-120">Używa niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieją) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="434eb-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="434eb-121">Docelowa platforma architektury używanej do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="434eb-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="434eb-122">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="434eb-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="434eb-123">Wersja docelowa.NET Framework używanego do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="434eb-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="434eb-124">Prawidłowe wartości należą do nich `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="434eb-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="434eb-125">Inne obsługiwane wartości to `Framework40`, `Framework45`, `FrameworkCore10`, i `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="434eb-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="434eb-126">Wykonuj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="434eb-126">Execute tests in parallel.</span></span> <span data-ttu-id="434eb-127">Domyślnie wszystkie dostępne rdzenie maszyny są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="434eb-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="434eb-128">Określ jawną liczby rdzeni, ustawiając właściwość MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="434eb-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="434eb-129">Uruchom testy, które odpowiadają danemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="434eb-129">Run tests that match the given expression.</span></span> <span data-ttu-id="434eb-130">`<Expression>` Format `<property>Operator<value>[|&<Expression>]`, w której Operator jest jednym z `=`, `!=`, lub `~`.</span><span class="sxs-lookup"><span data-stu-id="434eb-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="434eb-131">Operator `~` ma "zawiera" semantykę i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="434eb-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="434eb-132">Nawias `()` służą do podrzędną wyrażeniach grupy.</span><span class="sxs-lookup"><span data-stu-id="434eb-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="434eb-133">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="434eb-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="434eb-134">Określ Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="434eb-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="434eb-135">Aby opublikować wyniki testu z Team Foundation Server, użyj `TfsPublisher` rejestratora dostawcy:</span><span class="sxs-lookup"><span data-stu-id="434eb-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="434eb-136">Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), użyj `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="434eb-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="434eb-137">Ten przełącznik tworzy plik w wynikach testu katalogu przy użyciu danej nazwy pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="434eb-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="434eb-138">Jeśli `LogFileName` nie jest udostępniany unikatowej nazwy pliku jest utworzona w celu przechowywania wyników testów.</span><span class="sxs-lookup"><span data-stu-id="434eb-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="434eb-139">Wyświetla listę wszystkich odnalezionych testów z podanego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="434eb-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="434eb-140">Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="434eb-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="434eb-141">Określa port do połączenia z gniazdem i odbierania komunikatów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="434eb-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="434eb-142">Włącza pełne dzienniki platformy testów.</span><span class="sxs-lookup"><span data-stu-id="434eb-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="434eb-143">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="434eb-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="434eb-144">Uruchamia testy w trybie polecenia blame.</span><span class="sxs-lookup"><span data-stu-id="434eb-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="434eb-145">Ta opcja jest przydatna polega na wyizolowaniu problematyczne testy, powodując hosta testów ulega awarii.</span><span class="sxs-lookup"><span data-stu-id="434eb-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="434eb-146">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* , przechwytuje kolejność wykonywania testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="434eb-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="434eb-147">Uruchamia testy w procesie izolowanym.</span><span class="sxs-lookup"><span data-stu-id="434eb-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="434eb-148">To sprawia, że *vstest.console.exe* procesu mniej prawdopodobne zatrzymane w przypadku błędu w testach, ale testy mogą działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="434eb-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="434eb-149">Odczytuje plik odpowiedzi, aby wyświetlić więcej opcji.</span><span class="sxs-lookup"><span data-stu-id="434eb-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="434eb-150">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="434eb-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="434eb-151">Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="434eb-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="434eb-152">Użyj spacji do oddzielania wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="434eb-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="434eb-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="434eb-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="434eb-154">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="434eb-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="434eb-155">Uruchom testy o nazwach odpowiadających podanej wartości.</span><span class="sxs-lookup"><span data-stu-id="434eb-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="434eb-156">Wiele wartości należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="434eb-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="434eb-157">Używa niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieją) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="434eb-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="434eb-158">Docelowa platforma architektury używanej do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="434eb-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="434eb-159">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="434eb-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="434eb-160">Wersja docelowa.NET Framework używanego do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="434eb-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="434eb-161">Prawidłowe wartości należą do nich `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="434eb-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="434eb-162">Inne obsługiwane wartości to `Framework40`, `Framework45`, i `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="434eb-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="434eb-163">Wykonuj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="434eb-163">Execute tests in parallel.</span></span> <span data-ttu-id="434eb-164">Domyślnie wszystkie dostępne rdzenie maszyny są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="434eb-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="434eb-165">Określ jawną liczby rdzeni, ustawiając właściwość MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="434eb-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="434eb-166">Uruchom testy, które odpowiadają danemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="434eb-166">Run tests that match the given expression.</span></span> <span data-ttu-id="434eb-167">`<Expression>` Format `<property>Operator<value>[|&<Expression>]`, w której Operator jest jednym z `=`, `!=`, lub `~`.</span><span class="sxs-lookup"><span data-stu-id="434eb-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="434eb-168">Operator `~` ma "zawiera" semantykę i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="434eb-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="434eb-169">Nawias `()` służą do podrzędną wyrażeniach grupy.</span><span class="sxs-lookup"><span data-stu-id="434eb-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="434eb-170">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="434eb-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="434eb-171">Określ Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="434eb-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="434eb-172">Aby opublikować wyniki testu z Team Foundation Server, użyj `TfsPublisher` rejestratora dostawcy:</span><span class="sxs-lookup"><span data-stu-id="434eb-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="434eb-173">Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), użyj `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="434eb-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="434eb-174">Ten przełącznik tworzy plik w wynikach testu katalogu przy użyciu danej nazwy pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="434eb-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="434eb-175">Jeśli `LogFileName` nie jest udostępniany unikatowej nazwy pliku jest utworzona w celu przechowywania wyników testów.</span><span class="sxs-lookup"><span data-stu-id="434eb-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="434eb-176">Wyświetla listę wszystkich odnalezionych testów z podanego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="434eb-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="434eb-177">Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="434eb-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="434eb-178">Określa port do połączenia z gniazdem i odbierania komunikatów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="434eb-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="434eb-179">Włącza pełne dzienniki platformy testów.</span><span class="sxs-lookup"><span data-stu-id="434eb-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="434eb-180">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="434eb-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="434eb-181">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="434eb-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="434eb-182">Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="434eb-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="434eb-183">Użyj spacji do oddzielania wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="434eb-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="434eb-184">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="434eb-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="434eb-185">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="434eb-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="434eb-186">Uruchom testy o nazwach odpowiadających podanej wartości.</span><span class="sxs-lookup"><span data-stu-id="434eb-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="434eb-187">Wiele wartości należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="434eb-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="434eb-188">Używa niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieją) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="434eb-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="434eb-189">Docelowa platforma architektury używanej do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="434eb-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="434eb-190">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="434eb-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="434eb-191">Wersja docelowa.NET Framework używanego do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="434eb-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="434eb-192">Prawidłowe wartości należą do nich `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="434eb-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="434eb-193">Inne obsługiwane wartości to `Framework40`, `Framework45`, i `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="434eb-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="434eb-194">Wykonuj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="434eb-194">Execute tests in parallel.</span></span> <span data-ttu-id="434eb-195">Domyślnie wszystkie dostępne rdzenie maszyny są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="434eb-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="434eb-196">Określ jawną liczby rdzeni, ustawiając właściwość MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="434eb-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="434eb-197">Uruchom testy, które odpowiadają danemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="434eb-197">Run tests that match the given expression.</span></span> <span data-ttu-id="434eb-198">`<Expression>` Format `<property>Operator<value>[|&<Expression>]`, w której Operator jest jednym z `=`, `!=`, lub `~`.</span><span class="sxs-lookup"><span data-stu-id="434eb-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="434eb-199">Operator `~` ma "zawiera" semantykę i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="434eb-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="434eb-200">Nawias `()` służą do podrzędną wyrażeniach grupy.</span><span class="sxs-lookup"><span data-stu-id="434eb-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="434eb-201">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="434eb-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="434eb-202">Określ Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="434eb-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="434eb-203">Aby opublikować wyniki testu z Team Foundation Server, użyj `TfsPublisher` rejestratora dostawcy:</span><span class="sxs-lookup"><span data-stu-id="434eb-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="434eb-204">Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), użyj `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="434eb-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="434eb-205">Ten przełącznik tworzy plik w wynikach testu katalogu przy użyciu danej nazwy pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="434eb-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="434eb-206">Jeśli `LogFileName` nie jest udostępniany unikatowej nazwy pliku jest utworzona w celu przechowywania wyników testów.</span><span class="sxs-lookup"><span data-stu-id="434eb-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="434eb-207">Wyświetla listę wszystkich odnalezionych testów z podanego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="434eb-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="434eb-208">Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="434eb-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="434eb-209">Określa port do połączenia z gniazdem i odbierania komunikatów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="434eb-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="434eb-210">Włącza pełne dzienniki platformy testów.</span><span class="sxs-lookup"><span data-stu-id="434eb-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="434eb-211">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="434eb-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="434eb-212">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="434eb-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="434eb-213">Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="434eb-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="434eb-214">Użyj spacji do oddzielania wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="434eb-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="434eb-215">Przykłady</span><span class="sxs-lookup"><span data-stu-id="434eb-215">Examples</span></span>

<span data-ttu-id="434eb-216">Uruchom testy w `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="434eb-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="434eb-217">Uruchom testy w `mytestproject.dll`, eksportowania do niestandardowego folderu o nazwie niestandardowy:</span><span class="sxs-lookup"><span data-stu-id="434eb-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="434eb-218">Uruchom testy w `mytestproject.dll` i `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="434eb-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="434eb-219">Uruchom `TestMethod1` testów:</span><span class="sxs-lookup"><span data-stu-id="434eb-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="434eb-220">Uruchom `TestMethod1` i `TestMethod2` testów:</span><span class="sxs-lookup"><span data-stu-id="434eb-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
