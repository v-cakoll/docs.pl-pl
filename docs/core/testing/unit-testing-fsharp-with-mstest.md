---
title: Testy F# jednostkowe w środowisku .NET Core z testami dotnet i MSTest
description: Poznaj koncepcje testów jednostkowych dla F# platformy .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania krok po kroku przy użyciu testu dotnet i MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 3b93f4ed21d9d5eccf1dd02f253e7456aec02807
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626465"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="75051-103">Biblioteki testów F# jednostkowych w programie .NET Core przy użyciu testu dotnet i MSTest</span><span class="sxs-lookup"><span data-stu-id="75051-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="75051-104">Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="75051-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="75051-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) .</span><span class="sxs-lookup"><span data-stu-id="75051-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="75051-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="75051-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="75051-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="75051-107">Creating the source project</span></span>

<span data-ttu-id="75051-108">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="75051-108">Open a shell window.</span></span> <span data-ttu-id="75051-109">Utwórz katalog o nazwie *Unit-Test-with-FSharp* , aby pomieścić rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="75051-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="75051-110">W tym nowym katalogu Uruchom [`dotnet new sln`](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="75051-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="75051-111">Ułatwia to zarządzanie biblioteką klas i projektem testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="75051-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="75051-112">W katalogu rozwiązania Utwórz katalog *mathservice* .</span><span class="sxs-lookup"><span data-stu-id="75051-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="75051-113">W tej chwili struktura katalogów i plików jest pokazana poniżej:</span><span class="sxs-lookup"><span data-stu-id="75051-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="75051-114">Ustaw *mathservice* w bieżącym katalogu i uruchom [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) , aby utworzyć projekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="75051-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="75051-115">Utworzysz nieprawidłową implementację usługi matematycznej:</span><span class="sxs-lookup"><span data-stu-id="75051-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="75051-116">Zmień katalog z powrotem na katalog *test-z-FSharp* .</span><span class="sxs-lookup"><span data-stu-id="75051-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="75051-117">Uruchom [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) , aby dodać projekt biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="75051-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="75051-118">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="75051-118">Creating the test project</span></span>

<span data-ttu-id="75051-119">Następnie Utwórz katalog *mathservice. Tests* .</span><span class="sxs-lookup"><span data-stu-id="75051-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="75051-120">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="75051-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="75051-121">Utwórz katalog *mathservice. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą [`dotnet new mstest -lang F#`](../tools/dotnet-new.md)polecenia.</span><span class="sxs-lookup"><span data-stu-id="75051-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="75051-122">Spowoduje to utworzenie projektu testowego, który używa MSTest jako środowiska testowego.</span><span class="sxs-lookup"><span data-stu-id="75051-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="75051-123">Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w *MathServiceTests. fsproj*:</span><span class="sxs-lookup"><span data-stu-id="75051-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="75051-124">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="75051-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="75051-125">`dotnet new`w poprzednim kroku dodano MSTest i moduł uruchamiający MSTest.</span><span class="sxs-lookup"><span data-stu-id="75051-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="75051-126">Teraz Dodaj `MathService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="75051-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="75051-127">[`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:</span><span class="sxs-lookup"><span data-stu-id="75051-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="75051-128">Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="75051-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="75051-129">Dysponujesz następującym końcowym układem rozwiązań:</span><span class="sxs-lookup"><span data-stu-id="75051-129">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

<span data-ttu-id="75051-130">Wykonaj [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) w katalogu *test-z-FSharp* .</span><span class="sxs-lookup"><span data-stu-id="75051-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="75051-131">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="75051-131">Creating the first test</span></span>

<span data-ttu-id="75051-132">Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces.</span><span class="sxs-lookup"><span data-stu-id="75051-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="75051-133">Otwórz aplet *testy. FS* i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="75051-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open Microsoft.VisualStudio.TestTools.UnitTesting
open MathService

[<TestClass>]
type TestClass () =

    [<TestMethod>]
    member this.TestMethodPassing() =
        Assert.IsTrue(true)

    [<TestMethod>]
     member this.FailEveryTime() = Assert.IsTrue(false)
```

<span data-ttu-id="75051-134">Ten `[<TestClass>]` atrybut oznacza klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="75051-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="75051-135">Ten `[<TestMethod>]` atrybut oznacza metodę testową, która jest uruchamiana przez program Test Runner.</span><span class="sxs-lookup"><span data-stu-id="75051-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="75051-136">W katalogu *test jednostkowy-with-FSharp* wykonaj [`dotnet test`](../tools/dotnet-test.md) , aby skompilować testy i bibliotekę klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="75051-136">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="75051-137">Program MSTest Test Runner zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="75051-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="75051-138">`dotnet test`uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="75051-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="75051-139">Te dwa testy pokazują najbardziej podstawowe testy dotyczące przekazywania i niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="75051-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="75051-140">`My test``Fail every time` kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="75051-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="75051-141">Teraz Utwórz test dla `squaresOfOdds` metody.</span><span class="sxs-lookup"><span data-stu-id="75051-141">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="75051-142">`squaresOfOdds` Metoda zwraca listę kwadratów wszystkich nieparzystych wartości całkowitych, które są częścią sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="75051-142">The `squaresOfOdds` method returns a list of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="75051-143">Zamiast próbować zapisywać wszystkie te funkcje jednocześnie, można iteracyjnie utworzyć testy, które weryfikują funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="75051-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="75051-144">Każdy przebieg testowy oznacza tworzenie niezbędnych funkcji dla metody.</span><span class="sxs-lookup"><span data-stu-id="75051-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="75051-145">Najprostszym testem możemy napisać jest wywołanie `squaresOfOdds` ze wszystkimi parzystymi liczbami, gdzie wynik powinien być pustą sekwencją liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="75051-145">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="75051-146">Oto test:</span><span class="sxs-lookup"><span data-stu-id="75051-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="75051-147">Zauważ, że `expected` sekwencja została przekonwertowana na listę.</span><span class="sxs-lookup"><span data-stu-id="75051-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="75051-148">Biblioteka MSTest opiera się na wielu standardowych typach .NET.</span><span class="sxs-lookup"><span data-stu-id="75051-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="75051-149">Ta zależność oznacza, że interfejs publiczny i oczekiwane wyniki <xref:System.Collections.ICollection> są obsługiwane <xref:System.Collections.IEnumerable>, a nie.</span><span class="sxs-lookup"><span data-stu-id="75051-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="75051-150">Po uruchomieniu testu zobaczysz, że test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="75051-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="75051-151">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="75051-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="75051-152">Wykonaj ten test, pisząc najprostszy kod w `Mathservice` klasie, która działa:</span><span class="sxs-lookup"><span data-stu-id="75051-152">Make this test pass by writing the simplest code in the `Mathservice` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="75051-153">W katalogu *testy jednostkowe-with-FSharp* Uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="75051-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="75051-154">Polecenie uruchamia kompilację `MathService` dla `MathService.Tests` projektu, a następnie dla projektu. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="75051-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="75051-155">Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="75051-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="75051-156">Przekazuje.</span><span class="sxs-lookup"><span data-stu-id="75051-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="75051-157">Spełnienie wymagań</span><span class="sxs-lookup"><span data-stu-id="75051-157">Completing the requirements</span></span>

<span data-ttu-id="75051-158">Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="75051-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="75051-159">Następny prosty przypadek działa z sekwencją, której jedyną liczbą nieparzystą jest `1`.</span><span class="sxs-lookup"><span data-stu-id="75051-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="75051-160">Numer 1 jest łatwiejszy, ponieważ kwadrat 1 ma wartość 1.</span><span class="sxs-lookup"><span data-stu-id="75051-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="75051-161">Oto następny test:</span><span class="sxs-lookup"><span data-stu-id="75051-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="75051-162">Wykonywanie `dotnet test` nowego testu nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="75051-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="75051-163">Musisz zaktualizować `squaresOfOdds` metodę, aby obsłużyć ten nowy test.</span><span class="sxs-lookup"><span data-stu-id="75051-163">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="75051-164">Należy odfiltrować wszystkie liczby parzyste z sekwencji, aby wykonać ten test.</span><span class="sxs-lookup"><span data-stu-id="75051-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="75051-165">Możesz to zrobić, pisząc małą funkcję filtrowania i używając `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="75051-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="75051-166">Zwróć uwagę na `Seq.toList`wywołanie.</span><span class="sxs-lookup"><span data-stu-id="75051-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="75051-167">Tworzy listę, która implementuje <xref:System.Collections.ICollection> interfejs.</span><span class="sxs-lookup"><span data-stu-id="75051-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="75051-168">Istnieje jeden krok do przechodzenia: kwadrat każdej z liczb nieparzystych.</span><span class="sxs-lookup"><span data-stu-id="75051-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="75051-169">Zacznij od zapisania nowego testu:</span><span class="sxs-lookup"><span data-stu-id="75051-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="75051-170">Możesz naprawić test, przechodząc sekwencję przefiltrowanych przez operację mapowania, aby obliczyć kwadrat dla każdej liczby nieparzystej:</span><span class="sxs-lookup"><span data-stu-id="75051-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="75051-171">Utworzono niewielką bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="75051-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="75051-172">Rozbudowane rozwiązanie jest przeznaczone do dodawania nowych pakietów i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="75051-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="75051-173">Zbyt najwięcej czasu i wysiłku na rozwiązywanie celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="75051-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
