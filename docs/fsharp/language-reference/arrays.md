---
title: Tablice
description: Dowiedz się, jak tworzyć tablice i używać F# ich w języku programowania.
ms.date: 05/16/2016
ms.openlocfilehash: 8470e01087e417635bcd5c528df9b9e089cbf59f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320490"
---
# <a name="arrays"></a>Tablice

> [!NOTE]
> Link odwołania do interfejsu API spowoduje przejście do witryny MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

Tablice są stałymi, niemodyfikowalnymi kolekcjami kolejnych elementów danych, które są tego samego typu.

## <a name="creating-arrays"></a>Tworzenie tablic

Tablice można tworzyć na kilka sposobów. Możesz utworzyć małą tablicę, wymieniając kolejne wartości między `[|` i `|]` i rozdzielone średnikami, jak pokazano w poniższych przykładach.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

Można również umieścić każdy element w osobnym wierszu, w którym przypadku separator średników jest opcjonalny.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

Typ elementów tablicy jest wywnioskowany na podstawie używanych literałów i musi być spójny. Poniższy kod powoduje błąd, ponieważ 1,0 jest zmiennoprzecinkowa i 2 i 3 są liczbami całkowitymi.

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

Można również użyć wyrażeń sekwencji do tworzenia tablic. Poniżej znajduje się przykład, który tworzy tablicę kwadratów liczb całkowitych z zakresu od 1 do 10.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

Aby utworzyć tablicę, w której wszystkie elementy są zainicjowane do zera, użyj `Array.zeroCreate`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a>Uzyskiwanie dostępu do elementów

Możesz uzyskać dostęp do elementów tablicy przy użyciu operatora kropki (`.`) i nawiasów kwadratowych (`[` i `]`).

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

Indeksy tablicy zaczynają się od 0.

Możesz również uzyskać dostęp do elementów tablicy przy użyciu notacji wycinka, która umożliwia określenie podzakresu tablicy. Przykłady zapisu wycinka są następujące.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

Gdy jest używana notacja wycinka, tworzona jest nowa kopia tablicy.

## <a name="array-types-and-modules"></a>Typy tablic i moduły

Typ wszystkich F# tablic jest typu .NET Framework <xref:System.Array?displayProperty=nameWithType>. W związku F# z tym tablice obsługują wszystkie funkcje dostępne w <xref:System.Array?displayProperty=nameWithType>.

Moduł biblioteki [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) obsługuje operacje w tablicach jednowymiarowych. Moduły `Array2D`, `Array3D` i `Array4D` zawierają funkcje, które obsługują operacje na tablicach odpowiednio dwa, trzy i cztery wymiary. Można utworzyć tablice rangi większe niż cztery przy użyciu <xref:System.Array?displayProperty=nameWithType>.

### <a name="simple-functions"></a>Proste funkcje

[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) Pobiera element. [`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) podaje długość tablicy. [`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) ustawia element na określoną wartość. Poniższy przykład kodu ilustruje sposób korzystania z tych funkcji.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

Dane wyjściowe są następujące:

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>Funkcje tworzące tablice

Kilka funkcji tworzy tablice bez konieczności stosowania istniejącej tablicy. [`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) tworzy nową tablicę, która nie zawiera żadnych elementów. [`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) tworzy tablicę o określonym rozmiarze i ustawia wszystkie elementy na dostarczone wartości. [`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) tworzy tablicę, uwzględniając wymiar i funkcję do wygenerowania elementów. [`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) tworzy tablicę, w której wszystkie elementy są inicjowane do wartości zero dla typu tablicy. Poniższy kod ilustruje te funkcje.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

Dane wyjściowe są następujące:

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) tworzy nową tablicę zawierającą elementy, które są kopiowane z istniejącej tablicy. Należy pamiętać, że kopia jest kopią skróconą, co oznacza, że jeśli typem elementu jest typ referencyjny, kopiowane jest tylko odwołanie, a nie obiekt źródłowy. Pokazano to w poniższym przykładzie kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

Dane wyjściowe powyższego kodu są następujące:

```console
[|Test1; Test2; |]
[|; Test2; |]
```

Ciąg `Test1` pojawia się tylko w pierwszej tablicy, ponieważ operacja tworzenia nowego elementu zastępuje odwołanie w `firstArray`, ale nie wpływa na oryginalne odwołanie do pustego ciągu, który nadal występuje w `secondArray`. Ciąg `Test2` pojawia się w obu tablicach, ponieważ operacja `Insert` w typie <xref:System.Text.StringBuilder?displayProperty=nameWithType> ma wpływ na bazowy obiekt <xref:System.Text.StringBuilder?displayProperty=nameWithType>, do którego odwołuje się obie tablice.

[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generuje nową tablicę z podzakresu tablicy. Należy określić Podzakres, podając początkowy indeks i długość. Poniższy kod ilustruje użycie `Array.sub`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

Dane wyjściowe pokazują, że podtablica zaczyna się od elementu 5 i zawiera 10 elementów.

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) tworzy nową tablicę przez połączenie dwóch istniejących tablic.

Poniższy kod ilustruje **tablicę Array. Append**.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

Dane wyjściowe powyższego kodu są następujące.

```console
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) wybiera elementy tablicy do uwzględnienia w nowej tablicy. Poniższy kod ilustruje `Array.choose`. Należy zauważyć, że typ elementu tablicy nie musi być zgodny z typem wartości zwracanej w typie opcji. W tym przykładzie typem elementu jest `int`, a opcja jest wynikiem funkcji wielomianu, `elem*elem - 1`, jako liczby zmiennoprzecinkowej.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

Dane wyjściowe powyższego kodu są następujące.

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) uruchamia określoną funkcję dla każdego elementu tablicy istniejącej tablicy, a następnie zbiera elementy wygenerowane przez funkcję i łączy je w nową tablicę. Poniższy kod ilustruje `Array.collect`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

Dane wyjściowe powyższego kodu są następujące.

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) przyjmuje sekwencję tablic i łączy je w jedną tablicę. Poniższy kod ilustruje `Array.concat`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

Dane wyjściowe powyższego kodu są następujące.

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) przyjmuje funkcję warunku logicznego i generuje nową tablicę zawierającą tylko te elementy z tablicy wejściowej, dla których warunek ma wartość true. Poniższy kod ilustruje `Array.filter`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

Dane wyjściowe powyższego kodu są następujące.

```console
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generuje nową tablicę przez odwrócenie kolejności istniejącej tablicy. Poniższy kod ilustruje `Array.rev`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

Dane wyjściowe powyższego kodu są następujące.

```console
"Hello world!"
```

Można łatwo łączyć funkcje w module Array, które przekształcają tablice za pomocą operatora potoku (`|>`), jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

Dane wyjściowe to

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>Tablice wielowymiarowe

Można utworzyć tablicę wielowymiarową, ale nie ma składni do pisania wielowymiarowego literału tablicy. Użyj operatora [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) , aby utworzyć tablicę z sekwencji sekwencji elementów tablicy. Sekwencje mogą być literałami tablicowymi lub listami. Na przykład poniższy kod tworzy tablicę dwuwymiarową.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

Można również użyć funkcji [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) do zainicjowania tablic dwóch wymiarów, a podobne funkcje są dostępne dla tablic składających się z trzech i czterech wymiarów. Funkcje te przyjmują funkcję, która jest używana do tworzenia elementów. Aby utworzyć dwuwymiarową tablicę, która zawiera elementy ustawione na wartość początkową zamiast określania funkcji, użyj funkcji [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) , która jest również dostępna dla tablic do czterech wymiarów. Poniższy przykład kodu najpierw pokazuje, jak utworzyć tablicę tablic zawierających żądane elementy, a następnie użyć `Array2D.init` do wygenerowania odpowiedniej tablicy dwuwymiarowej.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

Składnia indeksowania tablicy i skalowanie wycinków jest obsługiwana w przypadku tablic o wartości do rangi 4. Po określeniu indeksu w wielu wymiarach, należy użyć przecinków do oddzielenia indeksów, jak pokazano w poniższym przykładzie kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

Typ tablicy dwuwymiarowej jest zapisywana jako `<type>[,]` (na przykład `int[,]`, `double[,]`), a typ trójwymiarowej tablicy jest zapisywana jako `<type>[,,]` i tak dalej dla tablic o wyższym wymiarze.

Tylko podzestaw funkcji dostępnych dla tablic jednowymiarowych jest również dostępny dla tablic wielowymiarowych. Aby uzyskać więcej informacji, zobacz [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d)i [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).

### <a name="array-slicing-and-multidimensional-arrays"></a>Dzielenie tablic i tablice wielowymiarowe

W tablicy dwuwymiarowej (macierzy) można wyodrębnić tablicę podrzędną, określając zakresy i używając symbolu wieloznacznego (`*`) do określenia całych wierszy lub kolumn.

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

Od F# 3,1 można rozłożyć tablicę wielowymiarową na podtablice tego samego lub niższego wymiaru. Na przykład można uzyskać wektor z macierzy, określając pojedynczy wiersz lub kolumnę.

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

Można użyć tej składni wycinków dla typów implementujących operatory dostępu do elementów i przeciążonych metod `GetSlice`. Na przykład poniższy kod tworzy typ macierzy, która otacza tablicę F# 2D, implementuje właściwość elementu w celu zapewnienia obsługi indeksowania tablicy i implementuje trzy wersje `GetSlice`. Jeśli możesz użyć tego kodu jako szablonu dla typów macierzy, możesz użyć wszystkich operacji tworzenia wycinków, które opisano w tej sekcji.

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a>Funkcje logiczne w tablicach

Funkcje [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) i [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) elementy testowe odpowiednio w jednej lub dwóch tablicach. Te funkcje przyjmują funkcję testową i zwracają `true`, jeśli istnieje element (lub para elementów dla `Array.exists2`), który spełnia warunek.

Poniższy kod ilustruje użycie `Array.exists` i `Array.exists2`. W tych przykładach nowe funkcje są tworzone przez zastosowanie tylko jednego z argumentów, w takich przypadkach, argumentu funkcji.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

Dane wyjściowe powyższego kodu są następujące.

```console
true
false
false
true
```

Podobnie funkcja [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) testuje tablicę, aby określić, czy każdy element spełnia warunek logiczny. Odmiana [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) wykonuje tę samą czynność przy użyciu funkcji logicznej, która obejmuje elementy dwóch tablic o równej długości. Poniższy kod ilustruje sposób korzystania z tych funkcji.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

Dane wyjściowe dla tych przykładów są następujące.

```console
false
true
true
false
```

### <a name="searching-arrays"></a>Wyszukiwanie tablic

[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) przyjmuje funkcję logiczną i zwraca pierwszy element, dla którego funkcja zwraca `true`, lub wywołuje <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType>, jeśli nie zostanie znaleziony żaden element spełniający warunek. [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) przypomina `Array.find`, z tą różnicą, że zwraca indeks elementu zamiast samego elementu.

Poniższy kod używa `Array.find` i `Array.findIndex` do lokalizowania liczby, która jest idealnym kwadratem i idealnym modułem.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

Dane wyjściowe są następujące:

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) przypomina `Array.find`, z tą różnicą, że jego wynik jest typem opcji i zwraca `None`, jeśli nie znaleziono elementu. Jeśli nie wiesz, czy pasujący element znajduje się w tablicy, należy używać `Array.tryFind` zamiast `Array.find`. Podobnie [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) jest podobne do [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) , z wyjątkiem tego, że typ opcji jest wartością zwracaną. Jeśli nie zostanie znaleziony żaden element, opcja jest `None`.

Poniższy kod ilustruje użycie `Array.tryFind`. Ten kod zależy od poprzedniego kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

Dane wyjściowe są następujące:

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

Użyj [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) , gdy musisz przekształcić element, a także go znaleźć. Wynikiem jest pierwszy element, dla którego funkcja zwraca przekształcony element jako wartość opcji lub `None`, jeśli taki element nie zostanie znaleziony.

Poniższy kod ilustruje użycie `Array.tryPick`. W tym przypadku zamiast wyrażenia lambda, kilka lokalnych funkcji pomocniczych jest zdefiniowanych do uproszczenia kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

Dane wyjściowe są następujące:

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="performing-computations-on-arrays"></a>Wykonywanie obliczeń w tablicach

Funkcja [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) zwraca średnią każdego elementu w tablicy. Jest ono ograniczone do typów elementów, które obsługują dokładne dzielenie przez liczbę całkowitą, która obejmuje typy zmiennoprzecinkowe, ale nie typy całkowite. Funkcja [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) zwraca średnią wyników wywołania funkcji dla każdego elementu. Dla tablicy typu całkowitego można użyć `Array.averageBy` i mieć funkcję Konwertuj każdy element na typ zmiennoprzecinkowy dla obliczenia.

Użyj [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) lub [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) , aby uzyskać element maksymalny lub minimalny, jeśli typ elementu obsługuje tę funkcję. Podobnie, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) i [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) umożliwiają pierwsze wykonanie funkcji, na przykład w celu przekształcenia do typu, który obsługuje porównanie.

[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) dodaje elementy tablicy, a [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) wywołuje funkcję na każdym elemencie i dodaje wyniki razem.

Aby wykonać funkcję dla każdego elementu w tablicy bez przechowywania wartości zwracanych, użyj [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516). Dla funkcji obejmującej dwie tablice o równej długości Użyj [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc). Jeśli trzeba również zachować tablicę wyników funkcji, użyj [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) lub [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), które działają na dwóch tablicach jednocześnie.

Różnice [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) i [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) umożliwiają indeks elementu, który ma być uwzględniony w obliczeniach; Ta sama wartość dotyczy [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) i [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).

Funkcje [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0)i [1](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) wykonywania algorytmów, które obejmują wszystkie elementy tablicy. Podobnie różnice [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) i [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) wykonują obliczenia na dwóch tablicach.

Te funkcje do wykonywania obliczeń odpowiadają funkcjom o tej samej nazwie w [module list](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Aby zapoznać się z przykładami użycia, zobacz [listy](lists.md).

### <a name="modifying-arrays"></a>Modyfikowanie tablic

[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) ustawia element na określoną wartość. [`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) ustawia zakres elementów w tablicy do określonej wartości. Poniższy kod zawiera przykład `Array.fill`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

Dane wyjściowe są następujące:

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

Można użyć [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) , aby skopiować podsekcję jednej tablicy do innej tablicy.

### <a name="converting-to-and-from-other-types"></a>Konwertowanie na i z innych typów

[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) tworzy tablicę z listy. [`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) tworzy tablicę z sekwencji. [`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) i [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) konwertują na te inne typy kolekcji z typu tablicy.

### <a name="sorting-arrays"></a>Sortowanie tablic

Użyj [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) , aby posortować tablicę przy użyciu funkcji porównywania generycznego. Użyj [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) , aby określić funkcję generującą wartość, która jest określana jako *klucz*, aby sortować przy użyciu funkcji porównywania generycznego w kluczu. Użyj [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) , jeśli chcesz podać niestandardową funkcję porównania. `Array.sort`, `Array.sortBy` i `Array.sortWith` wszystkie zwracają posortowaną tablicę jako nową tablicę. Wariacje [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f)i [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modyfikują istniejącą tablicę zamiast zwracać nowe.

### <a name="arrays-and-tuples"></a>Tablice i krotki

Funkcje [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) i [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) konwertują tablice par krotek na krotki tablic i na odwrót. [`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) i [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) są podobne, z tą różnicą, że pracują z krotkami trzech elementów lub krotekmi trzech tablic.

## <a name="parallel-computations-on-arrays"></a>Obliczenia równoległe w tablicach

Moduł [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) zawiera funkcje do wykonywania obliczeń równoległych w tablicach. Ten moduł nie jest dostępny w aplikacjach przeznaczonych dla wersji .NET Framework wcześniejszych niż wersja 4.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Typy F#](fsharp-types.md)
