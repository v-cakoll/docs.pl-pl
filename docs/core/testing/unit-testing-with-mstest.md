---
title: Jednostka testowania C# .NET Core i MSTest
description: Dowiedz się pojęcia testu jednostki w języku C# i .NET Core za pośrednictwem interaktywnego środowisko tworzenia przykładowe rozwiązanie krok po kroku przy użyciu platformy dotnet testu i MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: 6cfc389a1ee526d8dc4383c5efd6fb3299eb08d8
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105605"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="32f96-103">Jednostka testowania C# .NET Core i MSTest</span><span class="sxs-lookup"><span data-stu-id="32f96-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="32f96-104">Ten samouczek przedstawia interaktywna tworzenia przykładowe rozwiązanie krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="32f96-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="32f96-105">Jeśli chcesz wykonać czynności opisane w samouczku za pomocą wbudowanych rozwiązania, [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="32f96-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="32f96-106">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="32f96-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="32f96-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="32f96-107">Creating the source project</span></span>

<span data-ttu-id="32f96-108">Umożliwia otwarcie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="32f96-108">Open a shell window.</span></span> <span data-ttu-id="32f96-109">Utwórz katalog o nazwie *jednostki — testowanie — przy użyciu mstest* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="32f96-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="32f96-110">Wewnątrz tego nowego katalogu Uruchom [ `dotnet new sln` ](../tools/dotnet-new.md) do utworzenia nowego pliku rozwiązania dla biblioteki klas i projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="32f96-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="32f96-111">Następnie należy utworzyć *PrimeService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="32f96-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="32f96-112">Następujące konspektu dotychczasowych przedstawia strukturę katalogów i plików:</span><span class="sxs-lookup"><span data-stu-id="32f96-112">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="32f96-113">Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib` ](../tools/dotnet-new.md) do tworzenia projektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="32f96-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="32f96-114">Zmień nazwę *Class1.cs* do *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="32f96-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="32f96-115">Aby użyć projektowanie oparte na testach (TDD), należy utworzyć niepowodzenie wykonania `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="32f96-115">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="32f96-116">Zmień katalog z powrotem do *jednostki — testowanie — przy użyciu mstest* katalogu.</span><span class="sxs-lookup"><span data-stu-id="32f96-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="32f96-117">Uruchom [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="32f96-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span> 

### <a name="creating-the-test-project"></a><span data-ttu-id="32f96-118">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="32f96-118">Creating the test project</span></span>

<span data-ttu-id="32f96-119">Następnie należy utworzyć *PrimeService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="32f96-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="32f96-120">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="32f96-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="32f96-121">Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new mstest` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="32f96-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="32f96-122">Nowe polecenie dotnet tworzy projekt testowy używającą MStest jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="32f96-122">The dotnet new command creates a test project that uses MStest as the test library.</span></span> <span data-ttu-id="32f96-123">Wygenerowanego szablonu konfiguruje uruchamiający w *PrimeServiceTests.csproj* pliku:</span><span class="sxs-lookup"><span data-stu-id="32f96-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="32f96-124">Projekt testowy wymaga inne pakiety do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="32f96-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="32f96-125">`dotnet new` w poprzednim kroku, dodać zestawu SDK MSTest, MSTest testowania framework i MSTest runner.</span><span class="sxs-lookup"><span data-stu-id="32f96-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="32f96-126">Teraz Dodaj `PrimeService` biblioteki klas jako zależność od innego projektu.</span><span class="sxs-lookup"><span data-stu-id="32f96-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="32f96-127">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="32f96-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="32f96-128">Widoczny cały plik w [przykłady repozytorium](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="32f96-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="32f96-129">Następujące konspektu przedstawiono układu ostatecznego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="32f96-129">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="32f96-130">Wykonanie [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) w *testowania — przy użyciu dotnet testu jednostkowego* katalogu.</span><span class="sxs-lookup"><span data-stu-id="32f96-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="32f96-131">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="32f96-131">Creating the first test</span></span>

<span data-ttu-id="32f96-132">Podejście TDD odwołuje się do pisania niepowodzeniu jednego testu, co Przekaż, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="32f96-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="32f96-133">Usuń *UnitTest1.cs* z *PrimeService.Tests* katalogu i Utwórz nowy plik C# o nazwie *PrimeService_IsPrimeShould.cs* o następującej treści:</span><span class="sxs-lookup"><span data-stu-id="32f96-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="32f96-134">`[TestClass]` Atrybut określa klasę, która zawiera testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="32f96-134">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="32f96-135">`[TestMethod]` Atrybut oznacza metodę metody testowej.</span><span class="sxs-lookup"><span data-stu-id="32f96-135">The `[TestMethod]` attribute indicates a method is a test method.</span></span> 

<span data-ttu-id="32f96-136">Zapisz ten plik i wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="32f96-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="32f96-137">Moduł uruchamiający MSTest zawiera punkt wejścia programu do uruchomienia testów.</span><span class="sxs-lookup"><span data-stu-id="32f96-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="32f96-138">`dotnet test` Uruchamia uruchamiający przy użyciu jednostkowy projekt testowy, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="32f96-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="32f96-139">Test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="32f96-139">Your test fails.</span></span> <span data-ttu-id="32f96-140">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="32f96-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="32f96-141">Należy ten test jest przekazywany za pomocą pisania kodu najprostsza w `PrimeService` klasy, która działa:</span><span class="sxs-lookup"><span data-stu-id="32f96-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="32f96-142">W *jednostki — testowanie — przy użyciu mstest* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="32f96-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="32f96-143">`dotnet test` Polecenia uruchamiane kompilacji dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="32f96-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="32f96-144">Po utworzeniu oba projekty, jest uruchamiana ta pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="32f96-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="32f96-145">Przekazuje ono.</span><span class="sxs-lookup"><span data-stu-id="32f96-145">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="32f96-146">Dodawanie więcej funkcji.</span><span class="sxs-lookup"><span data-stu-id="32f96-146">Adding more features</span></span>

<span data-ttu-id="32f96-147">Teraz, kiedy dokonano jeden test przekazać nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="32f96-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="32f96-148">Istnieje kilka innych przypadków proste dla liczb pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="32f96-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="32f96-149">Można dodać nowe testy z `[TestMethod]` atrybut, ale szybko staje się nużące.</span><span class="sxs-lookup"><span data-stu-id="32f96-149">You could add new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="32f96-150">Istnieją inne atrybuty MSTest, które pozwalają na zapis zestaw testów podobne.</span><span class="sxs-lookup"><span data-stu-id="32f96-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="32f96-151">A `[DataTestMethod]`atrybut reprezentuje zestaw testów, wykonanie tego samego kodu, które mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="32f96-151">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="32f96-152">Można użyć `[DataRow]` atrybutu, aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="32f96-152">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="32f96-153">Zamiast tworzyć nowe testy, należy zastosować te atrybuty do utworzenia jednego testu opartego na danych.</span><span class="sxs-lookup"><span data-stu-id="32f96-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="32f96-154">Testu opartego na danych to metoda, która sprawdza kilka wartości mniejszej niż dwa, czyli o najniższej liczbie prime::</span><span class="sxs-lookup"><span data-stu-id="32f96-154">The data driven test is a method that tests several values less than two, which is the lowest prime number: :</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="32f96-155">Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="32f96-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="32f96-156">Aby wszystkie karty testy, należy zmienić `if` klauzuli na początku metody:</span><span class="sxs-lookup"><span data-stu-id="32f96-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="32f96-157">Nadal Iterowanie przez dodanie większej liczby testów, więcej teorii i więcej kodu w bibliotece głównego.</span><span class="sxs-lookup"><span data-stu-id="32f96-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="32f96-158">Masz [Zakończono wersji testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [zakończenia wdrożenia biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="32f96-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="32f96-159">Został utworzony małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="32f96-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="32f96-160">Zostały strukturę rozwiązania, aby dodać nowe pakiety i testów jest częścią Normalny przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="32f96-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="32f96-161">Już skoncentrowany większość czasu i uwagi na temat rozwiązywania problemów celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32f96-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
