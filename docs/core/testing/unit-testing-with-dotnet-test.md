---
title: Kod testu C# jednostkowego w programie .NET Core przy użyciu testu dotnet i xUnit
description: Poznaj koncepcje testów jednostkowych w C# oprogramowaniu i .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania krok po kroku przy użyciu testu dotnet i xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 5319e33c314187ccce3e9832c4b01d93ba86c3ce
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626412"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="338c5-103">Testowanie C# jednostkowe w programie .NET Core przy użyciu testu dotnet i xUnit</span><span class="sxs-lookup"><span data-stu-id="338c5-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="338c5-104">Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="338c5-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="338c5-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) .</span><span class="sxs-lookup"><span data-stu-id="338c5-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="338c5-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="338c5-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="338c5-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="338c5-107">Creating the source project</span></span>

<span data-ttu-id="338c5-108">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="338c5-108">Open a shell window.</span></span> <span data-ttu-id="338c5-109">Utwórz katalog o nazwie *Unit-Test-using-dotnet-Testuj* , aby obtrzymać rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="338c5-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="338c5-110">W tym nowym katalogu Uruchom [`dotnet new sln`](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="338c5-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="338c5-111">Rozwiązanie ułatwia zarządzanie zarówno biblioteką klas, jak i projektem testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="338c5-111">Having a solution makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="338c5-112">W katalogu rozwiązania Utwórz katalog *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="338c5-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="338c5-113">W tej chwili struktura katalogów i plików powinna być następująca:</span><span class="sxs-lookup"><span data-stu-id="338c5-113">The directory and file structure thus far should be as follows:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="338c5-114">Ustaw *PrimeService* w bieżącym katalogu i uruchom [`dotnet new classlib`](../tools/dotnet-new.md) , aby utworzyć projekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="338c5-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="338c5-115">Zmień nazwę *Class1.cs* na *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="338c5-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="338c5-116">Najpierw utwórz nieprawidłową implementację `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="338c5-116">You first create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first.");
        }
    }
}
```

<span data-ttu-id="338c5-117">Zmień katalog z powrotem na katalog *testów jednostkowych-using-dotnet-test* .</span><span class="sxs-lookup"><span data-stu-id="338c5-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span>

<span data-ttu-id="338c5-118">Uruchom polecenie [dotnet sln](../tools/dotnet-sln.md) , aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="338c5-118">Run the [dotnet sln](../tools/dotnet-sln.md) command to add the class library project to the solution:</span></span>

```
dotnet sln add ./PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="338c5-119">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="338c5-119">Creating the test project</span></span>

<span data-ttu-id="338c5-120">Następnie Utwórz katalog *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="338c5-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="338c5-121">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="338c5-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="338c5-122">Utwórz katalog *PrimeService. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą [`dotnet new xunit`](../tools/dotnet-new.md)polecenia.</span><span class="sxs-lookup"><span data-stu-id="338c5-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="338c5-123">To polecenie tworzy projekt testowy, który używa [xUnit](https://xunit.github.io/) jako biblioteki testowej.</span><span class="sxs-lookup"><span data-stu-id="338c5-123">This command creates a test project that uses [xUnit](https://xunit.github.io/) as the test library.</span></span> <span data-ttu-id="338c5-124">Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w pliku *PrimeServiceTests. csproj* podobnie jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="338c5-124">The generated template configures the test runner in the *PrimeServiceTests.csproj* file similar to the following code:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="338c5-125">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="338c5-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="338c5-126">`dotnet new`w poprzednim kroku dodano xUnit i moduł uruchamiający xUnit.</span><span class="sxs-lookup"><span data-stu-id="338c5-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="338c5-127">Teraz Dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="338c5-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="338c5-128">[`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:</span><span class="sxs-lookup"><span data-stu-id="338c5-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="338c5-129">Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="338c5-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="338c5-130">Poniżej przedstawiono końcowy układ rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="338c5-130">The following shows the final solution layout:</span></span>

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

<span data-ttu-id="338c5-131">Aby dodać projekt testowy do rozwiązania, uruchom polecenie [dotnet sln](../tools/dotnet-sln.md) w katalogu *Unit-Test-using-dotnet* :</span><span class="sxs-lookup"><span data-stu-id="338c5-131">To add the test project to the solution, run the [dotnet sln](../tools/dotnet-sln.md) command in the *unit-testing-using-dotnet-test* directory:</span></span>

```
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="338c5-132">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="338c5-132">Creating the first test</span></span>

<span data-ttu-id="338c5-133">Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces.</span><span class="sxs-lookup"><span data-stu-id="338c5-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="338c5-134">Usuń *UnitTest1.cs* z katalogu *PrimeService. Tests* i Utwórz nowy C# plik o nazwie *PrimeService_IsPrimeShould. cs*.</span><span class="sxs-lookup"><span data-stu-id="338c5-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="338c5-135">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="338c5-135">Add the following code:</span></span>

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

<span data-ttu-id="338c5-136">Ten `[Fact]` atrybut wskazuje metodę testową, która jest uruchamiana przez program Test Runner.</span><span class="sxs-lookup"><span data-stu-id="338c5-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="338c5-137">W folderze *PrimeService. Tests* wykonaj [`dotnet test`](../tools/dotnet-test.md) polecenie, aby skompilować testy i bibliotekę klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="338c5-137">From the *PrimeService.Tests* folder, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="338c5-138">Program xUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="338c5-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="338c5-139">`dotnet test`uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="338c5-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="338c5-140">Test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="338c5-140">Your test fails.</span></span> <span data-ttu-id="338c5-141">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="338c5-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="338c5-142">Wykonaj ten test, pisząc najprostszy kod w `PrimeService` klasie, która działa.</span><span class="sxs-lookup"><span data-stu-id="338c5-142">Make this test pass by writing the simplest code in the `PrimeService` class that works.</span></span> <span data-ttu-id="338c5-143">Zastąp istniejącą `IsPrime` implementację metody następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="338c5-143">Replace the existing `IsPrime` method implementation with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first.");
}
```

<span data-ttu-id="338c5-144">W katalogu *PrimeService. Tests* ponownie uruchom `dotnet test` polecenie.</span><span class="sxs-lookup"><span data-stu-id="338c5-144">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="338c5-145">Polecenie uruchamia kompilację `PrimeService` dla `PrimeService.Tests` projektu, a następnie dla projektu. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="338c5-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="338c5-146">Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="338c5-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="338c5-147">Przekazuje.</span><span class="sxs-lookup"><span data-stu-id="338c5-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="338c5-148">Dodawanie większej liczby funkcji</span><span class="sxs-lookup"><span data-stu-id="338c5-148">Adding more features</span></span>

<span data-ttu-id="338c5-149">Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="338c5-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="338c5-150">Istnieje kilka innych prostych przypadków dla numerów pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="338c5-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="338c5-151">Te przypadki można dodać jako nowe testy z `[Fact]` atrybutem, ale szybko żmudnym.</span><span class="sxs-lookup"><span data-stu-id="338c5-151">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="338c5-152">Istnieją inne atrybuty xUnit, które umożliwiają pisanie zestawu podobnych testów:</span><span class="sxs-lookup"><span data-stu-id="338c5-152">There are other xUnit attributes that enable you to write a suite of similar tests:</span></span>

- <span data-ttu-id="338c5-153">`[Theory]`reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="338c5-153">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="338c5-154">`[InlineData]`atrybut określa wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="338c5-154">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="338c5-155">Zamiast tworzyć nowe testy, Zastosuj te dwa atrybuty `[Theory]` i `[InlineData]`, aby utworzyć pojedynczy teorii w pliku *PrimeService_IsPrimeShould. cs* .</span><span class="sxs-lookup"><span data-stu-id="338c5-155">Instead of creating new tests, apply these two attributes, `[Theory]` and `[InlineData]`, to create a single theory in the *PrimeService_IsPrimeShould.cs* file.</span></span> <span data-ttu-id="338c5-156">Teoretyczna jest metoda, która sprawdza kilka wartości mniejszej niż dwa, które jest najniższą liczbą:</span><span class="sxs-lookup"><span data-stu-id="338c5-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="338c5-157">Uruchom `dotnet test` ponownie, a dwa z tych testów nie powiodą się.</span><span class="sxs-lookup"><span data-stu-id="338c5-157">Run `dotnet test` again, and two of these tests should fail.</span></span> <span data-ttu-id="338c5-158">Aby wszystkie testy zostały zakończone pomyślnie, należy zmienić `if` klauzulę na początku `IsPrime` metody w pliku *PrimeService.cs* :</span><span class="sxs-lookup"><span data-stu-id="338c5-158">To make all of the tests pass, change the `if` clause at the beginning of the `IsPrime` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="338c5-159">Kontynuuj iteracje, dodając więcej testów, więcej teorie i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="338c5-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="338c5-160">Masz ukończoną [wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i kompletną implementację [biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="338c5-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="338c5-161">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="338c5-161">Additional resources</span></span>

- [<span data-ttu-id="338c5-162">Oficjalna witryna xUnit.net</span><span class="sxs-lookup"><span data-stu-id="338c5-162">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="338c5-163">Testowanie logiki kontrolera w ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="338c5-163">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
