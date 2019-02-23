---
title: Testy jednostkowe F# platformie .NET Core za pomocą polecenia dotnet test i struktury xUnit
description: Informacje na temat testów jednostek dla F# platformy .NET Core za pomocą interaktywnych doświadczenia przykładowe rozwiązanie krok po kroku za pomocą polecenia dotnet test i struktury xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 9765c463bb427f79dcd0308e7e4fc643fdc06968
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745949"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a>Testy jednostkowe F# bibliotek w programie .NET Core za pomocą polecenia dotnet test i struktury xUnit

Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych. Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) przed przystąpieniem do wykonywania. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwieranie okna powłoki. Utwórz katalog o nazwie *jednostki — testowanie z fsharp* do przechowywania rozwiązania.
Wewnątrz tego nowy katalog uruchamiania [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania. Dzięki temu można łatwiej zarządzać biblioteki klas i projekt testów jednostkowych.
Utwórz katalog rozwiązania *MathService* katalogu. Struktura katalogów i plików dotychczasowych znajdują się poniżej:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Wprowadź *MathService* bieżącego katalogu i uruchom [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) do utworzenia projektu źródłowego.  Utworzysz niepowodzenie stosowania usługi matematyczne:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Zmień katalog kopii do *jednostki — testowanie z fsharp* katalogu. Uruchom [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas w rozwiązaniu.

## <a name="creating-the-test-project"></a>Tworzenie projektu testu

Następnie należy utworzyć *MathService.Tests* katalogu. Następujące konspektu przedstawia strukturę katalogów:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Wprowadź *MathService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md). Spowoduje to utworzenie projektu testowego, który używa rozwiązania xUnit, jako biblioteka testów. Wygenerowany szablon konfiguruje narzędzie test runner w *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe. `dotnet new` w poprzednim kroku dodawany xUnit, a moduł uruchamiający testy xUnit. Teraz Dodaj `MathService` biblioteki klas jako inny zależności do projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```
dotnet add reference ../MathService/MathService.fsproj
```

Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w witrynie GitHub.

Masz następujące układ ostateczne rozwiązanie:

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

Wykonaj [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) w *jednostki — testowanie z fsharp* katalogu. 

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Jeden zapisu kończy się niepowodzeniem testu, ułatwiają — dostęp próbny, a następnie powtórz ten proces. Otwórz *Tests.fs* i Dodaj następujący kod:

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

`[<Fact>]` Atrybut oznacza metodę testową, która jest uruchamiany przez narzędzie test runner. Z *jednostki — testowanie z fsharp*, wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy. Moduł uruchamiający xUnit zawiera punkt wejścia programu, aby uruchomić testy. `dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.

Testy te dwa Pokaż najbardziej podstawowym, przekazywanie i niepowodzenie testów. `My test` przekazuje, i `Fail every time` zakończy się niepowodzeniem. Teraz Utwórz test `squaresOfOdds` metody. `squaresOfOdds` Metoda zwraca sekwencję kwadratów wszystkie wartości nieparzystej liczby całkowitej, które są częścią sekwencji wejściowych. Zamiast próbowania zapisać wszystkie te funkcje na raz, iteracyjne można tworzyć testy, które sprawdzają poprawność funkcji. Dzięki czemu każdy przebieg sprowadza się do utworzenia niezbędnych funkcji dla metody testu.

Najprostsza testów, możemy napisać jest wywołanie `squaresOfOdds` z wszystkie liczby parzyste z zakresu, gdzie powinna zostać pustą sekwencją liczb całkowitych.  Oto tego testu:

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Test nie powiedzie się. Nie utworzono jeszcze wdrożenia. Należy ten test przez napisanie kodu najprostsza `MathService` klasę, która działa:

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

W *jednostki — testowanie z fsharp* katalogu, uruchom `dotnet test` ponownie. `dotnet test` Polecenie uruchamia kompilację dla `MathService` projektu i następnie `MathService.Tests` projektu. Po utworzeniu obu projektów, działa ten jeden test. Przekazuje on.

## <a name="completing-the-requirements"></a>Korzystanie z wymaganiami

Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej. Dalej prostym przypadku współpracuje z sekwencji jest liczbą nieparzystą tylko `1`. Numer 1 jest łatwiejsze, ponieważ kwadrat 1 jest 1. Oto tego Następny test:

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Wykonywanie `dotnet test` uruchamia testy i dowiesz się, że nowy test kończy się niepowodzeniem. Teraz zaktualizuj `squaresOfOdds` metody, aby obsłużyć ten nowy test. Możesz filtrować wszystkie liczby parzyste poza kolejnością, aby ten przebieg testu. Możesz to zrobić przez pisanie funkcji filtru małe i przy użyciu `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Istnieje jeszcze jeden krok do: każdej liczby nieparzyste kwadratowe. Rozpocznij od pisania nowego testu:

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

Test można naprawić przez przekazanie w potoku filtrowane sekwencji za pomocą operacji mapy do obliczenia kwadratowy poszczególnych nieparzysta:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

Gdy masz utworzoną małych biblioteki i zestaw testów jednostkowych dla tej biblioteki. Tak, aby dodawania nowych pakietów została ze strukturą rozwiązania i testów jest częścią normalnego przepływu pracy. Po skoncentrowany większość czasu i wysiłku niewiele rozwiązywania cele aplikacji.
