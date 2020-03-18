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
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a>Testowanie jednostkowe bibliotek F# w .NET Core przy użyciu testu dotnet i mstest

W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) przed rozpoczęciem. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

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

Utwórz *MathService* bieżącego `dotnet new classlib -lang "F#"` katalogu i uruchom, aby utworzyć projekt źródłowy.  Utworzysz nieudołężej wykonania usługi matematycznej:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Zmień katalog z powrotem do katalogu *testowania jednostek z fsharp.* Uruchom, `dotnet sln add .\MathService\MathService.fsproj` aby dodać projekt biblioteki klas do rozwiązania.

## <a name="creating-the-test-project"></a>Tworzenie projektu testowego

Następnie utwórz katalog *MathService.Tests.* Poniższy konspekt przedstawia strukturę katalogów:

```console
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Utwórz katalog *MathService.Tests* jako bieżący katalog `dotnet new mstest -lang "F#"`i utwórz nowy projekt przy użyciu . Spowoduje to utworzenie projektu testowego, który używa MSTest jako struktury testowej. Wygenerowany szablon konfiguruje testrunner w *MathServiceTests.fsproj:*

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano MSTest i mstest runner. Teraz dodaj `MathService` bibliotekę klas jako inną zależność do projektu. Użyj `dotnet add reference` polecenia:

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

Atrybut `[<TestClass>]` oznacza klasę, która zawiera testy. Atrybut `[<TestMethod>]` oznacza metodę testową, która jest uruchamiana przez test runner. Z *katalogu testowania jednostek z fsharp* `dotnet test` wykonaj, aby utworzyć testy i biblioteki klas, a następnie uruchomić testy. Program testowy MSTest zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.

Te dwa testy pokazują najbardziej podstawowe testy zaliczenia i niepowodzenia. `My test`przechodzi i `Fail every time` nie powiedzie się. Teraz utwórz test `squaresOfOdds` dla metody. Metoda `squaresOfOdds` zwraca listę kwadratów wszystkich wartości nieparzystych liczb całkowitych, które są częścią sekwencji wejściowej. Zamiast próbować napisać wszystkie te funkcje naraz, można iteracyjne tworzenie testów, które sprawdzają poprawność funkcji. Dokonywanie każdego testu oznacza tworzenie niezbędnych funkcji dla metody.

Najprostszym testem, który `squaresOfOdds` możemy napisać, jest wywołanie ze wszystkimi parzystymi numerami, gdzie wynik powinien być pustą sekwencją liczb całkowitych.  Oto ten test:

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

Należy zauważyć, że sekwencja `expected` została przekonwertowana na listę. Biblioteka MSTest opiera się na wielu standardowych typach .NET. Ta zależność oznacza, że interfejs publiczny <xref:System.Collections.ICollection> i <xref:System.Collections.IEnumerable>oczekiwane wyniki obsługują, a nie .

Po uruchomieniu testu, widać, że test nie powiedzie się. Implementacja nie została jeszcze utworzona. Zrób ten test przejść, pisząc najprostszy kod w `Mathservice` klasie, która działa:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

W katalogu *testowania jednostek z fsharp* `dotnet test` uruchom ponownie. Polecenie `dotnet test` uruchamia kompilację `MathService` dla projektu, `MathService.Tests` a następnie dla projektu. Po zbudowaniu obu projektów uruchamia ten pojedynczy test. Mija.

## <a name="completing-the-requirements"></a>Wypełnianie wymagań

Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej. Następny prosty przypadek działa z sekwencją, `1`której jedyną liczbą nieparzystą jest . Liczba 1 jest łatwiejsza, ponieważ kwadrat 1 wynosi 1. Oto następny test:

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

Wykonywanie `dotnet test` nie powiedzie się nowy test. Należy zaktualizować `squaresOfOdds` metodę obsługi tego nowego testu. Należy filtrować wszystkie numery parzyste z sekwencji, aby ten test przeszedł. Można to zrobić, pisząc małą funkcję `Seq.filter`filtra i używając:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

Zwróć uwagę `Seq.toList`na wywołanie . Który tworzy listę, która <xref:System.Collections.ICollection> implementuje interfejs.

Jest jeszcze jeden krok do zrobienia: kwadrat każdej z liczb nieparzystych. Zacznij od napisania nowego testu:

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

Test można naprawić, przeinacząc przefiltrowaną sekwencję za pomocą operacji mapy, aby obliczyć kwadrat każdego nieparzystego numeru:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy. Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.

## <a name="see-also"></a>Zobacz też

- [dotnet new](../tools/dotnet-new.md)
- [dotnet sln](../tools/dotnet-sln.md)
- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
