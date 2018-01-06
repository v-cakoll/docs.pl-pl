---
title: polecenie vstest DotNet - .NET Core interfejsu wiersza polecenia
description: "Polecenie vstest dotnet tworzy projekt i wszystkie jego zależności."
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: f2ad875430b2dc7f0ffbadfb9a39dd83854557cb
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="dotnet-vstest"></a><span data-ttu-id="b8f63-103">DotNet vstest</span><span class="sxs-lookup"><span data-stu-id="b8f63-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b8f63-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b8f63-104">Name</span></span>

<span data-ttu-id="b8f63-105">`dotnet-vstest`-Uruchamia testy z określonych plików.</span><span class="sxs-lookup"><span data-stu-id="b8f63-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b8f63-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="b8f63-106">Synopsis</span></span>

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a><span data-ttu-id="b8f63-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b8f63-107">Description</span></span>

<span data-ttu-id="b8f63-108">`dotnet-vstest` Polecenia `VSTest.Console` wiersza polecenia do uruchomienia aplikacji zautomatyzowane jednostkowe i kodowane testy interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b8f63-108">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="b8f63-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b8f63-109">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="b8f63-110">Uruchom testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="b8f63-110">Run tests from the specified assemblies.</span></span> <span data-ttu-id="b8f63-111">Oddziel wiele nazw zestawów testów ze spacjami.</span><span class="sxs-lookup"><span data-stu-id="b8f63-111">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="b8f63-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="b8f63-112">Options</span></span>

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="b8f63-113">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="b8f63-113">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="b8f63-114">Uruchom testy o nazwach odpowiadających podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="b8f63-114">Run tests with names that match the provided values.</span></span> <span data-ttu-id="b8f63-115">Wiele wartości należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="b8f63-115">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="b8f63-116">Używa niestandardowych adapterów testowych z danej ścieżce (jeśli istnieją) w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="b8f63-116">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="b8f63-117">Docelowa architektura platformy, używany do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="b8f63-117">Target platform architecture used for test execution.</span></span> <span data-ttu-id="b8f63-118">Prawidłowe wartości to `x86`, `x64`, i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="b8f63-118">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="b8f63-119">Docelowy .NET Framework w wersji używany do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="b8f63-119">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="b8f63-120">Przykłady prawidłowych wartości `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`itp. Inne obsługiwane wartości to `Framework35`, `Framework40`, `Framework45`, i `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="b8f63-120">Examples of valid values are `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="b8f63-121">Wykonywać testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="b8f63-121">Execute tests in parallel.</span></span> <span data-ttu-id="b8f63-122">Domyślnie wszystkie dostępne rdzenie komputera są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="b8f63-122">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="b8f63-123">Ustaw jawne liczba rdzeni z pliku ustawień.</span><span class="sxs-lookup"><span data-stu-id="b8f63-123">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="b8f63-124">Uruchom testy, które odpowiada danemu wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="b8f63-124">Run tests that match the given expression.</span></span> <span data-ttu-id="b8f63-125">`<Expression>`jest w formacie `<property>Operator<value>[|&<Expression>]`, w którym Operator jest jednym z `=`, `!=`, lub `~`.</span><span class="sxs-lookup"><span data-stu-id="b8f63-125">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span>  <span data-ttu-id="b8f63-126">Operator `~` ma semantykę "zawiera" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="b8f63-126">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="b8f63-127">Nawias `()` służą do grupy wyrażeń podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b8f63-127">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="b8f63-128">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="b8f63-128">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="b8f63-129">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="b8f63-129">Specify a logger for test results.</span></span>  

* <span data-ttu-id="b8f63-130">Aby opublikować wyniki testu z Team Foundation Server, należy użyć `TfsPublisher` rejestratora dostawcy:</span><span class="sxs-lookup"><span data-stu-id="b8f63-130">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="b8f63-131">Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), należy użyć `trx` dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="b8f63-131">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="b8f63-132">Ten przełącznik tworzy plik w wynikach testów katalogu z podana nazwa pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="b8f63-132">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="b8f63-133">Jeśli `LogFileName` nie jest podana unikatowa nazwa pliku jest tworzony dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="b8f63-133">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="b8f63-134">Listy wykrytych testów w danym kontenerze testowym.</span><span class="sxs-lookup"><span data-stu-id="b8f63-134">Lists discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="b8f63-135">Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="b8f63-135">Process Id of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="b8f63-136">Określa port na potrzeby połączenia gniazda i odbieranie komunikatów zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b8f63-136">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="b8f63-137">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="b8f63-137">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="b8f63-138">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="b8f63-138">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="b8f63-139">Określa dodatkowe argumenty do przekazania do karty sieciowej.</span><span class="sxs-lookup"><span data-stu-id="b8f63-139">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="b8f63-140">Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="b8f63-140">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="b8f63-141">Użyj miejscem do oddzielania wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="b8f63-141">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="b8f63-142">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b8f63-142">Examples</span></span>

<span data-ttu-id="b8f63-143">Uruchom testy w `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="b8f63-143">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="b8f63-144">Uruchom testy w `mytestproject.dll`, eksportowanie do niestandardowego folderu o nazwie niestandardowych:</span><span class="sxs-lookup"><span data-stu-id="b8f63-144">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="b8f63-145">Uruchom testy w `mytestproject.dll` i `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="b8f63-145">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="b8f63-146">Uruchom `TestMethod1` testów:</span><span class="sxs-lookup"><span data-stu-id="b8f63-146">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="b8f63-147">Uruchom `TestMethod1` i `TestMethod2` testów:</span><span class="sxs-lookup"><span data-stu-id="b8f63-147">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`

