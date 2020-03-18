---
title: Testowanie jednostkowe F# w .NET Core z testem dotnet i xUnit
description: Poznaj pojęcia testu jednostkowego dla języka F# w platformie .NET Core za pomocą interaktywnego środowiska, które krok po kroku przy użyciu testu dotnet i xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 5fe4a8faddd87334439513368f24d808abc58e65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157313"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="6d556-103">Testowanie jednostkowe bibliotek F# w .NET Core przy użyciu testu dotnet i xUnit</span><span class="sxs-lookup"><span data-stu-id="6d556-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="6d556-104">W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="6d556-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="6d556-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="6d556-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="6d556-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="6d556-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="6d556-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="6d556-107">Creating the source project</span></span>

<span data-ttu-id="6d556-108">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="6d556-108">Open a shell window.</span></span> <span data-ttu-id="6d556-109">Utwórz katalog o nazwie *unit-testing-with-fsharp* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6d556-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="6d556-110">Wewnątrz tego nowego `dotnet new sln` katalogu uruchom, aby utworzyć nowe rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6d556-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="6d556-111">Ułatwia to zarządzanie zarówno biblioteki klas i projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="6d556-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="6d556-112">Wewnątrz katalogu rozwiązania utwórz katalog *MathService.*</span><span class="sxs-lookup"><span data-stu-id="6d556-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="6d556-113">Struktura katalogów i plików do tej pory jest pokazana poniżej:</span><span class="sxs-lookup"><span data-stu-id="6d556-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="6d556-114">Utwórz *MathService* bieżącego `dotnet new classlib -lang "F#"` katalogu i uruchom, aby utworzyć projekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="6d556-114">Make *MathService* the current directory, and run `dotnet new classlib -lang "F#"` to create the source project.</span></span> <span data-ttu-id="6d556-115">Utworzysz nieudołężej wykonania usługi matematycznej:</span><span class="sxs-lookup"><span data-stu-id="6d556-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="6d556-116">Zmień katalog z powrotem do katalogu *testowania jednostek z fsharp.*</span><span class="sxs-lookup"><span data-stu-id="6d556-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="6d556-117">Uruchom, `dotnet sln add .\MathService\MathService.fsproj` aby dodać projekt biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6d556-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="6d556-118">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="6d556-118">Creating the test project</span></span>

<span data-ttu-id="6d556-119">Następnie utwórz katalog *MathService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="6d556-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="6d556-120">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="6d556-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="6d556-121">Utwórz katalog *MathService.Tests* jako bieżący katalog `dotnet new xunit -lang "F#"`i utwórz nowy projekt przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="6d556-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new xunit -lang "F#"`.</span></span> <span data-ttu-id="6d556-122">Spowoduje to utworzenie projektu testowego, który używa xUnit jako biblioteki testowej.</span><span class="sxs-lookup"><span data-stu-id="6d556-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="6d556-123">Wygenerowany szablon konfiguruje testrunner w *MathServiceTests.fsproj:*</span><span class="sxs-lookup"><span data-stu-id="6d556-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="6d556-124">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="6d556-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="6d556-125">`dotnet new`w poprzednim kroku dodano xUnit i xUnit runner.</span><span class="sxs-lookup"><span data-stu-id="6d556-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="6d556-126">Teraz dodaj `MathService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="6d556-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="6d556-127">Użyj `dotnet add reference` polecenia:</span><span class="sxs-lookup"><span data-stu-id="6d556-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="6d556-128">Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w uspolu GitHub.</span><span class="sxs-lookup"><span data-stu-id="6d556-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="6d556-129">Masz następujący ostateczny układ rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="6d556-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="6d556-130">Wykonywanie `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` w katalogu *testowania jednostek z fsharp.*</span><span class="sxs-lookup"><span data-stu-id="6d556-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="6d556-131">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="6d556-131">Creating the first test</span></span>

<span data-ttu-id="6d556-132">Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="6d556-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="6d556-133">Otwórz *testy.fs* i dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="6d556-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="6d556-134">Atrybut `[<Fact>]` oznacza metodę testową, która jest uruchamiana przez test runner.</span><span class="sxs-lookup"><span data-stu-id="6d556-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="6d556-135">Z *jednostki testowania-with-fsharp*, `dotnet test` wykonaj do kompilacji testów i biblioteki klas, a następnie uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="6d556-135">From the *unit-testing-with-fsharp*, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="6d556-136">Program testowy xUnit zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="6d556-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="6d556-137">`dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="6d556-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="6d556-138">Te dwa testy pokazują najbardziej podstawowe testy zaliczenia i niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="6d556-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="6d556-139">`My test`przechodzi i `Fail every time` nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="6d556-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="6d556-140">Teraz utwórz test `squaresOfOdds` dla metody.</span><span class="sxs-lookup"><span data-stu-id="6d556-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="6d556-141">Metoda `squaresOfOdds` zwraca sekwencję kwadratów wszystkich wartości nieparzystych liczb całkowitych, które są częścią sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="6d556-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="6d556-142">Zamiast próbować napisać wszystkie te funkcje naraz, można iteracyjne tworzenie testów, które sprawdzają poprawność funkcji.</span><span class="sxs-lookup"><span data-stu-id="6d556-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="6d556-143">Dokonywanie każdego testu oznacza tworzenie niezbędnych funkcji dla metody.</span><span class="sxs-lookup"><span data-stu-id="6d556-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="6d556-144">Najprostszym testem, który `squaresOfOdds` możemy napisać, jest wywołanie ze wszystkimi parzystymi numerami, gdzie wynik powinien być pustą sekwencją liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="6d556-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="6d556-145">Oto ten test:</span><span class="sxs-lookup"><span data-stu-id="6d556-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="6d556-146">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="6d556-146">Your test fails.</span></span> <span data-ttu-id="6d556-147">Implementacja nie została jeszcze utworzona.</span><span class="sxs-lookup"><span data-stu-id="6d556-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="6d556-148">Zrób ten test przejść, pisząc najprostszy kod w `MathService` klasie, która działa:</span><span class="sxs-lookup"><span data-stu-id="6d556-148">Make this test pass by writing the simplest code in the `MathService` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="6d556-149">W katalogu *testowania jednostek z fsharp* `dotnet test` uruchom ponownie.</span><span class="sxs-lookup"><span data-stu-id="6d556-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="6d556-150">Polecenie `dotnet test` uruchamia kompilację `MathService` dla projektu, `MathService.Tests` a następnie dla projektu.</span><span class="sxs-lookup"><span data-stu-id="6d556-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="6d556-151">Po zbudowaniu obu projektów uruchamia ten pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="6d556-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="6d556-152">Mija.</span><span class="sxs-lookup"><span data-stu-id="6d556-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="6d556-153">Wypełnianie wymagań</span><span class="sxs-lookup"><span data-stu-id="6d556-153">Completing the requirements</span></span>

<span data-ttu-id="6d556-154">Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="6d556-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="6d556-155">Następny prosty przypadek działa z sekwencją, `1`której jedyną liczbą nieparzystą jest .</span><span class="sxs-lookup"><span data-stu-id="6d556-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="6d556-156">Liczba 1 jest łatwiejsza, ponieważ kwadrat 1 wynosi 1.</span><span class="sxs-lookup"><span data-stu-id="6d556-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="6d556-157">Oto następny test:</span><span class="sxs-lookup"><span data-stu-id="6d556-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="6d556-158">Wykonywanie `dotnet test` uruchamia testy i pokazuje, że nowy test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="6d556-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="6d556-159">Teraz zaktualizuj `squaresOfOdds` metodę obsługi tego nowego testu.</span><span class="sxs-lookup"><span data-stu-id="6d556-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="6d556-160">Możesz filtrować wszystkie numery parzyste z sekwencji, aby ten test przeszedł.</span><span class="sxs-lookup"><span data-stu-id="6d556-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="6d556-161">Można to zrobić, pisząc małą funkcję `Seq.filter`filtra i używając:</span><span class="sxs-lookup"><span data-stu-id="6d556-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="6d556-162">Jest jeszcze jeden krok do zrobienia: kwadrat każdej z liczb nieparzystych.</span><span class="sxs-lookup"><span data-stu-id="6d556-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="6d556-163">Zacznij od napisania nowego testu:</span><span class="sxs-lookup"><span data-stu-id="6d556-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="6d556-164">Test można naprawić, przeinacząc przefiltrowaną sekwencję za pomocą operacji mapy, aby obliczyć kwadrat każdego nieparzystego numeru:</span><span class="sxs-lookup"><span data-stu-id="6d556-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="6d556-165">Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="6d556-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="6d556-166">Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6d556-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="6d556-167">Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d556-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d556-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d556-168">See also</span></span>

- [<span data-ttu-id="6d556-169">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6d556-169">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="6d556-170">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="6d556-170">dotnet sln</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="6d556-171">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="6d556-171">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="6d556-172">dotnet test</span><span class="sxs-lookup"><span data-stu-id="6d556-172">dotnet test</span></span>](../tools/dotnet-test.md)
