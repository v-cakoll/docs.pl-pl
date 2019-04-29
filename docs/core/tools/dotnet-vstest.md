---
title: polecenie vstest DotNet
description: Polecenia dotnet vstest kompiluje projekt i wszystkie jego zależności.
author: guardrex
ms.date: 05/30/2018
ms.openlocfilehash: dcf17a59fea1f58757f39721c5dd5947ed30df0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648519"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="5009c-103">DotNet vstest</span><span class="sxs-lookup"><span data-stu-id="5009c-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5009c-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5009c-104">Name</span></span>

<span data-ttu-id="5009c-105">`dotnet-vstest` -Uruchamia testy z określonych plików.</span><span class="sxs-lookup"><span data-stu-id="5009c-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5009c-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5009c-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5009c-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5009c-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5009c-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5009c-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5009c-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5009c-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="5009c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5009c-110">Description</span></span>

<span data-ttu-id="5009c-111">`dotnet-vstest` Polecenia `VSTest.Console` aplikacji wiersza polecenia, aby uruchomić automatyczne testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="5009c-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="5009c-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5009c-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="5009c-113">Uruchom testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="5009c-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="5009c-114">Oddziel wiele nazw zestawów testowych spacjami.</span><span class="sxs-lookup"><span data-stu-id="5009c-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="5009c-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="5009c-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5009c-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5009c-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="5009c-117">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="5009c-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="5009c-118">Uruchom testy o nazwach odpowiadających podanej wartości.</span><span class="sxs-lookup"><span data-stu-id="5009c-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="5009c-119">Wiele wartości należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="5009c-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="5009c-120">Używa niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieją) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="5009c-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="5009c-121">Docelowa platforma architektury używanej do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="5009c-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="5009c-122">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="5009c-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="5009c-123">Wersja docelowa.NET Framework używanego do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="5009c-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="5009c-124">Prawidłowe wartości należą do nich `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="5009c-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="5009c-125">Inne obsługiwane wartości to `Framework40`, `Framework45`, `FrameworkCore10`, i `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="5009c-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="5009c-126">Wykonuj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="5009c-126">Execute tests in parallel.</span></span> <span data-ttu-id="5009c-127">Domyślnie wszystkie dostępne rdzenie maszyny są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="5009c-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="5009c-128">Określ jawną liczby rdzeni, ustawiając właściwość MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="5009c-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="5009c-129">Uruchom testy, które odpowiadają danemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="5009c-129">Run tests that match the given expression.</span></span> <span data-ttu-id="5009c-130">`<Expression>` Format `<property>Operator<value>[|&<Expression>]`, w której Operator jest jednym z `=`, `!=`, lub `~`.</span><span class="sxs-lookup"><span data-stu-id="5009c-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="5009c-131">Operator `~` ma "zawiera" semantykę i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="5009c-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="5009c-132">Nawias `()` służą do podrzędną wyrażeniach grupy.</span><span class="sxs-lookup"><span data-stu-id="5009c-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="5009c-133">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5009c-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="5009c-134">Określ Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="5009c-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="5009c-135">Aby opublikować wyniki testu z Team Foundation Server, użyj `TfsPublisher` rejestratora dostawcy:</span><span class="sxs-lookup"><span data-stu-id="5009c-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="5009c-136">Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), użyj `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="5009c-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="5009c-137">Ten przełącznik tworzy plik w wynikach testu katalogu przy użyciu danej nazwy pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="5009c-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="5009c-138">Jeśli `LogFileName` nie jest udostępniany unikatowej nazwy pliku jest utworzona w celu przechowywania wyników testów.</span><span class="sxs-lookup"><span data-stu-id="5009c-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="5009c-139">Wyświetla listę wszystkich odnalezionych testów z podanego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="5009c-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="5009c-140">Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="5009c-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="5009c-141">Określa port do połączenia z gniazdem i odbierania komunikatów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5009c-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="5009c-142">Włącza pełne dzienniki platformy testów.</span><span class="sxs-lookup"><span data-stu-id="5009c-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="5009c-143">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="5009c-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="5009c-144">Uruchamia testy w trybie polecenia blame.</span><span class="sxs-lookup"><span data-stu-id="5009c-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="5009c-145">Ta opcja jest przydatna polega na wyizolowaniu problematyczne testy, powodując hosta testów ulega awarii.</span><span class="sxs-lookup"><span data-stu-id="5009c-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="5009c-146">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* , przechwytuje kolejność wykonywania testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="5009c-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="5009c-147">Uruchamia testy w procesie izolowanym.</span><span class="sxs-lookup"><span data-stu-id="5009c-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="5009c-148">To sprawia, że *vstest.console.exe* procesu mniej prawdopodobne zatrzymane w przypadku błędu w testach, ale testy mogą działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="5009c-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="5009c-149">Odczytuje plik odpowiedzi, aby wyświetlić więcej opcji.</span><span class="sxs-lookup"><span data-stu-id="5009c-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="5009c-150">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="5009c-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="5009c-151">Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="5009c-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="5009c-152">Użyj spacji do oddzielania wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="5009c-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5009c-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5009c-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="5009c-154">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="5009c-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="5009c-155">Uruchom testy o nazwach odpowiadających podanej wartości.</span><span class="sxs-lookup"><span data-stu-id="5009c-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="5009c-156">Wiele wartości należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="5009c-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="5009c-157">Używa niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieją) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="5009c-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="5009c-158">Docelowa platforma architektury używanej do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="5009c-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="5009c-159">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="5009c-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="5009c-160">Wersja docelowa.NET Framework używanego do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="5009c-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="5009c-161">Prawidłowe wartości należą do nich `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="5009c-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="5009c-162">Inne obsługiwane wartości to `Framework40`, `Framework45`, i `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="5009c-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="5009c-163">Wykonuj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="5009c-163">Execute tests in parallel.</span></span> <span data-ttu-id="5009c-164">Domyślnie wszystkie dostępne rdzenie maszyny są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="5009c-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="5009c-165">Określ jawną liczby rdzeni, ustawiając właściwość MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="5009c-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="5009c-166">Uruchom testy, które odpowiadają danemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="5009c-166">Run tests that match the given expression.</span></span> <span data-ttu-id="5009c-167">`<Expression>` Format `<property>Operator<value>[|&<Expression>]`, w której Operator jest jednym z `=`, `!=`, lub `~`.</span><span class="sxs-lookup"><span data-stu-id="5009c-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="5009c-168">Operator `~` ma "zawiera" semantykę i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="5009c-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="5009c-169">Nawias `()` służą do podrzędną wyrażeniach grupy.</span><span class="sxs-lookup"><span data-stu-id="5009c-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="5009c-170">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5009c-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="5009c-171">Określ Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="5009c-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="5009c-172">Aby opublikować wyniki testu z Team Foundation Server, użyj `TfsPublisher` rejestratora dostawcy:</span><span class="sxs-lookup"><span data-stu-id="5009c-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="5009c-173">Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), użyj `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="5009c-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="5009c-174">Ten przełącznik tworzy plik w wynikach testu katalogu przy użyciu danej nazwy pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="5009c-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="5009c-175">Jeśli `LogFileName` nie jest udostępniany unikatowej nazwy pliku jest utworzona w celu przechowywania wyników testów.</span><span class="sxs-lookup"><span data-stu-id="5009c-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="5009c-176">Wyświetla listę wszystkich odnalezionych testów z podanego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="5009c-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="5009c-177">Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="5009c-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="5009c-178">Określa port do połączenia z gniazdem i odbierania komunikatów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5009c-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="5009c-179">Włącza pełne dzienniki platformy testów.</span><span class="sxs-lookup"><span data-stu-id="5009c-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="5009c-180">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="5009c-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="5009c-181">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="5009c-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="5009c-182">Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="5009c-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="5009c-183">Użyj spacji do oddzielania wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="5009c-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5009c-184">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5009c-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="5009c-185">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="5009c-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="5009c-186">Uruchom testy o nazwach odpowiadających podanej wartości.</span><span class="sxs-lookup"><span data-stu-id="5009c-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="5009c-187">Wiele wartości należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="5009c-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="5009c-188">Używa niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieją) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="5009c-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="5009c-189">Docelowa platforma architektury używanej do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="5009c-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="5009c-190">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="5009c-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="5009c-191">Wersja docelowa.NET Framework używanego do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="5009c-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="5009c-192">Prawidłowe wartości należą do nich `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="5009c-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="5009c-193">Inne obsługiwane wartości to `Framework40`, `Framework45`, i `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="5009c-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="5009c-194">Wykonuj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="5009c-194">Execute tests in parallel.</span></span> <span data-ttu-id="5009c-195">Domyślnie wszystkie dostępne rdzenie maszyny są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="5009c-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="5009c-196">Określ jawną liczby rdzeni, ustawiając właściwość MaxCpuCount w węźle RunConfiguration w pliku runsettings.</span><span class="sxs-lookup"><span data-stu-id="5009c-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="5009c-197">Uruchom testy, które odpowiadają danemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="5009c-197">Run tests that match the given expression.</span></span> <span data-ttu-id="5009c-198">`<Expression>` Format `<property>Operator<value>[|&<Expression>]`, w której Operator jest jednym z `=`, `!=`, lub `~`.</span><span class="sxs-lookup"><span data-stu-id="5009c-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="5009c-199">Operator `~` ma "zawiera" semantykę i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="5009c-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="5009c-200">Nawias `()` służą do podrzędną wyrażeniach grupy.</span><span class="sxs-lookup"><span data-stu-id="5009c-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="5009c-201">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5009c-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="5009c-202">Określ Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="5009c-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="5009c-203">Aby opublikować wyniki testu z Team Foundation Server, użyj `TfsPublisher` rejestratora dostawcy:</span><span class="sxs-lookup"><span data-stu-id="5009c-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="5009c-204">Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), użyj `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="5009c-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="5009c-205">Ten przełącznik tworzy plik w wynikach testu katalogu przy użyciu danej nazwy pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="5009c-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="5009c-206">Jeśli `LogFileName` nie jest udostępniany unikatowej nazwy pliku jest utworzona w celu przechowywania wyników testów.</span><span class="sxs-lookup"><span data-stu-id="5009c-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="5009c-207">Wyświetla listę wszystkich odnalezionych testów z podanego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="5009c-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="5009c-208">Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="5009c-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="5009c-209">Określa port do połączenia z gniazdem i odbierania komunikatów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5009c-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="5009c-210">Włącza pełne dzienniki platformy testów.</span><span class="sxs-lookup"><span data-stu-id="5009c-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="5009c-211">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="5009c-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="5009c-212">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="5009c-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="5009c-213">Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="5009c-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="5009c-214">Użyj spacji do oddzielania wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="5009c-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="5009c-215">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5009c-215">Examples</span></span>

<span data-ttu-id="5009c-216">Uruchom testy w `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="5009c-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="5009c-217">Uruchom testy w `mytestproject.dll`, eksportowania do niestandardowego folderu o nazwie niestandardowy:</span><span class="sxs-lookup"><span data-stu-id="5009c-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="5009c-218">Uruchom testy w `mytestproject.dll` i `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="5009c-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="5009c-219">Uruchom `TestMethod1` testów:</span><span class="sxs-lookup"><span data-stu-id="5009c-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="5009c-220">Uruchom `TestMethod1` i `TestMethod2` testów:</span><span class="sxs-lookup"><span data-stu-id="5009c-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
