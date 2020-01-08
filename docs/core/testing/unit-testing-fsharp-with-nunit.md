---
title: Testy F# jednostkowe w środowisku .NET Core z testami dotnet i nunit
description: Poznaj koncepcje testów jednostkowych dla F# platformy .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania krok po kroku przy użyciu testu dotnet i NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 3be4ec01137a96a9b38869cbbb81fb0e89b7d700
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559503"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="8c93d-103">Biblioteki testów F# jednostkowych w programie .NET Core przy użyciu testu dotnet i nunit</span><span class="sxs-lookup"><span data-stu-id="8c93d-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="8c93d-104">Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="8c93d-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="8c93d-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) .</span><span class="sxs-lookup"><span data-stu-id="8c93d-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="8c93d-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="8c93d-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="8c93d-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8c93d-107">Prerequisites</span></span>

- <span data-ttu-id="8c93d-108">[Zestaw .NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub jego nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="8c93d-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="8c93d-109">Wybrany edytor tekstu lub edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="8c93d-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="8c93d-110">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="8c93d-110">Creating the source project</span></span>

<span data-ttu-id="8c93d-111">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="8c93d-111">Open a shell window.</span></span> <span data-ttu-id="8c93d-112">Utwórz katalog o nazwie *Unit-Test-with-FSharp* , aby pomieścić rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="8c93d-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="8c93d-113">W tym nowym katalogu Uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:</span><span class="sxs-lookup"><span data-stu-id="8c93d-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="8c93d-114">Następnie Utwórz katalog *mathservice* .</span><span class="sxs-lookup"><span data-stu-id="8c93d-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="8c93d-115">Poniższy konspekt przedstawia strukturę katalogu i pliku do tej pory:</span><span class="sxs-lookup"><span data-stu-id="8c93d-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="8c93d-116">Ustaw *mathservice* w bieżącym katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:</span><span class="sxs-lookup"><span data-stu-id="8c93d-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang "F#"
```

<span data-ttu-id="8c93d-117">Tworzysz nieprawidłową implementację usługi matematycznej:</span><span class="sxs-lookup"><span data-stu-id="8c93d-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="8c93d-118">Zmień katalog z powrotem na katalog *test-z-FSharp* .</span><span class="sxs-lookup"><span data-stu-id="8c93d-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="8c93d-119">Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="8c93d-119">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="8c93d-120">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="8c93d-120">Creating the test project</span></span>

<span data-ttu-id="8c93d-121">Następnie Utwórz katalog *mathservice. Tests* .</span><span class="sxs-lookup"><span data-stu-id="8c93d-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="8c93d-122">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="8c93d-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="8c93d-123">Utwórz katalog *mathservice. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="8c93d-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang "F#"
```

<span data-ttu-id="8c93d-124">Spowoduje to utworzenie projektu testowego, który używa NUnit jako środowiska testowego.</span><span class="sxs-lookup"><span data-stu-id="8c93d-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="8c93d-125">Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w *MathServiceTests. fsproj*:</span><span class="sxs-lookup"><span data-stu-id="8c93d-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="8c93d-126">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="8c93d-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="8c93d-127">`dotnet new` w poprzednim kroku został dodany NUnit i adapter testowy NUnit.</span><span class="sxs-lookup"><span data-stu-id="8c93d-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="8c93d-128">Teraz dodaj bibliotekę klas `MathService` jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="8c93d-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="8c93d-129">Użyj `dotnet add reference` polecenia:</span><span class="sxs-lookup"><span data-stu-id="8c93d-129">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="8c93d-130">Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="8c93d-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="8c93d-131">Dysponujesz następującym końcowym układem rozwiązań:</span><span class="sxs-lookup"><span data-stu-id="8c93d-131">You have the following final solution layout:</span></span>

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

<span data-ttu-id="8c93d-132">Wykonaj następujące polecenie w katalogu *Unit-Test-with-FSharp* :</span><span class="sxs-lookup"><span data-stu-id="8c93d-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="8c93d-133">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="8c93d-133">Creating the first test</span></span>

<span data-ttu-id="8c93d-134">Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces.</span><span class="sxs-lookup"><span data-stu-id="8c93d-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="8c93d-135">Otwórz *UnitTest1. FS* i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="8c93d-135">Open *UnitTest1.fs* and add the following code:</span></span>

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

<span data-ttu-id="8c93d-136">Atrybut `[<TestFixture>]` oznacza klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="8c93d-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="8c93d-137">Atrybut `[<Test>]` oznacza metodę testową, która jest uruchamiana przez program Test Runner.</span><span class="sxs-lookup"><span data-stu-id="8c93d-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="8c93d-138">W katalogu *testy jednostkowe-with-FSharp* należy wykonać `dotnet test`, aby skompilować testy i bibliotekę klas, a następnie uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="8c93d-138">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="8c93d-139">Program NUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="8c93d-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="8c93d-140">`dotnet test` uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="8c93d-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="8c93d-141">Te dwa testy pokazują najbardziej podstawowe testy dotyczące przekazywania i niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="8c93d-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="8c93d-142">`My test` passs i `Fail every time` nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="8c93d-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="8c93d-143">Teraz Utwórz test dla metody `squaresOfOdds`.</span><span class="sxs-lookup"><span data-stu-id="8c93d-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="8c93d-144">Metoda `squaresOfOdds` zwraca sekwencję kwadratów wszystkich nieparzystych wartości całkowitych, które są częścią sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="8c93d-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="8c93d-145">Zamiast próbować zapisywać wszystkie te funkcje jednocześnie, można iteracyjnie utworzyć testy, które weryfikują funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="8c93d-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="8c93d-146">Każdy przebieg testowy oznacza tworzenie niezbędnych funkcji dla metody.</span><span class="sxs-lookup"><span data-stu-id="8c93d-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="8c93d-147">Najprostszym testem możemy napisać jest wywołanie `squaresOfOdds` ze wszystkimi parzystymi liczbami, gdzie wynik powinien być pustą sekwencją liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="8c93d-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="8c93d-148">Oto test:</span><span class="sxs-lookup"><span data-stu-id="8c93d-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="8c93d-149">Zwróć uwagę, że sekwencja `expected` została przekonwertowana na listę.</span><span class="sxs-lookup"><span data-stu-id="8c93d-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="8c93d-150">Platforma NUnit jest oparta na wielu standardowych typach .NET.</span><span class="sxs-lookup"><span data-stu-id="8c93d-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="8c93d-151">Ta zależność oznacza, że interfejs publiczny i oczekiwane wyniki obsługują <xref:System.Collections.ICollection>, a nie <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="8c93d-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="8c93d-152">Po uruchomieniu testu zobaczysz, że test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8c93d-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="8c93d-153">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="8c93d-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="8c93d-154">Wykonaj ten test, pisząc najprostszy kod w klasie *Library. FS* w projekcie mathservice, który działa:</span><span class="sxs-lookup"><span data-stu-id="8c93d-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="8c93d-155">W katalogu *testy jednostkowe-with-FSharp* uruchom ponownie `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="8c93d-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="8c93d-156">`dotnet test` polecenie uruchamia kompilację dla projektu `MathService`, a następnie dla projektu `MathService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="8c93d-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="8c93d-157">Po skompilowaniu obu projektów uruchamiamy testy.</span><span class="sxs-lookup"><span data-stu-id="8c93d-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="8c93d-158">Dwa testy są teraz zakończone pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8c93d-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="8c93d-159">Spełnienie wymagań</span><span class="sxs-lookup"><span data-stu-id="8c93d-159">Completing the requirements</span></span>

<span data-ttu-id="8c93d-160">Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="8c93d-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="8c93d-161">Następny prosty przypadek działa z sekwencją, której tylko numer nieparzysty jest `1`.</span><span class="sxs-lookup"><span data-stu-id="8c93d-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="8c93d-162">Numer 1 jest łatwiejszy, ponieważ kwadrat 1 ma wartość 1.</span><span class="sxs-lookup"><span data-stu-id="8c93d-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="8c93d-163">Oto następny test:</span><span class="sxs-lookup"><span data-stu-id="8c93d-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="8c93d-164">Wykonanie `dotnet test` nie powiedzie się w nowym teście.</span><span class="sxs-lookup"><span data-stu-id="8c93d-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="8c93d-165">Należy zaktualizować metodę `squaresOfOdds`, aby obsługiwała ten nowy test.</span><span class="sxs-lookup"><span data-stu-id="8c93d-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="8c93d-166">Należy odfiltrować wszystkie liczby parzyste z sekwencji, aby wykonać ten test.</span><span class="sxs-lookup"><span data-stu-id="8c93d-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="8c93d-167">Możesz to zrobić, pisząc małą funkcję filtrowania i używając `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="8c93d-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="8c93d-168">Zwróć uwagę na wywołanie `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="8c93d-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="8c93d-169">Tworzy listę, która implementuje interfejs <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="8c93d-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="8c93d-170">Istnieje jeden krok do przechodzenia: kwadrat każdej z liczb nieparzystych.</span><span class="sxs-lookup"><span data-stu-id="8c93d-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="8c93d-171">Zacznij od zapisania nowego testu:</span><span class="sxs-lookup"><span data-stu-id="8c93d-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="8c93d-172">Możesz naprawić test, przechodząc sekwencję przefiltrowanych przez operację mapowania, aby obliczyć kwadrat dla każdej liczby nieparzystej:</span><span class="sxs-lookup"><span data-stu-id="8c93d-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="8c93d-173">Utworzono niewielką bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="8c93d-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="8c93d-174">Rozbudowane rozwiązanie jest przeznaczone do dodawania nowych pakietów i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8c93d-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="8c93d-175">Zbyt najwięcej czasu i wysiłku na rozwiązywanie celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c93d-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c93d-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c93d-176">See also</span></span>

- [<span data-ttu-id="8c93d-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="8c93d-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="8c93d-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8c93d-178">dotnet test</span></span>](../tools/dotnet-test.md)
