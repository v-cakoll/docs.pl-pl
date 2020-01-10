---
title: Testy F# jednostkowe w środowisku .NET Core z testami dotnet i nunit
description: Poznaj koncepcje testów jednostkowych dla F# platformy .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania krok po kroku przy użyciu testu dotnet i NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 3347e5b90c31589e9a0f99ac0d9298927a717f56
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715450"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>Biblioteki testów F# jednostkowych w programie .NET Core przy użyciu testu dotnet i nunit

Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) . Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- [Zestaw .NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub jego nowsze wersje.
- Wybrany edytor tekstu lub edytor kodu.

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *Unit-Test-with-FSharp* , aby pomieścić rozwiązanie.
W tym nowym katalogu Uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:

```dotnetcli
dotnet new sln
```

Następnie Utwórz katalog *mathservice* . Poniższy konspekt przedstawia strukturę katalogu i pliku do tej pory:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Ustaw *mathservice* w bieżącym katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:

```dotnetcli
dotnet new classlib -lang "F#"
```

Tworzysz nieprawidłową implementację usługi matematycznej:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Zmień katalog z powrotem na katalog *test-z-FSharp* . Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

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

Utwórz katalog *mathservice. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą następującego polecenia:

```dotnetcli
dotnet new nunit -lang "F#"
```

Spowoduje to utworzenie projektu testowego, który używa NUnit jako środowiska testowego. Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w *MathServiceTests. fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new` w poprzednim kroku został dodany NUnit i adapter testowy NUnit. Teraz dodaj bibliotekę klas `MathService` jako inną zależność do projektu. Użyj `dotnet add reference` polecenia:

```dotnetcli
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
        MathService.Tests.fsproj
```

Wykonaj następujące polecenie w katalogu *Unit-Test-with-FSharp* :

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces. Otwórz *UnitTest1. FS* i Dodaj następujący kod:

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

Atrybut `[<TestFixture>]` oznacza klasę, która zawiera testy. Atrybut `[<Test>]` oznacza metodę testową, która jest uruchamiana przez program Test Runner. W katalogu *testy jednostkowe-with-FSharp* należy wykonać `dotnet test`, aby skompilować testy i bibliotekę klas, a następnie uruchomić testy. Program NUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów. `dotnet test` uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.

Te dwa testy pokazują najbardziej podstawowe testy dotyczące przekazywania i niepowodzenia. `My test` passs i `Fail every time` nie powiedzie się. Teraz Utwórz test dla metody `squaresOfOdds`. Metoda `squaresOfOdds` zwraca sekwencję kwadratów wszystkich nieparzystych wartości całkowitych, które są częścią sekwencji wejściowej. Zamiast próbować zapisywać wszystkie te funkcje jednocześnie, można iteracyjnie utworzyć testy, które weryfikują funkcjonalność. Każdy przebieg testowy oznacza tworzenie niezbędnych funkcji dla metody.

Najprostszym testem możemy napisać jest wywołanie `squaresOfOdds` ze wszystkimi parzystymi liczbami, gdzie wynik powinien być pustą sekwencją liczb całkowitych.  Oto test:

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Zwróć uwagę, że sekwencja `expected` została przekonwertowana na listę. Platforma NUnit jest oparta na wielu standardowych typach .NET. Ta zależność oznacza, że interfejs publiczny i oczekiwane wyniki obsługują <xref:System.Collections.ICollection>, a nie <xref:System.Collections.IEnumerable>.

Po uruchomieniu testu zobaczysz, że test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Wykonaj ten test, pisząc najprostszy kod w klasie *Library. FS* w projekcie mathservice, który działa:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

W katalogu *testy jednostkowe-with-FSharp* uruchom ponownie `dotnet test`. `dotnet test` polecenie uruchamia kompilację dla projektu `MathService`, a następnie dla projektu `MathService.Tests`. Po skompilowaniu obu projektów uruchamiamy testy. Dwa testy są teraz zakończone pomyślnie.

## <a name="completing-the-requirements"></a>Spełnienie wymagań

Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej. Następny prosty przypadek działa z sekwencją, której tylko numer nieparzysty jest `1`. Numer 1 jest łatwiejszy, ponieważ kwadrat 1 ma wartość 1. Oto następny test:

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Wykonanie `dotnet test` nie powiedzie się w nowym teście. Należy zaktualizować metodę `squaresOfOdds`, aby obsługiwała ten nowy test. Należy odfiltrować wszystkie liczby parzyste z sekwencji, aby wykonać ten test. Możesz to zrobić, pisząc małą funkcję filtrowania i używając `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Zwróć uwagę na wywołanie `Seq.toList`. Tworzy listę, która implementuje interfejs <xref:System.Collections.ICollection>.

Istnieje jeden krok do przechodzenia: kwadrat każdej z liczb nieparzystych. Zacznij od zapisania nowego testu:

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
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

## <a name="see-also"></a>Zobacz także

- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
