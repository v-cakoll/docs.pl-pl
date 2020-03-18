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
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a>Testowanie jednostkowe bibliotek F# w .NET Core przy użyciu testu dotnet i xUnit

W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) przed rozpoczęciem. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *unit-testing-with-fsharp* do przechowywania rozwiązania.
Wewnątrz tego nowego `dotnet new sln` katalogu uruchom, aby utworzyć nowe rozwiązanie. Ułatwia to zarządzanie zarówno biblioteki klas i projektu testu jednostkowego.
Wewnątrz katalogu rozwiązania utwórz katalog *MathService.* Struktura katalogów i plików do tej pory jest pokazana poniżej:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Utwórz *MathService* bieżącego `dotnet new classlib -lang "F#"` katalogu i uruchom, aby utworzyć projekt źródłowy. Utworzysz nieudołężej wykonania usługi matematycznej:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Zmień katalog z powrotem do katalogu *testowania jednostek z fsharp.* Uruchom, `dotnet sln add .\MathService\MathService.fsproj` aby dodać projekt biblioteki klas do rozwiązania.

## <a name="creating-the-test-project"></a>Tworzenie projektu testowego

Następnie utwórz katalog *MathService.Tests.* Poniższy konspekt przedstawia strukturę katalogów:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Utwórz katalog *MathService.Tests* jako bieżący katalog `dotnet new xunit -lang "F#"`i utwórz nowy projekt przy użyciu . Spowoduje to utworzenie projektu testowego, który używa xUnit jako biblioteki testowej. Wygenerowany szablon konfiguruje testrunner w *MathServiceTests.fsproj:*

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano xUnit i xUnit runner. Teraz dodaj `MathService` bibliotekę klas jako inną zależność do projektu. Użyj `dotnet add reference` polecenia:

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w uspolu GitHub.

Masz następujący ostateczny układ rozwiązania:

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

Wykonywanie `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` w katalogu *testowania jednostek z fsharp.*

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces. Otwórz *testy.fs* i dodaj następujący kod:

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

Atrybut `[<Fact>]` oznacza metodę testową, która jest uruchamiana przez test runner. Z *jednostki testowania-with-fsharp*, `dotnet test` wykonaj do kompilacji testów i biblioteki klas, a następnie uruchomić testy. Program testowy xUnit zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.

Te dwa testy pokazują najbardziej podstawowe testy zaliczenia i niepowodzenia. `My test`przechodzi i `Fail every time` nie powiedzie się. Teraz utwórz test `squaresOfOdds` dla metody. Metoda `squaresOfOdds` zwraca sekwencję kwadratów wszystkich wartości nieparzystych liczb całkowitych, które są częścią sekwencji wejściowej. Zamiast próbować napisać wszystkie te funkcje naraz, można iteracyjne tworzenie testów, które sprawdzają poprawność funkcji. Dokonywanie każdego testu oznacza tworzenie niezbędnych funkcji dla metody.

Najprostszym testem, który `squaresOfOdds` możemy napisać, jest wywołanie ze wszystkimi parzystymi numerami, gdzie wynik powinien być pustą sekwencją liczb całkowitych.  Oto ten test:

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Test nie powiedzie się. Implementacja nie została jeszcze utworzona. Zrób ten test przejść, pisząc najprostszy kod w `MathService` klasie, która działa:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

W katalogu *testowania jednostek z fsharp* `dotnet test` uruchom ponownie. Polecenie `dotnet test` uruchamia kompilację `MathService` dla projektu, `MathService.Tests` a następnie dla projektu. Po zbudowaniu obu projektów uruchamia ten pojedynczy test. Mija.

## <a name="completing-the-requirements"></a>Wypełnianie wymagań

Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej. Następny prosty przypadek działa z sekwencją, `1`której jedyną liczbą nieparzystą jest . Liczba 1 jest łatwiejsza, ponieważ kwadrat 1 wynosi 1. Oto następny test:

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Wykonywanie `dotnet test` uruchamia testy i pokazuje, że nowy test nie powiedzie się. Teraz zaktualizuj `squaresOfOdds` metodę obsługi tego nowego testu. Możesz filtrować wszystkie numery parzyste z sekwencji, aby ten test przeszedł. Można to zrobić, pisząc małą funkcję `Seq.filter`filtra i używając:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Jest jeszcze jeden krok do zrobienia: kwadrat każdej z liczb nieparzystych. Zacznij od napisania nowego testu:

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

Test można naprawić, przeinacząc przefiltrowaną sekwencję za pomocą operacji mapy, aby obliczyć kwadrat każdego nieparzystego numeru:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy. Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.

## <a name="see-also"></a>Zobacz też

- [dotnet new](../tools/dotnet-new.md)
- [dotnet sln](../tools/dotnet-new.md)
- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
