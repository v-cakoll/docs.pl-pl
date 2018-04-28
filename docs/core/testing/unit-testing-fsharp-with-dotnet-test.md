---
title: 'Testowanie biblioteki F # w .NET Core za pomocą testu dotnet i xUnit jednostki'
description: 'Informacje pojęcia testów jednostkowych dla F # w .NET Core za pomocą interaktywna tworzenia przykładowe rozwiązanie krok po kroku przy użyciu platformy dotnet testu i xUnit.'
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: conceptual
dev_langs:
- fsharp
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 11fab52cb426b0dbb173c9c6e2bd7b5766501964
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="fd0a4-103">Testowanie biblioteki F # w .NET Core za pomocą testu dotnet i xUnit jednostki</span><span class="sxs-lookup"><span data-stu-id="fd0a4-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="fd0a4-104">Ten samouczek przedstawia interaktywna tworzenia przykładowe rozwiązanie krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="fd0a4-105">Jeśli chcesz wykonać czynności opisane w samouczku za pomocą wbudowanych rozwiązania, [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="fd0a4-106">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="fd0a4-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="fd0a4-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="fd0a4-107">Creating the source project</span></span>

<span data-ttu-id="fd0a4-108">Umożliwia otwarcie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-108">Open a shell window.</span></span> <span data-ttu-id="fd0a4-109">Utwórz katalog o nazwie *jednostki — testowanie z — języka fsharp* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="fd0a4-110">Wewnątrz tego nowego katalogu Uruchom [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="fd0a4-111">Ułatwia to zarządzanie biblioteki klas i jednostkowy projekt testowy.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="fd0a4-112">Utwórz katalog rozwiązania *MathService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="fd0a4-113">Struktura katalogów i plików dotychczasowych jest pokazany poniżej:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="fd0a4-114">Wprowadź *MathService* bieżącego katalogu i uruchom [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) do tworzenia projektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="fd0a4-115">Aby użyć projektowanie oparte na testach (TDD), należy utworzyć niepowodzenie stosowania usługi matematyczne:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="fd0a4-116">Zmień katalog z powrotem do *jednostki — testowanie z — języka fsharp* katalogu.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="fd0a4-117">Uruchom [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="fd0a4-118">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="fd0a4-118">Creating the test project</span></span>

<span data-ttu-id="fd0a4-119">Następnie należy utworzyć *MathService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="fd0a4-120">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="fd0a4-121">Wprowadź *MathService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="fd0a4-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="fd0a4-122">Spowoduje to utworzenie projektu testowego używającą xUnit jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="fd0a4-123">Wygenerowanego szablonu konfiguruje uruchamiający w *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="fd0a4-124">Projekt testowy wymaga inne pakiety do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="fd0a4-125">`dotnet new` w poprzednim kroku należy dodać xUnit i xUnit modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="fd0a4-126">Teraz Dodaj `MathService` biblioteki klas jako zależność od innego projektu.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="fd0a4-127">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="fd0a4-128">Widoczny cały plik w [przykłady repozytorium](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="fd0a4-129">Masz następujące układu ostatecznego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="fd0a4-130">Wykonanie [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) w *jednostki — testowanie z — języka fsharp* katalogu.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="fd0a4-131">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="fd0a4-131">Creating the first test</span></span>

<span data-ttu-id="fd0a4-132">Podejście TDD odwołuje się do pisania niepowodzeniu jednego testu, co Przekaż, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="fd0a4-133">Otwórz *Tests.fs* i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="fd0a4-134">`[<Fact>]` Atrybut oznacza metodę test jest uruchamiany przez moduł uruchamiający.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="fd0a4-135">Z *jednostki — testowanie z — języka fsharp*, wykonać [ `dotnet test` ](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-135">From the *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="fd0a4-136">Moduł uruchamiający xUnit zawiera punkt wejścia programu do uruchomienia testów.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="fd0a4-137">`dotnet test` Uruchamia uruchamiający przy użyciu jednostkowy projekt testowy, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="fd0a4-138">Tych dwóch testów Pokaż najbardziej podstawową, przekazywanie i w przypadku braku testy.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="fd0a4-139">`My test` przekazuje, i `Fail every time` nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="fd0a4-140">Teraz, Utwórz test `squaresOfOdds` metody.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="fd0a4-141">`squaresOfOdds` Metoda zwraca sekwencję kwadratów wszystkie wartości nieparzystą liczbą całkowitą, które są częścią sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="fd0a4-142">Zamiast w trakcie zapisanie wszystkich tych funkcji na raz, można utworzyć wielokrotnie powtarzane testy sprawdzania poprawności funkcji.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="fd0a4-143">Wprowadzenie każdego z testów przekazać oznacza, że tworzenie funkcji niezbędne dla metody.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="fd0a4-144">Jest najprostsza testu, firma Microsoft może zapisywać do wywołania `squaresOfOdds` z wszystkie liczby parzyste, w którym wynik powinien być pustą sekwencją liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="fd0a4-145">Oto tego testu:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="fd0a4-146">Test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-146">Your test fails.</span></span> <span data-ttu-id="fd0a4-147">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="fd0a4-148">Należy ten test przez pisania kodu najprostsza w `MathService` klasy, która działa:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-148">Make this test by writing the simplest code in the `MathService` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="fd0a4-149">W *jednostki — testowanie z — języka fsharp* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="fd0a4-150">`dotnet test` Polecenia uruchamiane kompilacji dla `MathService` projektu i następnie `MathService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="fd0a4-151">Po utworzeniu oba projekty, jest uruchamiana ta pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="fd0a4-152">Przekazuje ono.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="fd0a4-153">Korzystanie z wymaganiami</span><span class="sxs-lookup"><span data-stu-id="fd0a4-153">Completing the requirements</span></span>

<span data-ttu-id="fd0a4-154">Teraz, kiedy dokonano jeden test przekazać nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="fd0a4-155">Następny prostym przypadku współpracuje z sekwencji, których tylko nieparzysta liczba jest `1`.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="fd0a4-156">Numer 1 jest łatwiejsze, ponieważ kwadrat 1 jest 1.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="fd0a4-157">Oto Następny test:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="fd0a4-158">Wykonywanie `dotnet test` uruchomi testy i pokazuje, że nowy test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="fd0a4-159">Teraz zaktualizuj `squaresOfOdds` można obsłużyć tego nowego testu.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="fd0a4-160">Można filtrować wszystkie liczby parzyste poza kolejnością, aby ten test przekazywania.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="fd0a4-161">Możesz to zrobić pisanie funkcji małych filtru i używając `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="fd0a4-162">Istnieje jeden krok Przejdź: kwadratowe każdego nieparzyste numery.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="fd0a4-163">Rozpocznij od zapisywania nowego testu:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="fd0a4-164">Test można rozwiązać przez przekazanie w potoku filtrowane sekwencji za pomocą operacji mapy do obliczenia wartości kwadratu każdą nieparzystą liczbę:</span><span class="sxs-lookup"><span data-stu-id="fd0a4-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

<span data-ttu-id="fd0a4-165">Został utworzony małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="fd0a4-166">Zostały strukturę rozwiązania, aby dodać nowe pakiety i testów jest częścią Normalny przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="fd0a4-167">Już skoncentrowany większość czasu i uwagi na temat rozwiązywania problemów celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd0a4-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
