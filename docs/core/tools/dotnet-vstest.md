---
title: dotnet VSTest — polecenie
description: Polecenie dotnet VSTest kompiluje projekt i wszystkie jego zależności.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156936"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="1eddf-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="1eddf-103">dotnet vstest</span></span>

<span data-ttu-id="1eddf-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="1eddf-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1eddf-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="1eddf-105">Name</span></span>

<span data-ttu-id="1eddf-106">`dotnet-vstest` — uruchamia testy z określonych plików.</span><span class="sxs-lookup"><span data-stu-id="1eddf-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1eddf-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="1eddf-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a><span data-ttu-id="1eddf-108">Opis</span><span class="sxs-lookup"><span data-stu-id="1eddf-108">Description</span></span>

<span data-ttu-id="1eddf-109">Polecenie `dotnet-vstest` uruchamia `VSTest.Console` aplikację wiersza polecenia w celu uruchomienia zautomatyzowanych testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="1eddf-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="1eddf-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1eddf-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="1eddf-111">Uruchom testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="1eddf-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="1eddf-112">Oddziel wiele nazw zestawów testowych spacjami.</span><span class="sxs-lookup"><span data-stu-id="1eddf-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="1eddf-113">Symbole wieloznaczne są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="1eddf-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="1eddf-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="1eddf-114">Options</span></span>

- **`--Settings <Settings File>`**

  <span data-ttu-id="1eddf-115">Ustawienia do użycia podczas przeprowadzania testów.</span><span class="sxs-lookup"><span data-stu-id="1eddf-115">Settings to use when running tests.</span></span>

- **`--Tests <Test Names>`**

  <span data-ttu-id="1eddf-116">Uruchom testy z nazwami, które pasują do podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="1eddf-116">Run tests with names that match the provided values.</span></span> <span data-ttu-id="1eddf-117">Rozdziel wiele wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="1eddf-117">Separate multiple values with commas.</span></span>

- **`--TestAdapterPath`**

  <span data-ttu-id="1eddf-118">Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="1eddf-118">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--Platform <Platform type>`**

  <span data-ttu-id="1eddf-119">Architektura platformy docelowej używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="1eddf-119">Target platform architecture used for test execution.</span></span> <span data-ttu-id="1eddf-120">Prawidłowe wartości to `x86`, `x64`i `ARM`.</span><span class="sxs-lookup"><span data-stu-id="1eddf-120">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Framework <Framework Version>`**

  <span data-ttu-id="1eddf-121">Docelowa wersja .NET Framework używana do wykonania testu.</span><span class="sxs-lookup"><span data-stu-id="1eddf-121">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="1eddf-122">Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="1eddf-122">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="1eddf-123">Inne obsługiwane wartości to `Framework40`, `Framework45`, `FrameworkCore10`i `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="1eddf-123">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--Parallel`**

  <span data-ttu-id="1eddf-124">Uruchom testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="1eddf-124">Run tests in parallel.</span></span> <span data-ttu-id="1eddf-125">Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="1eddf-125">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="1eddf-126">Określ jawną liczbę rdzeni przez ustawienie właściwości `MaxCpuCount` w węźle `RunConfiguration` w pliku *runsettings* .</span><span class="sxs-lookup"><span data-stu-id="1eddf-126">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--TestCaseFilter <Expression>`**

  <span data-ttu-id="1eddf-127">Uruchom testy zgodne z podanym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="1eddf-127">Run tests that match the given expression.</span></span> <span data-ttu-id="1eddf-128">`<Expression>` ma format `<property>Operator<value>[|&<Expression>]`, gdzie operator jest jednym z `=`, `!=`lub `~`.</span><span class="sxs-lookup"><span data-stu-id="1eddf-128">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="1eddf-129">`~` operatora ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="1eddf-129">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="1eddf-130">`()` nawiasów są używane do grupowania podwyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1eddf-130">Parenthesis `()` are used to group subexpressions.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="1eddf-131">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="1eddf-131">Prints out a short help for the command.</span></span>

- **`--logger <Logger Uri/FriendlyName>`**

  <span data-ttu-id="1eddf-132">Określ Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="1eddf-132">Specify a logger for test results.</span></span>

  - <span data-ttu-id="1eddf-133">Aby opublikować wyniki testów w Team Foundation Server, użyj dostawcy rejestratora `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="1eddf-133">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="1eddf-134">Aby zarejestrować wyniki do pliku Wyniki testów programu Visual Studio (TRX), użyj dostawcy rejestratora `trx`.</span><span class="sxs-lookup"><span data-stu-id="1eddf-134">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="1eddf-135">Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="1eddf-135">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="1eddf-136">Jeśli nie podano `LogFileName`, zostanie utworzona unikatowa nazwa pliku do przechowywania wyników testu.</span><span class="sxs-lookup"><span data-stu-id="1eddf-136">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  <span data-ttu-id="1eddf-137">Wyświetla wszystkie odnalezione testy z danego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="1eddf-137">Lists all discovered tests from the given test container.</span></span>

- **`--ParentProcessId <ParentProcessId>`**

  <span data-ttu-id="1eddf-138">Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="1eddf-138">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Port <Port>`**

  <span data-ttu-id="1eddf-139">Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="1eddf-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--Diag <Path to log file>`**

  <span data-ttu-id="1eddf-140">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="1eddf-140">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="1eddf-141">Dzienniki są zapisywane do podanego pliku.</span><span class="sxs-lookup"><span data-stu-id="1eddf-141">Logs are written to the provided file.</span></span>

- **`--Blame`**

  <span data-ttu-id="1eddf-142">Uruchamia testy w trybie polecenia Blame.</span><span class="sxs-lookup"><span data-stu-id="1eddf-142">Runs the tests in blame mode.</span></span> <span data-ttu-id="1eddf-143">Ta opcja jest pomocna w odizolowaniu problematycznych testów powodujących awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="1eddf-143">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="1eddf-144">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="1eddf-144">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="1eddf-145">Uruchamia testy w procesie izolowanym.</span><span class="sxs-lookup"><span data-stu-id="1eddf-145">Runs the tests in an isolated process.</span></span> <span data-ttu-id="1eddf-146">Powoduje to, że proces *VSTest. Console. exe* jest mniej prawdopodobnie zatrzymany w przypadku błędu w testach, ale testy mogą działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="1eddf-146">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`@<file>`**

  <span data-ttu-id="1eddf-147">Odczytuje plik odpowiedzi w celu uzyskania dodatkowych opcji.</span><span class="sxs-lookup"><span data-stu-id="1eddf-147">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="1eddf-148">Określa dodatkowe argumenty do przekazania do adaptera.</span><span class="sxs-lookup"><span data-stu-id="1eddf-148">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="1eddf-149">Argumenty są określane jako pary nazwa-wartość w formularzu `<n>=<v>`, gdzie `<n>` jest nazwą argumentu, a `<v>` to wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="1eddf-149">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="1eddf-150">Użyj spacji, aby rozdzielić wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="1eddf-150">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="1eddf-151">Przykłady</span><span class="sxs-lookup"><span data-stu-id="1eddf-151">Examples</span></span>

<span data-ttu-id="1eddf-152">Uruchom testy w *mytestproject. dll*:</span><span class="sxs-lookup"><span data-stu-id="1eddf-152">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="1eddf-153">Uruchom testy w *mytestproject. dll*, eksportując do folderu niestandardowego z nazwą niestandardową:</span><span class="sxs-lookup"><span data-stu-id="1eddf-153">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="1eddf-154">Uruchom testy w *mytestproject. dll* i *myothertestproject. exe*:</span><span class="sxs-lookup"><span data-stu-id="1eddf-154">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="1eddf-155">Uruchom testy `TestMethod1`:</span><span class="sxs-lookup"><span data-stu-id="1eddf-155">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="1eddf-156">Uruchom testy `TestMethod1` i `TestMethod2`:</span><span class="sxs-lookup"><span data-stu-id="1eddf-156">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
