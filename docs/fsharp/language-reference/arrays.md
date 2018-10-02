---
title: Tablice (F#)
description: 'Dowiedz się, jak utworzyć i korzystanie z tablic w języku programowania F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 27b73efc900ac2efc813fe66f81baa2e9ae1e843
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032734"
---
# <a name="arrays"></a>Tablice

> [!NOTE]
Łącze odwołania API spowoduje przejście do MSDN.  Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.

Tablice są stałym rozmiarze, zaczynający się od zera, mutable kolekcjami kolejnych elementów danych, które są wszystkie tego samego typu.

## <a name="creating-arrays"></a>Tworzenie tablic

Tablice można tworzyć na kilka sposobów. Możesz utworzyć małą tablicę wymieniając kolejne wartości między `[|` i `|]` , oddzielone średnikami, jak pokazano w poniższych przykładach.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

Możesz również umieścić każdy element w osobnym wierszu, w którego przypadku Użycie średnika jako separatora jest opcjonalne.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

Typ elementów tablicy jest wnioskowany z używanych literałów i musi być zgodne. Poniższy kod powoduje błąd, ponieważ 1.0 to liczba zmiennoprzecinkowa, a 2 i 3 są liczbami całkowitymi.

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

Można również używać wyrażeń sekwencji, do tworzenia tablic. Poniżej przedstawiono przykład tworzenia tablica kwadratów liczb całkowitych z zakresu od 1 do 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

Aby utworzyć tablicę, w którym wszystkie elementy są ustawione na zero, użyj `Array.zeroCreate`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a>Dostęp do elementów

Dostęp do elementów tablicy przy użyciu operatora kropka (`.`) i nawiasy (`[` i `]`).

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

Indeksy tablicy rozpoczynają się od 0.

Można także przejść elementów tablicy przy użyciu zapisu wycinkowego, który umożliwia określanie podzakresu tablicy. Przykłady zapisu wycinkowego.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

Stosowania zapisu wycinkowego tworzona jest nowa kopia tablicy.

## <a name="array-types-and-modules"></a>Typy tablic i moduły

Typ wszystkich tablic F # to typ .NET Framework <xref:System.Array?displayProperty=nameWithType>. W związku z tym, tablice F # obsługują wszystkie funkcje dostępne w <xref:System.Array?displayProperty=nameWithType>.

Moduł biblioteki [ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) obsługuje operacje na tablicach jednowymiarowych. Moduły `Array2D`, `Array3D`, i `Array4D` zawierają funkcje obsługujące operacje w tablicach o dwóch, trzech i czterech wymiarach, odpowiednio. Można utworzyć tablice o randze większej niż cztery za pomocą <xref:System.Array?displayProperty=nameWithType>.

### <a name="simple-functions"></a>Proste funkcje

[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) pobiera element. [`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) podaje długość tablicy. [`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) Ustawia element na określoną wartość. Poniższy przykład kodu ilustruje użycie tych funkcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

Dane wyjściowe są następujące:

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>Funkcje, które tworzą tablice

Kilka funkcji tworzy tablice bez konieczności istniejącej tablicy. [`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) Tworzy nową tablicę, która nie zawiera żadnych elementów. [`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) tworzy tablicę o określonym rozmiarze i ustawia wszystkie elementy do podanych wartości. [`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) tworzy tablicę, biorąc pod uwagę wymiar i funkcję do generowania elementów. [`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) tworzy tablicę, w którym wszystkie elementy są inicjowane na wartość zero dla typu tablicy. Poniższy kod demonstruje te funkcje.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

Dane wyjściowe są następujące:

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) Tworzy nową tablicę, która zawiera elementy, które są kopiowane z istniejącej tablicy. Zwróć uwagę, że kopią pobieżną, co oznacza, że jeśli typ elementu to typ odwołania, kopiowane jest tylko odwołanie, nie obiekt podstawowy. Pokazano to w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

Dane wyjściowe dla poprzedniego kodu jest następująca:

```
[|Test1; Test2; |]
[|; Test2; |]
```

Ciąg `Test1` pojawia się tylko w pierwszej tablicy, ponieważ operacja tworzenia nowego elementu zastępuje odniesienie w `firstArray` , ale nie wpływa na pierwotne odniesienie do pustego ciągu, który jest nadal obecny w `secondArray`. Ciąg `Test2` pojawia się w obu tablicach, ponieważ `Insert` operacja <xref:System.Text.StringBuilder?displayProperty=nameWithType> typu, który wpływa na podlegający <xref:System.Text.StringBuilder?displayProperty=nameWithType> obiektu, który odwołuje się w obu tablicach.

[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generuje nową tablicę z podzakresu tablicy. Określasz Podzakres podając indeks początkowy i długość. Poniższy przykład demonstruje użycie `Array.sub`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

Dane wyjściowe pokazują, że podtablica rozpoczyna się na elemencie 5 i zawiera 10 elementów.

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) Tworzy nową tablicę przez połączenie dwóch istniejących tablic.

Poniższy przykład demonstruje **Array.append**.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

Dane wyjściowe dla poprzedniego kodu wyglądają następująco.

```
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) wybiera elementy tablicy do uwzględnienia w nowej tablicy. Poniższy przykład demonstruje `Array.choose`. Pamiętaj, że typ elementu tablicy nie musi odpowiadać typowi wartości zwracanej w typie opcji. W tym przykładzie typ elementu to typ `int` i opcja jest wynikiem funkcji wielomianowej `elem*elem - 1`, jako zmiennoprzecinkowy numer punktu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

Dane wyjściowe dla poprzedniego kodu wyglądają następująco.

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) Uruchamia określoną funkcję na każdym elemencie istniejącej tablicy, a następnie zbiera elementy wygenerowane przez tę funkcję i łączy je do nowej tablicy. Poniższy przykład demonstruje `Array.collect`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

Dane wyjściowe dla poprzedniego kodu wyglądają następująco.

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) wykonuje sekwencję tablic i łączy je w jedną. Poniższy przykład demonstruje `Array.concat`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

Dane wyjściowe dla poprzedniego kodu wyglądają następująco.

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) przyjmuje funkcję logiczną warunku i generuje nową tablicę, która zawiera tylko elementy z tablicy wejściowej, dla których warunek jest prawdziwy. Poniższy przykład demonstruje `Array.filter`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

Dane wyjściowe dla poprzedniego kodu wyglądają następująco.

```
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generuje nową tablicę przez odwrócenie kolejności istniejącej tablicy. Poniższy przykład demonstruje `Array.rev`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

Dane wyjściowe dla poprzedniego kodu wyglądają następująco.

```
"Hello world!"
```

Łatwo można połączyć funkcje w module tablicy, które przetwarzają tablice za pomocą operatora potoku (`|>`), jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

Dane wyjściowe są

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>Tablice wielowymiarowe

Można utworzyć tablicy wielowymiarowej, ale nie ma składni do pisania tablicy wielowymiarowej literału. Użyj operatora [ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) Aby utworzyć tablicę z sekwencji sekwencji elementów tablicy. Sekwencje mogą być literałami tablicy lub listy. Na przykład poniższy kod tworzy dwuwymiarową tablicę.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

Można również użyć funkcji [ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) zainicjować tablice dwuwymiarowe i podobne funkcje są dostępne dla tablic trójwymiarowych i czterowymiarowych. Te funkcje biorą funkcję, która jest używana do tworzenia elementów. Aby utworzyć dwuwymiarową tablicę zawierająca elementy ustawione na wartość początkową zamiast określania funkcji, użyj [ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) funkcji, która jest również dostępna dla tablic maksymalnie czterech wymiarów. Poniższy przykład kodu po pierwsze ukazuje sposób tworzenia tablicy tablic, które zawierają żądane elementy, a następnie używa `Array2D.init` do wygenerowania pożądanej tablicy dwuwymiarowej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

Tablica indeksowania i składnia wycinków jest obsługiwana dla tablic do rangi 4. Po określeniu indeksu w wielu wymiarach, używasz przecinków do oddzielenia indeksów, jak pokazano w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]

Rodzaj tablicy dwuwymiarowej jest zapisywany jako `<type>[,]` (na przykład `int[,]`, `double[,]`), a rodzaj tablicy trójwymiarowej jest zapisywany jako `<type>[,,]`, i tak dalej dla tablic wyższych wymiarów.

Tylko podzbiór funkcji dostępnych dla tablic jednowymiarowych jest również dostępny dla tablic wielowymiarowych. Aby uzyskać więcej informacji, zobacz [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), i [ `Collections.Array4D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).

### <a name="array-slicing-and-multidimensional-arrays"></a>Tablica wycinków i tablice wielowymiarowe

W dwuwymiarowej tablicy (macierzy), można wyodrębnić podrzędną macierzy, określając zakresy i użycie symbolu wieloznacznego (`*`) znak do określenia całych wierszy lub kolumn.

```fsharp
/ Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

Jak dla F # 3.1 można rozkładać tablicę wielowymiarową na podtablice tego samego lub niższego wymiaru. Na przykład można uzyskać wektor z macierzy, określając pojedynczy wiersz lub kolumnę.

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

Możesz użyć tej składni wycinków dla typów, które implementuje operatory dostępu do elementu i przeciążone `GetSlice` metody. Na przykład, poniższy kod tworzy typ macierzy, który otacza tablicę 2D języka F #, implementuje właściwość element zapewniającą wsparcia dla indeksowania tablic i implementuje trzy wersje obiektu `GetSlice`. Jeśli tego kodu można użyć jako szablonu dla typów macierzy użytkownika, można użyć wszystkich operacji tworzenia wycinków, które w tej sekcji opisano.

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

Funkcje [ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) i [ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) testują elementy w jednej lub dwóch tablicach, odpowiednio. Te funkcje biorą funkcję testu i zwracają `true` w przypadku elementu (lub para elementów dla `Array.exists2`) który spełnia warunek.

Poniższy przykład demonstruje użycie `Array.exists` i `Array.exists2`. W tych przykładach nowe funkcje są tworzone poprzez stosowanie tylko jednego z argumentów, w tych przypadkach argumentu funkcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

Dane wyjściowe dla poprzedniego kodu wyglądają następująco.

```
true
false
false
true
```

Podobnie, funkcja [ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) testuje tablicę, aby ustalić, czy każdy element spełnia warunek logiczny. Zmiana [ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) działa tak samo za pomocą funkcji logicznej, która obejmuje elementy dwóch tablic o równej długości. Poniższy kod ilustruje sposób korzystania z tych funkcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

Dane wyjściowe dla tych przykładów wyglądają następująco.

```
false
true
true
false
```

### <a name="searching-arrays"></a>Przeszukiwanie tablic

[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) przyjmuje wartość logiczną funkcji i zwraca pierwszy element, dla którego funkcja zwraca `true`, lub podwyższa <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> Jeśli zostanie znaleziony żaden element, który spełnia warunek. [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) przypomina `Array.find`, chyba że zwraca ona indeks elementu, a nie samego elementu.

Poniższy kod używa `Array.find` i `Array.findIndex` aby zlokalizować numer, który jest idealnym kwadratem i idealnym sześcianem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

Dane wyjściowe są następujące:

```
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) przypomina `Array.find`, z tą różnicą, że jej wynik jest typem opcji i zwraca `None` Jeśli zostanie znaleziony żaden element. `Array.tryFind` należy użyć zamiast `Array.find` kiedy nie wiesz, czy jest pasujący element znajduje się w tablicy. Podobnie [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) przypomina [ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) z tą różnicą, że typ opcji jest wartością zwracaną. Jeśli zostanie znaleziony żaden element, ta opcja jest `None`.

Poniższy przykład demonstruje użycie `Array.tryFind`. Ten kod zależy od poprzedniego kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

Dane wyjściowe są następujące:

```
Found an element: 1
Found an element: 729
```

Użyj [ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) konieczność możliwość przekształcenia elementu tylko go znaleźć. Wynik jest pierwszym elementem, dla którego funkcja zwraca przekształcony element jako wartość opcji lub `None` jeśli taki element nie zostanie znaleziony.

Poniższy kod przedstawia użycie `Array.tryPick`. W tym przypadku zamiast wyrażenia lambda kilka lokalnych funkcji pomocniczych są definiowane w celu uproszczenia kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

Dane wyjściowe są następujące:

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a>Wykonywanie obliczeń na tablicach

[ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) Funkcja zwraca średnią dla każdego elementu w tablicy. Jest ograniczony do typów elementów, które obsługują dzielenie bez reszty przez liczbę całkowitą, która obejmuje typy zmiennoprzecinkowe, ale nie typy całkowitoliczbowe. [ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) Funkcja zwraca średnią z wyników wywołania funkcji dla każdego elementu. W przypadku tablicy typu całkowitego, można użyć `Array.averageBy` i funkcja konwertowała każdy element zmiennoprzecinkowej typu do obliczeń punktu.

Użyj [ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) lub [ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) można pobrać element maksymalny lub minimalny, jeśli typ elementu obsługuje tę funkcję. Podobnie [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) i [ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) Zezwalaj na funkcję do wykonania, najpierw, być może do przekształcenia do typu, który obsługuje porównania.

[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) Dodaje elementy tablicy, a [ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) wywołuje funkcję dla każdego elementu i dodaje wyniki razem.

Aby wykonać funkcję dla każdego elementu w tablicy bez przechowywania wartości zwracane, użyj [ `Array.iter` ](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516). Dla funkcji używającej dwóch tablic o równej długości użyj [ `Array.iter2` ](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc). Jeśli potrzebujesz również zachować tablicę wyników funkcji, użyj [ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) lub [ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), która działa na dwóch tablicach jednocześnie.

Odchylenia [ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) i [ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) Zezwalaj na indeks elementu do uczestniczenia w obliczeń; dotyczy to także [ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) i [ `Array.mapi2` ](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).

Funkcje [ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [ `Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), i [ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) wykonują algorytmy, które obejmują wszystkie elementy tablicy. Podobnie, odmiany [ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) i [ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) wykonują obliczenia na dwóch tablicach.

Te funkcje do wykonywania obliczeń odpowiadają funkcjom o tej samej nazwie w [lista modułów](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Aby uzyskać przykłady użycia, zobacz [Wyświetla](lists.md).

### <a name="modifying-arrays"></a>Modyfikowanie tablic

[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) Ustawia element na określoną wartość. [`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) Ustawia zakres elementów w tablicy na określoną wartość. Poniższy kod stanowi przykład `Array.fill`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

Dane wyjściowe są następujące:

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

Możesz użyć [ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) można skopiować podsekcję jednej tablicy do innej tablicy.

### <a name="converting-to-and-from-other-types"></a>Konwertowanie do i z innych typów

[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) tworzy tablicę z listy. [`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) tworzy tablicę z sekwencji. [`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) i [ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) Konwertuj na inne typy kolekcji z typu tablicy.

### <a name="sorting-arrays"></a>Sortowanie tablic

Użyj [ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) Aby posortować tablicę za pomocą funkcji porównania rodzajowego. Użyj [ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) Aby określić funkcję, która generuje wartość, nazywane *klucz*, aby sortować przy użyciu funkcji porównywania w kluczu. Użyj [ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) Jeśli chcesz zapewnić niestandardową funkcję porównywania. `Array.sort`, `Array.sortBy`, i `Array.sortWith` zwracają posortowaną tablicę jako nową tablicę. Odchylenia [ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), i [ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modyfikują istniejącą tablicę zamiast zwracać nową.

### <a name="arrays-and-tuples"></a>Tablice i krotki

Funkcje [ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) i [ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) konwertują tablice par krotek na krotki tablic i na odwrót. [`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) i [ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) są podobne, z tą różnicą, że pracują z krotek trzech elementów lub krotek trzech tablic.

## <a name="parallel-computations-on-arrays"></a>Obliczenia równoległe na tablicach

Moduł [ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) zawiera funkcje do wykonywania obliczeń równoległych na tablicach. Ten moduł nie jest dostępny w aplikacjach przeznaczonych dla wersji programu .NET Framework wcześniejszych niż wersja 4.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [F #; Typy](fsharp-types.md)
