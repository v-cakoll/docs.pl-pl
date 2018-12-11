---
title: Testowanie jednostek kodu języka Visual Basic w .NET Core za pomocą polecenia dotnet test i struktury MSTest
description: Pojęcia dotyczące jednostek testów platformie .NET Core za pomocą środowisko interaktywne tworzenie rozwiązania języka Visual Basic przykładowe instrukcje krok po kroku przy użyciu przełącznika MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: 105046da426d1aa6cd7dece0e37fe890cd7487e1
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170325"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="3e1bd-103">Biblioteki języka Visual Basic .NET Core za pomocą polecenia dotnet test i struktury MStest testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="3e1bd-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MStest</span></span>

<span data-ttu-id="3e1bd-104">Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="3e1bd-105">Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) przed przystąpieniem do wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="3e1bd-106">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="3e1bd-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="3e1bd-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="3e1bd-107">Creating the source project</span></span>

<span data-ttu-id="3e1bd-108">Otwieranie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-108">Open a shell window.</span></span> <span data-ttu-id="3e1bd-109">Utwórz katalog o nazwie *jednostki — testowanie-języka vb — mstest* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="3e1bd-110">Wewnątrz tego nowy katalog uruchamiania [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="3e1bd-111">Praktyka ta ułatwia zarządzać biblioteki klas i projekt testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="3e1bd-112">Utwórz katalog rozwiązania *PrimeService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="3e1bd-113">Mają następującą strukturę katalogów i plików z tej pory:</span><span class="sxs-lookup"><span data-stu-id="3e1bd-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="3e1bd-114">Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) do utworzenia projektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="3e1bd-115">Zmień nazwę *Class1.VB* do *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="3e1bd-116">Aby użyć Programowanie oparte na testach (TDD), należy utworzyć z implementacją niepowodzenie `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="3e1bd-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="3e1bd-117">Zmień katalog kopii do *jednostki — testowanie-języka vb — przy użyciu stest* katalogu.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="3e1bd-118">Uruchom [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="3e1bd-119">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="3e1bd-119">Creating the test project</span></span>

<span data-ttu-id="3e1bd-120">Następnie należy utworzyć *PrimeService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="3e1bd-121">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="3e1bd-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="3e1bd-122">Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new mstest -lang VB` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="3e1bd-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="3e1bd-123">To polecenie umożliwia utworzenie projektu testowego, który używa MSTest jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="3e1bd-124">Wygenerowany szablon konfiguruje narzędzie test runner w *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="3e1bd-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="3e1bd-125">Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="3e1bd-126">`dotnet new` w poprzednim kroku dodano MSTest i modułu uruchamiającego MSTest.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="3e1bd-127">Teraz Dodaj `PrimeService` biblioteki klas jako inny zależności do projektu.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="3e1bd-128">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="3e1bd-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="3e1bd-129">Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="3e1bd-130">Masz następujące układ ostateczne rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="3e1bd-130">You have the following final solution layout:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="3e1bd-131">Wykonaj [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) w *jednostki — testowanie-języka vb — mstest* katalogu.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="3e1bd-132">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="3e1bd-132">Creating the first test</span></span>

<span data-ttu-id="3e1bd-133">Podejścia TDD wymaga zapisywania niepowodzenie jednego testu, dzięki czemu przekazać, a następnie powtórzyć ten proces.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="3e1bd-134">Usuń *UnitTest1.vb* z *PrimeService.Tests* katalogu i Utwórz nowy plik języka Visual Basic o nazwie *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="3e1bd-135">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="3e1bd-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="3e1bd-136">`<TestClass>` Atrybut wskazuje klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="3e1bd-137">`<TestMethod>` Atrybut oznacza metodę, która jest uruchamiany przez narzędzie test runner.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="3e1bd-138">Z *jednostki — testowanie-języka vb — mstest*, wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="3e1bd-139">Moduł uruchamiający MSTest zawiera punkt wejścia programu, aby uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="3e1bd-140">`dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="3e1bd-141">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-141">Your test fails.</span></span> <span data-ttu-id="3e1bd-142">Nie utworzono jeszcze wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="3e1bd-143">Należy ten test przez napisanie kodu najprostsza `PrimeService` klasę, która działa:</span><span class="sxs-lookup"><span data-stu-id="3e1bd-143">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="3e1bd-144">W *jednostki — testowanie-języka vb — mstest* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="3e1bd-145">`dotnet test` Polecenie uruchamia kompilację dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="3e1bd-146">Po utworzeniu obu projektów, działa ten jeden test.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="3e1bd-147">Przekazuje on.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="3e1bd-148">Dodawanie większej liczby funkcji</span><span class="sxs-lookup"><span data-stu-id="3e1bd-148">Adding more features</span></span>

<span data-ttu-id="3e1bd-149">Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="3e1bd-150">Istnieje kilka innych przypadkach proste dla liczby pierwsze: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="3e1bd-151">Możesz dodać te przypadki jako nowe testy za pomocą `<TestMethod>` atrybut, ale który szybko staje się uciążliwe.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="3e1bd-152">Istnieją inne atrybuty MSTest, które umożliwiają pisanie zestaw testów podobne.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="3e1bd-153">A `<DataTestMethod>` atrybut reprezentuje zestaw testów, które wykonania tego samego kodu, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="3e1bd-154">Możesz użyć `<DataRow>` atrybutu, aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="3e1bd-155">Zamiast tworzyć nowe testy, należy zastosować te atrybuty do utworzenia pojedynczego teorii.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="3e1bd-156">Teorii to metoda, która sprawdza kilka wartości mniejszej niż dwa, czyli najniższy numer prime:</span><span class="sxs-lookup"><span data-stu-id="3e1bd-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="3e1bd-157">Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="3e1bd-158">Aby wszystkie przebieg testów, należy zmienić `if` klauzuli na początku metody:</span><span class="sxs-lookup"><span data-stu-id="3e1bd-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="3e1bd-159">Przejdź do iteracji, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="3e1bd-160">Masz [ukończoną wersję testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="3e1bd-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="3e1bd-161">Gdy masz utworzoną małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="3e1bd-162">Tak, aby dodawania nowych pakietów została ze strukturą rozwiązania i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="3e1bd-163">Po skoncentrowany większość czasu i wysiłku niewiele rozwiązywania cele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e1bd-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
