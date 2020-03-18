---
title: Testowanie jednostkowe języka Visual Basic w programie .NET Core z testem dotnetowym i mstestem
description: Poznaj pojęcia dotyczące testów jednostkowych w programie .NET Core, korzystając z interakcyjnego środowiska, w ramach które krok po kroku przy użyciu narzędzia MSTest jest tworzenie przykładowego rozwiązania visual basic.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: df167e0559c841510df17ba39801e43315036241
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240938"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="5fa3a-103">Testowanie jednostkowe bibliotek programu Visual Basic .NET Core przy użyciu testu dotnet i programu MSTest</span><span class="sxs-lookup"><span data-stu-id="5fa3a-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MSTest</span></span>

<span data-ttu-id="5fa3a-104">W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="5fa3a-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="5fa3a-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="5fa3a-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="5fa3a-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="5fa3a-107">Creating the source project</span></span>

<span data-ttu-id="5fa3a-108">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-108">Open a shell window.</span></span> <span data-ttu-id="5fa3a-109">Utwórz katalog o nazwie *unit-testing-vb-mstest* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="5fa3a-110">Wewnątrz tego nowego [`dotnet new sln`](../tools/dotnet-new.md) katalogu uruchom, aby utworzyć nowe rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="5fa3a-111">Ta praktyka ułatwia zarządzanie zarówno biblioteki klas i projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="5fa3a-112">W katalogu rozwiązania utwórz katalog *PrimeService.*</span><span class="sxs-lookup"><span data-stu-id="5fa3a-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="5fa3a-113">Do tej pory masz następującą strukturę katalogów i plików:</span><span class="sxs-lookup"><span data-stu-id="5fa3a-113">You have the following directory and file structure thus far:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="5fa3a-114">Utwórz *PrimeService* bieżący [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) katalog i uruchom, aby utworzyć projekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="5fa3a-115">Zmień nazwę *Class1.VB* na *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="5fa3a-116">Tworzenie nieudanej implementacji `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="5fa3a-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="5fa3a-117">Zmień katalog z powrotem na katalog *testów jednostkowych-vb-using-mstest.*</span><span class="sxs-lookup"><span data-stu-id="5fa3a-117">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="5fa3a-118">Uruchom, [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) aby dodać projekt biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="5fa3a-119">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="5fa3a-119">Creating the test project</span></span>

<span data-ttu-id="5fa3a-120">Następnie utwórz katalog *PrimeService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="5fa3a-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="5fa3a-121">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="5fa3a-121">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="5fa3a-122">Utwórz katalog *PrimeService.Tests* jako bieżący katalog [`dotnet new mstest -lang VB`](../tools/dotnet-new.md)i utwórz nowy projekt przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="5fa3a-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="5fa3a-123">To polecenie tworzy projekt testowy, który używa MSTest jako biblioteki testowej.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="5fa3a-124">Wygenerowany szablon konfiguruje testrunner w *PrimeServiceTests.vbproj:*</span><span class="sxs-lookup"><span data-stu-id="5fa3a-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="5fa3a-125">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="5fa3a-126">`dotnet new`w poprzednim kroku dodano MSTest i mstest runner.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="5fa3a-127">Teraz dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="5fa3a-128">Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="5fa3a-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="5fa3a-129">Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) w uspolu GitHub.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="5fa3a-130">Masz następujący ostateczny układ rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="5fa3a-130">You have the following final solution layout:</span></span>

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

<span data-ttu-id="5fa3a-131">Wykonywanie [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) w katalogu *testów jednostkowych vb-mstest.*</span><span class="sxs-lookup"><span data-stu-id="5fa3a-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="5fa3a-132">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="5fa3a-132">Creating the first test</span></span>

<span data-ttu-id="5fa3a-133">Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="5fa3a-134">Usuń *UnitTest1.vb* z katalogu *PrimeService.Tests* i utwórz nowy plik Języka Visual Basic o nazwie *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="5fa3a-135">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="5fa3a-135">Add the following code:</span></span>

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

<span data-ttu-id="5fa3a-136">Atrybut `<TestClass>` wskazuje klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="5fa3a-137">Atrybut `<TestMethod>` oznacza metodę, która jest uruchamiana przez test runner.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="5fa3a-138">Z *jednostki testowania vb-mstest*, [`dotnet test`](../tools/dotnet-test.md) wykonaj, aby utworzyć testy i biblioteki klas, a następnie uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="5fa3a-139">Program testowy MSTest zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="5fa3a-140">`dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="5fa3a-141">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-141">Your test fails.</span></span> <span data-ttu-id="5fa3a-142">Implementacja nie została jeszcze utworzona.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="5fa3a-143">Zrób ten test przejść, pisząc najprostszy kod w `PrimeService` klasie, która działa:</span><span class="sxs-lookup"><span data-stu-id="5fa3a-143">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="5fa3a-144">W katalogu *testów jednostkowych vb-mstest* uruchom ponownie. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="5fa3a-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="5fa3a-145">Polecenie `dotnet test` uruchamia kompilację `PrimeService` dla projektu, `PrimeService.Tests` a następnie dla projektu.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="5fa3a-146">Po zbudowaniu obu projektów uruchamia ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="5fa3a-147">Mija.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="5fa3a-148">Dodawanie kolejnych funkcji</span><span class="sxs-lookup"><span data-stu-id="5fa3a-148">Adding more features</span></span>

<span data-ttu-id="5fa3a-149">Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="5fa3a-150">Istnieje kilka innych prostych przypadków liczb pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="5fa3a-151">Można dodać te przypadki jako `<TestMethod>` nowe testy z atrybutem, ale szybko staje się nużące.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="5fa3a-152">Istnieją inne atrybuty MSTest, które umożliwiają pisanie zestawu podobnych testów.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="5fa3a-153">Atrybut `<DataTestMethod>` reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="5fa3a-154">Atrybutu `<DataRow>` można użyć do określenia wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="5fa3a-155">Zamiast tworzyć nowe testy, zastosuj te dwa atrybuty, aby utworzyć jedną teorię.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="5fa3a-156">Teoria jest metodą, która testuje kilka wartości mniej niż dwie, co jest najniższą liczbą pierwszą:</span><span class="sxs-lookup"><span data-stu-id="5fa3a-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-mstest/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="5fa3a-157">Uruchom `dotnet test`, a dwa z tych testów nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="5fa3a-158">Aby wszystkie testy zostały zdatce, zmień klauzulę `if` na początku metody:</span><span class="sxs-lookup"><span data-stu-id="5fa3a-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="5fa3a-159">Kontynuuj iterowanie, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="5fa3a-160">Masz [gotową wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [pełną implementację biblioteki.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb)</span><span class="sxs-lookup"><span data-stu-id="5fa3a-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="5fa3a-161">Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="5fa3a-162">Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="5fa3a-163">Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5fa3a-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
