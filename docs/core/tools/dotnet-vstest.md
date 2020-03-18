---
title: polecenie dotnet vstest
description: Polecenie dotnet vstest tworzy projekt i wszystkie jego zależności.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156936"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="e22f4-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="e22f4-103">dotnet vstest</span></span>

<span data-ttu-id="e22f4-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="e22f4-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e22f4-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e22f4-105">Name</span></span>

<span data-ttu-id="e22f4-106">`dotnet-vstest`- Uruchamia testy z określonych plików.</span><span class="sxs-lookup"><span data-stu-id="e22f4-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e22f4-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e22f4-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a><span data-ttu-id="e22f4-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e22f4-108">Description</span></span>

<span data-ttu-id="e22f4-109">Polecenie `dotnet-vstest` uruchamia `VSTest.Console` aplikację wiersza polecenia w celu uruchomienia automatycznych testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="e22f4-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="e22f4-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e22f4-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="e22f4-111">Uruchom testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="e22f4-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="e22f4-112">Oddziel wiele nazw zespołów testowych sposobnikami.</span><span class="sxs-lookup"><span data-stu-id="e22f4-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="e22f4-113">Symbole wieloznaczne są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e22f4-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="e22f4-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="e22f4-114">Options</span></span>

- **`--Settings <Settings File>`**

  <span data-ttu-id="e22f4-115">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="e22f4-115">Settings to use when running tests.</span></span>

- **`--Tests <Test Names>`**

  <span data-ttu-id="e22f4-116">Uruchom testy z nazwami, które pasują do podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="e22f4-116">Run tests with names that match the provided values.</span></span> <span data-ttu-id="e22f4-117">Oddziel wiele wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="e22f4-117">Separate multiple values with commas.</span></span>

- **`--TestAdapterPath`**

  <span data-ttu-id="e22f4-118">Użyj niestandardowych kart testowych z danej ścieżki (jeśli istnieje) w przebiegu testowym.</span><span class="sxs-lookup"><span data-stu-id="e22f4-118">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--Platform <Platform type>`**

  <span data-ttu-id="e22f4-119">Architektura platformy docelowej używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="e22f4-119">Target platform architecture used for test execution.</span></span> <span data-ttu-id="e22f4-120">Prawidłowe wartości `x86` `x64`to `ARM`, i .</span><span class="sxs-lookup"><span data-stu-id="e22f4-120">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Framework <Framework Version>`**

  <span data-ttu-id="e22f4-121">Wersja docelowa .NET Framework używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="e22f4-121">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="e22f4-122">Przykładami prawidłowych `.NETFramework,Version=v4.6` wartości `.NETCoreApp,Version=v1.0`są lub .</span><span class="sxs-lookup"><span data-stu-id="e22f4-122">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="e22f4-123">Inne obsługiwane wartości `Framework40` `Framework45`to `FrameworkCore10`, `FrameworkUap10`, i .</span><span class="sxs-lookup"><span data-stu-id="e22f4-123">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--Parallel`**

  <span data-ttu-id="e22f4-124">Uruchamiaj testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="e22f4-124">Run tests in parallel.</span></span> <span data-ttu-id="e22f4-125">Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użytku.</span><span class="sxs-lookup"><span data-stu-id="e22f4-125">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="e22f4-126">Określ jawną liczbę rdzeni, `MaxCpuCount` ustawiając `RunConfiguration` właściwość pod węzłem w pliku *runsettings.*</span><span class="sxs-lookup"><span data-stu-id="e22f4-126">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--TestCaseFilter <Expression>`**

  <span data-ttu-id="e22f4-127">Uruchom testy, które pasują do danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e22f4-127">Run tests that match the given expression.</span></span> <span data-ttu-id="e22f4-128">`<Expression>`jest w `<property>Operator<value>[|&<Expression>]`formacie, gdzie Operator `=` `!=`jest `~`jednym z , lub .</span><span class="sxs-lookup"><span data-stu-id="e22f4-128">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="e22f4-129">Operator `~` ma semantyki "zawiera" i ma `DisplayName`zastosowanie do właściwości ciągu, takich jak .</span><span class="sxs-lookup"><span data-stu-id="e22f4-129">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="e22f4-130">Nawiasy `()` są używane do grupowania podwyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e22f4-130">Parenthesis `()` are used to group subexpressions.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="e22f4-131">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="e22f4-131">Prints out a short help for the command.</span></span>

- **`--logger <Logger Uri/FriendlyName>`**

  <span data-ttu-id="e22f4-132">Określ rejestrator dla wyników testów.</span><span class="sxs-lookup"><span data-stu-id="e22f4-132">Specify a logger for test results.</span></span>

  - <span data-ttu-id="e22f4-133">Aby opublikować wyniki testów na `TfsPublisher` serwerze Team Foundation Server, należy użyć dostawcy rejestratora:</span><span class="sxs-lookup"><span data-stu-id="e22f4-133">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="e22f4-134">Aby zalogować wyniki do pliku wyników testów `trx` programu Visual Studio (TRX), należy użyć dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="e22f4-134">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="e22f4-135">Ten przełącznik tworzy plik w katalogu wyników testów z podaną nazwą pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="e22f4-135">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="e22f4-136">Jeśli `LogFileName` nie jest podana, unikatowa nazwa pliku jest tworzona do przechowywania wyników testu.</span><span class="sxs-lookup"><span data-stu-id="e22f4-136">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  <span data-ttu-id="e22f4-137">Wyświetla listę wszystkich odnalezionych testów z danego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="e22f4-137">Lists all discovered tests from the given test container.</span></span>

- **`--ParentProcessId <ParentProcessId>`**

  <span data-ttu-id="e22f4-138">Identyfikator procesu nadrzędnego odpowiedzialnego za uruchomienie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="e22f4-138">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Port <Port>`**

  <span data-ttu-id="e22f4-139">Określa port dla połączenia gniazda i odbierania komunikatów o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="e22f4-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--Diag <Path to log file>`**

  <span data-ttu-id="e22f4-140">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="e22f4-140">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="e22f4-141">Dzienniki są zapisywane w podanych plikach.</span><span class="sxs-lookup"><span data-stu-id="e22f4-141">Logs are written to the provided file.</span></span>

- **`--Blame`**

  <span data-ttu-id="e22f4-142">Uruchamia testy w trybie winy.</span><span class="sxs-lookup"><span data-stu-id="e22f4-142">Runs the tests in blame mode.</span></span> <span data-ttu-id="e22f4-143">Ta opcja jest pomocna w izolowaniu problematycznych testów powodujących awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="e22f4-143">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="e22f4-144">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml,* który przechwytuje kolejność wykonywania testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="e22f4-144">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="e22f4-145">Uruchamia testy w izolowanym procesie.</span><span class="sxs-lookup"><span data-stu-id="e22f4-145">Runs the tests in an isolated process.</span></span> <span data-ttu-id="e22f4-146">To sprawia, że *vstest.console.exe* proces mniej prawdopodobne, aby być zatrzymane na błąd w testach, ale testy mogą działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="e22f4-146">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`@<file>`**

  <span data-ttu-id="e22f4-147">Odczytuje plik odpowiedzi, aby uzyskać więcej opcji.</span><span class="sxs-lookup"><span data-stu-id="e22f4-147">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="e22f4-148">Określa dodatkowe argumenty, które mają zostać przekazane do karty.</span><span class="sxs-lookup"><span data-stu-id="e22f4-148">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="e22f4-149">Argumenty są określane jako pary name-value `<n>=<v>` `<n>` formularza , gdzie `<v>` jest nazwa argumentu i jest wartością argumentu.</span><span class="sxs-lookup"><span data-stu-id="e22f4-149">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="e22f4-150">Spatonie służy do oddzielania wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="e22f4-150">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="e22f4-151">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e22f4-151">Examples</span></span>

<span data-ttu-id="e22f4-152">Uruchom testy w *mytestproject.dll*:</span><span class="sxs-lookup"><span data-stu-id="e22f4-152">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="e22f4-153">Uruchom testy w *mytestproject.dll*, eksportowanie do folderu niestandardowego o nazwie niestandardowej:</span><span class="sxs-lookup"><span data-stu-id="e22f4-153">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="e22f4-154">Uruchom testy w *mytestproject.dll* i *myothertestproject.exe:*</span><span class="sxs-lookup"><span data-stu-id="e22f4-154">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="e22f4-155">Uruchom `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="e22f4-155">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="e22f4-156">Uruchom `TestMethod1` `TestMethod2` i testy:</span><span class="sxs-lookup"><span data-stu-id="e22f4-156">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
