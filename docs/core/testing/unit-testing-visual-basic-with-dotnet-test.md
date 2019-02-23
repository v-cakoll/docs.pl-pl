---
title: Testowanie jednostek kodu języka Visual Basic w .NET Core za pomocą polecenia dotnet test i struktury xUnit
description: Pojęcia dotyczące jednostek testów platformie .NET Core za pomocą środowisko interaktywne tworzenie rozwiązania języka Visual Basic przykładowe instrukcje krok po kroku za pomocą polecenia dotnet test i struktury xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: 193746e8efda5d7bc9e086bb0abf934cfeb1741a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748599"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="ec693-103">Jednostki testowania bibliotek języka Visual Basic .NET Core za pomocą polecenia dotnet test i struktury xUnit</span><span class="sxs-lookup"><span data-stu-id="ec693-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="ec693-104">Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="ec693-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="ec693-105">Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) przed przystąpieniem do wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ec693-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) before you begin.</span></span> <span data-ttu-id="ec693-106">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ec693-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="ec693-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="ec693-107">Creating the source project</span></span>

<span data-ttu-id="ec693-108">Otwieranie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="ec693-108">Open a shell window.</span></span> <span data-ttu-id="ec693-109">Utwórz katalog o nazwie *unit-testing-vb-using-dotnet-test* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ec693-109">Create a directory called *unit-testing-vb-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="ec693-110">Wewnątrz tego nowy katalog uruchamiania [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ec693-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="ec693-111">Praktyka ta ułatwia zarządzać biblioteki klas i projekt testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="ec693-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="ec693-112">Utwórz katalog rozwiązania *PrimeService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="ec693-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="ec693-113">Mają następującą strukturę katalogów i plików z tej pory:</span><span class="sxs-lookup"><span data-stu-id="ec693-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="ec693-114">Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) do utworzenia projektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="ec693-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="ec693-115">Zmień nazwę *Class1.VB* do *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="ec693-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="ec693-116">Tworzenie wdrożenia niepowodzenie `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="ec693-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="ec693-117">Zmień katalog kopii do *unit-testing-vb-using-dotnet-test* katalogu.</span><span class="sxs-lookup"><span data-stu-id="ec693-117">Change the directory back to the *unit-testing-vb-using-dotnet-test* directory.</span></span> <span data-ttu-id="ec693-118">Uruchom [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="ec693-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="ec693-119">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="ec693-119">Creating the test project</span></span>

<span data-ttu-id="ec693-120">Następnie należy utworzyć *PrimeService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="ec693-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="ec693-121">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="ec693-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="ec693-122">Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new xunit -lang VB` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="ec693-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="ec693-123">To polecenie umożliwia utworzenie projektu testowego, który używa rozwiązania xUnit, jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="ec693-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="ec693-124">Wygenerowany szablon konfiguruje narzędzie test runner w *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="ec693-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="ec693-125">Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="ec693-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="ec693-126">`dotnet new` w poprzednim kroku dodawany xUnit, a moduł uruchamiający testy xUnit.</span><span class="sxs-lookup"><span data-stu-id="ec693-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="ec693-127">Teraz Dodaj `PrimeService` biblioteki klas jako inny zależności do projektu.</span><span class="sxs-lookup"><span data-stu-id="ec693-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="ec693-128">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="ec693-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="ec693-129">Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="ec693-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="ec693-130">Masz następujące nazwie ostatniego folderu układu:</span><span class="sxs-lookup"><span data-stu-id="ec693-130">You have the following final folder layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="ec693-131">Wykonaj [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) w *unit-testing-vb-using-dotnet-test* katalogu.</span><span class="sxs-lookup"><span data-stu-id="ec693-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="ec693-132">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="ec693-132">Creating the first test</span></span>

<span data-ttu-id="ec693-133">Jeden zapisu kończy się niepowodzeniem testu, ułatwiają — dostęp próbny, a następnie powtórz ten proces.</span><span class="sxs-lookup"><span data-stu-id="ec693-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="ec693-134">Usuń *UnitTest1.vb* z *PrimeService.Tests* katalogu i Utwórz nowy plik języka Visual Basic o nazwie *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="ec693-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="ec693-135">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="ec693-135">Add the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="ec693-136">`<Fact>` Atrybut oznacza metodę testową, która jest uruchamiany przez narzędzie test runner.</span><span class="sxs-lookup"><span data-stu-id="ec693-136">The `<Fact>` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="ec693-137">Z *testowania — przy użyciu dotnet-test jednostkowy*, wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="ec693-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="ec693-138">Moduł uruchamiający xUnit zawiera punkt wejścia programu, aby uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="ec693-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="ec693-139">`dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="ec693-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="ec693-140">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="ec693-140">Your test fails.</span></span> <span data-ttu-id="ec693-141">Nie utworzono jeszcze wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="ec693-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="ec693-142">Należy ten test przez napisanie kodu najprostsza `PrimeService` klasę, która działa:</span><span class="sxs-lookup"><span data-stu-id="ec693-142">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="ec693-143">W *unit-testing-vb-using-dotnet-test* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="ec693-143">In the *unit-testing-vb-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="ec693-144">`dotnet test` Polecenie uruchamia kompilację dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="ec693-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="ec693-145">Po utworzeniu obu projektów, działa ten jeden test.</span><span class="sxs-lookup"><span data-stu-id="ec693-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="ec693-146">Przekazuje on.</span><span class="sxs-lookup"><span data-stu-id="ec693-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="ec693-147">Dodawanie większej liczby funkcji</span><span class="sxs-lookup"><span data-stu-id="ec693-147">Adding more features</span></span>

<span data-ttu-id="ec693-148">Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="ec693-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="ec693-149">Istnieje kilka innych przypadkach proste dla liczby pierwsze: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="ec693-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="ec693-150">Możesz dodać te przypadki jako nowe testy za pomocą `<Fact>` atrybut, ale który szybko staje się uciążliwe.</span><span class="sxs-lookup"><span data-stu-id="ec693-150">You could add those cases as new tests with the `<Fact>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="ec693-151">Istnieją inne atrybuty xUnit, które umożliwiają pisanie zestaw testów podobne.</span><span class="sxs-lookup"><span data-stu-id="ec693-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="ec693-152">A `<Theory>` atrybut reprezentuje zestaw testów, które wykonania tego samego kodu, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="ec693-152">A `<Theory>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="ec693-153">Możesz użyć `<InlineData>` atrybutu, aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ec693-153">You can use the `<InlineData>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="ec693-154">Zamiast tworzyć nowe testy, należy zastosować te atrybuty do utworzenia pojedynczego teorii.</span><span class="sxs-lookup"><span data-stu-id="ec693-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="ec693-155">Teorii to metoda, która sprawdza kilka wartości mniejszej niż dwa, czyli najniższy numer prime:</span><span class="sxs-lookup"><span data-stu-id="ec693-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="ec693-156">Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ec693-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="ec693-157">Aby wszystkie przebieg testów, należy zmienić `if` klauzuli na początku metody:</span><span class="sxs-lookup"><span data-stu-id="ec693-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="ec693-158">Przejdź do iteracji, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="ec693-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="ec693-159">Masz [ukończoną wersję testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="ec693-159">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="ec693-160">Gdy masz utworzoną małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ec693-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="ec693-161">Tak, aby dodawania nowych pakietów została ze strukturą rozwiązania i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ec693-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="ec693-162">Po skoncentrowany większość czasu i wysiłku niewiele rozwiązywania cele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ec693-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
