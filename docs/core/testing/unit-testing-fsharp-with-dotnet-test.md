---
title: "Testowanie biblioteki F # w .NET Core za pomocą testu dotnet i xUnit jednostki"
description: "Informacje pojęcia testów jednostkowych dla F # w .NET Core za pomocą interaktywna tworzenia przykładowe rozwiązanie krok po kroku przy użyciu platformy dotnet testu i xUnit."
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: article
dev_langs: fsharp
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 6a9596db49024bead9c33b52642f46f519bb2b4c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a>Testowanie biblioteki F # w .NET Core za pomocą testu dotnet i xUnit jednostki

Ten samouczek przedstawia interaktywna tworzenia przykładowe rozwiązanie krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli chcesz wykonać czynności opisane w samouczku za pomocą wbudowanych rozwiązania, [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp/) przed rozpoczęciem. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Umożliwia otwarcie okna powłoki. Utwórz katalog o nazwie *jednostki — testowanie z — języka fsharp* do przechowywania rozwiązania.
Wewnątrz tego nowego katalogu Uruchom [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania. Ułatwia to zarządzanie biblioteki klas i jednostkowy projekt testowy.
Utwórz katalog rozwiązania *MathService* katalogu. Struktura katalogów i plików dotychczasowych jest pokazany poniżej:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Wprowadź *MathService* bieżącego katalogu i uruchom [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) do tworzenia projektu źródłowego.  Aby użyć projektowanie oparte na testach (TDD), należy utworzyć niepowodzenie stosowania usługi matematyczne:

```fsharp
module MyMath =
    let sumOfSquares xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Zmień katalog z powrotem do *jednostki — testowanie z — języka fsharp* katalogu. Uruchom [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas do rozwiązania.

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

Wprowadź *MathService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md). Spowoduje to utworzenie projektu testowego używającą xUnit jako biblioteka testów. Wygenerowanego szablonu konfiguruje uruchamiający w *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testowy wymaga inne pakiety do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku należy dodać xUnit i xUnit modułu uruchamiającego testy. Teraz Dodaj `MathService` biblioteki klas jako zależność od innego projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```
dotnet add reference ../MathService/MathService.fsproj
```

Widoczny cały plik w [przykłady repozytorium](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) w witrynie GitHub.

Masz następujące układu ostatecznego rozwiązania:

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

Wykonanie [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) w *jednostki — testowanie z — języka fsharp* katalogu. 

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Podejście TDD odwołuje się do pisania niepowodzeniu jednego testu, co Przekaż, a następnie powtórzyć proces. Otwórz *Tests.fs* i Dodaj następujący kod:

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

`[<Fact>]` Atrybut oznacza metodę test jest uruchamiany przez moduł uruchamiający. Z *jednostki — testowanie z — języka fsharp*, wykonać [ `dotnet test` ](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchom testy. Moduł uruchamiający xUnit zawiera punkt wejścia programu do uruchomienia testów. `dotnet test`Uruchamia uruchamiający przy użyciu jednostkowy projekt testowy, który został utworzony.

Tych dwóch testów Pokaż najbardziej podstawową, przekazywanie i w przypadku braku testy. `My test`przekazuje, i `Fail every time` nie powiedzie się. Teraz, Utwórz test `sumOfSquares` metody. `sumOfSquares` Metoda zwraca sumę kwadratów wszystkie wartości nieparzystą liczbą całkowitą, które są częścią sekwencji wejściowych. Zamiast w trakcie zapisanie wszystkich tych funkcji na raz, można utworzyć wielokrotnie powtarzane testy sprawdzania poprawności funkcji. Wprowadzenie każdego z testów przekazać oznacza, że tworzenie funkcji niezbędne dla metody.

Jest najprostsza testu, firma Microsoft może zapisywać do wywołania `sumOfSquares` z wszystkie liczby parzyste, w którym wynik powinien być pustą sekwencją liczb całkowitych.  Oto tego testu:

```fsharp
[<Fact>]
let ``Sum of evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.sumOfSquares [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Należy ten test przez pisania kodu najprostsza w `MathService` klasy, która działa:

```csharp
let sumOfSquares xs =
    Seq.empty<int>
```

W *jednostki — testowanie z — języka fsharp* katalogu, uruchom `dotnet test` ponownie. `dotnet test` Polecenia uruchamiane kompilacji dla `MathService` projektu i następnie `MathService.Tests` projektu. Po utworzeniu oba projekty, jest uruchamiana ta pojedynczy test. Przekazuje ono.

## <a name="completing-the-requirements"></a>Korzystanie z wymaganiami

Teraz, kiedy dokonano jeden test przekazać nadszedł czas na zapis więcej. Następny prostym przypadku współpracuje z sekwencji, których tylko nieparzysta liczba jest `1`. Numer 1 jest łatwiejsze, ponieważ kwadrat 1 jest 1. Oto Następny test:

```fsharp
[<Fact>]
let ``Sum of sequences of Ones and Evens`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.sumOfSquares [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Wykonywanie `dotnet test` uruchomi testy i pokazuje, że nowy test zakończy się niepowodzeniem. Teraz zaktualizuj `sumOfSquares` można obsłużyć tego nowego testu. Można filtrować wszystkie liczby parzyste poza kolejnością, aby ten test przekazywania. Możesz to zrobić pisanie funkcji małych filtru i używając `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd
```

Istnieje jeden krok Przejdź: kwadratowe każdego nieparzyste numery. Rozpocznij od zapisywania nowego testu:

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.sumOfSquares [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

Test można rozwiązać przez przekazanie w potoku filtrowane sekwencji za pomocą operacji mapy do obliczenia wartości kwadratu każdą nieparzystą liczbę:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let sumOfSquares xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

Został utworzony małych biblioteki i zestaw testów jednostkowych dla tej biblioteki. Zostały strukturę rozwiązania, aby dodać nowe pakiety i testów jest częścią Normalny przepływ pracy. Już skoncentrowany większość czasu i uwagi na temat rozwiązywania problemów celów aplikacji.
