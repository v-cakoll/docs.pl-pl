---
title: Jednostki testowania C# przy użyciu MSTest i .NET Core
description: Pojęcia dotyczące jednostek testów w języku C# i .NET Core za pomocą interaktywnych doświadczenia przykładowe rozwiązanie krok po kroku za pomocą polecenia dotnet test i struktury MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.custom: seodec18
ms.openlocfilehash: 4f6e1bb9a03a8f98052ec7bc911f22c288df6fe0
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746853"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="91dec-103">Jednostki testowania C# przy użyciu MSTest i .NET Core</span><span class="sxs-lookup"><span data-stu-id="91dec-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="91dec-104">Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="91dec-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="91dec-105">Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) przed przystąpieniem do wykonywania.</span><span class="sxs-lookup"><span data-stu-id="91dec-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="91dec-106">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="91dec-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="91dec-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="91dec-107">Creating the source project</span></span>

<span data-ttu-id="91dec-108">Otwieranie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="91dec-108">Open a shell window.</span></span> <span data-ttu-id="91dec-109">Utwórz katalog o nazwie *jednostki — testowanie-przy użyciu mstest* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="91dec-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="91dec-110">Wewnątrz tego nowy katalog uruchamiania [ `dotnet new sln` ](../tools/dotnet-new.md) do utworzenia nowego pliku rozwiązania projekt testu i biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="91dec-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="91dec-111">Następnie należy utworzyć *PrimeService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="91dec-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="91dec-112">Następujące konspektu przedstawia strukturę katalogów i plików tej pory:</span><span class="sxs-lookup"><span data-stu-id="91dec-112">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="91dec-113">Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib` ](../tools/dotnet-new.md) do utworzenia projektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="91dec-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="91dec-114">Zmień nazwę *Class1.cs* do *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="91dec-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="91dec-115">Tworzenie wdrożenia niepowodzenie `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="91dec-115">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="91dec-116">Zmień katalog kopii do *jednostki — testowanie-przy użyciu mstest* katalogu.</span><span class="sxs-lookup"><span data-stu-id="91dec-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="91dec-117">Uruchom [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="91dec-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span> 

### <a name="creating-the-test-project"></a><span data-ttu-id="91dec-118">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="91dec-118">Creating the test project</span></span>

<span data-ttu-id="91dec-119">Następnie należy utworzyć *PrimeService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="91dec-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="91dec-120">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="91dec-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="91dec-121">Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new mstest` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="91dec-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="91dec-122">Nowe polecenie dotnet tworzy projekt testowy, który używa MStest jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="91dec-122">The dotnet new command creates a test project that uses MStest as the test library.</span></span> <span data-ttu-id="91dec-123">Wygenerowany szablon konfiguruje narzędzie test runner w *PrimeServiceTests.csproj* pliku:</span><span class="sxs-lookup"><span data-stu-id="91dec-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="91dec-124">Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="91dec-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="91dec-125">`dotnet new` w poprzednim kroku, które są dodawane do zestawu SDK MSTest, MSTest przetestować framework i modułu uruchamiającego MSTest.</span><span class="sxs-lookup"><span data-stu-id="91dec-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="91dec-126">Teraz Dodaj `PrimeService` biblioteki klas jako inny zależności do projektu.</span><span class="sxs-lookup"><span data-stu-id="91dec-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="91dec-127">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="91dec-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="91dec-128">Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="91dec-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="91dec-129">Następujące konspektu przedstawia wybrany układ ostateczne rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="91dec-129">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="91dec-130">Wykonaj [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) w *jednostki — testowanie-przy użyciu mstest* katalogu.</span><span class="sxs-lookup"><span data-stu-id="91dec-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-mstest* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="91dec-131">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="91dec-131">Creating the first test</span></span>

<span data-ttu-id="91dec-132">Jeden zapisu kończy się niepowodzeniem testu, ułatwiają — dostęp próbny, a następnie powtórz ten proces.</span><span class="sxs-lookup"><span data-stu-id="91dec-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="91dec-133">Usuń *UnitTest1.cs* z *PrimeService.Tests* katalogu i Utwórz nowy C# plik o nazwie *PrimeService_IsPrimeShould.cs* o następującej zawartości:</span><span class="sxs-lookup"><span data-stu-id="91dec-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="91dec-134">`[TestClass]` Atrybut wskazuje klasę, która zawiera testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="91dec-134">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="91dec-135">`[TestMethod]` Atrybut wskazuje, metoda jest metodą testową.</span><span class="sxs-lookup"><span data-stu-id="91dec-135">The `[TestMethod]` attribute indicates a method is a test method.</span></span> 

<span data-ttu-id="91dec-136">Zapisz ten plik i wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="91dec-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="91dec-137">Moduł uruchamiający MSTest zawiera punkt wejścia programu, aby uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="91dec-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="91dec-138">`dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="91dec-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="91dec-139">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="91dec-139">Your test fails.</span></span> <span data-ttu-id="91dec-140">Nie utworzono jeszcze wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="91dec-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="91dec-141">Wprowadź ten test, przekazać przez napisanie kodu najprostsza `PrimeService` klasę, która działa:</span><span class="sxs-lookup"><span data-stu-id="91dec-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="91dec-142">W *jednostki — testowanie-przy użyciu mstest* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="91dec-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="91dec-143">`dotnet test` Polecenie uruchamia kompilację dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="91dec-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="91dec-144">Po utworzeniu obu projektów, działa ten jeden test.</span><span class="sxs-lookup"><span data-stu-id="91dec-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="91dec-145">Przekazuje on.</span><span class="sxs-lookup"><span data-stu-id="91dec-145">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="91dec-146">Dodawanie większej liczby funkcji</span><span class="sxs-lookup"><span data-stu-id="91dec-146">Adding more features</span></span>

<span data-ttu-id="91dec-147">Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="91dec-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="91dec-148">Istnieje kilka innych przypadkach proste dla liczby pierwsze: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="91dec-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="91dec-149">Można dodać nowe testy za pomocą `[TestMethod]` atrybut, ale który szybko staje się uciążliwe.</span><span class="sxs-lookup"><span data-stu-id="91dec-149">You could add new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="91dec-150">Istnieją inne atrybuty MSTest, które umożliwiają pisanie zestaw testów podobne.</span><span class="sxs-lookup"><span data-stu-id="91dec-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="91dec-151">A `[DataTestMethod]`atrybut reprezentuje zestaw testów, które wykonania tego samego kodu, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="91dec-151">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="91dec-152">Możesz użyć `[DataRow]` atrybutu, aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="91dec-152">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="91dec-153">Zamiast tworzyć nowe testy, należy zastosować te atrybuty do utworzenia pojedynczego testu opartego na danych.</span><span class="sxs-lookup"><span data-stu-id="91dec-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="91dec-154">Opartych na test danych to metoda, która sprawdza kilka wartości mniejszej niż dwa, czyli najniższy numer prime:</span><span class="sxs-lookup"><span data-stu-id="91dec-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="91dec-155">Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="91dec-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="91dec-156">Aby wszystkie przebieg testów, należy zmienić `if` klauzuli na początku metody:</span><span class="sxs-lookup"><span data-stu-id="91dec-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="91dec-157">Przejdź do iteracji, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="91dec-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="91dec-158">Masz [ukończoną wersję testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="91dec-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="91dec-159">Gdy masz utworzoną małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="91dec-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="91dec-160">Tak, aby dodawania nowych pakietów została ze strukturą rozwiązania i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="91dec-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="91dec-161">Po skoncentrowany większość czasu i wysiłku niewiele rozwiązywania cele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91dec-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
