---
title: Testowanie jednostkowe F# w .NET Core z testem dotnet owym i Jednostką NUnit
description: Poznaj pojęcia testu jednostkowego dla języka F# w platformie .NET Core za pomocą interaktywnego środowiska, tworząc przykładowe rozwiązanie krok po kroku przy użyciu testu dotnet i NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 3347e5b90c31589e9a0f99ac0d9298927a717f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715450"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="efb11-103">Testowanie jednostkowe bibliotek F# w .NET Core przy użyciu testu dotnet i NUnit</span><span class="sxs-lookup"><span data-stu-id="efb11-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="efb11-104">W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="efb11-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="efb11-105">Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="efb11-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="efb11-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="efb11-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="efb11-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="efb11-107">Prerequisites</span></span>

- <span data-ttu-id="efb11-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="efb11-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="efb11-109">Wybrany edytor tekstu lub edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="efb11-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="efb11-110">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="efb11-110">Creating the source project</span></span>

<span data-ttu-id="efb11-111">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="efb11-111">Open a shell window.</span></span> <span data-ttu-id="efb11-112">Utwórz katalog o nazwie *unit-testing-with-fsharp* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="efb11-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="efb11-113">W tym nowym katalogu uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:</span><span class="sxs-lookup"><span data-stu-id="efb11-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="efb11-114">Następnie utwórz katalog *MathService.*</span><span class="sxs-lookup"><span data-stu-id="efb11-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="efb11-115">Poniższy konspekt pokazuje strukturę katalogów i plików do tej pory:</span><span class="sxs-lookup"><span data-stu-id="efb11-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="efb11-116">Utwórz *MathService* bieżącego katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:</span><span class="sxs-lookup"><span data-stu-id="efb11-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang "F#"
```

<span data-ttu-id="efb11-117">Tworzenie nieudanej implementacji usługi matematycznej:</span><span class="sxs-lookup"><span data-stu-id="efb11-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="efb11-118">Zmień katalog z powrotem do katalogu *testowania jednostek z fsharp.*</span><span class="sxs-lookup"><span data-stu-id="efb11-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="efb11-119">Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="efb11-119">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="efb11-120">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="efb11-120">Creating the test project</span></span>

<span data-ttu-id="efb11-121">Następnie utwórz katalog *MathService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="efb11-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="efb11-122">Poniższy konspekt przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="efb11-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="efb11-123">Utwórz katalog *MathService.Tests* bieżącego katalogu i utwórz nowy projekt przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="efb11-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang "F#"
```

<span data-ttu-id="efb11-124">Spowoduje to utworzenie projektu testowego, który używa NUnit jako struktury testowej.</span><span class="sxs-lookup"><span data-stu-id="efb11-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="efb11-125">Wygenerowany szablon konfiguruje testrunner w *MathServiceTests.fsproj:*</span><span class="sxs-lookup"><span data-stu-id="efb11-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="efb11-126">Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="efb11-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="efb11-127">`dotnet new`w poprzednim kroku dodano NUnit i kartę testową NUnit.</span><span class="sxs-lookup"><span data-stu-id="efb11-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="efb11-128">Teraz dodaj `MathService` bibliotekę klas jako inną zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="efb11-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="efb11-129">Użyj `dotnet add reference` polecenia:</span><span class="sxs-lookup"><span data-stu-id="efb11-129">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="efb11-130">Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w uspolu GitHub.</span><span class="sxs-lookup"><span data-stu-id="efb11-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="efb11-131">Masz następujący ostateczny układ rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="efb11-131">You have the following final solution layout:</span></span>

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

<span data-ttu-id="efb11-132">Wykonaj następujące polecenie w katalogu testów jednostkowych:Execute the following command in the *unit-testing-with-fsharp* directory:</span><span class="sxs-lookup"><span data-stu-id="efb11-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="efb11-133">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="efb11-133">Creating the first test</span></span>

<span data-ttu-id="efb11-134">Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="efb11-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="efb11-135">Otwórz *program UnitTest1.fs* i dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="efb11-135">Open *UnitTest1.fs* and add the following code:</span></span>

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

<span data-ttu-id="efb11-136">Atrybut `[<TestFixture>]` oznacza klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="efb11-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="efb11-137">Atrybut `[<Test>]` oznacza metodę testową, która jest uruchamiana przez test runner.</span><span class="sxs-lookup"><span data-stu-id="efb11-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="efb11-138">Z *katalogu testowania jednostek z fsharp* `dotnet test` wykonaj, aby utworzyć testy i biblioteki klas, a następnie uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="efb11-138">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="efb11-139">Program testowy NUnit zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="efb11-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="efb11-140">`dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="efb11-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="efb11-141">Te dwa testy pokazują najbardziej podstawowe testy zaliczenia i niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="efb11-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="efb11-142">`My test`przechodzi i `Fail every time` nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="efb11-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="efb11-143">Teraz utwórz test `squaresOfOdds` dla metody.</span><span class="sxs-lookup"><span data-stu-id="efb11-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="efb11-144">Metoda `squaresOfOdds` zwraca sekwencję kwadratów wszystkich wartości nieparzystych liczb całkowitych, które są częścią sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="efb11-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="efb11-145">Zamiast próbować napisać wszystkie te funkcje naraz, można iteracyjne tworzenie testów, które sprawdzają poprawność funkcji.</span><span class="sxs-lookup"><span data-stu-id="efb11-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="efb11-146">Dokonywanie każdego testu oznacza tworzenie niezbędnych funkcji dla metody.</span><span class="sxs-lookup"><span data-stu-id="efb11-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="efb11-147">Najprostszym testem, który `squaresOfOdds` możemy napisać, jest wywołanie ze wszystkimi parzystymi numerami, gdzie wynik powinien być pustą sekwencją liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="efb11-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="efb11-148">Oto ten test:</span><span class="sxs-lookup"><span data-stu-id="efb11-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="efb11-149">Należy zauważyć, że sekwencja `expected` została przekonwertowana na listę.</span><span class="sxs-lookup"><span data-stu-id="efb11-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="efb11-150">Struktura NUnit opiera się na wielu standardowych typach .NET.</span><span class="sxs-lookup"><span data-stu-id="efb11-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="efb11-151">Ta zależność oznacza, że interfejs publiczny <xref:System.Collections.ICollection> i <xref:System.Collections.IEnumerable>oczekiwane wyniki obsługują, a nie .</span><span class="sxs-lookup"><span data-stu-id="efb11-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="efb11-152">Po uruchomieniu testu, widać, że test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="efb11-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="efb11-153">Implementacja nie została jeszcze utworzona.</span><span class="sxs-lookup"><span data-stu-id="efb11-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="efb11-154">Zrób ten test pass, pisząc najprostszy kod w *Library.fs* klasy w projekcie MathService, który działa:</span><span class="sxs-lookup"><span data-stu-id="efb11-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="efb11-155">W katalogu *testowania jednostek z fsharp* `dotnet test` uruchom ponownie.</span><span class="sxs-lookup"><span data-stu-id="efb11-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="efb11-156">Polecenie `dotnet test` uruchamia kompilację `MathService` dla projektu, `MathService.Tests` a następnie dla projektu.</span><span class="sxs-lookup"><span data-stu-id="efb11-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="efb11-157">Po zbudowaniu obu projektów uruchamia testy.</span><span class="sxs-lookup"><span data-stu-id="efb11-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="efb11-158">Teraz przechodzą dwa testy.</span><span class="sxs-lookup"><span data-stu-id="efb11-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="efb11-159">Wypełnianie wymagań</span><span class="sxs-lookup"><span data-stu-id="efb11-159">Completing the requirements</span></span>

<span data-ttu-id="efb11-160">Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej.</span><span class="sxs-lookup"><span data-stu-id="efb11-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="efb11-161">Następny prosty przypadek działa z sekwencją, `1`której jedyną liczbą nieparzystą jest .</span><span class="sxs-lookup"><span data-stu-id="efb11-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="efb11-162">Liczba 1 jest łatwiejsza, ponieważ kwadrat 1 wynosi 1.</span><span class="sxs-lookup"><span data-stu-id="efb11-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="efb11-163">Oto następny test:</span><span class="sxs-lookup"><span data-stu-id="efb11-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="efb11-164">Wykonywanie `dotnet test` nie powiedzie się nowy test.</span><span class="sxs-lookup"><span data-stu-id="efb11-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="efb11-165">Należy zaktualizować `squaresOfOdds` metodę obsługi tego nowego testu.</span><span class="sxs-lookup"><span data-stu-id="efb11-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="efb11-166">Należy filtrować wszystkie numery parzyste z sekwencji, aby ten test przeszedł.</span><span class="sxs-lookup"><span data-stu-id="efb11-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="efb11-167">Można to zrobić, pisząc małą funkcję `Seq.filter`filtra i używając:</span><span class="sxs-lookup"><span data-stu-id="efb11-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="efb11-168">Zwróć uwagę `Seq.toList`na wywołanie .</span><span class="sxs-lookup"><span data-stu-id="efb11-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="efb11-169">Który tworzy listę, która <xref:System.Collections.ICollection> implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="efb11-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="efb11-170">Jest jeszcze jeden krok do zrobienia: kwadrat każdej z liczb nieparzystych.</span><span class="sxs-lookup"><span data-stu-id="efb11-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="efb11-171">Zacznij od napisania nowego testu:</span><span class="sxs-lookup"><span data-stu-id="efb11-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="efb11-172">Test można naprawić, przeinacząc przefiltrowaną sekwencję za pomocą operacji mapy, aby obliczyć kwadrat każdego nieparzystego numeru:</span><span class="sxs-lookup"><span data-stu-id="efb11-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="efb11-173">Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="efb11-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="efb11-174">Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="efb11-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="efb11-175">Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efb11-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="efb11-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efb11-176">See also</span></span>

- [<span data-ttu-id="efb11-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="efb11-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="efb11-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="efb11-178">dotnet test</span></span>](../tools/dotnet-test.md)
