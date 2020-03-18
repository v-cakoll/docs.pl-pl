---
title: Testowanie jednostkowe języka Visual Basic w programie .NET Core z testem dotnetowym i jednostką NUnit
description: Poznaj pojęcia dotyczące testów jednostkowych w programie .NET Core, korzystając z interaktywnego środowiska, w ramach które krok po kroku przy użyciu funkcji NUnit można znaleźć w przykładzie rozwiązania Visual Basic.
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: a33447457344b241b4c2376d777b0deb7f556874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240925"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="835a8-103">Testowanie jednostkowe bibliotek programu Visual Basic .NET Core przy użyciu testu dotnet i jednostki NUnit</span><span class="sxs-lookup"><span data-stu-id="835a8-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="835a8-104">W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="835a8-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="835a8-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="835a8-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="835a8-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="835a8-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="835a8-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="835a8-107">Prerequisites</span></span>

- <span data-ttu-id="835a8-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="835a8-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="835a8-109">Wybrany edytor tekstu lub edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="835a8-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="835a8-110">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="835a8-110">Creating the source project</span></span>

<span data-ttu-id="835a8-111">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="835a8-111">Open a shell window.</span></span> <span data-ttu-id="835a8-112">Utwórz katalog o nazwie *unit-testing-vb-nunit* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="835a8-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="835a8-113">W tym nowym katalogu uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:</span><span class="sxs-lookup"><span data-stu-id="835a8-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="835a8-114">Następnie utwórz katalog *PrimeService.*</span><span class="sxs-lookup"><span data-stu-id="835a8-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="835a8-115">Poniższy konspekt pokazuje strukturę plików do tej pory:</span><span class="sxs-lookup"><span data-stu-id="835a8-115">The following outline shows the file structure so far:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="835a8-116">Utwórz *PrimeService* bieżący katalog i uruchom następujące polecenie, aby utworzyć projekt źródłowy:</span><span class="sxs-lookup"><span data-stu-id="835a8-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang VB
```

<span data-ttu-id="835a8-117">Zmień nazwę *Class1.VB* na *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="835a8-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="835a8-118">Tworzenie nieudanej implementacji `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="835a8-118">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="835a8-119">Zmień katalog z powrotem na katalog *testów jednostkowych-vb-using-mstest.*</span><span class="sxs-lookup"><span data-stu-id="835a8-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="835a8-120">Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="835a8-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="835a8-121">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="835a8-121">Creating the test project</span></span>

<span data-ttu-id="835a8-122">Następnie utwórz katalog *PrimeService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="835a8-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="835a8-123">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="835a8-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="835a8-124">Utwórz katalog *PrimeService.Tests* jako bieżący katalog i utwórz nowy projekt przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="835a8-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang VB
```

<span data-ttu-id="835a8-125">[Dotnet nowe](../tools/dotnet-new.md) polecenie tworzy projekt testowy, który używa NUnit jako biblioteki testowej.</span><span class="sxs-lookup"><span data-stu-id="835a8-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="835a8-126">Wygenerowany szablon konfiguruje testrunner w pliku *PrimeServiceTests.vbproj:*</span><span class="sxs-lookup"><span data-stu-id="835a8-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="835a8-127">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="835a8-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="835a8-128">`dotnet new`w poprzednim kroku dodano NUnit i kartę testową NUnit.</span><span class="sxs-lookup"><span data-stu-id="835a8-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="835a8-129">Teraz dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="835a8-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="835a8-130">Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="835a8-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="835a8-131">Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) w uspolu GitHub.</span><span class="sxs-lookup"><span data-stu-id="835a8-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="835a8-132">Masz następujący ostateczny układ rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="835a8-132">You have the following final solution layout:</span></span>

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

<span data-ttu-id="835a8-133">Wykonaj następujące polecenie w katalogu *jednostek testujących-vb-nunit:*</span><span class="sxs-lookup"><span data-stu-id="835a8-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="835a8-134">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="835a8-134">Creating the first test</span></span>

<span data-ttu-id="835a8-135">Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="835a8-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="835a8-136">W katalogu *PrimeService.Tests* zmień nazwę pliku *UnitTest1.vb* na *PrimeService_IsPrimeShould.VB* i zastąp całą jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="835a8-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

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

<span data-ttu-id="835a8-137">Atrybut `<TestFixture>` wskazuje klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="835a8-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="835a8-138">Atrybut `<Test>` oznacza metodę, która jest uruchamiana przez test runner.</span><span class="sxs-lookup"><span data-stu-id="835a8-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="835a8-139">Z *jednostki testowania vb-nunit*, [`dotnet test`](../tools/dotnet-test.md) wykonaj do kompilacji testów i biblioteki klas, a następnie uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="835a8-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="835a8-140">Program testowy NUnit zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="835a8-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="835a8-141">`dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="835a8-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="835a8-142">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="835a8-142">Your test fails.</span></span> <span data-ttu-id="835a8-143">Implementacja nie została jeszcze utworzona.</span><span class="sxs-lookup"><span data-stu-id="835a8-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="835a8-144">Zrób ten test przejść, pisząc najprostszy kod w `PrimeService` klasie, która działa:</span><span class="sxs-lookup"><span data-stu-id="835a8-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="835a8-145">W katalogu *testów jednostkowych vb-nunit* uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="835a8-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="835a8-146">Polecenie `dotnet test` uruchamia kompilację `PrimeService` dla projektu, `PrimeService.Tests` a następnie dla projektu.</span><span class="sxs-lookup"><span data-stu-id="835a8-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="835a8-147">Po zbudowaniu obu projektów uruchamia ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="835a8-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="835a8-148">Mija.</span><span class="sxs-lookup"><span data-stu-id="835a8-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="835a8-149">Dodawanie kolejnych funkcji</span><span class="sxs-lookup"><span data-stu-id="835a8-149">Adding more features</span></span>

<span data-ttu-id="835a8-150">Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="835a8-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="835a8-151">Istnieje kilka innych prostych przypadków liczb pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="835a8-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="835a8-152">Można dodać te przypadki jako `<Test>` nowe testy z atrybutem, ale szybko staje się nużące.</span><span class="sxs-lookup"><span data-stu-id="835a8-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="835a8-153">Istnieją inne atrybuty xUnit, które umożliwiają napisanie zestawu podobnych testów.</span><span class="sxs-lookup"><span data-stu-id="835a8-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="835a8-154">Atrybut `<TestCase>` reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="835a8-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="835a8-155">Atrybutu `<TestCase>` można użyć do określenia wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="835a8-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="835a8-156">Zamiast tworzyć nowe testy, należy zastosować te dwa atrybuty, aby utworzyć serię testów, które testują kilka wartości mniejszych niż dwa, co jest najniższą liczbą pierwszą:</span><span class="sxs-lookup"><span data-stu-id="835a8-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="835a8-157">Uruchom `dotnet test`, a dwa z tych testów nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="835a8-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="835a8-158">Aby wszystkie testy zostały zdatce, zmień `if` `Main` klauzulę na początku metody w *pliku PrimeServices.cs:*</span><span class="sxs-lookup"><span data-stu-id="835a8-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="835a8-159">Kontynuuj iterowanie, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="835a8-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="835a8-160">Masz [gotową wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [pełną implementację biblioteki.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb)</span><span class="sxs-lookup"><span data-stu-id="835a8-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="835a8-161">Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="835a8-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="835a8-162">Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="835a8-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="835a8-163">Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="835a8-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
