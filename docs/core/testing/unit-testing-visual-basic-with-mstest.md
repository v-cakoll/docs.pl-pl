---
title: Testowanie jednostkowe Visual Basic w .NET Core z testowaniem dotnet i MSTest
description: Poznaj koncepcje testów jednostkowych w oprogramowaniu .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania Visual Basic krok po kroku przy użyciu MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.custom: seodec18
ms.openlocfilehash: 0b9dee45c980ae9288637967af20caf375f03fd1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117040"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="84510-103">Testowanie jednostkowe Visual Basic biblioteki .NET Core przy użyciu testu dotnet i MSTest</span><span class="sxs-lookup"><span data-stu-id="84510-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MSTest</span></span>

<span data-ttu-id="84510-104">Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="84510-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="84510-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) .</span><span class="sxs-lookup"><span data-stu-id="84510-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="84510-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="84510-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="84510-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="84510-107">Creating the source project</span></span>

<span data-ttu-id="84510-108">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="84510-108">Open a shell window.</span></span> <span data-ttu-id="84510-109">Utwórz katalog o nazwie *Unit-Tests-VB-MSTest* , aby obtrzymać rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="84510-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="84510-110">W tym nowym katalogu Uruchom [`dotnet new sln`](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="84510-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="84510-111">To rozwiązanie ułatwia zarządzanie zarówno biblioteką klas, jak i projektem testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="84510-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="84510-112">W katalogu rozwiązania Utwórz katalog *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="84510-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="84510-113">W tej chwili istnieje następujący katalog i struktura pliku:</span><span class="sxs-lookup"><span data-stu-id="84510-113">You have the following directory and file structure thus far:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="84510-114">Ustaw *PrimeService* w bieżącym katalogu i uruchom [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) , aby utworzyć projekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="84510-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="84510-115">Zmień nazwę *Class1. vb* na *PrimeService. vb*.</span><span class="sxs-lookup"><span data-stu-id="84510-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="84510-116">Tworzysz nieprawidłową implementację `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="84510-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="84510-117">Zmień katalog z powrotem na katalog *Test Unit-VB-using-MSTest* .</span><span class="sxs-lookup"><span data-stu-id="84510-117">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="84510-118">Uruchom [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) , aby dodać projekt biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="84510-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="84510-119">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="84510-119">Creating the test project</span></span>

<span data-ttu-id="84510-120">Następnie Utwórz katalog *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="84510-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="84510-121">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="84510-121">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="84510-122">Utwórz katalog *PrimeService. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą [`dotnet new mstest -lang VB`](../tools/dotnet-new.md)polecenia.</span><span class="sxs-lookup"><span data-stu-id="84510-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="84510-123">To polecenie tworzy projekt testowy, który używa MSTest jako biblioteki testowej.</span><span class="sxs-lookup"><span data-stu-id="84510-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="84510-124">Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w *PrimeServiceTests. vbproj*:</span><span class="sxs-lookup"><span data-stu-id="84510-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="84510-125">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="84510-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="84510-126">`dotnet new`w poprzednim kroku dodano MSTest i moduł uruchamiający MSTest.</span><span class="sxs-lookup"><span data-stu-id="84510-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="84510-127">Teraz Dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="84510-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="84510-128">[`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:</span><span class="sxs-lookup"><span data-stu-id="84510-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="84510-129">Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="84510-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="84510-130">Dysponujesz następującym końcowym układem rozwiązań:</span><span class="sxs-lookup"><span data-stu-id="84510-130">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="84510-131">Wykonaj [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) w katalogu *testowania jednostkowego — VB-MSTest* .</span><span class="sxs-lookup"><span data-stu-id="84510-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="84510-132">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="84510-132">Creating the first test</span></span>

<span data-ttu-id="84510-133">Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces.</span><span class="sxs-lookup"><span data-stu-id="84510-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="84510-134">Usuń *UnitTest1. vb* z katalogu *PrimeService. Tests* i Utwórz nowy plik Visual Basic o nazwie *PrimeService_IsPrimeShould. vb*.</span><span class="sxs-lookup"><span data-stu-id="84510-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="84510-135">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="84510-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.IsFalse(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="84510-136">Ten `<TestClass>` atrybut wskazuje klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="84510-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="84510-137">Ten `<TestMethod>` atrybut oznacza metodę, która jest uruchamiana przez program Test Runner.</span><span class="sxs-lookup"><span data-stu-id="84510-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="84510-138">Z *jednostki-test-VB-MSTest*wykonaj [`dotnet test`](../tools/dotnet-test.md) , aby skompilować testy i bibliotekę klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="84510-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="84510-139">Program MSTest Test Runner zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="84510-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="84510-140">`dotnet test`uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="84510-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="84510-141">Test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="84510-141">Your test fails.</span></span> <span data-ttu-id="84510-142">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="84510-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="84510-143">Wykonaj ten test, pisząc najprostszy kod w `PrimeService` klasie, która działa:</span><span class="sxs-lookup"><span data-stu-id="84510-143">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="84510-144">W katalogu *Test Unit-VB-MSTest* Uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="84510-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="84510-145">Polecenie uruchamia kompilację `PrimeService` dla `PrimeService.Tests` projektu, a następnie dla projektu. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="84510-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="84510-146">Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="84510-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="84510-147">Przekazuje.</span><span class="sxs-lookup"><span data-stu-id="84510-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="84510-148">Dodawanie większej liczby funkcji</span><span class="sxs-lookup"><span data-stu-id="84510-148">Adding more features</span></span>

<span data-ttu-id="84510-149">Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="84510-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="84510-150">Istnieje kilka innych prostych przypadków dla numerów pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="84510-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="84510-151">Te przypadki można dodać jako nowe testy z `<TestMethod>` atrybutem, ale szybko żmudnym.</span><span class="sxs-lookup"><span data-stu-id="84510-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="84510-152">Istnieją inne atrybuty MSTest, które umożliwiają pisanie zestawu podobnych testów.</span><span class="sxs-lookup"><span data-stu-id="84510-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="84510-153">`<DataTestMethod>` Atrybut reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="84510-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="84510-154">Możesz użyć atrybutu, `<DataRow>` aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="84510-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="84510-155">Zamiast tworzyć nowe testy, Zastosuj te dwa atrybuty, aby utworzyć jedno teoretyczne.</span><span class="sxs-lookup"><span data-stu-id="84510-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="84510-156">Teoretyczna jest metoda, która sprawdza kilka wartości mniejszej niż dwa, które jest najniższą liczbą:</span><span class="sxs-lookup"><span data-stu-id="84510-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="84510-157">Uruchom `dotnet test`i dwa z tych testów zakończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="84510-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="84510-158">Aby wszystkie testy zostały zakończone pomyślnie, należy zmienić `if` klauzulę na początku metody:</span><span class="sxs-lookup"><span data-stu-id="84510-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="84510-159">Kontynuuj iteracje, dodając więcej testów, więcej teorie i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="84510-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="84510-160">Masz [ukończoną wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [kompletną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="84510-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="84510-161">Utworzono niewielką bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="84510-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="84510-162">Rozbudowane rozwiązanie jest przeznaczone do dodawania nowych pakietów i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="84510-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="84510-163">Zbyt najwięcej czasu i wysiłku na rozwiązywanie celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="84510-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
