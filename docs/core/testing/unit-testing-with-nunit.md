---
title: Testowanie jednostkowe C# z NUnit i .NET Core
description: Poznaj pojęcia dotyczące testów jednostkowych w językach C# i .NET Core, korzystając z interakcyjnego środowiska, które krok po kroku przy użyciu testu dotnet i NUnit.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 283aa5a28ed213d4290eb3c73a98af56ec074ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240886"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="fe903-103">Testowanie jednostkowe C# z NUnit i .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe903-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="fe903-104">W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="fe903-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="fe903-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="fe903-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="fe903-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="fe903-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="fe903-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fe903-107">Prerequisites</span></span>

- <span data-ttu-id="fe903-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="fe903-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="fe903-109">Wybrany edytor tekstu lub edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="fe903-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="fe903-110">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="fe903-110">Creating the source project</span></span>

<span data-ttu-id="fe903-111">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="fe903-111">Open a shell window.</span></span> <span data-ttu-id="fe903-112">Utwórz katalog o nazwie *unit-testing-using-nunit* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="fe903-112">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="fe903-113">W tym nowym katalogu uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:</span><span class="sxs-lookup"><span data-stu-id="fe903-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="fe903-114">Następnie utwórz katalog *PrimeService.*</span><span class="sxs-lookup"><span data-stu-id="fe903-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="fe903-115">Poniższy konspekt pokazuje strukturę katalogów i plików do tej pory:</span><span class="sxs-lookup"><span data-stu-id="fe903-115">The following outline shows the directory and file structure so far:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="fe903-116">Utwórz *PrimeService* bieżący katalog i uruchom następujące polecenie, aby utworzyć projekt źródłowy:</span><span class="sxs-lookup"><span data-stu-id="fe903-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib
```

<span data-ttu-id="fe903-117">Zmień nazwę *Class1.cs* na *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="fe903-117">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="fe903-118">Tworzenie nieudanej implementacji `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="fe903-118">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="fe903-119">Zmień katalog z powrotem na katalog *jednostek testujących-przyużyciu nunit.*</span><span class="sxs-lookup"><span data-stu-id="fe903-119">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="fe903-120">Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="fe903-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="fe903-121">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="fe903-121">Creating the test project</span></span>

<span data-ttu-id="fe903-122">Następnie utwórz katalog *PrimeService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="fe903-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="fe903-123">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="fe903-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="fe903-124">Utwórz katalog *PrimeService.Tests* jako bieżący katalog i utwórz nowy projekt przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="fe903-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit
```

<span data-ttu-id="fe903-125">[Dotnet nowe](../tools/dotnet-new.md) polecenie tworzy projekt testowy, który używa NUnit jako biblioteki testowej.</span><span class="sxs-lookup"><span data-stu-id="fe903-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="fe903-126">Wygenerowany szablon konfiguruje testrunner w pliku *PrimeService.Tests.csproj:*</span><span class="sxs-lookup"><span data-stu-id="fe903-126">The generated template configures the test runner in the *PrimeService.Tests.csproj* file:</span></span>

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

<span data-ttu-id="fe903-127">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="fe903-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="fe903-128">`dotnet new`w poprzednim kroku dodano zestaw SDK testów firmy Microsoft, platformę testową NUnit i kartę testową NUnit.</span><span class="sxs-lookup"><span data-stu-id="fe903-128">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="fe903-129">Teraz dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="fe903-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="fe903-130">Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="fe903-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="fe903-131">Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) w uspolu GitHub.</span><span class="sxs-lookup"><span data-stu-id="fe903-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="fe903-132">Poniższy konspekt przedstawia ostateczny układ rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="fe903-132">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

<span data-ttu-id="fe903-133">Wykonaj następujące polecenie w katalogu jednostek testujących jednostkę:Execute the following command in the *unit-testing-using-nunit directory:*</span><span class="sxs-lookup"><span data-stu-id="fe903-133">Execute the following command in the *unit-testing-using-nunit* directory:</span></span>

```dotnetcli
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="fe903-134">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="fe903-134">Creating the first test</span></span>

<span data-ttu-id="fe903-135">Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="fe903-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="fe903-136">W katalogu *PrimeService.Tests* zmień nazwę *pliku UnitTest1.cs* na *PrimeService_IsPrimeShould.cs* i zastąp całą jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="fe903-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.cs* file to *PrimeService_IsPrimeShould.cs* and replace its entire contents with the following code:</span></span>

[!code-csharp[Sample_FirstTest](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_FirstTest)]

<span data-ttu-id="fe903-137">Atrybut `[TestFixture]` oznacza klasę, która zawiera testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="fe903-137">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="fe903-138">Atrybut `[Test]` wskazuje, że metoda jest metodą testową.</span><span class="sxs-lookup"><span data-stu-id="fe903-138">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="fe903-139">Zapisz ten plik [`dotnet test`](../tools/dotnet-test.md) i wykonaj, aby utworzyć testy i biblioteki klas, a następnie uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="fe903-139">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="fe903-140">Program testowy NUnit zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="fe903-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="fe903-141">`dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="fe903-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="fe903-142">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="fe903-142">Your test fails.</span></span> <span data-ttu-id="fe903-143">Implementacja nie została jeszcze utworzona.</span><span class="sxs-lookup"><span data-stu-id="fe903-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="fe903-144">Zrób ten test przejść, pisząc najprostszy kod w `PrimeService` klasie, która działa:</span><span class="sxs-lookup"><span data-stu-id="fe903-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="fe903-145">W katalogu *unit-testing-using-nunit* `dotnet test` uruchom ponownie.</span><span class="sxs-lookup"><span data-stu-id="fe903-145">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="fe903-146">Polecenie `dotnet test` uruchamia kompilację `PrimeService` dla projektu, `PrimeService.Tests` a następnie dla projektu.</span><span class="sxs-lookup"><span data-stu-id="fe903-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="fe903-147">Po zbudowaniu obu projektów uruchamia ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="fe903-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="fe903-148">Mija.</span><span class="sxs-lookup"><span data-stu-id="fe903-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="fe903-149">Dodawanie kolejnych funkcji</span><span class="sxs-lookup"><span data-stu-id="fe903-149">Adding more features</span></span>

<span data-ttu-id="fe903-150">Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="fe903-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="fe903-151">Istnieje kilka innych prostych przypadków liczb pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="fe903-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="fe903-152">Można dodać nowe testy `[Test]` z atrybutem, ale szybko staje się żmudne.</span><span class="sxs-lookup"><span data-stu-id="fe903-152">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="fe903-153">Istnieją inne atrybuty Jednostki Jednostki, które umożliwiają pisanie zestawu podobnych testów.</span><span class="sxs-lookup"><span data-stu-id="fe903-153">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="fe903-154">Atrybut `[TestCase]` służy do tworzenia zestawu testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="fe903-154">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="fe903-155">Atrybutu `[TestCase]` można użyć do określenia wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="fe903-155">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="fe903-156">Zamiast tworzyć nowe testy, należy zastosować ten atrybut, aby utworzyć test oparty na pojedynczej podstawie danych.</span><span class="sxs-lookup"><span data-stu-id="fe903-156">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="fe903-157">Test oparty na danych jest metodą, która testuje kilka wartości mniej niż dwie, co jest najniższą liczbą pierwszą:</span><span class="sxs-lookup"><span data-stu-id="fe903-157">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="fe903-158">Uruchom `dotnet test`, a dwa z tych testów nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="fe903-158">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="fe903-159">Aby wszystkie testy zostały zdatce, zmień `if` `Main` klauzulę na początku metody w *pliku PrimeService.cs:*</span><span class="sxs-lookup"><span data-stu-id="fe903-159">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="fe903-160">Kontynuuj iterowanie, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="fe903-160">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="fe903-161">Masz [gotową wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs)</span><span class="sxs-lookup"><span data-stu-id="fe903-161">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="fe903-162">Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="fe903-162">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="fe903-163">Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fe903-163">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="fe903-164">Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe903-164">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
