---
title: Testy F# jednostkowe w środowisku .NET Core z testami dotnet i MSTest
description: Poznaj koncepcje testów jednostkowych dla F# platformy .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania krok po kroku przy użyciu testu dotnet i MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: d402d6a8e4d9285f7107d0cacaea9f00e1e9344b
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374178"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a>Biblioteki testów F# jednostkowych w programie .NET Core przy użyciu testu dotnet i MSTest

Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) . Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

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

```console
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Utwórz katalog *mathservice. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą [`dotnet new mstest -lang F#`](../tools/dotnet-new.md)polecenia. Spowoduje to utworzenie projektu testowego, który używa MSTest jako środowiska testowego. Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w *MathServiceTests. fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano MSTest i moduł uruchamiający MSTest. Teraz Dodaj `MathService` bibliotekę klas jako inną zależność do projektu. [`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:

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

Ten `[<TestClass>]` atrybut oznacza klasę, która zawiera testy. Ten `[<TestMethod>]` atrybut oznacza metodę testową, która jest uruchamiana przez program Test Runner. W katalogu *test jednostkowy-with-FSharp* wykonaj [`dotnet test`](../tools/dotnet-test.md) , aby skompilować testy i bibliotekę klas, a następnie uruchom testy. Program MSTest Test Runner zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.

Te dwa testy pokazują najbardziej podstawowe testy dotyczące przekazywania i niepowodzenia. `My test``Fail every time` kończy się niepowodzeniem. Teraz Utwórz test dla `squaresOfOdds` metody. `squaresOfOdds` Metoda zwraca listę kwadratów wszystkich nieparzystych wartości całkowitych, które są częścią sekwencji wejściowej. Zamiast próbować zapisywać wszystkie te funkcje jednocześnie, można iteracyjnie utworzyć testy, które weryfikują funkcjonalność. Każdy przebieg testowy oznacza tworzenie niezbędnych funkcji dla metody.

Najprostszym testem możemy napisać jest wywołanie `squaresOfOdds` ze wszystkimi parzystymi liczbami, gdzie wynik powinien być pustą sekwencją liczb całkowitych.  Oto test:

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

Zauważ, że `expected` sekwencja została przekonwertowana na listę. Biblioteka MSTest opiera się na wielu standardowych typach .NET. Ta zależność oznacza, że interfejs publiczny i oczekiwane wyniki <xref:System.Collections.ICollection> są obsługiwane <xref:System.Collections.IEnumerable>, a nie.

Po uruchomieniu testu zobaczysz, że test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Wykonaj ten test, pisząc najprostszy kod w `Mathservice` klasie, która działa:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

W katalogu *testy jednostkowe-with-FSharp* Uruchom `dotnet test` ponownie. Polecenie uruchamia kompilację `MathService` dla `MathService.Tests` projektu, a następnie dla projektu. `dotnet test` Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test. Przekazuje.

## <a name="completing-the-requirements"></a>Spełnienie wymagań

Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej. Następny prosty przypadek działa z sekwencją, której jedyną liczbą nieparzystą jest `1`. Numer 1 jest łatwiejszy, ponieważ kwadrat 1 ma wartość 1. Oto następny test:

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

Wykonywanie `dotnet test` nowego testu nie powiodło się. Musisz zaktualizować `squaresOfOdds` metodę, aby obsłużyć ten nowy test. Należy odfiltrować wszystkie liczby parzyste z sekwencji, aby wykonać ten test. Możesz to zrobić, pisząc małą funkcję filtrowania i używając `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

Zwróć uwagę na `Seq.toList`wywołanie. Tworzy listę, która implementuje <xref:System.Collections.ICollection> interfejs.

Istnieje jeden krok do przechodzenia: kwadrat każdej z liczb nieparzystych. Zacznij od zapisania nowego testu:

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

Możesz naprawić test, przechodząc sekwencję przefiltrowanych przez operację mapowania, aby obliczyć kwadrat dla każdej liczby nieparzystej:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

Utworzono niewielką bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Rozbudowane rozwiązanie jest przeznaczone do dodawania nowych pakietów i testów jest częścią normalnego przepływu pracy. Zbyt najwięcej czasu i wysiłku na rozwiązywanie celów aplikacji.
