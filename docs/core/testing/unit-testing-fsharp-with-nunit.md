---
title: 'Testowanie jednostek biblioteki F # w .NET Core za pomocą polecenia dotnet test i NUnit'
description: 'Pojęcia dotyczące jednostki test dla języka F # w .NET Core za pomocą interaktywnych doświadczenia przykładowe rozwiązanie krok po kroku za pomocą polecenia dotnet test i NUnit.'
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: adadfc0358814f4600255aac7076f9ba6fbb4feb
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308432"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>Testowanie jednostek biblioteki F # w .NET Core za pomocą polecenia dotnet test i NUnit

Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych. Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) przed przystąpieniem do wykonywania. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne 
- [.NET core SDK 2.1 (v. 2.1.400)](https://www.microsoft.com/net/download) lub nowszy. 
- Edytor tekstu lub ulubionego edytora kodu.

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwieranie okna powłoki. Utwórz katalog o nazwie *jednostki — testowanie z fsharp* do przechowywania rozwiązania.
Wewnątrz tego nowy katalog uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:

```console
dotnet new sln
```

Następnie należy utworzyć *MathService* katalogu. Następujące konspektu przedstawia strukturę katalogów i plików do tej pory:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Wprowadź *MathService* bieżącego katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:

```console
dotnet new classlib -lang F#
```

Aby użyć Programowanie oparte na testach (TDD), należy utworzyć niepowodzenie stosowania usługi matematyczne:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Zmień katalog kopii do *jednostki — testowanie z fsharp* katalogu. Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:

```console
dotnet sln add .\MathService\MathService.fsproj
```

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

Wprowadź *MathService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt, używając następującego polecenia:

```console
dotnet new nunit -lang F#
```

Spowoduje to utworzenie projektu testowego, który używa NUnit jako struktury testowej. Wygenerowany szablon konfiguruje narzędzie test runner w *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe. `dotnet new` w poprzednim kroku należy dodać kartę testu NUnit i NUnit. Teraz Dodaj `MathService` biblioteki klas jako inny zależności do projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```console
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
        MathService.Tests.fsproj
```

Wykonaj następujące polecenie w *jednostki — testowanie z fsharp* katalogu:

```console
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Podejścia TDD wymaga zapisywania niepowodzenie jednego testu, dzięki czemu przekazać, a następnie powtórzyć ten proces. Otwórz *UnitTest1.fs* i Dodaj następujący kod:

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

`[<TestFixture>]` Atrybut wskazuje klasę, która zawiera testy. `[<Test>]` Atrybut oznacza metodę testową, która jest uruchamiany przez narzędzie test runner. Z *jednostki — testowanie z fsharp* katalogu, wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy. Moduł uruchamiający NUnit zawiera punkt wejścia programu, aby uruchomić testy. `dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.

Testy te dwa Pokaż najbardziej podstawowym, przekazywanie i niepowodzenie testów. `My test` przekazuje, i `Fail every time` zakończy się niepowodzeniem. Teraz Utwórz test `squaresOfOdds` metody. `squaresOfOdds` Metoda zwraca sekwencję kwadratów wszystkie wartości nieparzystej liczby całkowitej, które są częścią sekwencji wejściowych. Zamiast próbowania zapisać wszystkie te funkcje na raz, iteracyjne można tworzyć testy, które sprawdzają poprawność funkcji. Dzięki czemu każdy przebieg sprowadza się do utworzenia niezbędnych funkcji dla metody testu.

Najprostsza testów, możemy napisać jest wywołanie `squaresOfOdds` z wszystkie liczby parzyste z zakresu, gdzie powinna zostać pustą sekwencją liczb całkowitych.  Oto tego testu:

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Należy zauważyć, że `expected` sekwencji została przekonwertowana na listę. NUnit framework opiera się na różnych typach .NET standard. Czy zależności oznacza, że Twoje interfejsu publicznego i oczekiwane wyniki pomocy technicznej <xref:System.Collections.ICollection> zamiast <xref:System.Collections.IEnumerable>.

Po uruchomieniu testu, zobaczysz, że test zakończy się niepowodzeniem. Nie utworzono jeszcze wdrożenia. Wprowadź ten test, przekazać przez napisanie kodu najprostsza *Library.fs* klasy w projekcie MathService, który działa:

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

W *jednostki — testowanie z fsharp* katalogu, uruchom `dotnet test` ponownie. `dotnet test` Polecenie uruchamia kompilację dla `MathService` projektu i następnie `MathService.Tests` projektu. Po utworzeniu obu projektów, jest uruchamiane testy. Teraz kod przechodzi dwa testy.

## <a name="completing-the-requirements"></a>Korzystanie z wymaganiami

Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej. Dalej prostym przypadku współpracuje z sekwencji jest liczbą nieparzystą tylko `1`. Numer 1 jest łatwiejsze, ponieważ kwadrat 1 jest 1. Oto tego Następny test:

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Wykonywanie `dotnet test` nie powiedzie się nowy test. Należy zaktualizować `squaresOfOdds` metody, aby obsłużyć ten nowy test. Należy filtrować wszystkie liczby parzyste poza kolejnością, aby ten przebieg testu. Możesz to zrobić przez pisanie funkcji filtru małe i przy użyciu `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Zwróć uwagę, wywołanie `Seq.toList`. Który tworzy listę, która implementuje <xref:System.Collections.ICollection> interfejsu.

Istnieje jeszcze jeden krok do: każdej liczby nieparzyste kwadratowe. Rozpocznij od pisania nowego testu:

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
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
