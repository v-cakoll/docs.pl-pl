---
title: Testowanie jednostkowe kodu C# w .NET Core przy użyciu testu dotnet i xUnit
description: Poznaj pojęcia dotyczące testów jednostkowych w językach C# i .NET Core, korzystając z interakcyjnego środowiska, które krok po kroku przy użyciu testu dotnet i xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9e3d63a2cf4f560591459833340b729ffec1b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240899"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="daed5-103">Testowanie jednostkowe C# w .NET Core przy użyciu testu dotnet i xUnit</span><span class="sxs-lookup"><span data-stu-id="daed5-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="daed5-104">W tym samouczku pokazano, jak utworzyć rozwiązanie zawierające projekt testu jednostkowego i projekt kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="daed5-104">This tutorial shows how to build a solution containing a unit test project and source code project.</span></span> <span data-ttu-id="daed5-105">Aby postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span><span class="sxs-lookup"><span data-stu-id="daed5-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="daed5-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="daed5-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="daed5-107">Tworzenie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="daed5-107">Create the solution</span></span>

<span data-ttu-id="daed5-108">W tej sekcji tworzone jest rozwiązanie zawierające projekty źródłowe i testowe.</span><span class="sxs-lookup"><span data-stu-id="daed5-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="daed5-109">Ukończone rozwiązanie ma następującą strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="daed5-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

<span data-ttu-id="daed5-110">Poniższe instrukcje zawierają kroki, aby utworzyć rozwiązanie testowe.</span><span class="sxs-lookup"><span data-stu-id="daed5-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="daed5-111">Zobacz [Polecenia, aby utworzyć rozwiązanie testowe,](#create-test-cmd) aby uzyskać instrukcje dotyczące tworzenia rozwiązania testowego w jednym kroku.</span><span class="sxs-lookup"><span data-stu-id="daed5-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="daed5-112">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="daed5-112">Open a shell window.</span></span>
* <span data-ttu-id="daed5-113">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="daed5-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="daed5-114">Polecenie [`dotnet new sln`](../tools/dotnet-new.md) tworzy nowe rozwiązanie w katalogu *testów jednostkowych z używających dotnet-testów.*</span><span class="sxs-lookup"><span data-stu-id="daed5-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="daed5-115">Zmień katalog na folder *testów jednostkowych z wykorzystaniem dotnet-test.*</span><span class="sxs-lookup"><span data-stu-id="daed5-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="daed5-116">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="daed5-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   <span data-ttu-id="daed5-117">Polecenie [`dotnet new classlib`](../tools/dotnet-new.md) tworzy nowy projekt biblioteki klas w folderze *PrimeService.*</span><span class="sxs-lookup"><span data-stu-id="daed5-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="daed5-118">Nowa biblioteka klas będzie zawierać kod, który ma zostać przetestowany.</span><span class="sxs-lookup"><span data-stu-id="daed5-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="daed5-119">Zmień nazwę *Class1.cs* na *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="daed5-119">Rename *Class1.cs* to *PrimeService.cs*.</span></span>
* <span data-ttu-id="daed5-120">Zamień kod w *PrimeService.cs* na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="daed5-120">Replace the code in *PrimeService.cs* with the following code:</span></span>
  
  ```csharp
    using System;

    namespace Prime.Services
    {
        public class PrimeService
        {
            public bool IsPrime(int candidate)
            {
                throw new NotImplementedException("Not implemented.");
            }
        }
    }
  ```

* <span data-ttu-id="daed5-121">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="daed5-121">The preceding code:</span></span>
  * <span data-ttu-id="daed5-122">Zgłasza wiadomość <xref:System.NotImplementedException> z informacją, że nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="daed5-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="daed5-123">Jest aktualizowany w dalszej części samouczka.</span><span class="sxs-lookup"><span data-stu-id="daed5-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="daed5-124">W katalogu *testów jednostkowych z używając dotnet-test* uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="daed5-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* <span data-ttu-id="daed5-125">Utwórz projekt *PrimeService.Tests,* uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="daed5-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="daed5-126">Poprzednie polecenie:</span><span class="sxs-lookup"><span data-stu-id="daed5-126">The preceding command:</span></span>
  * <span data-ttu-id="daed5-127">Tworzy *PrimeService.Tests* projektu w katalogu *PrimeService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="daed5-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="daed5-128">Projekt testowy używa [xUnit](https://xunit.github.io/) jako biblioteki testowej.</span><span class="sxs-lookup"><span data-stu-id="daed5-128">The test project uses [xUnit](https://xunit.github.io/) as the test library.</span></span>
  * <span data-ttu-id="daed5-129">Konfiguruje program testowy, `<PackageReference />`dodając następujące elementy do pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="daed5-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="daed5-130">"Microsoft.NET.Test.Sdk"</span><span class="sxs-lookup"><span data-stu-id="daed5-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="daed5-131">"xunit"</span><span class="sxs-lookup"><span data-stu-id="daed5-131">"xunit"</span></span>
    * <span data-ttu-id="daed5-132">"xunit.runner.visualstudio"</span><span class="sxs-lookup"><span data-stu-id="daed5-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="daed5-133">Dodaj projekt testowy do pliku rozwiązania, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="daed5-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* <span data-ttu-id="daed5-134">Dodaj `PrimeService` bibliotekę klas jako zależność do *primeservice.tests* projektu:</span><span class="sxs-lookup"><span data-stu-id="daed5-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="daed5-135">Polecenia służące do tworzenia rozwiązania</span><span class="sxs-lookup"><span data-stu-id="daed5-135">Commands to create the solution</span></span>

<span data-ttu-id="daed5-136">W tej sekcji podsumowano wszystkie polecenia w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="daed5-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="daed5-137">Pomiń tę sekcję, jeśli wykonanie kroków w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="daed5-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="daed5-138">Następujące polecenia utworzyć rozwiązanie testowe na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="daed5-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="daed5-139">W przypadku systemów macOS `ren` i Unix zaktualizuj polecenie do wersji systemu operacyjnego, `ren` aby zmienić nazwę pliku:</span><span class="sxs-lookup"><span data-stu-id="daed5-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

<span data-ttu-id="daed5-140">Postępuj zgodnie z instrukcjami "Zamień kod w *PrimeService.cs* na następujący kod" w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="daed5-140">Follow the instructions for "Replace the code in *PrimeService.cs* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="daed5-141">Tworzenie testu</span><span class="sxs-lookup"><span data-stu-id="daed5-141">Create a test</span></span>

<span data-ttu-id="daed5-142">Popularnym podejściem w rozwoju opartym na testach (TDD) jest napisanie testu przed wdrożeniem kodu docelowego.</span><span class="sxs-lookup"><span data-stu-id="daed5-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="daed5-143">Ten samouczek używa podejścia TDD.</span><span class="sxs-lookup"><span data-stu-id="daed5-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="daed5-144">Metoda `IsPrime` jest wywoływana, ale nie zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="daed5-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="daed5-145">Wywołanie testowe `IsPrime` nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="daed5-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="daed5-146">Z TDD test jest zapisywany, który jest znany nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="daed5-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="daed5-147">Kod docelowy jest aktualizowany, aby test przeszedł.</span><span class="sxs-lookup"><span data-stu-id="daed5-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="daed5-148">Powtarzasz to podejście, zapisując test niepowysady, a następnie aktualizujesz kod docelowy do przekazania.</span><span class="sxs-lookup"><span data-stu-id="daed5-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="daed5-149">Zaktualizuj projekt *PrimeService.Tests:*</span><span class="sxs-lookup"><span data-stu-id="daed5-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="daed5-150">Usuń *PrimeService.Tests/UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="daed5-150">Delete *PrimeService.Tests/UnitTest1.cs*.</span></span>
* <span data-ttu-id="daed5-151">Utwórz plik *PrimeService.Tests/PrimeService_IsPrimeShould.cs.*</span><span class="sxs-lookup"><span data-stu-id="daed5-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.cs*  file.</span></span>
* <span data-ttu-id="daed5-152">Zamień kod w *PrimeService_IsPrimeShould.cs* na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="daed5-152">Replace the code in *PrimeService_IsPrimeShould.cs* with the following code:</span></span>

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="daed5-153">Atrybut `[Fact]` deklaruje metodę testową, która jest uruchamiana przez test runner.</span><span class="sxs-lookup"><span data-stu-id="daed5-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="daed5-154">Z *primeservice.tests* folderu `dotnet test`uruchom .</span><span class="sxs-lookup"><span data-stu-id="daed5-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="daed5-155">Polecenie [testu dotnet](../tools/dotnet-test.md) tworzy zarówno projekty, jak i uruchamia testy.</span><span class="sxs-lookup"><span data-stu-id="daed5-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="daed5-156">Program testowy xUnit zawiera punkt wejścia programu do uruchomienia testów.</span><span class="sxs-lookup"><span data-stu-id="daed5-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="daed5-157">`dotnet test`uruchamia testowiec za pomocą projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="daed5-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="daed5-158">Test nie `IsPrime` powiedzie się, ponieważ nie został zaimplementowany.</span><span class="sxs-lookup"><span data-stu-id="daed5-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="daed5-159">Przy użyciu podejścia TDD, napisać tylko tyle kodu, aby ten test przebiega.</span><span class="sxs-lookup"><span data-stu-id="daed5-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="daed5-160">Zaktualizuj `IsPrime` za pomocą następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="daed5-160">Update `IsPrime` with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="daed5-161">Uruchom polecenie `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="daed5-161">Run `dotnet test`.</span></span> <span data-ttu-id="daed5-162">Test przebiega pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="daed5-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="daed5-163">Dodaj więcej testów</span><span class="sxs-lookup"><span data-stu-id="daed5-163">Add more tests</span></span>

<span data-ttu-id="daed5-164">Dodaj testy liczb pierwszych dla 0 i -1.</span><span class="sxs-lookup"><span data-stu-id="daed5-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="daed5-165">Można skopiować poprzedni test i zmienić następujący kod, aby użyć 0 i -1:</span><span class="sxs-lookup"><span data-stu-id="daed5-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

<span data-ttu-id="daed5-166">Kopiowanie kodu testu, gdy tylko parametr zmienia wyniki w duplikacji kodu i bloat test.</span><span class="sxs-lookup"><span data-stu-id="daed5-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="daed5-167">Następujące atrybuty xUnit umożliwiają zapisywanie zestawu podobnych testów:</span><span class="sxs-lookup"><span data-stu-id="daed5-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="daed5-168">`[Theory]`reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="daed5-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="daed5-169">`[InlineData]`atrybut określa wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="daed5-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="daed5-170">Zamiast tworzyć nowe testy, należy zastosować poprzednie atrybuty xUnit, aby utworzyć jedną teorię.</span><span class="sxs-lookup"><span data-stu-id="daed5-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="daed5-171">Zamień następujący kod:</span><span class="sxs-lookup"><span data-stu-id="daed5-171">Replace the following code:</span></span>

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

<span data-ttu-id="daed5-172">z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="daed5-172">with the following code:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="daed5-173">W poprzednim kodzie `[Theory]` `[InlineData]` i włączyć testowanie kilku wartości mniej niż dwa.</span><span class="sxs-lookup"><span data-stu-id="daed5-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="daed5-174">Dwa to najmniejsza liczba pierwsza.</span><span class="sxs-lookup"><span data-stu-id="daed5-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="daed5-175">Uruchom `dotnet test`, dwa testy nie powiodły się.</span><span class="sxs-lookup"><span data-stu-id="daed5-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="daed5-176">Aby wszystkie testy zostały zdatnięte, zaktualizuj `IsPrime` metodę za pomocą następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="daed5-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="daed5-177">Zgodnie z podejściem TDD, dodaj więcej testów nieudanych, a następnie zaktualizuj kod docelowy.</span><span class="sxs-lookup"><span data-stu-id="daed5-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="daed5-178">Zobacz [gotową wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="daed5-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="daed5-179">Ukończona `IsPrime` metoda nie jest wydajnym algorytmem testowania pierwotności.</span><span class="sxs-lookup"><span data-stu-id="daed5-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="daed5-180">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="daed5-180">Additional resources</span></span>

- [<span data-ttu-id="daed5-181">xUnit.net oficjalna strona</span><span class="sxs-lookup"><span data-stu-id="daed5-181">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="daed5-182">Testowanie logiki kontrolera w ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="daed5-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
