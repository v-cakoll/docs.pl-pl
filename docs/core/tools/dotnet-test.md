---
title: polecenie test DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 6102281c4daf149f31e65ef8360831fe9e0ef4f6
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="dotnet-test"></a><span data-ttu-id="a2fe9-103">DotNet test</span><span class="sxs-lookup"><span data-stu-id="a2fe9-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a2fe9-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a2fe9-104">Name</span></span>

<span data-ttu-id="a2fe9-105">`dotnet test` — .NET testowanie sterowników używane do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a2fe9-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a2fe9-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a2fe9-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="a2fe9-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a2fe9-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a2fe9-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="a2fe9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a2fe9-109">Description</span></span>

<span data-ttu-id="a2fe9-110">`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="a2fe9-111">`dotnet test` Polecenie uruchamia aplikację konsoli test runner określony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-111">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="a2fe9-112">Moduł uruchamiający wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raporty powodzenie lub niepowodzenie każdego z testów.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-112">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="a2fe9-113">Moduł uruchamiający Biblioteka testów jednostkowych są dostarczane w pakietach NuGet i zostaną przywrócone jako zwykłej zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="a2fe9-114">Projekty testowe Określ uruchamiający przy użyciu zwykłego `<PackageReference>` element, taki jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="a2fe9-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="a2fe9-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a2fe9-115">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a2fe9-116">Określa ścieżkę do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-116">Specifies a path to the test project.</span></span> <span data-ttu-id="a2fe9-117">W przypadku jego pominięcia domyślnie bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-117">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="a2fe9-118">Opcje</span><span class="sxs-lookup"><span data-stu-id="a2fe9-118">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a2fe9-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="a2fe9-119">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="a2fe9-120">Używa niestandardowych adapterów testowych z określonej ścieżki w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-120">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a2fe9-121">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-121">Defines the build configuration.</span></span> <span data-ttu-id="a2fe9-122">Wartość domyślna to `Debug`, ale konfiguracja projektu można zastąpić to ustawienie domyślne zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-122">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="a2fe9-123">Włącza moduł zbierający dane dla uruchomienia testu.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-123">Enables data collector for the test run.</span></span> <span data-ttu-id="a2fe9-124">Aby uzyskać więcej informacji, zobacz [monitora i analizować uruchomienia testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="a2fe9-124">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="a2fe9-125">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-125">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a2fe9-126">Wyszukuje pliki binarne testów dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a2fe9-126">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="a2fe9-127">Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-127">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="a2fe9-128">Aby uzyskać więcej informacji, zobacz [opcję Szczegóły filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-128">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="a2fe9-129">Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów selektywnego jednostki, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="a2fe9-129">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="a2fe9-130">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-130">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="a2fe9-131">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-131">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="a2fe9-132">Nie kompilacji projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-132">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="a2fe9-133">Nie wykonać przywracanie niejawne, podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-133">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a2fe9-134">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-134">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="a2fe9-135">Katalog, w której będzie można umieścić wyników testu.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-135">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="a2fe9-136">Określony katalog zostanie utworzony, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-136">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="a2fe9-137">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-137">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="a2fe9-138">Lista wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-138">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a2fe9-139">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-139">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a2fe9-140">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-140">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a2fe9-141">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a2fe9-141">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="a2fe9-142">Używa niestandardowych adapterów testowych z określonej ścieżki w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-142">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a2fe9-143">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-143">Defines the build configuration.</span></span> <span data-ttu-id="a2fe9-144">Wartość domyślna to `Debug`, ale konfiguracja projektu można zastąpić to ustawienie domyślne zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-144">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="a2fe9-145">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-145">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a2fe9-146">Wyszukuje pliki binarne testów dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a2fe9-146">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="a2fe9-147">Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="a2fe9-148">Aby uzyskać więcej informacji, zobacz [opcję Szczegóły filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="a2fe9-149">Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów selektywnego jednostki, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="a2fe9-149">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="a2fe9-150">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-150">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="a2fe9-151">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-151">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="a2fe9-152">Nie kompilacji projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-152">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a2fe9-153">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-153">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="a2fe9-154">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-154">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="a2fe9-155">Lista wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-155">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a2fe9-156">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a2fe9-157">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="a2fe9-158">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a2fe9-158">Examples</span></span>

<span data-ttu-id="a2fe9-159">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="a2fe9-159">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="a2fe9-160">Uruchom testy `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="a2fe9-160">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="a2fe9-161">Szczegóły opcji filtru</span><span class="sxs-lookup"><span data-stu-id="a2fe9-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="a2fe9-162">`<Expression>` ma format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="a2fe9-163">`<property>` atrybut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="a2fe9-164">Właściwości obsługiwanych przez platform testów jednostkowych popularnych są następujące:</span><span class="sxs-lookup"><span data-stu-id="a2fe9-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="a2fe9-165">Struktury testowej</span><span class="sxs-lookup"><span data-stu-id="a2fe9-165">Test Framework</span></span> | <span data-ttu-id="a2fe9-166">Obsługiwanych właściwości</span><span class="sxs-lookup"><span data-stu-id="a2fe9-166">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="a2fe9-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="a2fe9-167">MSTest</span></span>         | <ul><li><span data-ttu-id="a2fe9-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="a2fe9-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="a2fe9-169">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a2fe9-169">Name</span></span></li><li><span data-ttu-id="a2fe9-170">className</span><span class="sxs-lookup"><span data-stu-id="a2fe9-170">ClassName</span></span></li><li><span data-ttu-id="a2fe9-171">Priorytet</span><span class="sxs-lookup"><span data-stu-id="a2fe9-171">Priority</span></span></li><li><span data-ttu-id="a2fe9-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="a2fe9-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="a2fe9-173">Xunit</span><span class="sxs-lookup"><span data-stu-id="a2fe9-173">Xunit</span></span>          | <ul><li><span data-ttu-id="a2fe9-174">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="a2fe9-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="a2fe9-175">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="a2fe9-175">DisplayName</span></span></li><li><span data-ttu-id="a2fe9-176">Cechy</span><span class="sxs-lookup"><span data-stu-id="a2fe9-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="a2fe9-177">`<operator>` Opisuje relację między właściwości i wartość:</span><span class="sxs-lookup"><span data-stu-id="a2fe9-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="a2fe9-178">Operator</span><span class="sxs-lookup"><span data-stu-id="a2fe9-178">Operator</span></span> | <span data-ttu-id="a2fe9-179">Funkcja</span><span class="sxs-lookup"><span data-stu-id="a2fe9-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="a2fe9-180">Dokładnego dopasowania</span><span class="sxs-lookup"><span data-stu-id="a2fe9-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="a2fe9-181">Nie dokładnego dopasowania</span><span class="sxs-lookup"><span data-stu-id="a2fe9-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="a2fe9-182">Zawiera</span><span class="sxs-lookup"><span data-stu-id="a2fe9-182">Contains</span></span>        |

<span data-ttu-id="a2fe9-183">`<value>` jest to ciąg.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-183">`<value>` is a string.</span></span> <span data-ttu-id="a2fe9-184">Wszystkie wyszukiwania są bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="a2fe9-184">All the lookups are case insensitive.</span></span>

<span data-ttu-id="a2fe9-185">Wyrażenia bez `<operator>` jest automatycznie traktowane jako `contains` na `FullyQualifiedName` właściwości (na przykład `dotnet test --filter xyz` jest taka sama jak `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="a2fe9-185">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="a2fe9-186">Może być częścią wyrażenia z operatorami warunkowego:</span><span class="sxs-lookup"><span data-stu-id="a2fe9-186">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="a2fe9-187">Operator</span><span class="sxs-lookup"><span data-stu-id="a2fe9-187">Operator</span></span> | <span data-ttu-id="a2fe9-188">Funkcja</span><span class="sxs-lookup"><span data-stu-id="a2fe9-188">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="a2fe9-189">LUB</span><span class="sxs-lookup"><span data-stu-id="a2fe9-189">OR</span></span>       |
| `&`      | <span data-ttu-id="a2fe9-190">AND</span><span class="sxs-lookup"><span data-stu-id="a2fe9-190">AND</span></span>      |

<span data-ttu-id="a2fe9-191">Może być częścią wyrażenia w nawiasach przy użyciu operatorów warunkowych (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="a2fe9-191">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="a2fe9-192">Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów selektywnego jednostki, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="a2fe9-192">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a2fe9-193">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2fe9-193">See also</span></span>

 [<span data-ttu-id="a2fe9-194">Struktury i cele</span><span class="sxs-lookup"><span data-stu-id="a2fe9-194">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
 [<span data-ttu-id="a2fe9-195">Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="a2fe9-195">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
