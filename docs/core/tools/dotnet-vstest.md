---
title: polecenie vstest DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie vstest dotnet tworzy projekt i wszystkie jego zależności.
author: guardrex
ms.author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: 84b9d9eebfbf20fefe8153dd3ae9bec0f34986c8
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696341"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="55a8b-103">DotNet vstest</span><span class="sxs-lookup"><span data-stu-id="55a8b-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="55a8b-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="55a8b-104">Name</span></span>

<span data-ttu-id="55a8b-105">`dotnet-vstest` -Uruchamia testy z określonych plików.</span><span class="sxs-lookup"><span data-stu-id="55a8b-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="55a8b-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="55a8b-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="55a8b-107">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="55a8b-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="55a8b-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="55a8b-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="55a8b-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="55a8b-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
---

## <a name="description"></a><span data-ttu-id="55a8b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="55a8b-110">Description</span></span>

<span data-ttu-id="55a8b-111">`dotnet-vstest` Polecenia `VSTest.Console` wiersza polecenia do uruchomienia aplikacji zautomatyzowane jednostkowe i kodowane testy interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55a8b-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="55a8b-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="55a8b-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="55a8b-113">Uruchom testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="55a8b-114">Oddziel wiele nazw zestawów testów ze spacjami.</span><span class="sxs-lookup"><span data-stu-id="55a8b-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="55a8b-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="55a8b-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="55a8b-116">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="55a8b-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="55a8b-117">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="55a8b-118">Uruchom testy o nazwach odpowiadających podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="55a8b-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="55a8b-119">Wiele wartości należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="55a8b-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="55a8b-120">Używa niestandardowych adapterów testowych z danej ścieżce (jeśli istnieją) w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="55a8b-121">Docelowa architektura platformy, używany do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="55a8b-122">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="55a8b-123">Docelowy .NET Framework w wersji używany do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="55a8b-124">Przykłady prawidłowych wartości `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="55a8b-125">Inne obsługiwane wartości to `Framework35`, `Framework40`, `Framework45`, `FrameworkCore10`, i `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-125">Other supported values are `Framework35`, `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="55a8b-126">Wykonywać testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="55a8b-126">Execute tests in parallel.</span></span> <span data-ttu-id="55a8b-127">Domyślnie wszystkie dostępne rdzenie komputera są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="55a8b-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="55a8b-128">Ustaw jawne liczba rdzeni z pliku ustawień.</span><span class="sxs-lookup"><span data-stu-id="55a8b-128">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="55a8b-129">Uruchom testy, które odpowiada danemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-129">Run tests that match the given expression.</span></span> <span data-ttu-id="55a8b-130">`<Expression>` jest w formacie `<property>Operator<value>[|&<Expression>]`, w którym Operator jest jednym z `=`, `!=`, lub `~`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="55a8b-131">Operator `~` ma semantykę "zawiera" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="55a8b-132">Nawias `()` służą do grupy wyrażeń podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="55a8b-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="55a8b-133">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="55a8b-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="55a8b-134">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="55a8b-135">Aby opublikować wyniki testu z Team Foundation Server, należy użyć `TfsPublisher` rejestratora dostawcy:</span><span class="sxs-lookup"><span data-stu-id="55a8b-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="55a8b-136">Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), należy użyć `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="55a8b-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="55a8b-137">Ten przełącznik tworzy plik w wynikach testów katalogu z podana nazwa pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="55a8b-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="55a8b-138">Jeśli `LogFileName` nie jest podana unikatowa nazwa pliku jest tworzony dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="55a8b-139">Wyświetla listę wszystkich wykrytych testów w danym kontenerze testowym.</span><span class="sxs-lookup"><span data-stu-id="55a8b-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="55a8b-140">Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="55a8b-141">Określa port na potrzeby połączenia gniazda i odbieranie komunikatów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="55a8b-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="55a8b-142">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="55a8b-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="55a8b-143">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="55a8b-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="55a8b-144">Uruchamia testy w trybie winy.</span><span class="sxs-lookup"><span data-stu-id="55a8b-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="55a8b-145">Ta opcja jest pomocna w izolowanie testów problemy powodujące hosta testów do awarii.</span><span class="sxs-lookup"><span data-stu-id="55a8b-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="55a8b-146">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* który przechwytuje kolejność wykonywania testów przed tej awarii.</span><span class="sxs-lookup"><span data-stu-id="55a8b-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="55a8b-147">Uruchamia testy w proces izolowanym.</span><span class="sxs-lookup"><span data-stu-id="55a8b-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="55a8b-148">Dzięki temu *vstest.console.exe* przetworzyć mniej prawdopodobne w przypadku błędu w testach, ale testy mogą być wykonywane wolniej.</span><span class="sxs-lookup"><span data-stu-id="55a8b-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="55a8b-149">Odczytuje plik odpowiedzi, aby wyświetlić więcej opcji.</span><span class="sxs-lookup"><span data-stu-id="55a8b-149">Reads response file for more options.</span></span>


`args`

<span data-ttu-id="55a8b-150">Określa dodatkowe argumenty do przekazania do karty sieciowej.</span><span class="sxs-lookup"><span data-stu-id="55a8b-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="55a8b-151">Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="55a8b-152">Użyj miejscem do oddzielania wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="55a8b-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="55a8b-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="55a8b-154">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="55a8b-155">Uruchom testy o nazwach odpowiadających podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="55a8b-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="55a8b-156">Wiele wartości należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="55a8b-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="55a8b-157">Używa niestandardowych adapterów testowych z danej ścieżce (jeśli istnieją) w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="55a8b-158">Docelowa architektura platformy, używany do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="55a8b-159">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="55a8b-160">Docelowy .NET Framework w wersji używany do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="55a8b-161">Przykłady prawidłowych wartości `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="55a8b-162">Inne obsługiwane wartości to `Framework35`, `Framework40`, `Framework45`, i `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-162">Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="55a8b-163">Wykonywać testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="55a8b-163">Execute tests in parallel.</span></span> <span data-ttu-id="55a8b-164">Domyślnie wszystkie dostępne rdzenie komputera są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="55a8b-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="55a8b-165">Ustaw jawne liczba rdzeni z pliku ustawień.</span><span class="sxs-lookup"><span data-stu-id="55a8b-165">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="55a8b-166">Uruchom testy, które odpowiada danemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-166">Run tests that match the given expression.</span></span> <span data-ttu-id="55a8b-167">`<Expression>` jest w formacie `<property>Operator<value>[|&<Expression>]`, w którym Operator jest jednym z `=`, `!=`, lub `~`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="55a8b-168">Operator `~` ma semantykę "zawiera" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="55a8b-169">Nawias `()` służą do grupy wyrażeń podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="55a8b-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="55a8b-170">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="55a8b-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="55a8b-171">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="55a8b-172">Aby opublikować wyniki testu z Team Foundation Server, należy użyć `TfsPublisher` rejestratora dostawcy:</span><span class="sxs-lookup"><span data-stu-id="55a8b-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="55a8b-173">Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), należy użyć `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="55a8b-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="55a8b-174">Ten przełącznik tworzy plik w wynikach testów katalogu z podana nazwa pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="55a8b-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="55a8b-175">Jeśli `LogFileName` nie jest podana unikatowa nazwa pliku jest tworzony dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="55a8b-176">Wyświetla listę wszystkich wykrytych testów w danym kontenerze testowym.</span><span class="sxs-lookup"><span data-stu-id="55a8b-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="55a8b-177">Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="55a8b-178">Określa port na potrzeby połączenia gniazda i odbieranie komunikatów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="55a8b-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="55a8b-179">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="55a8b-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="55a8b-180">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="55a8b-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="55a8b-181">Określa dodatkowe argumenty do przekazania do karty sieciowej.</span><span class="sxs-lookup"><span data-stu-id="55a8b-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="55a8b-182">Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="55a8b-183">Użyj miejscem do oddzielania wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="55a8b-184">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="55a8b-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="55a8b-185">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="55a8b-186">Uruchom testy o nazwach odpowiadających podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="55a8b-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="55a8b-187">Wiele wartości należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="55a8b-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="55a8b-188">Używa niestandardowych adapterów testowych z danej ścieżce (jeśli istnieją) w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="55a8b-189">Docelowa architektura platformy, używany do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="55a8b-190">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="55a8b-191">Docelowy .NET Framework w wersji używany do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="55a8b-192">Przykłady prawidłowych wartości `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="55a8b-193">Inne obsługiwane wartości to `Framework35`, `Framework40`, `Framework45`, i `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-193">Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="55a8b-194">Wykonywać testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="55a8b-194">Execute tests in parallel.</span></span> <span data-ttu-id="55a8b-195">Domyślnie wszystkie dostępne rdzenie komputera są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="55a8b-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="55a8b-196">Ustaw jawne liczba rdzeni z pliku ustawień.</span><span class="sxs-lookup"><span data-stu-id="55a8b-196">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="55a8b-197">Uruchom testy, które odpowiada danemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-197">Run tests that match the given expression.</span></span> <span data-ttu-id="55a8b-198">`<Expression>` jest w formacie `<property>Operator<value>[|&<Expression>]`, w którym Operator jest jednym z `=`, `!=`, lub `~`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="55a8b-199">Operator `~` ma semantykę "zawiera" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="55a8b-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="55a8b-200">Nawias `()` służą do grupy wyrażeń podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="55a8b-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="55a8b-201">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="55a8b-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="55a8b-202">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="55a8b-203">Aby opublikować wyniki testu z Team Foundation Server, należy użyć `TfsPublisher` rejestratora dostawcy:</span><span class="sxs-lookup"><span data-stu-id="55a8b-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="55a8b-204">Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), należy użyć `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="55a8b-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="55a8b-205">Ten przełącznik tworzy plik w wynikach testów katalogu z podana nazwa pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="55a8b-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="55a8b-206">Jeśli `LogFileName` nie jest podana unikatowa nazwa pliku jest tworzony dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="55a8b-207">Wyświetla listę wszystkich wykrytych testów w danym kontenerze testowym.</span><span class="sxs-lookup"><span data-stu-id="55a8b-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="55a8b-208">Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="55a8b-209">Określa port na potrzeby połączenia gniazda i odbieranie komunikatów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="55a8b-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="55a8b-210">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="55a8b-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="55a8b-211">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="55a8b-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="55a8b-212">Określa dodatkowe argumenty do przekazania do karty sieciowej.</span><span class="sxs-lookup"><span data-stu-id="55a8b-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="55a8b-213">Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="55a8b-214">Użyj miejscem do oddzielania wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="55a8b-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="55a8b-215">Przykłady</span><span class="sxs-lookup"><span data-stu-id="55a8b-215">Examples</span></span>

<span data-ttu-id="55a8b-216">Uruchom testy w `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="55a8b-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="55a8b-217">Uruchom testy w `mytestproject.dll`, eksportowanie do niestandardowego folderu o nazwie niestandardowych:</span><span class="sxs-lookup"><span data-stu-id="55a8b-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="55a8b-218">Uruchom testy w `mytestproject.dll` i `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="55a8b-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="55a8b-219">Uruchom `TestMethod1` testów:</span><span class="sxs-lookup"><span data-stu-id="55a8b-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="55a8b-220">Uruchom `TestMethod1` i `TestMethod2` testów:</span><span class="sxs-lookup"><span data-stu-id="55a8b-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`