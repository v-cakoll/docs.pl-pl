---
title: dotnet vstest, polecenie
description: Polecenie dotnet vstest tworzy projekt i wszystkie jego zależności.
ms.date: 02/27/2020
ms.openlocfilehash: 4941a6d08d45953039eb406a30f0ff984128ba1c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389629"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="56c2c-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="56c2c-103">dotnet vstest</span></span>

<span data-ttu-id="56c2c-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="56c2c-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="56c2c-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="56c2c-105">Name</span></span>

<span data-ttu-id="56c2c-106">`dotnet-vstest`- Uruchamia testy z określonych plików.</span><span class="sxs-lookup"><span data-stu-id="56c2c-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="56c2c-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="56c2c-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag]
    [--Framework] [--InIsolation] [-lt|--ListTests] [--logger]
    [--Parallel] [--ParentProcessId] [--Platform] [--Port]
    [--ResultsDirectory] [--Settings] [--TestAdapterPath]
    [--TestCaseFilter] [--Tests] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a><span data-ttu-id="56c2c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="56c2c-108">Description</span></span>

<span data-ttu-id="56c2c-109">Polecenie `dotnet-vstest` uruchamia `VSTest.Console` aplikację wiersza polecenia w celu uruchomienia automatycznych testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="56c2c-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="56c2c-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="56c2c-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="56c2c-111">Uruchom testy z określonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="56c2c-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="56c2c-112">Oddziel wiele nazw zestawów testowych spacjami.</span><span class="sxs-lookup"><span data-stu-id="56c2c-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="56c2c-113">Obsługiwane są symbole wieloznaczne.</span><span class="sxs-lookup"><span data-stu-id="56c2c-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="56c2c-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="56c2c-114">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="56c2c-115">Uruchamia testy w trybie winy.</span><span class="sxs-lookup"><span data-stu-id="56c2c-115">Runs the tests in blame mode.</span></span> <span data-ttu-id="56c2c-116">Ta opcja jest przydatna w izolowaniu problematycznych testów powodujących awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="56c2c-116">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="56c2c-117">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml,* który przechwytuje kolejność wykonywania testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="56c2c-117">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <Path to log file>`**

  <span data-ttu-id="56c2c-118">Włącza pełne dzienniki dla platformy testowej.</span><span class="sxs-lookup"><span data-stu-id="56c2c-118">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="56c2c-119">Dzienniki są zapisywane w podanym pliku.</span><span class="sxs-lookup"><span data-stu-id="56c2c-119">Logs are written to the provided file.</span></span>

- **`--Framework <Framework Version>`**

  <span data-ttu-id="56c2c-120">Docelowa wersja programu .NET Framework używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="56c2c-120">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="56c2c-121">Przykładami prawidłowych `.NETFramework,Version=v4.6` wartości `.NETCoreApp,Version=v1.0`są lub .</span><span class="sxs-lookup"><span data-stu-id="56c2c-121">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="56c2c-122">Inne obsługiwane wartości `Framework40` `Framework45`to `FrameworkCore10`, `FrameworkUap10`, i .</span><span class="sxs-lookup"><span data-stu-id="56c2c-122">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="56c2c-123">Uruchamia testy w procesie izolowanym.</span><span class="sxs-lookup"><span data-stu-id="56c2c-123">Runs the tests in an isolated process.</span></span> <span data-ttu-id="56c2c-124">To sprawia, że proces *vstest.console.exe* jest mniej prawdopodobne, aby zatrzymać się na błąd w testach, ale testy mogą działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="56c2c-124">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <File Name>`**

  <span data-ttu-id="56c2c-125">Wyświetla listę wszystkich wykrytych testów z danego kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="56c2c-125">Lists all discovered tests from the given test container.</span></span>

- **`--logger <Logger Uri/FriendlyName>`**

  <span data-ttu-id="56c2c-126">Określ rejestrator dla wyników testów.</span><span class="sxs-lookup"><span data-stu-id="56c2c-126">Specify a logger for test results.</span></span>

  - <span data-ttu-id="56c2c-127">Aby opublikować wyniki testów na `TfsPublisher` serwerze Team Foundation Server, użyj dostawcy rejestratora:</span><span class="sxs-lookup"><span data-stu-id="56c2c-127">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="56c2c-128">Aby rejestrować wyniki w pliku wyników testów programu `trx` Visual Studio (TRX), należy użyć dostawcy rejestratora.</span><span class="sxs-lookup"><span data-stu-id="56c2c-128">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="56c2c-129">Ten przełącznik tworzy plik w katalogu wyników testów o podanej nazwie pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="56c2c-129">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="56c2c-130">Jeśli `LogFileName` nie podano, zostanie utworzona unikatowa nazwa pliku w celu przechowywania wyników testów.</span><span class="sxs-lookup"><span data-stu-id="56c2c-130">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="56c2c-131">Uruchom testy równolegle.</span><span class="sxs-lookup"><span data-stu-id="56c2c-131">Run tests in parallel.</span></span> <span data-ttu-id="56c2c-132">Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="56c2c-132">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="56c2c-133">Określ jawną liczbę rdzeni, `MaxCpuCount` ustawiając `RunConfiguration` właściwość pod węzłem w pliku *runsettings.*</span><span class="sxs-lookup"><span data-stu-id="56c2c-133">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <ParentProcessId>`**

  <span data-ttu-id="56c2c-134">Identyfikator procesu nadrzędnego odpowiedzialnego za uruchomienie bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="56c2c-134">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <Platform type>`**

  <span data-ttu-id="56c2c-135">Architektura platformy docelowej używana do wykonywania testów.</span><span class="sxs-lookup"><span data-stu-id="56c2c-135">Target platform architecture used for test execution.</span></span> <span data-ttu-id="56c2c-136">Prawidłowe `x86`wartości `x64`to `ARM`, i .</span><span class="sxs-lookup"><span data-stu-id="56c2c-136">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <Port>`**

  <span data-ttu-id="56c2c-137">Określa port połączenia gniazda i odbieranie komunikatów o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="56c2c-137">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PathToResulsDirectory>`**

  <span data-ttu-id="56c2c-138">Katalog wyników testów zostanie utworzony w określonej ścieżce, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="56c2c-138">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <Settings File>`**

  <span data-ttu-id="56c2c-139">Ustawienia, które mają być używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="56c2c-139">Settings to use when running tests.</span></span>

- **`--TestAdapterPath`**

  <span data-ttu-id="56c2c-140">Użyj niestandardowych kart testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="56c2c-140">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <Expression>`**

  <span data-ttu-id="56c2c-141">Uruchom testy, które pasują do danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="56c2c-141">Run tests that match the given expression.</span></span> <span data-ttu-id="56c2c-142">`<Expression>`ma format, `<property>Operator<value>[|&<Expression>]`w którym Operator `=` `!=`jest `~`jednym z , lub .</span><span class="sxs-lookup"><span data-stu-id="56c2c-142">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="56c2c-143">Operator `~` ma "zawiera" semantykę i ma `DisplayName`zastosowanie do właściwości ciągu, takich jak .</span><span class="sxs-lookup"><span data-stu-id="56c2c-143">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="56c2c-144">Nawiasy `()` są używane do grupowanie podwyrażenia.</span><span class="sxs-lookup"><span data-stu-id="56c2c-144">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="56c2c-145">Aby uzyskać więcej informacji, zobacz [Filtr Skrzynia testowa](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="56c2c-145">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <Test Names>`**

  <span data-ttu-id="56c2c-146">Uruchom testy z nazwami, które odpowiadają podanym wartościom.</span><span class="sxs-lookup"><span data-stu-id="56c2c-146">Run tests with names that match the provided values.</span></span> <span data-ttu-id="56c2c-147">Oddziel wiele wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="56c2c-147">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="56c2c-148">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="56c2c-148">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="56c2c-149">Odczytuje plik odpowiedzi, aby uzyskać więcej opcji.</span><span class="sxs-lookup"><span data-stu-id="56c2c-149">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="56c2c-150">Określa dodatkowe argumenty, które mają być przerzucene do karty.</span><span class="sxs-lookup"><span data-stu-id="56c2c-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="56c2c-151">Argumenty są określane jako pary nazwa-wartość `<n>=<v>` `<n>` formularza , gdzie `<v>` jest nazwą argumentu i jest wartością argumentu.</span><span class="sxs-lookup"><span data-stu-id="56c2c-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="56c2c-152">Użyj spacji, aby oddzielić wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="56c2c-152">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="56c2c-153">Przykłady</span><span class="sxs-lookup"><span data-stu-id="56c2c-153">Examples</span></span>

<span data-ttu-id="56c2c-154">Uruchom testy w *mytestproject.dll*:</span><span class="sxs-lookup"><span data-stu-id="56c2c-154">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="56c2c-155">Uruchom testy w *pliku mytestproject.dll*, eksportując do folderu niestandardowego o niestandardowej nazwie:</span><span class="sxs-lookup"><span data-stu-id="56c2c-155">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="56c2c-156">Uruchom testy w *mytestproject.dll* i *myothertestproject.exe*:</span><span class="sxs-lookup"><span data-stu-id="56c2c-156">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="56c2c-157">Uruchom `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="56c2c-157">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="56c2c-158">`TestMethod1` Uruchamianie `TestMethod2` i testy:</span><span class="sxs-lookup"><span data-stu-id="56c2c-158">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="56c2c-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56c2c-159">See also</span></span>

- [<span data-ttu-id="56c2c-160">Opcje wiersza poleceń narzędzia VSTest.Console.exe</span><span class="sxs-lookup"><span data-stu-id="56c2c-160">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
