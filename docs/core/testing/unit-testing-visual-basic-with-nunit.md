---
title: Testowanie jednostkowe Visual Basic w .NET Core z testowaniem dotnet i NUnit
description: Poznaj koncepcje testów jednostkowych w oprogramowaniu .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania Visual Basic krok po kroku przy użyciu NUnit.
author: rprouse
ms.date: 10/04/2018
ms.custom: seodec18
ms.openlocfilehash: c48b2777b451598a0f3ccbb383d702d0069ff6ff
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373820"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="cfaca-103">Testowanie jednostkowe Visual Basic biblioteki .NET Core przy użyciu testu dotnet i NUnit</span><span class="sxs-lookup"><span data-stu-id="cfaca-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="cfaca-104">Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="cfaca-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="cfaca-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) .</span><span class="sxs-lookup"><span data-stu-id="cfaca-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="cfaca-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="cfaca-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="cfaca-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="cfaca-107">Prerequisites</span></span>

- <span data-ttu-id="cfaca-108">[Zestaw .NET Core 2,1 SDK](https://www.microsoft.com/net/download) lub jego nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="cfaca-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="cfaca-109">Edytor tekstu lub Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="cfaca-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="cfaca-110">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="cfaca-110">Creating the source project</span></span>

<span data-ttu-id="cfaca-111">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="cfaca-111">Open a shell window.</span></span> <span data-ttu-id="cfaca-112">Utwórz katalog o nazwie *Unit-Tests-VB-nunit* , aby obtrzymać rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="cfaca-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="cfaca-113">W tym nowym katalogu Uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:</span><span class="sxs-lookup"><span data-stu-id="cfaca-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="cfaca-114">Następnie Utwórz katalog *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="cfaca-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="cfaca-115">Poniższy konspekt przedstawia strukturę plików do tej pory:</span><span class="sxs-lookup"><span data-stu-id="cfaca-115">The following outline shows the file structure so far:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="cfaca-116">Ustaw *PrimeService* w bieżącym katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:</span><span class="sxs-lookup"><span data-stu-id="cfaca-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang VB
```

<span data-ttu-id="cfaca-117">Zmień nazwę *Class1. vb* na *PrimeService. vb*.</span><span class="sxs-lookup"><span data-stu-id="cfaca-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="cfaca-118">Tworzysz nieprawidłową implementację `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="cfaca-118">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="cfaca-119">Zmień katalog z powrotem na katalog *Test Unit-VB-using-MSTest* .</span><span class="sxs-lookup"><span data-stu-id="cfaca-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="cfaca-120">Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="cfaca-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="cfaca-121">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="cfaca-121">Creating the test project</span></span>

<span data-ttu-id="cfaca-122">Następnie Utwórz katalog *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="cfaca-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="cfaca-123">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="cfaca-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="cfaca-124">Utwórz katalog *PrimeService. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="cfaca-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang VB
```

<span data-ttu-id="cfaca-125">Polecenie [dotnet New](../tools/dotnet-new.md) umożliwia utworzenie projektu testowego, który używa nunit jako biblioteki testowej.</span><span class="sxs-lookup"><span data-stu-id="cfaca-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="cfaca-126">Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w pliku *PrimeServiceTests. vbproj* :</span><span class="sxs-lookup"><span data-stu-id="cfaca-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="cfaca-127">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="cfaca-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="cfaca-128">`dotnet new`w poprzednim kroku dodano NUnit i kartę testową NUnit.</span><span class="sxs-lookup"><span data-stu-id="cfaca-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="cfaca-129">Teraz Dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="cfaca-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="cfaca-130">[`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:</span><span class="sxs-lookup"><span data-stu-id="cfaca-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="cfaca-131">Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="cfaca-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="cfaca-132">Dysponujesz następującym końcowym układem rozwiązań:</span><span class="sxs-lookup"><span data-stu-id="cfaca-132">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

<span data-ttu-id="cfaca-133">Wykonaj następujące polecenie w katalogu *Unit-Test-VB-nunit* :</span><span class="sxs-lookup"><span data-stu-id="cfaca-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="cfaca-134">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="cfaca-134">Creating the first test</span></span>

<span data-ttu-id="cfaca-135">Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces.</span><span class="sxs-lookup"><span data-stu-id="cfaca-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="cfaca-136">W katalogu *PrimeService. Tests* Zmień nazwę pliku *UnitTest1. vb* na *PrimeService_IsPrimeShould. vb* i Zastąp całą zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="cfaca-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="cfaca-137">Ten `<TestFixture>` atrybut wskazuje klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="cfaca-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="cfaca-138">Ten `<Test>` atrybut oznacza metodę, która jest uruchamiana przez program Test Runner.</span><span class="sxs-lookup"><span data-stu-id="cfaca-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="cfaca-139">Z *jednostki-test-VB-nunit*wykonaj [`dotnet test`](../tools/dotnet-test.md) , aby skompilować testy i bibliotekę klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="cfaca-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="cfaca-140">Program NUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="cfaca-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="cfaca-141">`dotnet test`uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="cfaca-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="cfaca-142">Test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="cfaca-142">Your test fails.</span></span> <span data-ttu-id="cfaca-143">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="cfaca-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="cfaca-144">Wykonaj ten test, pisząc najprostszy kod w `PrimeService` klasie, która działa:</span><span class="sxs-lookup"><span data-stu-id="cfaca-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="cfaca-145">W katalogu *Test Unit-VB-nunit* Uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="cfaca-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="cfaca-146">Polecenie uruchamia kompilację `PrimeService` dla `PrimeService.Tests` projektu, a następnie dla projektu. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="cfaca-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="cfaca-147">Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="cfaca-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="cfaca-148">Przekazuje.</span><span class="sxs-lookup"><span data-stu-id="cfaca-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="cfaca-149">Dodawanie większej liczby funkcji</span><span class="sxs-lookup"><span data-stu-id="cfaca-149">Adding more features</span></span>

<span data-ttu-id="cfaca-150">Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="cfaca-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="cfaca-151">Istnieje kilka innych prostych przypadków dla numerów pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="cfaca-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="cfaca-152">Te przypadki można dodać jako nowe testy z `<Test>` atrybutem, ale szybko żmudnym.</span><span class="sxs-lookup"><span data-stu-id="cfaca-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="cfaca-153">Istnieją inne atrybuty xUnit, które umożliwiają pisanie zestawu podobnych testów.</span><span class="sxs-lookup"><span data-stu-id="cfaca-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="cfaca-154">`<TestCase>` Atrybut reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="cfaca-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="cfaca-155">Możesz użyć atrybutu, `<TestCase>` aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="cfaca-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="cfaca-156">Zamiast tworzyć nowe testy, Zastosuj te dwa atrybuty, aby utworzyć serię testów, które testują kilka wartości mniejszej niż dwa, czyli najniższy numer podstawowy:</span><span class="sxs-lookup"><span data-stu-id="cfaca-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="cfaca-157">Uruchom `dotnet test`i dwa z tych testów zakończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="cfaca-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="cfaca-158">Aby wszystkie testy zostały zakończone pomyślnie, należy zmienić `if` klauzulę na początku `Main` metody w pliku *PrimeServices.cs* :</span><span class="sxs-lookup"><span data-stu-id="cfaca-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="cfaca-159">Kontynuuj iteracje, dodając więcej testów, więcej teorie i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="cfaca-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="cfaca-160">Masz [ukończoną wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [kompletną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="cfaca-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="cfaca-161">Utworzono niewielką bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="cfaca-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="cfaca-162">Rozbudowane rozwiązanie jest przeznaczone do dodawania nowych pakietów i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="cfaca-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="cfaca-163">Zbyt najwięcej czasu i wysiłku na rozwiązywanie celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfaca-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
