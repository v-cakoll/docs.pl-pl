---
title: Testowanie jednostek kodu języka C# w .NET Core za pomocą polecenia dotnet test i struktury xUnit
description: Pojęcia dotyczące jednostek testów w języku C# i .NET Core za pomocą interaktywnych doświadczenia przykładowe rozwiązanie krok po kroku za pomocą polecenia dotnet test i struktury xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 556da93d6237836dc32fc3f6715909593907ba74
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738737"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="40dd6-103">Testowanie jednostek języka C# w .NET Core za pomocą polecenia dotnet test i struktury xUnit</span><span class="sxs-lookup"><span data-stu-id="40dd6-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="40dd6-104">Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="40dd6-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="40dd6-105">Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) przed przystąpieniem do wykonywania.</span><span class="sxs-lookup"><span data-stu-id="40dd6-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="40dd6-106">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="40dd6-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="40dd6-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="40dd6-107">Creating the source project</span></span>

<span data-ttu-id="40dd6-108">Otwieranie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="40dd6-108">Open a shell window.</span></span> <span data-ttu-id="40dd6-109">Utwórz katalog o nazwie *testowania — przy użyciu dotnet-test jednostkowy* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="40dd6-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="40dd6-110">Wewnątrz tego nowy katalog uruchamiania [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="40dd6-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="40dd6-111">Rozwiązanie ułatwia zarządzanie zarówno biblioteki klas, jak i projekt testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="40dd6-111">Having a solution makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="40dd6-112">Utwórz katalog rozwiązania *PrimeService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="40dd6-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="40dd6-113">Struktura katalogów i plików pory powinna być następująca:</span><span class="sxs-lookup"><span data-stu-id="40dd6-113">The directory and file structure thus far should be as follows:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="40dd6-114">Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib` ](../tools/dotnet-new.md) do utworzenia projektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="40dd6-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="40dd6-115">Zmień nazwę *Class1.cs* do *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="40dd6-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="40dd6-116">Aby korzystać z projektowania opartego na testach (TDD), należy najpierw utworzyć niepowodzenie wykonania `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="40dd6-116">To use test-driven development (TDD), you first create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first");
        }
    }
}
```

<span data-ttu-id="40dd6-117">Zmień katalog kopii do *testowania — przy użyciu dotnet-test jednostkowy* katalogu.</span><span class="sxs-lookup"><span data-stu-id="40dd6-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span>

<span data-ttu-id="40dd6-118">Uruchom [dotnet sln](../tools/dotnet-sln.md) polecenie, aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="40dd6-118">Run the [dotnet sln](../tools/dotnet-sln.md) command to add the class library project to the solution:</span></span>

```
dotnet sln add .\PrimeService\PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="40dd6-119">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="40dd6-119">Creating the test project</span></span>

<span data-ttu-id="40dd6-120">Następnie należy utworzyć *PrimeService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="40dd6-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="40dd6-121">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="40dd6-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="40dd6-122">Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new xunit` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="40dd6-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="40dd6-123">To polecenie umożliwia utworzenie projektu testowego, który używa [xUnit](https://xunit.github.io/) jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="40dd6-123">This command creates a test project that uses [xUnit](https://xunit.github.io/) as the test library.</span></span> <span data-ttu-id="40dd6-124">Wygenerowany szablon konfiguruje narzędzie test runner w *PrimeServiceTests.csproj* pliku podobny do następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="40dd6-124">The generated template configures the test runner in the *PrimeServiceTests.csproj* file similar to the following code:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="40dd6-125">Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="40dd6-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="40dd6-126">`dotnet new` w poprzednim kroku dodawany xUnit, a moduł uruchamiający testy xUnit.</span><span class="sxs-lookup"><span data-stu-id="40dd6-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="40dd6-127">Teraz Dodaj `PrimeService` biblioteki klas jako inny zależności do projektu.</span><span class="sxs-lookup"><span data-stu-id="40dd6-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="40dd6-128">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="40dd6-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="40dd6-129">Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="40dd6-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="40dd6-130">Na poniższym obrazie przedstawiono układ ostateczne rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="40dd6-130">The following shows the final solution layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="40dd6-131">Aby dodać projekt testu w rozwiązaniu, uruchom [dotnet sln](../tools/dotnet-sln.md) polecenia w pliku *testowania — przy użyciu dotnet-test jednostkowy* katalogu:</span><span class="sxs-lookup"><span data-stu-id="40dd6-131">To add the test project to the solution, run the [dotnet sln](../tools/dotnet-sln.md) command in the *unit-testing-using-dotnet-test* directory:</span></span>

```
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="40dd6-132">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="40dd6-132">Creating the first test</span></span>

<span data-ttu-id="40dd6-133">Podejścia TDD wymaga zapisywania niepowodzenie jednego testu, dzięki czemu przekazać, a następnie powtórzyć ten proces.</span><span class="sxs-lookup"><span data-stu-id="40dd6-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="40dd6-134">Usuń *UnitTest1.cs* z *PrimeService.Tests* katalogu i Utwórz nowy C# plik o nazwie *PrimeService_IsPrimeShould.cs*.</span><span class="sxs-lookup"><span data-stu-id="40dd6-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="40dd6-135">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="40dd6-135">Add the following code:</span></span>

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
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="40dd6-136">`[Fact]` Atrybut oznacza metodę testową, która jest uruchamiany przez narzędzie test runner.</span><span class="sxs-lookup"><span data-stu-id="40dd6-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="40dd6-137">Z *PrimeService.Tests* folderu wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="40dd6-137">From the *PrimeService.Tests* folder, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="40dd6-138">Moduł uruchamiający xUnit zawiera punkt wejścia programu, aby uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="40dd6-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="40dd6-139">`dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="40dd6-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="40dd6-140">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="40dd6-140">Your test fails.</span></span> <span data-ttu-id="40dd6-141">Nie utworzono jeszcze wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="40dd6-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="40dd6-142">Wprowadź ten test, przekazać przez napisanie kodu najprostsza `PrimeService` klasę, która działa.</span><span class="sxs-lookup"><span data-stu-id="40dd6-142">Make this test pass by writing the simplest code in the `PrimeService` class that works.</span></span> <span data-ttu-id="40dd6-143">Zastąp istniejące `IsPrime` implementacji metody z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="40dd6-143">Replace the existing `IsPrime` method implementation with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

<span data-ttu-id="40dd6-144">W *PrimeService.Tests* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="40dd6-144">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="40dd6-145">`dotnet test` Polecenie uruchamia kompilację dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="40dd6-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="40dd6-146">Po utworzeniu obu projektów, działa ten jeden test.</span><span class="sxs-lookup"><span data-stu-id="40dd6-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="40dd6-147">Przekazuje on.</span><span class="sxs-lookup"><span data-stu-id="40dd6-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="40dd6-148">Dodawanie większej liczby funkcji</span><span class="sxs-lookup"><span data-stu-id="40dd6-148">Adding more features</span></span>

<span data-ttu-id="40dd6-149">Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="40dd6-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="40dd6-150">Istnieje kilka innych przypadkach proste dla liczby pierwsze: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="40dd6-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="40dd6-151">Możesz dodać te przypadki jako nowe testy za pomocą `[Fact]` atrybut, ale który szybko staje się uciążliwe.</span><span class="sxs-lookup"><span data-stu-id="40dd6-151">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="40dd6-152">Istnieją inne atrybuty xUnit, które umożliwiają pisanie zestaw testów podobne:</span><span class="sxs-lookup"><span data-stu-id="40dd6-152">There are other xUnit attributes that enable you to write a suite of similar tests:</span></span>

- <span data-ttu-id="40dd6-153">`[Theory]` reprezentuje zestaw testów, które wykonania tego samego kodu, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="40dd6-153">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="40dd6-154">`[InlineData]` atrybut określa wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="40dd6-154">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="40dd6-155">Zamiast tworzyć nowe testy, należy zastosować te dwa atrybuty `[Theory]` i `[InlineData]`, aby utworzyć pojedynczy teorii w *PrimeService_IsPrimeShould.cs* pliku.</span><span class="sxs-lookup"><span data-stu-id="40dd6-155">Instead of creating new tests, apply these two attributes, `[Theory]` and `[InlineData]`, to create a single theory in the *PrimeService_IsPrimeShould.cs* file.</span></span> <span data-ttu-id="40dd6-156">Teorii to metoda, która sprawdza kilka wartości mniejszej niż dwa, czyli najniższy numer prime:</span><span class="sxs-lookup"><span data-stu-id="40dd6-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="40dd6-157">Uruchom `dotnet test` ponownie, a dwa z tych testów powinna zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="40dd6-157">Run `dotnet test` again, and two of these tests should fail.</span></span> <span data-ttu-id="40dd6-158">Aby wszystkie przebieg testów, należy zmienić `if` klauzuli na początku `IsPrime` method in Class metoda *PrimeService.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="40dd6-158">To make all of the tests pass, change the `if` clause at the beginning of the `IsPrime` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="40dd6-159">Przejdź do iteracji, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="40dd6-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="40dd6-160">Masz [ukończoną wersję testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="40dd6-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="40dd6-161">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="40dd6-161">Additional resources</span></span>

- [<span data-ttu-id="40dd6-162">Oficjalna witryna xUnit.net</span><span class="sxs-lookup"><span data-stu-id="40dd6-162">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="40dd6-163">Testowanie logiką kontrolera w programie ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="40dd6-163">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
