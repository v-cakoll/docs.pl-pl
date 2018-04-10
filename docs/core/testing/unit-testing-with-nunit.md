---
title: Testowanie C# .NET Core i NUnit jednostki
description: Dowiedz się pojęcia testu jednostki w języku C# i .NET Core za pośrednictwem interaktywnego środowisko tworzenia przykładowe rozwiązanie krok po kroku przy użyciu platformy dotnet testu i NUnit.
keywords: NUnit, .NET, .NET Core
author: rprouse
ms.date: 12/01/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.openlocfilehash: b29912a58511305202a18e8da4ae57700605867a
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="29e1f-104">Testowanie C# .NET Core i NUnit jednostki</span><span class="sxs-lookup"><span data-stu-id="29e1f-104">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="29e1f-105">Ten samouczek przedstawia interaktywna tworzenia przykładowe rozwiązanie krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="29e1f-105">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="29e1f-106">Jeśli chcesz wykonać czynności opisane w samouczku za pomocą wbudowanych rozwiązania, [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="29e1f-106">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="29e1f-107">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="29e1f-107">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="29e1f-108">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="29e1f-108">Creating the source project</span></span>

<span data-ttu-id="29e1f-109">Umożliwia otwarcie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="29e1f-109">Open a shell window.</span></span> <span data-ttu-id="29e1f-110">Utwórz katalog o nazwie *jednostki — testowanie — przy użyciu nunit* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="29e1f-110">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="29e1f-111">Wewnątrz tego nowego katalogu Uruchom [ `dotnet new sln` ](../tools/dotnet-new.md) do utworzenia nowego pliku rozwiązania dla biblioteki klas i projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="29e1f-111">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="29e1f-112">Następnie należy utworzyć *PrimeService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="29e1f-112">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="29e1f-113">Następujące konspektu dotychczasowych przedstawia strukturę katalogów i plików:</span><span class="sxs-lookup"><span data-stu-id="29e1f-113">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="29e1f-114">Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib` ](../tools/dotnet-new.md) do tworzenia projektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="29e1f-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="29e1f-115">Zmień nazwę *Class1.cs* do *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="29e1f-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="29e1f-116">Aby użyć projektowanie oparte na testach (TDD), należy utworzyć niepowodzenie wykonania `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="29e1f-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="29e1f-117">Zmień katalog z powrotem do *jednostki — testowanie — przy użyciu nunit* katalogu.</span><span class="sxs-lookup"><span data-stu-id="29e1f-117">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="29e1f-118">Uruchom [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="29e1f-118">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="29e1f-119">Zainstaluj NUnit szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="29e1f-119">Install the NUnit project template</span></span>

<span data-ttu-id="29e1f-120">NUnit przetestować projekt, który szablony muszą być zainstalowane przed utworzeniem projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="29e1f-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="29e1f-121">To tylko należy jednak wykonać jeden raz na każdym komputerze dewelopera, w których zostaną utworzone nowe projekty NUnit.</span><span class="sxs-lookup"><span data-stu-id="29e1f-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="29e1f-122">Uruchom [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) zainstalować szablony NUnit.</span><span class="sxs-lookup"><span data-stu-id="29e1f-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

```
dotnet new -i NUnit3.DotNetNew.Template
```

### <a name="creating-the-test-project"></a><span data-ttu-id="29e1f-123">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="29e1f-123">Creating the test project</span></span>

<span data-ttu-id="29e1f-124">Następnie należy utworzyć *PrimeService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="29e1f-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="29e1f-125">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="29e1f-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="29e1f-126">Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new nunit` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="29e1f-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="29e1f-127">Nowe polecenie dotnet tworzy projekt testowy używającą NUnit jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="29e1f-127">The dotnet new command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="29e1f-128">Wygenerowanego szablonu konfiguruje uruchamiający w *PrimeServiceTests.csproj* pliku:</span><span class="sxs-lookup"><span data-stu-id="29e1f-128">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="29e1f-129">Projekt testowy wymaga inne pakiety do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="29e1f-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="29e1f-130">`dotnet new` w poprzednim kroku dodać Microsoft test zestawu SDK, struktury testowej NUnit i NUnit adapter testowy.</span><span class="sxs-lookup"><span data-stu-id="29e1f-130">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="29e1f-131">Teraz Dodaj `PrimeService` biblioteki klas jako zależność od innego projektu.</span><span class="sxs-lookup"><span data-stu-id="29e1f-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="29e1f-132">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="29e1f-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="29e1f-133">Widoczny cały plik w [przykłady repozytorium](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="29e1f-133">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="29e1f-134">Następujące konspektu przedstawiono układu ostatecznego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="29e1f-134">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="29e1f-135">Wykonanie [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) w *testowania — przy użyciu dotnet testu jednostkowego* katalogu.</span><span class="sxs-lookup"><span data-stu-id="29e1f-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="29e1f-136">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="29e1f-136">Creating the first test</span></span>

<span data-ttu-id="29e1f-137">Podejście TDD odwołuje się do pisania niepowodzeniu jednego testu, co Przekaż, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="29e1f-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="29e1f-138">Usuń *UnitTest1.cs* z *PrimeService.Tests* katalogu i Utwórz nowy plik C# o nazwie *PrimeService_IsPrimeShould.cs* o następującej treści:</span><span class="sxs-lookup"><span data-stu-id="29e1f-138">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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

<span data-ttu-id="29e1f-139">`[TestFixture]` Atrybut określa klasę, która zawiera testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="29e1f-139">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="29e1f-140">`[Test]` Atrybut oznacza metodę metody testowej.</span><span class="sxs-lookup"><span data-stu-id="29e1f-140">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="29e1f-141">Zapisz ten plik i wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="29e1f-141">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="29e1f-142">Moduł uruchamiający NUnit zawiera punkt wejścia programu do uruchomienia testów.</span><span class="sxs-lookup"><span data-stu-id="29e1f-142">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="29e1f-143">`dotnet test` Uruchamia uruchamiający przy użyciu jednostkowy projekt testowy, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="29e1f-143">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="29e1f-144">Test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="29e1f-144">Your test fails.</span></span> <span data-ttu-id="29e1f-145">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="29e1f-145">You haven't created the implementation yet.</span></span> <span data-ttu-id="29e1f-146">Należy ten test jest przekazywany za pomocą pisania kodu najprostsza w `PrimeService` klasy, która działa:</span><span class="sxs-lookup"><span data-stu-id="29e1f-146">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="29e1f-147">W *jednostki — testowanie — przy użyciu nunit* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="29e1f-147">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="29e1f-148">`dotnet test` Polecenia uruchamiane kompilacji dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="29e1f-148">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="29e1f-149">Po utworzeniu oba projekty, jest uruchamiana ta pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="29e1f-149">After building both projects, it runs this single test.</span></span> <span data-ttu-id="29e1f-150">Przekazuje ono.</span><span class="sxs-lookup"><span data-stu-id="29e1f-150">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="29e1f-151">Dodawanie więcej funkcji.</span><span class="sxs-lookup"><span data-stu-id="29e1f-151">Adding more features</span></span>

<span data-ttu-id="29e1f-152">Teraz, kiedy dokonano jeden test przekazać nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="29e1f-152">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="29e1f-153">Istnieje kilka innych przypadków proste dla liczb pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="29e1f-153">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="29e1f-154">Można dodać nowe testy z `[Test]` atrybut, ale szybko staje się nużące.</span><span class="sxs-lookup"><span data-stu-id="29e1f-154">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="29e1f-155">Istnieją inne atrybuty NUnit, które pozwalają na zapis zestaw testów podobne.</span><span class="sxs-lookup"><span data-stu-id="29e1f-155">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="29e1f-156">A `[TestCase]` atrybut służy do tworzenia zestaw testów, wykonanie tego samego kodu, które mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="29e1f-156">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="29e1f-157">Można użyć `[TestCase]` atrybutu, aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="29e1f-157">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="29e1f-158">Zamiast tworzyć nowe testy, zastosuj ten atrybut można utworzyć jeden testu opartego na danych.</span><span class="sxs-lookup"><span data-stu-id="29e1f-158">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="29e1f-159">Dane zmiennych testu jest metodę, która sprawdza kilka wartości mniejszej niż dwa, czyli o najniższej liczbie prime:</span><span class="sxs-lookup"><span data-stu-id="29e1f-159">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="29e1f-160">Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="29e1f-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="29e1f-161">Aby wszystkie karty testy, należy zmienić `if` klauzuli na początku metody:</span><span class="sxs-lookup"><span data-stu-id="29e1f-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="29e1f-162">Nadal Iterowanie przez dodanie większej liczby testów, więcej teorii i więcej kodu w bibliotece głównego.</span><span class="sxs-lookup"><span data-stu-id="29e1f-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="29e1f-163">Masz [Zakończono wersji testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [zakończenia wdrożenia biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="29e1f-163">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="29e1f-164">Został utworzony małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="29e1f-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="29e1f-165">Zostały strukturę rozwiązania, aby dodać nowe pakiety i testów jest częścią Normalny przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="29e1f-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="29e1f-166">Już skoncentrowany większość czasu i uwagi na temat rozwiązywania problemów celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29e1f-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
