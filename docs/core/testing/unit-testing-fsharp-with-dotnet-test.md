---
title: Testy F# jednostkowe w środowisku .NET Core z testami dotnet i xUnit
description: Poznaj koncepcje testów jednostkowych dla F# platformy .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania krok po kroku przy użyciu testu dotnet i xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 56cf97752251d9bf49226d919508d2f972f2982a
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373890"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a>Biblioteki testów F# jednostkowych w programie .NET Core przy użyciu testu dotnet i xUnit

Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) . Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *Unit-Test-with-FSharp* , aby pomieścić rozwiązanie.
W tym nowym katalogu Uruchom [`dotnet new sln`](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie. Ułatwia to zarządzanie biblioteką klas i projektem testów jednostkowych.
W katalogu rozwiązania Utwórz katalog *mathservice* . W tej chwili struktura katalogów i plików jest pokazana poniżej:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Ustaw *mathservice* w bieżącym katalogu i uruchom [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) , aby utworzyć projekt źródłowy.  Utworzysz nieprawidłową implementację usługi matematycznej:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Zmień katalog z powrotem na katalog *test-z-FSharp* . Uruchom [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) , aby dodać projekt biblioteki klas do rozwiązania.

## <a name="creating-the-test-project"></a>Tworzenie projektu testowego

Następnie Utwórz katalog *mathservice. Tests* . Poniższy konspekt przedstawia strukturę katalogów:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Utwórz katalog *mathservice. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą [`dotnet new xunit -lang F#`](../tools/dotnet-new.md)polecenia. Spowoduje to utworzenie projektu testowego, który używa xUnit jako biblioteki testowej. Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w *MathServiceTests. fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano xUnit i moduł uruchamiający xUnit. Teraz Dodaj `MathService` bibliotekę klas jako inną zależność do projektu. [`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:

```console
dotnet add reference ../MathService/MathService.fsproj
```

Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w witrynie GitHub.

Dysponujesz następującym końcowym układem rozwiązań:

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

Wykonaj [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) w katalogu *test-z-FSharp* . 

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces. Otwórz aplet *testy. FS* i Dodaj następujący kod:

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

Ten `[<Fact>]` atrybut oznacza metodę testową, która jest uruchamiana przez program Test Runner. Z *jednostki-test-with-FSharp*należy wykonać [`dotnet test`](../tools/dotnet-test.md) , aby skompilować testy i bibliotekę klas, a następnie uruchomić testy. Program xUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.

Te dwa testy pokazują najbardziej podstawowe testy dotyczące przekazywania i niepowodzenia. `My test``Fail every time` kończy się niepowodzeniem. Teraz Utwórz test dla `squaresOfOdds` metody. `squaresOfOdds` Metoda zwraca sekwencję kwadratów wszystkich nieparzystych wartości całkowitych, które są częścią sekwencji wejściowej. Zamiast próbować zapisywać wszystkie te funkcje jednocześnie, można iteracyjnie utworzyć testy, które weryfikują funkcjonalność. Każdy przebieg testowy oznacza tworzenie niezbędnych funkcji dla metody.

Najprostszym testem możemy napisać jest wywołanie `squaresOfOdds` ze wszystkimi parzystymi liczbami, gdzie wynik powinien być pustą sekwencją liczb całkowitych.  Oto test:

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Wykonaj ten test, pisząc najprostszy kod w `MathService` klasie, która działa:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

W katalogu *testy jednostkowe-with-FSharp* Uruchom `dotnet test` ponownie. Polecenie uruchamia kompilację `MathService` dla `MathService.Tests` projektu, a następnie dla projektu. `dotnet test` Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test. Przekazuje.

## <a name="completing-the-requirements"></a>Spełnienie wymagań

Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej. Następny prosty przypadek działa z sekwencją, której jedyną liczbą nieparzystą jest `1`. Numer 1 jest łatwiejszy, ponieważ kwadrat 1 ma wartość 1. Oto następny test:

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Wykonanie `dotnet test` uruchamia testy i pokazuje, że nowy test zakończy się niepowodzeniem. Teraz zaktualizuj `squaresOfOdds` metodę, aby obsłużyć ten nowy test. Wszystkie liczby parzyste z sekwencji są filtrowane, aby wykonać ten test. Możesz to zrobić, pisząc małą funkcję filtrowania i używając `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Istnieje jeden krok do przechodzenia: kwadrat każdej z liczb nieparzystych. Zacznij od zapisania nowego testu:

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

Możesz naprawić test, przechodząc sekwencję przefiltrowanych przez operację mapowania, aby obliczyć kwadrat dla każdej liczby nieparzystej:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

Utworzono niewielką bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Rozbudowane rozwiązanie jest przeznaczone do dodawania nowych pakietów i testów jest częścią normalnego przepływu pracy. Zbyt najwięcej czasu i wysiłku na rozwiązywanie celów aplikacji.
