---
title: Testy jednostkowe F# platformie .NET Core za pomocą polecenia dotnet test i struktury MSTest
description: Informacje na temat testów jednostek dla F# platformy .NET Core za pomocą interaktywnych doświadczenia przykładowe rozwiązanie krok po kroku za pomocą polecenia dotnet test i struktury MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 1765c16cb55857b83a8206ae97327d0fd2809019
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747495"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a>Testy jednostkowe F# bibliotek w programie .NET Core za pomocą polecenia dotnet test i struktury MSTest

Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych. Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) przed przystąpieniem do wykonywania. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

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

Wprowadź *MathService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new mstest -lang F#` ](../tools/dotnet-new.md). Spowoduje to utworzenie projektu testowego, który używa MSTest jako struktury testowej. Wygenerowany szablon konfiguruje narzędzie test runner w *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe. `dotnet new` w poprzednim kroku dodano MSTest i modułu uruchamiającego MSTest. Teraz Dodaj `MathService` biblioteki klas jako inny zależności do projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

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

`[<TestClass>]` Atrybut wskazuje klasę, która zawiera testy. `[<TestMethod>]` Atrybut oznacza metodę testową, która jest uruchamiany przez narzędzie test runner. Z *jednostki — testowanie z fsharp* katalogu, wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy. Moduł uruchamiający MSTest zawiera punkt wejścia programu, aby uruchomić testy. `dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.

Testy te dwa Pokaż najbardziej podstawowym, przekazywanie i niepowodzenie testów. `My test` przekazuje, i `Fail every time` zakończy się niepowodzeniem. Teraz Utwórz test `squaresOfOdds` metody. `squaresOfOdds` Metoda zwraca listę kwadratów wszystkie wartości nieparzystej liczby całkowitej, które są częścią sekwencji wejściowych. Zamiast próbowania zapisać wszystkie te funkcje na raz, iteracyjne można tworzyć testy, które sprawdzają poprawność funkcji. Dzięki czemu każdy przebieg sprowadza się do utworzenia niezbędnych funkcji dla metody testu.

Najprostsza testów, możemy napisać jest wywołanie `squaresOfOdds` z wszystkie liczby parzyste z zakresu, gdzie powinna zostać pustą sekwencją liczb całkowitych.  Oto tego testu:

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

Należy zauważyć, że `expected` sekwencji została przekonwertowana na listę. Biblioteka MSTest opiera się na różnych typach .NET standard. Czy zależności oznacza, że Twoje interfejsu publicznego i oczekiwane wyniki pomocy technicznej <xref:System.Collections.ICollection> zamiast <xref:System.Collections.IEnumerable>.

Po uruchomieniu testu, zobaczysz, że test zakończy się niepowodzeniem. Nie utworzono jeszcze wdrożenia. Należy ten test przez napisanie kodu najprostsza `Mathservice` klasę, która działa:

```csharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

W *jednostki — testowanie z fsharp* katalogu, uruchom `dotnet test` ponownie. `dotnet test` Polecenie uruchamia kompilację dla `MathService` projektu i następnie `MathService.Tests` projektu. Po utworzeniu obu projektów, działa ten jeden test. Przekazuje on.

## <a name="completing-the-requirements"></a>Korzystanie z wymaganiami

Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej. Dalej prostym przypadku współpracuje z sekwencji jest liczbą nieparzystą tylko `1`. Numer 1 jest łatwiejsze, ponieważ kwadrat 1 jest 1. Oto tego Następny test:

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

Wykonywanie `dotnet test` nie powiedzie się nowy test. Należy zaktualizować `squaresOfOdds` metody, aby obsłużyć ten nowy test. Należy filtrować wszystkie liczby parzyste poza kolejnością, aby ten przebieg testu. Możesz to zrobić przez pisanie funkcji filtru małe i przy użyciu `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

Zwróć uwagę, wywołanie `Seq.toList`. Który tworzy listę, która implementuje <xref:System.Collections.ICollection> interfejsu.

Istnieje jeszcze jeden krok do: każdej liczby nieparzyste kwadratowe. Rozpocznij od pisania nowego testu:

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

Test można naprawić przez przekazanie w potoku filtrowane sekwencji za pomocą operacji mapy do obliczenia kwadratowy poszczególnych nieparzysta:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

Gdy masz utworzoną małych biblioteki i zestaw testów jednostkowych dla tej biblioteki. Tak, aby dodawania nowych pakietów została ze strukturą rozwiązania i testów jest częścią normalnego przepływu pracy. Po skoncentrowany większość czasu i wysiłku niewiele rozwiązywania cele aplikacji.
