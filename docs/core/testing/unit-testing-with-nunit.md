---
title: Jednostki testowania C# za pomocą NUnit i .NET Core
description: Pojęcia dotyczące jednostek testów w języku C# i .NET Core za pomocą interaktywnych doświadczenia przykładowe rozwiązanie krok po kroku za pomocą polecenia dotnet test i NUnit.
author: rprouse
ms.date: 08/31/2018
ms.custom: seodec18
ms.openlocfilehash: 7d3daa344b2a6fb8694a255fdc26b5ba31e2d82a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665458"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="c378e-103">Jednostki testowania C# za pomocą NUnit i .NET Core</span><span class="sxs-lookup"><span data-stu-id="c378e-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="c378e-104">Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="c378e-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="c378e-105">Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) przed przystąpieniem do wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c378e-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="c378e-106">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="c378e-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c378e-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c378e-107">Prerequisites</span></span>

- <span data-ttu-id="c378e-108">[Zestaw SDK programu .NET core 2.1](https://www.microsoft.com/net/download) lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="c378e-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="c378e-109">Edytor tekstu lub ulubionego edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="c378e-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="c378e-110">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="c378e-110">Creating the source project</span></span>

<span data-ttu-id="c378e-111">Otwieranie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="c378e-111">Open a shell window.</span></span> <span data-ttu-id="c378e-112">Utwórz katalog o nazwie *jednostki — testowanie-przy użyciu nunit* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c378e-112">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="c378e-113">Wewnątrz tego nowy katalog uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:</span><span class="sxs-lookup"><span data-stu-id="c378e-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```
 
<span data-ttu-id="c378e-114">Następnie należy utworzyć *PrimeService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="c378e-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="c378e-115">Następujące konspektu przedstawia strukturę katalogów i plików do tej pory:</span><span class="sxs-lookup"><span data-stu-id="c378e-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="c378e-116">Wprowadź *PrimeService* bieżącego katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:</span><span class="sxs-lookup"><span data-stu-id="c378e-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib
```

<span data-ttu-id="c378e-117">Zmień nazwę *Class1.cs* do *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="c378e-117">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="c378e-118">Tworzenie wdrożenia niepowodzenie `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="c378e-118">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="c378e-119">Zmień katalog kopii do *jednostki — testowanie-przy użyciu nunit* katalogu.</span><span class="sxs-lookup"><span data-stu-id="c378e-119">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="c378e-120">Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="c378e-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="c378e-121">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="c378e-121">Creating the test project</span></span>

<span data-ttu-id="c378e-122">Następnie należy utworzyć *PrimeService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="c378e-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="c378e-123">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="c378e-123">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="c378e-124">Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt, używając następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c378e-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="c378e-125">[Dotnet nowe](../tools/dotnet-new.md) polecenie tworzy projekt testowy, który używa NUnit jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="c378e-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="c378e-126">Wygenerowany szablon konfiguruje narzędzie test runner w *PrimeService.Tests.csproj* pliku:</span><span class="sxs-lookup"><span data-stu-id="c378e-126">The generated template configures the test runner in the *PrimeService.Tests.csproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

<span data-ttu-id="c378e-127">Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="c378e-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="c378e-128">`dotnet new` w poprzednim kroku dodane testów firmy Microsoft zestawu SDK, struktury testów NUnit i NUnit adaptera testowego.</span><span class="sxs-lookup"><span data-stu-id="c378e-128">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="c378e-129">Teraz Dodaj `PrimeService` biblioteki klas jako inny zależności do projektu.</span><span class="sxs-lookup"><span data-stu-id="c378e-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="c378e-130">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="c378e-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="c378e-131">Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="c378e-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="c378e-132">Następujące konspektu przedstawia wybrany układ ostateczne rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="c378e-132">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

<span data-ttu-id="c378e-133">Wykonaj następujące polecenie w *jednostki — testowanie-przy użyciu nunit* katalogu:</span><span class="sxs-lookup"><span data-stu-id="c378e-133">Execute the following command in the *unit-testing-using-nunit* directory:</span></span>

```console
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="c378e-134">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="c378e-134">Creating the first test</span></span>

<span data-ttu-id="c378e-135">Jeden zapisu kończy się niepowodzeniem testu, ułatwiają — dostęp próbny, a następnie powtórz ten proces.</span><span class="sxs-lookup"><span data-stu-id="c378e-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="c378e-136">W *PrimeService.Tests* katalogu, zmiana nazwy *UnitTest1.cs* plik *PrimeService_IsPrimeShould.cs* i zastąp jego całą zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="c378e-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.cs* file to *PrimeService_IsPrimeShould.cs* and replace its entire contents with the following code:</span></span>

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="c378e-137">`[TestFixture]` Atrybut wskazuje klasę, która zawiera testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="c378e-137">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="c378e-138">`[Test]` Atrybut wskazuje, metoda jest metodą testową.</span><span class="sxs-lookup"><span data-stu-id="c378e-138">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="c378e-139">Zapisz ten plik i wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="c378e-139">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="c378e-140">Moduł uruchamiający NUnit zawiera punkt wejścia programu, aby uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="c378e-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="c378e-141">`dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="c378e-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="c378e-142">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="c378e-142">Your test fails.</span></span> <span data-ttu-id="c378e-143">Nie utworzono jeszcze wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="c378e-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="c378e-144">Wprowadź ten test, przekazać przez napisanie kodu najprostsza `PrimeService` klasę, która działa:</span><span class="sxs-lookup"><span data-stu-id="c378e-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="c378e-145">W *jednostki — testowanie-przy użyciu nunit* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="c378e-145">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="c378e-146">`dotnet test` Polecenie uruchamia kompilację dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="c378e-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="c378e-147">Po utworzeniu obu projektów, działa ten jeden test.</span><span class="sxs-lookup"><span data-stu-id="c378e-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="c378e-148">Przekazuje on.</span><span class="sxs-lookup"><span data-stu-id="c378e-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="c378e-149">Dodawanie większej liczby funkcji</span><span class="sxs-lookup"><span data-stu-id="c378e-149">Adding more features</span></span>

<span data-ttu-id="c378e-150">Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="c378e-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="c378e-151">Istnieje kilka innych przypadkach proste dla liczby pierwsze: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="c378e-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="c378e-152">Można dodać nowe testy za pomocą `[Test]` atrybut, ale który szybko staje się uciążliwe.</span><span class="sxs-lookup"><span data-stu-id="c378e-152">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="c378e-153">Istnieją inne atrybuty NUnit, które umożliwiają pisanie zestaw testów podobne.</span><span class="sxs-lookup"><span data-stu-id="c378e-153">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="c378e-154">A `[TestCase]` atrybut jest używany do tworzenia zestaw testów, które wykonania tego samego kodu, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="c378e-154">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="c378e-155">Możesz użyć `[TestCase]` atrybutu, aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="c378e-155">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="c378e-156">Zamiast tworzyć nowe testy, należy zastosować ten atrybut do utworzenia pojedynczego testu opartego na danych.</span><span class="sxs-lookup"><span data-stu-id="c378e-156">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="c378e-157">Opartych na test danych to metoda, która sprawdza kilka wartości mniejszej niż dwa, czyli najniższy numer prime:</span><span class="sxs-lookup"><span data-stu-id="c378e-157">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="c378e-158">Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c378e-158">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="c378e-159">Aby wszystkie przebieg testów, należy zmienić `if` klauzuli na początku `Main` method in Class metoda *PrimeService.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="c378e-159">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="c378e-160">Przejdź do iteracji, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="c378e-160">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="c378e-161">Masz [ukończoną wersję testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="c378e-161">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="c378e-162">Gdy masz utworzoną małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c378e-162">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="c378e-163">Tak, aby dodawania nowych pakietów została ze strukturą rozwiązania i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c378e-163">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="c378e-164">Po skoncentrowany większość czasu i wysiłku niewiele rozwiązywania cele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c378e-164">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
