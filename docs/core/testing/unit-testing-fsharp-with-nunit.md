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
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>Testowanie jednostkowe bibliotek F# w .NET Core przy użyciu testu dotnet i NUnit

W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) przed rozpoczęciem. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje.
- Wybrany edytor tekstu lub edytor kodu.

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *unit-testing-with-fsharp* do przechowywania rozwiązania.
W tym nowym katalogu uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:

```dotnetcli
dotnet new sln
```

Następnie utwórz katalog *MathService.* Poniższy konspekt pokazuje strukturę katalogów i plików do tej pory:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Utwórz *MathService* bieżącego katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:

```dotnetcli
dotnet new classlib -lang "F#"
```

Tworzenie nieudanej implementacji usługi matematycznej:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Zmień katalog z powrotem do katalogu *testowania jednostek z fsharp.* Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

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

Utwórz katalog *MathService.Tests* bieżącego katalogu i utwórz nowy projekt przy użyciu następującego polecenia:

```dotnetcli
dotnet new nunit -lang "F#"
```

Spowoduje to utworzenie projektu testowego, który używa NUnit jako struktury testowej. Wygenerowany szablon konfiguruje testrunner w *MathServiceTests.fsproj:*

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano NUnit i kartę testową NUnit. Teraz dodaj `MathService` bibliotekę klas jako inną zależność do projektu. Użyj `dotnet add reference` polecenia:

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
        MathService.Tests.fsproj
```

Wykonaj następujące polecenie w katalogu testów jednostkowych:Execute the following command in the *unit-testing-with-fsharp* directory:

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces. Otwórz *program UnitTest1.fs* i dodaj następujący kod:

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

Atrybut `[<TestFixture>]` oznacza klasę, która zawiera testy. Atrybut `[<Test>]` oznacza metodę testową, która jest uruchamiana przez test runner. Z *katalogu testowania jednostek z fsharp* `dotnet test` wykonaj, aby utworzyć testy i biblioteki klas, a następnie uruchomić testy. Program testowy NUnit zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.

Te dwa testy pokazują najbardziej podstawowe testy zaliczenia i niepowodzenia. `My test`przechodzi i `Fail every time` nie powiedzie się. Teraz utwórz test `squaresOfOdds` dla metody. Metoda `squaresOfOdds` zwraca sekwencję kwadratów wszystkich wartości nieparzystych liczb całkowitych, które są częścią sekwencji wejściowej. Zamiast próbować napisać wszystkie te funkcje naraz, można iteracyjne tworzenie testów, które sprawdzają poprawność funkcji. Dokonywanie każdego testu oznacza tworzenie niezbędnych funkcji dla metody.

Najprostszym testem, który `squaresOfOdds` możemy napisać, jest wywołanie ze wszystkimi parzystymi numerami, gdzie wynik powinien być pustą sekwencją liczb całkowitych.  Oto ten test:

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Należy zauważyć, że sekwencja `expected` została przekonwertowana na listę. Struktura NUnit opiera się na wielu standardowych typach .NET. Ta zależność oznacza, że interfejs publiczny <xref:System.Collections.ICollection> i <xref:System.Collections.IEnumerable>oczekiwane wyniki obsługują, a nie .

Po uruchomieniu testu, widać, że test nie powiedzie się. Implementacja nie została jeszcze utworzona. Zrób ten test pass, pisząc najprostszy kod w *Library.fs* klasy w projekcie MathService, który działa:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

W katalogu *testowania jednostek z fsharp* `dotnet test` uruchom ponownie. Polecenie `dotnet test` uruchamia kompilację `MathService` dla projektu, `MathService.Tests` a następnie dla projektu. Po zbudowaniu obu projektów uruchamia testy. Teraz przechodzą dwa testy.

## <a name="completing-the-requirements"></a>Wypełnianie wymagań

Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej. Następny prosty przypadek działa z sekwencją, `1`której jedyną liczbą nieparzystą jest . Liczba 1 jest łatwiejsza, ponieważ kwadrat 1 wynosi 1. Oto następny test:

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Wykonywanie `dotnet test` nie powiedzie się nowy test. Należy zaktualizować `squaresOfOdds` metodę obsługi tego nowego testu. Należy filtrować wszystkie numery parzyste z sekwencji, aby ten test przeszedł. Można to zrobić, pisząc małą funkcję `Seq.filter`filtra i używając:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Zwróć uwagę `Seq.toList`na wywołanie . Który tworzy listę, która <xref:System.Collections.ICollection> implementuje interfejs.

Jest jeszcze jeden krok do zrobienia: kwadrat każdej z liczb nieparzystych. Zacznij od napisania nowego testu:

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
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

- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
