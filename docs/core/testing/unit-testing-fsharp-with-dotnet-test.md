---
title: Testy jednostkowe F# platformie .NET Core za pomocą polecenia dotnet test i struktury xUnit
description: Informacje na temat testów jednostek dla F# platformy .NET Core za pomocą interaktywnych doświadczenia przykładowe rozwiązanie krok po kroku za pomocą polecenia dotnet test i struktury xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 08ebe39fd6e992fdcdc10e19d87d565e76d909a2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239202"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="70313-103">Testy jednostkowe F# bibliotek w programie .NET Core za pomocą polecenia dotnet test i struktury xUnit</span><span class="sxs-lookup"><span data-stu-id="70313-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="70313-104">Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="70313-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="70313-105">Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) przed przystąpieniem do wykonywania.</span><span class="sxs-lookup"><span data-stu-id="70313-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="70313-106">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="70313-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="70313-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="70313-107">Creating the source project</span></span>

<span data-ttu-id="70313-108">Otwieranie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="70313-108">Open a shell window.</span></span> <span data-ttu-id="70313-109">Utwórz katalog o nazwie *jednostki — testowanie z fsharp* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="70313-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="70313-110">Wewnątrz tego nowy katalog uruchamiania [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="70313-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="70313-111">Dzięki temu można łatwiej zarządzać biblioteki klas i projekt testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="70313-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="70313-112">Utwórz katalog rozwiązania *MathService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="70313-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="70313-113">Struktura katalogów i plików dotychczasowych znajdują się poniżej:</span><span class="sxs-lookup"><span data-stu-id="70313-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="70313-114">Wprowadź *MathService* bieżącego katalogu i uruchom [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) do utworzenia projektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="70313-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="70313-115">Aby korzystać z projektowania opartego na testach (TDD), należy utworzyć niepowodzenie stosowania usługi matematyczne:</span><span class="sxs-lookup"><span data-stu-id="70313-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="70313-116">Zmień katalog kopii do *jednostki — testowanie z fsharp* katalogu.</span><span class="sxs-lookup"><span data-stu-id="70313-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="70313-117">Uruchom [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="70313-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="70313-118">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="70313-118">Creating the test project</span></span>

<span data-ttu-id="70313-119">Następnie należy utworzyć *MathService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="70313-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="70313-120">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="70313-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="70313-121">Wprowadź *MathService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="70313-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="70313-122">Spowoduje to utworzenie projektu testowego, który używa rozwiązania xUnit, jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="70313-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="70313-123">Wygenerowany szablon konfiguruje narzędzie test runner w *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="70313-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="70313-124">Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="70313-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="70313-125">`dotnet new` w poprzednim kroku dodawany xUnit, a moduł uruchamiający testy xUnit.</span><span class="sxs-lookup"><span data-stu-id="70313-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="70313-126">Teraz Dodaj `MathService` biblioteki klas jako inny zależności do projektu.</span><span class="sxs-lookup"><span data-stu-id="70313-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="70313-127">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="70313-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="70313-128">Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="70313-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="70313-129">Masz następujące układ ostateczne rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="70313-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="70313-130">Wykonaj [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) w *jednostki — testowanie z fsharp* katalogu.</span><span class="sxs-lookup"><span data-stu-id="70313-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="70313-131">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="70313-131">Creating the first test</span></span>

<span data-ttu-id="70313-132">Podejścia TDD wymaga zapisywania niepowodzenie jednego testu, dzięki czemu przekazać, a następnie powtórzyć ten proces.</span><span class="sxs-lookup"><span data-stu-id="70313-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="70313-133">Otwórz *Tests.fs* i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="70313-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="70313-134">`[<Fact>]` Atrybut oznacza metodę testową, która jest uruchamiany przez narzędzie test runner.</span><span class="sxs-lookup"><span data-stu-id="70313-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="70313-135">Z *jednostki — testowanie z fsharp*, wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="70313-135">From the *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="70313-136">Moduł uruchamiający xUnit zawiera punkt wejścia programu, aby uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="70313-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="70313-137">`dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="70313-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="70313-138">Testy te dwa Pokaż najbardziej podstawowym, przekazywanie i niepowodzenie testów.</span><span class="sxs-lookup"><span data-stu-id="70313-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="70313-139">`My test` przekazuje, i `Fail every time` zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="70313-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="70313-140">Teraz Utwórz test `squaresOfOdds` metody.</span><span class="sxs-lookup"><span data-stu-id="70313-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="70313-141">`squaresOfOdds` Metoda zwraca sekwencję kwadratów wszystkie wartości nieparzystej liczby całkowitej, które są częścią sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="70313-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="70313-142">Zamiast próbowania zapisać wszystkie te funkcje na raz, iteracyjne można tworzyć testy, które sprawdzają poprawność funkcji.</span><span class="sxs-lookup"><span data-stu-id="70313-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="70313-143">Dzięki czemu każdy przebieg sprowadza się do utworzenia niezbędnych funkcji dla metody testu.</span><span class="sxs-lookup"><span data-stu-id="70313-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="70313-144">Najprostsza testów, możemy napisać jest wywołanie `squaresOfOdds` z wszystkie liczby parzyste z zakresu, gdzie powinna zostać pustą sekwencją liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="70313-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="70313-145">Oto tego testu:</span><span class="sxs-lookup"><span data-stu-id="70313-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="70313-146">Test nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="70313-146">Your test fails.</span></span> <span data-ttu-id="70313-147">Nie utworzono jeszcze wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="70313-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="70313-148">Należy ten test przez napisanie kodu najprostsza `MathService` klasę, która działa:</span><span class="sxs-lookup"><span data-stu-id="70313-148">Make this test by writing the simplest code in the `MathService` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="70313-149">W *jednostki — testowanie z fsharp* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="70313-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="70313-150">`dotnet test` Polecenie uruchamia kompilację dla `MathService` projektu i następnie `MathService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="70313-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="70313-151">Po utworzeniu obu projektów, działa ten jeden test.</span><span class="sxs-lookup"><span data-stu-id="70313-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="70313-152">Przekazuje on.</span><span class="sxs-lookup"><span data-stu-id="70313-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="70313-153">Korzystanie z wymaganiami</span><span class="sxs-lookup"><span data-stu-id="70313-153">Completing the requirements</span></span>

<span data-ttu-id="70313-154">Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="70313-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="70313-155">Dalej prostym przypadku współpracuje z sekwencji jest liczbą nieparzystą tylko `1`.</span><span class="sxs-lookup"><span data-stu-id="70313-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="70313-156">Numer 1 jest łatwiejsze, ponieważ kwadrat 1 jest 1.</span><span class="sxs-lookup"><span data-stu-id="70313-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="70313-157">Oto tego Następny test:</span><span class="sxs-lookup"><span data-stu-id="70313-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="70313-158">Wykonywanie `dotnet test` uruchamia testy i dowiesz się, że nowy test kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="70313-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="70313-159">Teraz zaktualizuj `squaresOfOdds` metody, aby obsłużyć ten nowy test.</span><span class="sxs-lookup"><span data-stu-id="70313-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="70313-160">Możesz filtrować wszystkie liczby parzyste poza kolejnością, aby ten przebieg testu.</span><span class="sxs-lookup"><span data-stu-id="70313-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="70313-161">Możesz to zrobić przez pisanie funkcji filtru małe i przy użyciu `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="70313-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="70313-162">Istnieje jeszcze jeden krok do: każdej liczby nieparzyste kwadratowe.</span><span class="sxs-lookup"><span data-stu-id="70313-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="70313-163">Rozpocznij od pisania nowego testu:</span><span class="sxs-lookup"><span data-stu-id="70313-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="70313-164">Test można naprawić przez przekazanie w potoku filtrowane sekwencji za pomocą operacji mapy do obliczenia kwadratowy poszczególnych nieparzysta:</span><span class="sxs-lookup"><span data-stu-id="70313-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

<span data-ttu-id="70313-165">Gdy masz utworzoną małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="70313-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="70313-166">Tak, aby dodawania nowych pakietów została ze strukturą rozwiązania i testów jest częścią normalnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="70313-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="70313-167">Po skoncentrowany większość czasu i wysiłku niewiele rozwiązywania cele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70313-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
