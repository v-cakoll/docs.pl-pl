---
title: Testowanie C# jednostkowe za pomocą MSTest i .NET Core
description: Poznaj koncepcje testów jednostkowych w C# oprogramowaniu i .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania krok po kroku przy użyciu testu dotnet i MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.custom: seodec18
ms.openlocfilehash: ae4ddd4df902cf8c3d50e50614b12af8dc0aebed
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168167"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="d6f8c-103">Testowanie C# jednostkowe za pomocą MSTest i .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6f8c-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="d6f8c-104">Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="d6f8c-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) .</span><span class="sxs-lookup"><span data-stu-id="d6f8c-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="d6f8c-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d6f8c-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="create-the-source-project"></a><span data-ttu-id="d6f8c-107">Utwórz projekt źródłowy</span><span class="sxs-lookup"><span data-stu-id="d6f8c-107">Create the source project</span></span>

<span data-ttu-id="d6f8c-108">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-108">Open a shell window.</span></span> <span data-ttu-id="d6f8c-109">Utwórz katalog o nazwie *Unit-Test-using-MSTest* , aby pomieścić rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="d6f8c-110">W tym nowym katalogu Uruchom [`dotnet new sln`](../tools/dotnet-new.md) polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="d6f8c-111">Następnie Utwórz katalog *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="d6f8c-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="d6f8c-112">W poniższym konspekcie przedstawiono strukturę katalogów i plików:</span><span class="sxs-lookup"><span data-stu-id="d6f8c-112">The following outline shows the directory and file structure thus far:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="d6f8c-113">Ustaw *PrimeService* w bieżącym katalogu i uruchom [`dotnet new classlib`](../tools/dotnet-new.md) , aby utworzyć projekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="d6f8c-114">Zmień nazwę *Class1.cs* na *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="d6f8c-115">Tworzysz nieprawidłową implementację `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="d6f8c-115">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="d6f8c-116">Zmień katalog z powrotem do katalogu *testowego MSTest* .</span><span class="sxs-lookup"><span data-stu-id="d6f8c-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="d6f8c-117">Uruchom [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) , aby dodać projekt biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span> 

## <a name="create-the-test-project"></a><span data-ttu-id="d6f8c-118">Utwórz projekt testu</span><span class="sxs-lookup"><span data-stu-id="d6f8c-118">Create the test project</span></span>

<span data-ttu-id="d6f8c-119">Następnie Utwórz katalog *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="d6f8c-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="d6f8c-120">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="d6f8c-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="d6f8c-121">Utwórz katalog *PrimeService. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą [`dotnet new mstest`](../tools/dotnet-new.md)polecenia.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="d6f8c-122">Polecenie dotnet New umożliwia utworzenie projektu testowego, który używa MSTest jako biblioteki testowej.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-122">The dotnet new command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="d6f8c-123">Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w pliku *PrimeServiceTests. csproj* :</span><span class="sxs-lookup"><span data-stu-id="d6f8c-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="d6f8c-124">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="d6f8c-125">`dotnet new`w poprzednim kroku dodano zestaw MSTest SDK, platformę test MSTest i moduł uruchamiający MSTest.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="d6f8c-126">Teraz Dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="d6f8c-127">[`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:</span><span class="sxs-lookup"><span data-stu-id="d6f8c-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="d6f8c-128">Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="d6f8c-129">W poniższym konspekcie przedstawiono końcowy układ rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="d6f8c-129">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="d6f8c-130">Wykonaj [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) w katalogu *testowym jednostkowym-using-MSTest* .</span><span class="sxs-lookup"><span data-stu-id="d6f8c-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-mstest* directory.</span></span> 

## <a name="create-the-first-test"></a><span data-ttu-id="d6f8c-131">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="d6f8c-131">Create the first test</span></span>

<span data-ttu-id="d6f8c-132">Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="d6f8c-133">Usuń *UnitTest1.cs* z katalogu *PrimeService. Tests* i Utwórz nowy C# plik o nazwie *PrimeService_IsPrimeShould. cs* z następującą zawartością:</span><span class="sxs-lookup"><span data-stu-id="d6f8c-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="d6f8c-134">[Atrybut TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) oznacza klasę, która zawiera testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-134">The [TestClass attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) denotes a class that contains unit tests.</span></span> <span data-ttu-id="d6f8c-135">[Atrybut TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) wskazuje, że metoda jest metodą testową.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-135">The [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) indicates a method is a test method.</span></span> 

<span data-ttu-id="d6f8c-136">Zapisz ten plik i wykonaj [`dotnet test`](../tools/dotnet-test.md) , aby skompilować testy i bibliotekę klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="d6f8c-137">Program MSTest Test Runner zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="d6f8c-138">`dotnet test`uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="d6f8c-139">Test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-139">Your test fails.</span></span> <span data-ttu-id="d6f8c-140">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="d6f8c-141">Wykonaj ten test, pisząc najprostszy kod w `PrimeService` klasie, która działa:</span><span class="sxs-lookup"><span data-stu-id="d6f8c-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="d6f8c-142">W katalogu *testy jednostkowe-using-MSTest* Uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="d6f8c-143">Polecenie uruchamia kompilację `PrimeService` dla `PrimeService.Tests` projektu, a następnie dla projektu. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="d6f8c-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="d6f8c-144">Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="d6f8c-145">Przekazuje.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-145">It passes.</span></span>

## <a name="add-more-features"></a><span data-ttu-id="d6f8c-146">Dodaj więcej funkcji</span><span class="sxs-lookup"><span data-stu-id="d6f8c-146">Add more features</span></span>

<span data-ttu-id="d6f8c-147">Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="d6f8c-148">Istnieje kilka innych prostych przypadków dla numerów pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="d6f8c-149">Można dodać nowe testy z atrybutem [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), ale szybko żmudnym.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-149">You could add new tests with the [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), but that quickly becomes tedious.</span></span> <span data-ttu-id="d6f8c-150">Istnieją inne atrybuty MSTest, które umożliwiają pisanie zestawu podobnych testów.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="d6f8c-151">[Atrybut DataTestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-151">A [DataTestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="d6f8c-152">Można użyć [atrybutu DataRow](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) , aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-152">You can use the [DataRow attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) to specify values for those inputs.</span></span>

<span data-ttu-id="d6f8c-153">Zamiast tworzyć nowe testy, Zastosuj te dwa atrybuty w celu utworzenia pojedynczego testu opartego na danych.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="d6f8c-154">Test oparty na danych to metoda, która sprawdza kilka wartości mniejszej niż dwa, co jest najniższym numerem:</span><span class="sxs-lookup"><span data-stu-id="d6f8c-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="d6f8c-155">Uruchom `dotnet test`i dwa z tych testów zakończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="d6f8c-156">Aby wszystkie testy zostały zakończone pomyślnie, należy zmienić `if` klauzulę na początku metody:</span><span class="sxs-lookup"><span data-stu-id="d6f8c-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="d6f8c-157">Kontynuuj iteracje, dodając więcej testów, więcej teorie i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="d6f8c-158">Masz ukończoną [wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i kompletną implementację [biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="d6f8c-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="d6f8c-159">Utworzono niewielką bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="d6f8c-160">Rozbudowane rozwiązanie jest przeznaczone do dodawania nowych pakietów i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="d6f8c-161">Zbyt najwięcej czasu i wysiłku na rozwiązywanie celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d6f8c-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6f8c-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6f8c-162">See also</span></span>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [<span data-ttu-id="d6f8c-163">Użyj struktury MSTest w testach jednostkowych</span><span class="sxs-lookup"><span data-stu-id="d6f8c-163">Use the MSTest framework in unit tests</span></span>](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [<span data-ttu-id="d6f8c-164">Dokumentacja platformy testowej MSTest v2</span><span class="sxs-lookup"><span data-stu-id="d6f8c-164">MSTest V2 test framework docs</span></span>](https://github.com/Microsoft/testfx-docs)
