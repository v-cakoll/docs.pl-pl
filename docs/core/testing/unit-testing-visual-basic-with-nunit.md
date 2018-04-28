---
title: Badanie Visual Basic .NET Core za pomocą testu dotnet i NUnit jednostki
description: Dowiedz się koncepcje testu jednostki w .NET Core za pośrednictwem interaktywnego środowisko budowania rozwiązania Visual Basic próbki krok po kroku przy użyciu NUnit.
author: rprouse
ms.date: 12/01/2017
ms.topic: conceptual
dev_langs:
- vb
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: b275d1da2c46b1ba8376bf0a77b4dcb8d6f76445
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="64a02-103">Biblioteki języka Visual Basic .NET Core za pomocą testu dotnet i NUnit testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="64a02-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="64a02-104">Ten samouczek przedstawia interaktywna tworzenia przykładowe rozwiązanie krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="64a02-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="64a02-105">Jeśli chcesz wykonać czynności opisane w samouczku za pomocą wbudowanych rozwiązania, [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="64a02-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="64a02-106">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="64a02-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="64a02-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="64a02-107">Creating the source project</span></span>

<span data-ttu-id="64a02-108">Umożliwia otwarcie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="64a02-108">Open a shell window.</span></span> <span data-ttu-id="64a02-109">Utwórz katalog o nazwie *jednostki — testowanie vb-nunit* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="64a02-109">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="64a02-110">Wewnątrz tego nowego katalogu Uruchom [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="64a02-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="64a02-111">Takie rozwiązanie ułatwia zarządzanie biblioteki klas i jednostkowy projekt testowy.</span><span class="sxs-lookup"><span data-stu-id="64a02-111">This practice makes it easier to manage both the class library and the unit test project.</span></span> <span data-ttu-id="64a02-112">Utwórz katalog rozwiązania *PrimeService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="64a02-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="64a02-113">Masz dotychczasowych następującą strukturę katalogów i plików:</span><span class="sxs-lookup"><span data-stu-id="64a02-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="64a02-114">Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) do tworzenia projektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="64a02-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="64a02-115">Zmień nazwę *Class1.VB* do *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="64a02-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="64a02-116">Aby użyć projektowanie oparte na testach (TDD), należy utworzyć niepowodzenie wykonania `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="64a02-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="64a02-117">Zmień katalog z powrotem do *jednostki — testowanie vb — przy użyciu stest* katalogu.</span><span class="sxs-lookup"><span data-stu-id="64a02-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="64a02-118">Uruchom [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="64a02-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="64a02-119">Zainstaluj NUnit szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="64a02-119">Install the NUnit project template</span></span>

<span data-ttu-id="64a02-120">NUnit przetestować projekt, który szablony muszą być zainstalowane przed utworzeniem projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="64a02-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="64a02-121">To tylko należy jednak wykonać jeden raz na każdym komputerze dewelopera, w których zostaną utworzone nowe projekty NUnit.</span><span class="sxs-lookup"><span data-stu-id="64a02-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="64a02-122">Uruchom [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) zainstalować szablony NUnit.</span><span class="sxs-lookup"><span data-stu-id="64a02-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="64a02-123">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="64a02-123">Creating the test project</span></span>

<span data-ttu-id="64a02-124">Następnie należy utworzyć *PrimeService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="64a02-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="64a02-125">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="64a02-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="64a02-126">Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new nunit -lang VB` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="64a02-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="64a02-127">To polecenie tworzy projekt testowy używającą NUnit jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="64a02-127">This command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="64a02-128">Wygenerowanego szablonu konfiguruje uruchamiający w *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="64a02-128">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="64a02-129">Projekt testowy wymaga inne pakiety do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="64a02-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="64a02-130">`dotnet new` w poprzednim kroku dodać NUnit i NUnit adapter testowy.</span><span class="sxs-lookup"><span data-stu-id="64a02-130">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="64a02-131">Teraz Dodaj `PrimeService` biblioteki klas jako zależność od innego projektu.</span><span class="sxs-lookup"><span data-stu-id="64a02-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="64a02-132">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="64a02-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="64a02-133">Widoczny cały plik w [przykłady repozytorium](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="64a02-133">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="64a02-134">Masz następujące układu ostatecznego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="64a02-134">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="64a02-135">Wykonanie [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) w *jednostki — testowanie vb-nunit* katalogu.</span><span class="sxs-lookup"><span data-stu-id="64a02-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-nunit* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="64a02-136">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="64a02-136">Creating the first test</span></span>

<span data-ttu-id="64a02-137">Podejście TDD odwołuje się do pisania niepowodzeniu jednego testu, co Przekaż, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="64a02-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="64a02-138">Usuń *UnitTest1.vb* z *PrimeService.Tests* katalogu i Utwórz nowy plik Visual Basic o nazwie *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="64a02-138">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="64a02-139">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="64a02-139">Add the following code:</span></span>

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

<span data-ttu-id="64a02-140">`<TestFixture>` Atrybut wskazuje klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="64a02-140">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="64a02-141">`<Test>` Atrybut oznacza metodę, która jest uruchamiana przez moduł uruchamiający.</span><span class="sxs-lookup"><span data-stu-id="64a02-141">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="64a02-142">Z *jednostki — testowanie vb-nunit*, wykonać [ `dotnet test` ](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="64a02-142">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="64a02-143">Moduł uruchamiający NUnit zawiera punkt wejścia programu do uruchomienia testów.</span><span class="sxs-lookup"><span data-stu-id="64a02-143">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="64a02-144">`dotnet test` Uruchamia uruchamiający przy użyciu jednostkowy projekt testowy, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="64a02-144">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="64a02-145">Test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="64a02-145">Your test fails.</span></span> <span data-ttu-id="64a02-146">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="64a02-146">You haven't created the implementation yet.</span></span> <span data-ttu-id="64a02-147">Należy ten test przez pisania kodu najprostsza w `PrimeService` klasy, która działa:</span><span class="sxs-lookup"><span data-stu-id="64a02-147">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="64a02-148">W *jednostki — testowanie vb-nunit* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="64a02-148">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="64a02-149">`dotnet test` Polecenia uruchamiane kompilacji dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="64a02-149">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="64a02-150">Po utworzeniu oba projekty, jest uruchamiana ta pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="64a02-150">After building both projects, it runs this single test.</span></span> <span data-ttu-id="64a02-151">Przekazuje ono.</span><span class="sxs-lookup"><span data-stu-id="64a02-151">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="64a02-152">Dodawanie więcej funkcji.</span><span class="sxs-lookup"><span data-stu-id="64a02-152">Adding more features</span></span>

<span data-ttu-id="64a02-153">Teraz, kiedy dokonano jeden test przekazać nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="64a02-153">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="64a02-154">Istnieje kilka innych przypadków proste dla liczb pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="64a02-154">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="64a02-155">Możesz dodać tych przypadkach jako nowe testy z `<Test>` atrybut, ale szybko staje się nużące.</span><span class="sxs-lookup"><span data-stu-id="64a02-155">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="64a02-156">Istnieją inne atrybuty xUnit, które pozwalają na zapis zestaw testów podobne.</span><span class="sxs-lookup"><span data-stu-id="64a02-156">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="64a02-157">A `<TestCase>` atrybut reprezentuje zestaw testów, wykonanie tego samego kodu, które mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="64a02-157">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="64a02-158">Można użyć `<TestCase>` atrybutu, aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="64a02-158">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="64a02-159">Zamiast tworzyć nowe testy, stosuje się te atrybuty do utworzenia serii testów, które test kilku wartości mniejszej niż dwa, czyli o najniższej liczbie pierwsze:</span><span class="sxs-lookup"><span data-stu-id="64a02-159">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="64a02-160">Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="64a02-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="64a02-161">Aby wszystkie karty testy, należy zmienić `if` klauzuli na początku metody:</span><span class="sxs-lookup"><span data-stu-id="64a02-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="64a02-162">Nadal Iterowanie przez dodanie większej liczby testów, więcej teorii i więcej kodu w bibliotece głównego.</span><span class="sxs-lookup"><span data-stu-id="64a02-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="64a02-163">Masz [Zakończono wersji testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [zakończenia wdrożenia biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="64a02-163">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="64a02-164">Został utworzony małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="64a02-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="64a02-165">Zostały strukturę rozwiązania, aby dodać nowe pakiety i testów jest częścią Normalny przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="64a02-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="64a02-166">Już skoncentrowany większość czasu i uwagi na temat rozwiązywania problemów celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64a02-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
