---
title: Testowanie jednostkowe C# z MSTest i .NET Core
description: Poznaj pojęcia dotyczące testów jednostkowych w językach C# i .NET Core, korzystając z interakcyjnego środowiska, które krok po kroku przy użyciu testu dotnet i programu MSTest jest oparte na interakcyjnym środowisku, w ramach tworzenia przykładowego rozwiązania.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: bd7891243d84277a7578089f8b4629ff5bada577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240912"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="6ddec-103">Testowanie jednostkowe C# z MSTest i .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ddec-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="6ddec-104">W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="6ddec-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="6ddec-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="6ddec-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="6ddec-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="6ddec-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="create-the-source-project"></a><span data-ttu-id="6ddec-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="6ddec-107">Create the source project</span></span>

<span data-ttu-id="6ddec-108">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="6ddec-108">Open a shell window.</span></span> <span data-ttu-id="6ddec-109">Utwórz katalog o nazwie *unit-testing-using-mstest* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6ddec-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="6ddec-110">Wewnątrz tego nowego [`dotnet new sln`](../tools/dotnet-new.md) katalogu uruchom, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="6ddec-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="6ddec-111">Następnie utwórz katalog *PrimeService.*</span><span class="sxs-lookup"><span data-stu-id="6ddec-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="6ddec-112">Poniższy konspekt pokazuje do tej pory strukturę katalogów i plików:</span><span class="sxs-lookup"><span data-stu-id="6ddec-112">The following outline shows the directory and file structure thus far:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="6ddec-113">Utwórz *PrimeService* bieżący [`dotnet new classlib`](../tools/dotnet-new.md) katalog i uruchom, aby utworzyć projekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="6ddec-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="6ddec-114">Zmień nazwę *Class1.cs* na *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="6ddec-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="6ddec-115">Tworzenie nieudanej implementacji `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="6ddec-115">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="6ddec-116">Zmień katalog z powrotem do katalogu *testów jednostkowych przy użyciu mstest.*</span><span class="sxs-lookup"><span data-stu-id="6ddec-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="6ddec-117">Uruchom, [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) aby dodać projekt biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6ddec-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="create-the-test-project"></a><span data-ttu-id="6ddec-118">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="6ddec-118">Create the test project</span></span>

<span data-ttu-id="6ddec-119">Następnie utwórz katalog *PrimeService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="6ddec-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="6ddec-120">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="6ddec-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="6ddec-121">Utwórz katalog *PrimeService.Tests* jako bieżący katalog [`dotnet new mstest`](../tools/dotnet-new.md)i utwórz nowy projekt przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="6ddec-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="6ddec-122">Dotnet nowe polecenie tworzy projekt testowy, który używa MSTest jako biblioteki testowej.</span><span class="sxs-lookup"><span data-stu-id="6ddec-122">The dotnet new command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="6ddec-123">Wygenerowany szablon konfiguruje testrunner w pliku *PrimeServiceTests.csproj:*</span><span class="sxs-lookup"><span data-stu-id="6ddec-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="6ddec-124">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="6ddec-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="6ddec-125">`dotnet new`w poprzednim kroku dodano zestaw MSTest SDK, platformę testową MSTest i program mstest runner.</span><span class="sxs-lookup"><span data-stu-id="6ddec-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="6ddec-126">Teraz dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="6ddec-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="6ddec-127">Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="6ddec-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="6ddec-128">Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) w uspolu GitHub.</span><span class="sxs-lookup"><span data-stu-id="6ddec-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="6ddec-129">Poniższy konspekt przedstawia ostateczny układ rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="6ddec-129">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="6ddec-130">Wykonywanie [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) w katalogu *testów jednostkowych przy użyciu-mstest.*</span><span class="sxs-lookup"><span data-stu-id="6ddec-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-mstest* directory.</span></span>

## <a name="create-the-first-test"></a><span data-ttu-id="6ddec-131">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="6ddec-131">Create the first test</span></span>

<span data-ttu-id="6ddec-132">Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="6ddec-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="6ddec-133">Usuń *UnitTest1.cs* z katalogu *PrimeService.Tests* i utwórz nowy plik C# o nazwie *PrimeService_IsPrimeShould.cs* z następującą zawartością:</span><span class="sxs-lookup"><span data-stu-id="6ddec-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="6ddec-134">[Atrybut TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) oznacza klasę, która zawiera testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="6ddec-134">The [TestClass attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) denotes a class that contains unit tests.</span></span> <span data-ttu-id="6ddec-135">[TestMethod Atrybut](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) wskazuje, że metoda jest metodą testową.</span><span class="sxs-lookup"><span data-stu-id="6ddec-135">The [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) indicates a method is a test method.</span></span>

<span data-ttu-id="6ddec-136">Zapisz ten plik [`dotnet test`](../tools/dotnet-test.md) i wykonaj, aby utworzyć testy i biblioteki klas, a następnie uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="6ddec-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="6ddec-137">Program testowy MSTest zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="6ddec-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="6ddec-138">`dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="6ddec-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="6ddec-139">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="6ddec-139">Your test fails.</span></span> <span data-ttu-id="6ddec-140">Implementacja nie została jeszcze utworzona.</span><span class="sxs-lookup"><span data-stu-id="6ddec-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="6ddec-141">Zrób ten test przejść, pisząc najprostszy kod w `PrimeService` klasie, która działa:</span><span class="sxs-lookup"><span data-stu-id="6ddec-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="6ddec-142">W katalogu *testów jednostkowych-using-mstest* uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="6ddec-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="6ddec-143">Polecenie `dotnet test` uruchamia kompilację `PrimeService` dla projektu, `PrimeService.Tests` a następnie dla projektu.</span><span class="sxs-lookup"><span data-stu-id="6ddec-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="6ddec-144">Po zbudowaniu obu projektów uruchamia ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="6ddec-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="6ddec-145">Mija.</span><span class="sxs-lookup"><span data-stu-id="6ddec-145">It passes.</span></span>

## <a name="add-more-features"></a><span data-ttu-id="6ddec-146">Dodaj więcej funkcji</span><span class="sxs-lookup"><span data-stu-id="6ddec-146">Add more features</span></span>

<span data-ttu-id="6ddec-147">Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="6ddec-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="6ddec-148">Istnieje kilka innych prostych przypadków liczb pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="6ddec-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="6ddec-149">Można dodać nowe testy z [TestMethod atrybut](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), ale szybko staje się żmudne.</span><span class="sxs-lookup"><span data-stu-id="6ddec-149">You could add new tests with the [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), but that quickly becomes tedious.</span></span> <span data-ttu-id="6ddec-150">Istnieją inne atrybuty MSTest, które umożliwiają pisanie zestawu podobnych testów.</span><span class="sxs-lookup"><span data-stu-id="6ddec-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="6ddec-151">[Atrybut DataTestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="6ddec-151">A [DataTestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="6ddec-152">Atrybut [DataRow](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) służy do określania wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6ddec-152">You can use the [DataRow attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) to specify values for those inputs.</span></span>

<span data-ttu-id="6ddec-153">Zamiast tworzyć nowe testy, należy zastosować te dwa atrybuty, aby utworzyć pojedynczy test oparty na danych.</span><span class="sxs-lookup"><span data-stu-id="6ddec-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="6ddec-154">Test oparty na danych jest metodą, która testuje kilka wartości mniej niż dwie, co jest najniższą liczbą pierwszą:</span><span class="sxs-lookup"><span data-stu-id="6ddec-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-mstest/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="6ddec-155">Uruchom `dotnet test`, a dwa z tych testów nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="6ddec-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="6ddec-156">Aby wszystkie testy zostały zdatce, zmień klauzulę `if` na początku metody:</span><span class="sxs-lookup"><span data-stu-id="6ddec-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="6ddec-157">Kontynuuj iterowanie, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej.</span><span class="sxs-lookup"><span data-stu-id="6ddec-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="6ddec-158">Masz [gotową wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)</span><span class="sxs-lookup"><span data-stu-id="6ddec-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="6ddec-159">Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="6ddec-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="6ddec-160">Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6ddec-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="6ddec-161">Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6ddec-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ddec-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ddec-162">See also</span></span>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [<span data-ttu-id="6ddec-163">Używanie struktury MSTest w testach jednostkowych</span><span class="sxs-lookup"><span data-stu-id="6ddec-163">Use the MSTest framework in unit tests</span></span>](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [<span data-ttu-id="6ddec-164">Dokumenty framework testów MSTest V2</span><span class="sxs-lookup"><span data-stu-id="6ddec-164">MSTest V2 test framework docs</span></span>](https://github.com/Microsoft/testfx-docs)
