---
title: Testowanie jednostek kodu języka Visual Basic w .NET Core za pomocą polecenia dotnet test i NUnit
description: Pojęcia dotyczące jednostek testów platformie .NET Core za pomocą środowisko interaktywne tworzenie rozwiązania języka Visual Basic przykładowe instrukcje krok po kroku przy użyciu narzędzia NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: cf8a81241c93a6eeecf04052aba57750774aa050
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397503"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="69d66-103">Biblioteki języka Visual Basic .NET Core za pomocą polecenia dotnet test i NUnit testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="69d66-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="69d66-104">Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="69d66-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="69d66-105">Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) przed przystąpieniem do wykonywania.</span><span class="sxs-lookup"><span data-stu-id="69d66-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="69d66-106">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="69d66-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="69d66-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="69d66-107">Prerequisites</span></span>

- <span data-ttu-id="69d66-108">[Zestaw SDK programu .NET core 2.1](https://www.microsoft.com/net/download) lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="69d66-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="69d66-109">Edytor tekstu lub ulubionego edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="69d66-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="69d66-110">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="69d66-110">Creating the source project</span></span>

<span data-ttu-id="69d66-111">Otwieranie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="69d66-111">Open a shell window.</span></span> <span data-ttu-id="69d66-112">Utwórz katalog o nazwie *jednostki — testowanie-języka vb — nunit* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="69d66-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="69d66-113">Wewnątrz tego nowy katalog uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:</span><span class="sxs-lookup"><span data-stu-id="69d66-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="69d66-114">Następnie należy utworzyć *PrimeService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="69d66-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="69d66-115">Następujące konspektu pokazuje struktury plików do tej pory:</span><span class="sxs-lookup"><span data-stu-id="69d66-115">The following outline shows the file structure so far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="69d66-116">Wprowadź *PrimeService* bieżącego katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:</span><span class="sxs-lookup"><span data-stu-id="69d66-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang VB
```

<span data-ttu-id="69d66-117">Zmień nazwę *Class1.VB* do *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="69d66-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="69d66-118">Tworzenie wdrożenia niepowodzenie `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="69d66-118">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="69d66-119">Zmień katalog kopii do *jednostki — testowanie-języka vb — przy użyciu mstest* katalogu.</span><span class="sxs-lookup"><span data-stu-id="69d66-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="69d66-120">Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="69d66-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="69d66-121">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="69d66-121">Creating the test project</span></span>

<span data-ttu-id="69d66-122">Następnie należy utworzyć *PrimeService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="69d66-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="69d66-123">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="69d66-123">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="69d66-124">Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt, używając następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="69d66-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang VB
```

<span data-ttu-id="69d66-125">[Dotnet nowe](../tools/dotnet-new.md) polecenie tworzy projekt testowy, który używa NUnit jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="69d66-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="69d66-126">Wygenerowany szablon konfiguruje narzędzie test runner w *PrimeServiceTests.vbproj* pliku:</span><span class="sxs-lookup"><span data-stu-id="69d66-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="69d66-127">Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="69d66-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="69d66-128">`dotnet new` w poprzednim kroku należy dodać kartę testu NUnit i NUnit.</span><span class="sxs-lookup"><span data-stu-id="69d66-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="69d66-129">Teraz Dodaj `PrimeService` biblioteki klas jako inny zależności do projektu.</span><span class="sxs-lookup"><span data-stu-id="69d66-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="69d66-130">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="69d66-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="69d66-131">Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="69d66-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="69d66-132">Masz następujące układ ostateczne rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="69d66-132">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

<span data-ttu-id="69d66-133">Wykonaj następujące polecenie w *jednostki — testowanie-języka vb — nunit* katalogu:</span><span class="sxs-lookup"><span data-stu-id="69d66-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="69d66-134">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="69d66-134">Creating the first test</span></span>

<span data-ttu-id="69d66-135">Jeden zapisu kończy się niepowodzeniem testu, ułatwiają — dostęp próbny, a następnie powtórz ten proces.</span><span class="sxs-lookup"><span data-stu-id="69d66-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="69d66-136">W *PrimeService.Tests* katalogu, zmiana nazwy *UnitTest1.vb* plik *PrimeService_IsPrimeShould.VB* i zastąp jego całą zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="69d66-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="69d66-137">`<TestFixture>` Atrybut wskazuje klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="69d66-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="69d66-138">`<Test>` Atrybut oznacza metodę, która jest uruchamiany przez narzędzie test runner.</span><span class="sxs-lookup"><span data-stu-id="69d66-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="69d66-139">Z *jednostki — testowanie-języka vb — nunit*, wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="69d66-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="69d66-140">Moduł uruchamiający NUnit zawiera punkt wejścia programu, aby uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="69d66-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="69d66-141">`dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="69d66-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="69d66-142">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="69d66-142">Your test fails.</span></span> <span data-ttu-id="69d66-143">Nie utworzono jeszcze wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="69d66-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="69d66-144">Należy ten test przez napisanie kodu najprostsza `PrimeService` klasę, która działa:</span><span class="sxs-lookup"><span data-stu-id="69d66-144">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="69d66-145">W *jednostki — testowanie-języka vb — nunit* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="69d66-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="69d66-146">`dotnet test` Polecenie uruchamia kompilację dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="69d66-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="69d66-147">Po utworzeniu obu projektów, działa ten jeden test.</span><span class="sxs-lookup"><span data-stu-id="69d66-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="69d66-148">Przekazuje on.</span><span class="sxs-lookup"><span data-stu-id="69d66-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="69d66-149">Dodawanie większej liczby funkcji</span><span class="sxs-lookup"><span data-stu-id="69d66-149">Adding more features</span></span>

<span data-ttu-id="69d66-150">Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="69d66-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="69d66-151">Istnieje kilka innych przypadkach proste dla liczby pierwsze: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="69d66-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="69d66-152">Możesz dodać te przypadki jako nowe testy za pomocą `<Test>` atrybut, ale który szybko staje się uciążliwe.</span><span class="sxs-lookup"><span data-stu-id="69d66-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="69d66-153">Istnieją inne atrybuty xUnit, które umożliwiają pisanie zestaw testów podobne.</span><span class="sxs-lookup"><span data-stu-id="69d66-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="69d66-154">A `<TestCase>` atrybut reprezentuje zestaw testów, które wykonania tego samego kodu, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="69d66-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="69d66-155">Możesz użyć `<TestCase>` atrybutu, aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="69d66-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="69d66-156">Zamiast tworzyć nowe testy, mają zastosowanie do utworzenia szereg testów testujące kilka wartości mniejszej niż dwa, czyli najniższy numer pierwsze dwa atrybuty:</span><span class="sxs-lookup"><span data-stu-id="69d66-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="69d66-157">Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="69d66-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="69d66-158">Aby wszystkie przebieg testów, należy zmienić `if` klauzuli na początku `Main` method in Class metoda *PrimeServices.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="69d66-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="69d66-159">Przejdź do iteracji, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="69d66-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="69d66-160">Masz [ukończoną wersję testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="69d66-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="69d66-161">Gdy masz utworzoną małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="69d66-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="69d66-162">Tak, aby dodawania nowych pakietów została ze strukturą rozwiązania i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="69d66-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="69d66-163">Po skoncentrowany większość czasu i wysiłku niewiele rozwiązywania cele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="69d66-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
