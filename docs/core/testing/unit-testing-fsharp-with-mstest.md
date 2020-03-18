---
title: Testowanie jednostkowe F# w .NET Core z testem dotnet owym i MSTest
description: Poznaj pojęcia dotyczące testu jednostkowego dla języka F# w platformie .NET Core za pomocą interaktywnego środowiska, które krok po kroku przy użyciu testu dotnet i programu MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: a685ed8a56393fb6e1c1b9400f0ed4bcef15f9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714279"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="eec49-103">Testowanie jednostkowe bibliotek F# w .NET Core przy użyciu testu dotnet i mstest</span><span class="sxs-lookup"><span data-stu-id="eec49-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="eec49-104">W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="eec49-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="eec49-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="eec49-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="eec49-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="eec49-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="eec49-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="eec49-107">Creating the source project</span></span>

<span data-ttu-id="eec49-108">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="eec49-108">Open a shell window.</span></span> <span data-ttu-id="eec49-109">Utwórz katalog o nazwie *unit-testing-with-fsharp* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="eec49-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="eec49-110">Wewnątrz tego nowego `dotnet new sln` katalogu uruchom, aby utworzyć nowe rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="eec49-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="eec49-111">Ułatwia to zarządzanie zarówno biblioteki klas i projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="eec49-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="eec49-112">Wewnątrz katalogu rozwiązania utwórz katalog *MathService.*</span><span class="sxs-lookup"><span data-stu-id="eec49-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="eec49-113">Struktura katalogów i plików do tej pory jest pokazana poniżej:</span><span class="sxs-lookup"><span data-stu-id="eec49-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="eec49-114">Utwórz *MathService* bieżącego `dotnet new classlib -lang "F#"` katalogu i uruchom, aby utworzyć projekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="eec49-114">Make *MathService* the current directory and run `dotnet new classlib -lang "F#"` to create the source project.</span></span>  <span data-ttu-id="eec49-115">Utworzysz nieudołężej wykonania usługi matematycznej:</span><span class="sxs-lookup"><span data-stu-id="eec49-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="eec49-116">Zmień katalog z powrotem do katalogu *testowania jednostek z fsharp.*</span><span class="sxs-lookup"><span data-stu-id="eec49-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="eec49-117">Uruchom, `dotnet sln add .\MathService\MathService.fsproj` aby dodać projekt biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="eec49-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="eec49-118">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="eec49-118">Creating the test project</span></span>

<span data-ttu-id="eec49-119">Następnie utwórz katalog *MathService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="eec49-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="eec49-120">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="eec49-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="eec49-121">Utwórz katalog *MathService.Tests* jako bieżący katalog `dotnet new mstest -lang "F#"`i utwórz nowy projekt przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="eec49-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new mstest -lang "F#"`.</span></span> <span data-ttu-id="eec49-122">Spowoduje to utworzenie projektu testowego, który używa MSTest jako struktury testowej.</span><span class="sxs-lookup"><span data-stu-id="eec49-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="eec49-123">Wygenerowany szablon konfiguruje testrunner w *MathServiceTests.fsproj:*</span><span class="sxs-lookup"><span data-stu-id="eec49-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="eec49-124">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="eec49-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="eec49-125">`dotnet new`w poprzednim kroku dodano MSTest i mstest runner.</span><span class="sxs-lookup"><span data-stu-id="eec49-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="eec49-126">Teraz dodaj `MathService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="eec49-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="eec49-127">Użyj `dotnet add reference` polecenia:</span><span class="sxs-lookup"><span data-stu-id="eec49-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="eec49-128">Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w uspolu GitHub.</span><span class="sxs-lookup"><span data-stu-id="eec49-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="eec49-129">Masz następujący ostateczny układ rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="eec49-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="eec49-130">Wykonywanie `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` w katalogu *testowania jednostek z fsharp.*</span><span class="sxs-lookup"><span data-stu-id="eec49-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="eec49-131">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="eec49-131">Creating the first test</span></span>

<span data-ttu-id="eec49-132">Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="eec49-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="eec49-133">Otwórz *testy.fs* i dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="eec49-133">Open *Tests.fs* and add the following code:</span></span>

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

<span data-ttu-id="eec49-134">Atrybut `[<TestClass>]` oznacza klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="eec49-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="eec49-135">Atrybut `[<TestMethod>]` oznacza metodę testową, która jest uruchamiana przez test runner.</span><span class="sxs-lookup"><span data-stu-id="eec49-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="eec49-136">Z *katalogu testowania jednostek z fsharp* `dotnet test` wykonaj, aby utworzyć testy i biblioteki klas, a następnie uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="eec49-136">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="eec49-137">Program testowy MSTest zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="eec49-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="eec49-138">`dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="eec49-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="eec49-139">Te dwa testy pokazują najbardziej podstawowe testy zaliczenia i niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="eec49-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="eec49-140">`My test`przechodzi i `Fail every time` nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="eec49-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="eec49-141">Teraz utwórz test `squaresOfOdds` dla metody.</span><span class="sxs-lookup"><span data-stu-id="eec49-141">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="eec49-142">Metoda `squaresOfOdds` zwraca listę kwadratów wszystkich wartości nieparzystych liczb całkowitych, które są częścią sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="eec49-142">The `squaresOfOdds` method returns a list of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="eec49-143">Zamiast próbować napisać wszystkie te funkcje naraz, można iteracyjne tworzenie testów, które sprawdzają poprawność funkcji.</span><span class="sxs-lookup"><span data-stu-id="eec49-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="eec49-144">Dokonywanie każdego testu oznacza tworzenie niezbędnych funkcji dla metody.</span><span class="sxs-lookup"><span data-stu-id="eec49-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="eec49-145">Najprostszym testem, który `squaresOfOdds` możemy napisać, jest wywołanie ze wszystkimi parzystymi numerami, gdzie wynik powinien być pustą sekwencją liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="eec49-145">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="eec49-146">Oto ten test:</span><span class="sxs-lookup"><span data-stu-id="eec49-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="eec49-147">Należy zauważyć, że sekwencja `expected` została przekonwertowana na listę.</span><span class="sxs-lookup"><span data-stu-id="eec49-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="eec49-148">Biblioteka MSTest opiera się na wielu standardowych typach .NET.</span><span class="sxs-lookup"><span data-stu-id="eec49-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="eec49-149">Ta zależność oznacza, że interfejs publiczny <xref:System.Collections.ICollection> i <xref:System.Collections.IEnumerable>oczekiwane wyniki obsługują, a nie .</span><span class="sxs-lookup"><span data-stu-id="eec49-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="eec49-150">Po uruchomieniu testu, widać, że test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="eec49-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="eec49-151">Implementacja nie została jeszcze utworzona.</span><span class="sxs-lookup"><span data-stu-id="eec49-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="eec49-152">Zrób ten test przejść, pisząc najprostszy kod w `Mathservice` klasie, która działa:</span><span class="sxs-lookup"><span data-stu-id="eec49-152">Make this test pass by writing the simplest code in the `Mathservice` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="eec49-153">W katalogu *testowania jednostek z fsharp* `dotnet test` uruchom ponownie.</span><span class="sxs-lookup"><span data-stu-id="eec49-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="eec49-154">Polecenie `dotnet test` uruchamia kompilację `MathService` dla projektu, `MathService.Tests` a następnie dla projektu.</span><span class="sxs-lookup"><span data-stu-id="eec49-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="eec49-155">Po zbudowaniu obu projektów uruchamia ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="eec49-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="eec49-156">Mija.</span><span class="sxs-lookup"><span data-stu-id="eec49-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="eec49-157">Wypełnianie wymagań</span><span class="sxs-lookup"><span data-stu-id="eec49-157">Completing the requirements</span></span>

<span data-ttu-id="eec49-158">Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="eec49-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="eec49-159">Następny prosty przypadek działa z sekwencją, `1`której jedyną liczbą nieparzystą jest .</span><span class="sxs-lookup"><span data-stu-id="eec49-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="eec49-160">Liczba 1 jest łatwiejsza, ponieważ kwadrat 1 wynosi 1.</span><span class="sxs-lookup"><span data-stu-id="eec49-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="eec49-161">Oto następny test:</span><span class="sxs-lookup"><span data-stu-id="eec49-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="eec49-162">Wykonywanie `dotnet test` nie powiedzie się nowy test.</span><span class="sxs-lookup"><span data-stu-id="eec49-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="eec49-163">Należy zaktualizować `squaresOfOdds` metodę obsługi tego nowego testu.</span><span class="sxs-lookup"><span data-stu-id="eec49-163">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="eec49-164">Należy filtrować wszystkie numery parzyste z sekwencji, aby ten test przeszedł.</span><span class="sxs-lookup"><span data-stu-id="eec49-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="eec49-165">Można to zrobić, pisząc małą funkcję `Seq.filter`filtra i używając:</span><span class="sxs-lookup"><span data-stu-id="eec49-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="eec49-166">Zwróć uwagę `Seq.toList`na wywołanie .</span><span class="sxs-lookup"><span data-stu-id="eec49-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="eec49-167">Który tworzy listę, która <xref:System.Collections.ICollection> implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="eec49-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="eec49-168">Jest jeszcze jeden krok do zrobienia: kwadrat każdej z liczb nieparzystych.</span><span class="sxs-lookup"><span data-stu-id="eec49-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="eec49-169">Zacznij od napisania nowego testu:</span><span class="sxs-lookup"><span data-stu-id="eec49-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="eec49-170">Test można naprawić, przeinacząc przefiltrowaną sekwencję za pomocą operacji mapy, aby obliczyć kwadrat każdego nieparzystego numeru:</span><span class="sxs-lookup"><span data-stu-id="eec49-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="eec49-171">Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="eec49-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="eec49-172">Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="eec49-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="eec49-173">Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eec49-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="eec49-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eec49-174">See also</span></span>

- [<span data-ttu-id="eec49-175">dotnet new</span><span class="sxs-lookup"><span data-stu-id="eec49-175">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="eec49-176">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="eec49-176">dotnet sln</span></span>](../tools/dotnet-sln.md)
- [<span data-ttu-id="eec49-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="eec49-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="eec49-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="eec49-178">dotnet test</span></span>](../tools/dotnet-test.md)
