---
title: Testowanie jednostkowe języka Visual Basic w programie .NET Core z testem dotnetowym i jednostką xUnit
description: Poznaj pojęcia dotyczące testów jednostkowych w programie .NET Core, korzystając z interaktywnego środowiska, w ramach które krok po kroku tworzenie przykładowego rozwiązania Visual Basic przy użyciu testu dotnet i xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: 9a99d9031711a3e958132416d0235df76f4a9092
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240951"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="0b1d5-103">Testowanie jednostkowe bibliotek programu Visual Basic .NET Core przy użyciu testu dotnet i xUnit</span><span class="sxs-lookup"><span data-stu-id="0b1d5-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="0b1d5-104">W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="0b1d5-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) before you begin.</span></span> <span data-ttu-id="0b1d5-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="0b1d5-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="0b1d5-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="0b1d5-107">Creating the source project</span></span>

<span data-ttu-id="0b1d5-108">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-108">Open a shell window.</span></span> <span data-ttu-id="0b1d5-109">Utwórz katalog o nazwie *unit-testing-vb-using-dotnet-test* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-109">Create a directory called *unit-testing-vb-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="0b1d5-110">Wewnątrz tego nowego [`dotnet new sln`](../tools/dotnet-new.md) katalogu uruchom, aby utworzyć nowe rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="0b1d5-111">Ta praktyka ułatwia zarządzanie zarówno biblioteki klas i projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="0b1d5-112">W katalogu rozwiązania utwórz katalog *PrimeService.*</span><span class="sxs-lookup"><span data-stu-id="0b1d5-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="0b1d5-113">Do tej pory masz następującą strukturę katalogów i plików:</span><span class="sxs-lookup"><span data-stu-id="0b1d5-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="0b1d5-114">Utwórz *PrimeService* bieżący [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) katalog i uruchom, aby utworzyć projekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="0b1d5-115">Zmień nazwę *Class1.VB* na *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="0b1d5-116">Tworzenie nieudanej implementacji `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="0b1d5-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="0b1d5-117">Zmień katalog z powrotem do *katalogu testów jednostkowych-vb-using-dotnet-test.*</span><span class="sxs-lookup"><span data-stu-id="0b1d5-117">Change the directory back to the *unit-testing-vb-using-dotnet-test* directory.</span></span> <span data-ttu-id="0b1d5-118">Uruchom, [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) aby dodać projekt biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="0b1d5-119">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="0b1d5-119">Creating the test project</span></span>

<span data-ttu-id="0b1d5-120">Następnie utwórz katalog *PrimeService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="0b1d5-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="0b1d5-121">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="0b1d5-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="0b1d5-122">Utwórz katalog *PrimeService.Tests* jako bieżący katalog [`dotnet new xunit -lang VB`](../tools/dotnet-new.md)i utwórz nowy projekt przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="0b1d5-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="0b1d5-123">To polecenie tworzy projekt testowy, który używa xUnit jako biblioteki testów.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="0b1d5-124">Wygenerowany szablon konfiguruje testrunner w *PrimeServiceTests.vbproj:*</span><span class="sxs-lookup"><span data-stu-id="0b1d5-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="0b1d5-125">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="0b1d5-126">`dotnet new`w poprzednim kroku dodano xUnit i xUnit runner.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="0b1d5-127">Teraz dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="0b1d5-128">Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="0b1d5-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="0b1d5-129">Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) w uspolu GitHub.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="0b1d5-130">Masz następujący ostateczny układ folderu:</span><span class="sxs-lookup"><span data-stu-id="0b1d5-130">You have the following final folder layout:</span></span>

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

<span data-ttu-id="0b1d5-131">Wykonaj [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) w katalogu *testów jednostkowych-vb-using-dotnet-test.*</span><span class="sxs-lookup"><span data-stu-id="0b1d5-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-using-dotnet-test* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="0b1d5-132">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="0b1d5-132">Creating the first test</span></span>

<span data-ttu-id="0b1d5-133">Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="0b1d5-134">Usuń *UnitTest1.vb* z katalogu *PrimeService.Tests* i utwórz nowy plik Języka Visual Basic o nazwie *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="0b1d5-135">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="0b1d5-135">Add the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="0b1d5-136">Atrybut `<Fact>` oznacza metodę testową, która jest uruchamiana przez test runner.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-136">The `<Fact>` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="0b1d5-137">Z *jednostki testowania za pomocą dotnet-test*, wykonaj [`dotnet test`](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="0b1d5-138">Program testowy xUnit zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="0b1d5-139">`dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="0b1d5-140">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-140">Your test fails.</span></span> <span data-ttu-id="0b1d5-141">Implementacja nie została jeszcze utworzona.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="0b1d5-142">Zrób ten test przejść, pisząc najprostszy kod w `PrimeService` klasie, która działa:</span><span class="sxs-lookup"><span data-stu-id="0b1d5-142">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="0b1d5-143">W katalogu *testów jednostkowych-vb-using-dotnet-test* uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-143">In the *unit-testing-vb-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="0b1d5-144">Polecenie `dotnet test` uruchamia kompilację `PrimeService` dla projektu, `PrimeService.Tests` a następnie dla projektu.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="0b1d5-145">Po zbudowaniu obu projektów uruchamia ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="0b1d5-146">Mija.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="0b1d5-147">Dodawanie kolejnych funkcji</span><span class="sxs-lookup"><span data-stu-id="0b1d5-147">Adding more features</span></span>

<span data-ttu-id="0b1d5-148">Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="0b1d5-149">Istnieje kilka innych prostych przypadków liczb pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="0b1d5-150">Można dodać te przypadki jako `<Fact>` nowe testy z atrybutem, ale szybko staje się nużące.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-150">You could add those cases as new tests with the `<Fact>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="0b1d5-151">Istnieją inne atrybuty xUnit, które umożliwiają napisanie zestawu podobnych testów.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="0b1d5-152">Atrybut `<Theory>` reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-152">A `<Theory>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="0b1d5-153">Atrybutu `<InlineData>` można użyć do określenia wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-153">You can use the `<InlineData>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="0b1d5-154">Zamiast tworzyć nowe testy, zastosuj te dwa atrybuty, aby utworzyć jedną teorię.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="0b1d5-155">Teoria jest metodą, która testuje kilka wartości mniej niż dwie, co jest najniższą liczbą pierwszą:</span><span class="sxs-lookup"><span data-stu-id="0b1d5-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-dotnet-test/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="0b1d5-156">Uruchom `dotnet test`, a dwa z tych testów nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="0b1d5-157">Aby wszystkie testy zostały zdatce, zmień klauzulę `if` na początku metody:</span><span class="sxs-lookup"><span data-stu-id="0b1d5-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="0b1d5-158">Kontynuuj iterowanie, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="0b1d5-159">Masz [gotową wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [pełną implementację biblioteki.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb)</span><span class="sxs-lookup"><span data-stu-id="0b1d5-159">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="0b1d5-160">Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="0b1d5-161">Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="0b1d5-162">Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b1d5-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
