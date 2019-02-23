---
title: Testy jednostkowe F# platformie .NET Core za pomocą polecenia dotnet test i NUnit
description: Informacje na temat testów jednostek dla F# platformy .NET Core za pomocą interaktywnych doświadczenia przykładowe rozwiązanie krok po kroku za pomocą polecenia dotnet test i NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 384d0ac9f36f9ef9daba851f52d577d97248cd67
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746049"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="4789a-103">Testy jednostkowe F# bibliotek w programie .NET Core za pomocą polecenia dotnet test i NUnit</span><span class="sxs-lookup"><span data-stu-id="4789a-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="4789a-104">Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="4789a-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="4789a-105">Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) przed przystąpieniem do wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4789a-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="4789a-106">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="4789a-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4789a-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4789a-107">Prerequisites</span></span>

- <span data-ttu-id="4789a-108">[Zestaw SDK programu .NET core 2.1](https://www.microsoft.com/net/download) lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="4789a-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="4789a-109">Edytor tekstu lub ulubionego edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="4789a-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="4789a-110">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="4789a-110">Creating the source project</span></span>

<span data-ttu-id="4789a-111">Otwieranie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="4789a-111">Open a shell window.</span></span> <span data-ttu-id="4789a-112">Utwórz katalog o nazwie *jednostki — testowanie z fsharp* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4789a-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="4789a-113">Wewnątrz tego nowy katalog uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:</span><span class="sxs-lookup"><span data-stu-id="4789a-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="4789a-114">Następnie należy utworzyć *MathService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="4789a-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="4789a-115">Następujące konspektu przedstawia strukturę katalogów i plików do tej pory:</span><span class="sxs-lookup"><span data-stu-id="4789a-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="4789a-116">Wprowadź *MathService* bieżącego katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:</span><span class="sxs-lookup"><span data-stu-id="4789a-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang F#
```

<span data-ttu-id="4789a-117">Możesz tworzyć niepowodzenie stosowania usługi matematyczne:</span><span class="sxs-lookup"><span data-stu-id="4789a-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="4789a-118">Zmień katalog kopii do *jednostki — testowanie z fsharp* katalogu.</span><span class="sxs-lookup"><span data-stu-id="4789a-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="4789a-119">Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="4789a-119">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="4789a-120">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="4789a-120">Creating the test project</span></span>

<span data-ttu-id="4789a-121">Następnie należy utworzyć *MathService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="4789a-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="4789a-122">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="4789a-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="4789a-123">Wprowadź *MathService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt, używając następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="4789a-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang F#
```

<span data-ttu-id="4789a-124">Spowoduje to utworzenie projektu testowego, który używa NUnit jako struktury testowej.</span><span class="sxs-lookup"><span data-stu-id="4789a-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="4789a-125">Wygenerowany szablon konfiguruje narzędzie test runner w *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="4789a-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="4789a-126">Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="4789a-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="4789a-127">`dotnet new` w poprzednim kroku należy dodać kartę testu NUnit i NUnit.</span><span class="sxs-lookup"><span data-stu-id="4789a-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="4789a-128">Teraz Dodaj `MathService` biblioteki klas jako inny zależności do projektu.</span><span class="sxs-lookup"><span data-stu-id="4789a-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="4789a-129">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="4789a-129">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="4789a-130">Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="4789a-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="4789a-131">Masz następujące układ ostateczne rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="4789a-131">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathService.Tests.fsproj
```

<span data-ttu-id="4789a-132">Wykonaj następujące polecenie w *jednostki — testowanie z fsharp* katalogu:</span><span class="sxs-lookup"><span data-stu-id="4789a-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```console
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="4789a-133">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="4789a-133">Creating the first test</span></span>

<span data-ttu-id="4789a-134">Jeden zapisu kończy się niepowodzeniem testu, ułatwiają — dostęp próbny, a następnie powtórz ten proces.</span><span class="sxs-lookup"><span data-stu-id="4789a-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="4789a-135">Otwórz *UnitTest1.fs* i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4789a-135">Open *UnitTest1.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

<span data-ttu-id="4789a-136">`[<TestFixture>]` Atrybut wskazuje klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="4789a-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="4789a-137">`[<Test>]` Atrybut oznacza metodę testową, która jest uruchamiany przez narzędzie test runner.</span><span class="sxs-lookup"><span data-stu-id="4789a-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="4789a-138">Z *jednostki — testowanie z fsharp* katalogu, wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="4789a-138">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="4789a-139">Moduł uruchamiający NUnit zawiera punkt wejścia programu, aby uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="4789a-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="4789a-140">`dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="4789a-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="4789a-141">Testy te dwa Pokaż najbardziej podstawowym, przekazywanie i niepowodzenie testów.</span><span class="sxs-lookup"><span data-stu-id="4789a-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="4789a-142">`My test` przekazuje, i `Fail every time` zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="4789a-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="4789a-143">Teraz Utwórz test `squaresOfOdds` metody.</span><span class="sxs-lookup"><span data-stu-id="4789a-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="4789a-144">`squaresOfOdds` Metoda zwraca sekwencję kwadratów wszystkie wartości nieparzystej liczby całkowitej, które są częścią sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="4789a-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="4789a-145">Zamiast próbowania zapisać wszystkie te funkcje na raz, iteracyjne można tworzyć testy, które sprawdzają poprawność funkcji.</span><span class="sxs-lookup"><span data-stu-id="4789a-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="4789a-146">Dzięki czemu każdy przebieg sprowadza się do utworzenia niezbędnych funkcji dla metody testu.</span><span class="sxs-lookup"><span data-stu-id="4789a-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="4789a-147">Najprostsza testów, możemy napisać jest wywołanie `squaresOfOdds` z wszystkie liczby parzyste z zakresu, gdzie powinna zostać pustą sekwencją liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="4789a-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="4789a-148">Oto tego testu:</span><span class="sxs-lookup"><span data-stu-id="4789a-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="4789a-149">Należy zauważyć, że `expected` sekwencji została przekonwertowana na listę.</span><span class="sxs-lookup"><span data-stu-id="4789a-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="4789a-150">NUnit framework opiera się na różnych typach .NET standard.</span><span class="sxs-lookup"><span data-stu-id="4789a-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="4789a-151">Czy zależności oznacza, że Twoje interfejsu publicznego i oczekiwane wyniki pomocy technicznej <xref:System.Collections.ICollection> zamiast <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="4789a-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="4789a-152">Po uruchomieniu testu, zobaczysz, że test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="4789a-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="4789a-153">Nie utworzono jeszcze wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="4789a-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="4789a-154">Wprowadź ten test, przekazać przez napisanie kodu najprostsza *Library.fs* klasy w projekcie MathService, który działa:</span><span class="sxs-lookup"><span data-stu-id="4789a-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="4789a-155">W *jednostki — testowanie z fsharp* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="4789a-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="4789a-156">`dotnet test` Polecenie uruchamia kompilację dla `MathService` projektu i następnie `MathService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="4789a-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="4789a-157">Po utworzeniu obu projektów, jest uruchamiane testy.</span><span class="sxs-lookup"><span data-stu-id="4789a-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="4789a-158">Teraz kod przechodzi dwa testy.</span><span class="sxs-lookup"><span data-stu-id="4789a-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="4789a-159">Korzystanie z wymaganiami</span><span class="sxs-lookup"><span data-stu-id="4789a-159">Completing the requirements</span></span>

<span data-ttu-id="4789a-160">Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="4789a-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="4789a-161">Dalej prostym przypadku współpracuje z sekwencji jest liczbą nieparzystą tylko `1`.</span><span class="sxs-lookup"><span data-stu-id="4789a-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="4789a-162">Numer 1 jest łatwiejsze, ponieważ kwadrat 1 jest 1.</span><span class="sxs-lookup"><span data-stu-id="4789a-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="4789a-163">Oto tego Następny test:</span><span class="sxs-lookup"><span data-stu-id="4789a-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="4789a-164">Wykonywanie `dotnet test` nie powiedzie się nowy test.</span><span class="sxs-lookup"><span data-stu-id="4789a-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="4789a-165">Należy zaktualizować `squaresOfOdds` metody, aby obsłużyć ten nowy test.</span><span class="sxs-lookup"><span data-stu-id="4789a-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="4789a-166">Należy filtrować wszystkie liczby parzyste poza kolejnością, aby ten przebieg testu.</span><span class="sxs-lookup"><span data-stu-id="4789a-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="4789a-167">Możesz to zrobić przez pisanie funkcji filtru małe i przy użyciu `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="4789a-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="4789a-168">Zwróć uwagę, wywołanie `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="4789a-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="4789a-169">Który tworzy listę, która implementuje <xref:System.Collections.ICollection> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4789a-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="4789a-170">Istnieje jeszcze jeden krok do: każdej liczby nieparzyste kwadratowe.</span><span class="sxs-lookup"><span data-stu-id="4789a-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="4789a-171">Rozpocznij od pisania nowego testu:</span><span class="sxs-lookup"><span data-stu-id="4789a-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="4789a-172">Test można naprawić przez przekazanie w potoku filtrowane sekwencji za pomocą operacji mapy do obliczenia kwadratowy poszczególnych nieparzysta:</span><span class="sxs-lookup"><span data-stu-id="4789a-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="4789a-173">Gdy masz utworzoną małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="4789a-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="4789a-174">Tak, aby dodawania nowych pakietów została ze strukturą rozwiązania i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4789a-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="4789a-175">Po skoncentrowany większość czasu i wysiłku niewiele rozwiązywania cele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4789a-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>