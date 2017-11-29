---
title: "Testowanie kodu C# w .NET Core za pomocą testu dotnet i xUnit jednostki"
description: "Dowiedz się pojęcia testu jednostki w języku C# i .NET Core za pośrednictwem interaktywnego środowisko tworzenia przykładowe rozwiązanie krok po kroku przy użyciu platformy dotnet testu i xUnit."
author: ardalis
ms.author: wiwagn
ms.date: 09/08/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 6e986e89d47ba4de9b8563f1a95cb1ae89accc89
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="412e9-103">Badanie C# .NET Core za pomocą testu dotnet i xUnit jednostki</span><span class="sxs-lookup"><span data-stu-id="412e9-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="412e9-104">Ten samouczek przedstawia interaktywna tworzenia przykładowe rozwiązanie krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="412e9-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="412e9-105">Jeśli chcesz wykonać czynności opisane w samouczku za pomocą wbudowanych rozwiązania, [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="412e9-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="412e9-106">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="412e9-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="412e9-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="412e9-107">Creating the source project</span></span>

<span data-ttu-id="412e9-108">Umożliwia otwarcie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="412e9-108">Open a shell window.</span></span> <span data-ttu-id="412e9-109">Utwórz katalog o nazwie *testowania — przy użyciu dotnet testu jednostkowego* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="412e9-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="412e9-110">Wewnątrz tego nowego katalogu Uruchom [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="412e9-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="412e9-111">Ułatwia to zarządzanie biblioteki klas i jednostkowy projekt testowy.</span><span class="sxs-lookup"><span data-stu-id="412e9-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="412e9-112">Utwórz katalog rozwiązania *PrimeService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="412e9-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="412e9-113">Struktura katalogów i plików dotychczasowych jest pokazany poniżej:</span><span class="sxs-lookup"><span data-stu-id="412e9-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="412e9-114">Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib` ](../tools/dotnet-new.md) do tworzenia projektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="412e9-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="412e9-115">Zmień nazwę *Class1.cs* do *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="412e9-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="412e9-116">Aby użyć projektowanie oparte na testach (TDD), należy utworzyć niepowodzenie wykonania `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="412e9-116">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="412e9-117">Zmień katalog z powrotem do *testowania — przy użyciu dotnet testu jednostkowego* katalogu.</span><span class="sxs-lookup"><span data-stu-id="412e9-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span> <span data-ttu-id="412e9-118">Uruchom [ `dotnet sln add .\PrimeService\PrimeService.csproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="412e9-118">Run [`dotnet sln add .\PrimeService\PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="412e9-119">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="412e9-119">Creating the test project</span></span>

<span data-ttu-id="412e9-120">Następnie należy utworzyć *PrimeService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="412e9-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="412e9-121">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="412e9-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="412e9-122">Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new xunit` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="412e9-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="412e9-123">Spowoduje to utworzenie projektu testowego używającą xUnit jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="412e9-123">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="412e9-124">Wygenerowanego szablonu konfiguruje uruchamiający w *PrimeServiceTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="412e9-124">The generated template configures the test runner in the *PrimeServiceTests.csproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="412e9-125">Projekt testowy wymaga inne pakiety do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="412e9-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="412e9-126">`dotnet new`w poprzednim kroku należy dodać xUnit i xUnit modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="412e9-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="412e9-127">Teraz Dodaj `PrimeService` biblioteki klas jako zależność od innego projektu.</span><span class="sxs-lookup"><span data-stu-id="412e9-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="412e9-128">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="412e9-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="412e9-129">Widoczny cały plik w [przykłady repozytorium](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="412e9-129">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="412e9-130">Poniżej przedstawiono układu ostatecznego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="412e9-130">The following shows the final solution layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="412e9-131">Wykonanie [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) w *testowania — przy użyciu dotnet testu jednostkowego* katalogu.</span><span class="sxs-lookup"><span data-stu-id="412e9-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="412e9-132">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="412e9-132">Creating the first test</span></span>

<span data-ttu-id="412e9-133">Podejście TDD odwołuje się do pisania niepowodzeniu jednego testu, co Przekaż, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="412e9-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="412e9-134">Usuń *UnitTest1.cs* z *PrimeService.Tests* katalogu i Utwórz nowy plik C# o nazwie *PrimeService_IsPrimeShould.cs*.</span><span class="sxs-lookup"><span data-stu-id="412e9-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="412e9-135">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="412e9-135">Add the following code:</span></span>

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="412e9-136">`[Fact]` Atrybut wskazuje metody testowej, który jest uruchamiany przez moduł uruchamiający.</span><span class="sxs-lookup"><span data-stu-id="412e9-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="412e9-137">Z *testowania — przy użyciu dotnet testu jednostkowego*, wykonać [ `dotnet test` ](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="412e9-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="412e9-138">Moduł uruchamiający xUnit zawiera punkt wejścia programu do uruchomienia testów.</span><span class="sxs-lookup"><span data-stu-id="412e9-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="412e9-139">`dotnet test`Uruchamia uruchamiający przy użyciu jednostkowy projekt testowy, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="412e9-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="412e9-140">Test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="412e9-140">Your test fails.</span></span> <span data-ttu-id="412e9-141">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="412e9-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="412e9-142">Należy ten test przez pisania kodu najprostsza w `PrimeService` klasy, która działa:</span><span class="sxs-lookup"><span data-stu-id="412e9-142">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="412e9-143">W *testowania — przy użyciu dotnet testu jednostkowego* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="412e9-143">In the *unit-testing-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="412e9-144">`dotnet test` Polecenia uruchamiane kompilacji dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="412e9-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="412e9-145">Po utworzeniu oba projekty, jest uruchamiana ta pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="412e9-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="412e9-146">Przekazuje ono.</span><span class="sxs-lookup"><span data-stu-id="412e9-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="412e9-147">Dodawanie więcej funkcji.</span><span class="sxs-lookup"><span data-stu-id="412e9-147">Adding more features</span></span>

<span data-ttu-id="412e9-148">Teraz, kiedy dokonano jeden test przekazać nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="412e9-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="412e9-149">Istnieje kilka innych przypadków proste dla liczb pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="412e9-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="412e9-150">Możesz dodać tych przypadkach jako nowe testy z `[Fact]` atrybut, ale szybko staje się nużące.</span><span class="sxs-lookup"><span data-stu-id="412e9-150">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="412e9-151">Istnieją inne atrybuty xUnit, które pozwalają na zapis zestaw testów podobne.</span><span class="sxs-lookup"><span data-stu-id="412e9-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="412e9-152">A `[Theory]` atrybut reprezentuje zestaw testów, wykonanie tego samego kodu, które mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="412e9-152">A `[Theory]` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="412e9-153">Można użyć `[InlineData]` atrybutu, aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="412e9-153">You can use the `[InlineData]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="412e9-154">Zamiast tworzyć nowe testy, należy zastosować te atrybuty można utworzyć jeden teorii.</span><span class="sxs-lookup"><span data-stu-id="412e9-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="412e9-155">Teorii jest metodę, która sprawdza kilka wartości mniejszej niż dwa, czyli o najniższej liczbie pierwsze:</span><span class="sxs-lookup"><span data-stu-id="412e9-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="412e9-156">Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="412e9-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="412e9-157">Aby wszystkie karty testy, należy zmienić `if` klauzuli na początku metody:</span><span class="sxs-lookup"><span data-stu-id="412e9-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="412e9-158">Nadal Iterowanie przez dodanie większej liczby testów, więcej teorii i więcej kodu w bibliotece głównego.</span><span class="sxs-lookup"><span data-stu-id="412e9-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="412e9-159">Masz [Zakończono wersji testów](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [zakończenia wdrożenia biblioteki](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="412e9-159">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="412e9-160">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="412e9-160">Additional resources</span></span>

[<span data-ttu-id="412e9-161">Testowanie logiką kontrolera w ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="412e9-161">Testing controller logic in ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)
