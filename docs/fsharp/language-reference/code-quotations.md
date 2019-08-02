---
title: Cytaty kodu
description: Dowiedz F# się więcej o cudzysłowach w kodzie, funkcji języka, która umożliwia programistyczne F# generowanie i Używanie wyrażeń kodu.
ms.date: 05/16/2016
ms.openlocfilehash: c6ec0078c685a6452f49edd289b01491dd62e3db
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630420"
---
# <a name="code-quotations"></a>Cytaty kodu

> [!NOTE]
> Link odwołania do interfejsu API spowoduje przejście do witryny MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

W tym temacie opisano *notowania kodu*, funkcję języka, która umożliwia programistyczne generowanie i używanie F# wyrażeń kodów. Ta funkcja umożliwia wygenerowanie drzewa składni abstrakcyjnej, które F# reprezentuje kod. Drzewo składni abstrakcyjnej można następnie przetworzyć i przetwarzać w zależności od potrzeb aplikacji. Można na przykład użyć drzewa do wygenerowania F# kodu lub wygenerowania kodu w innym języku.

## <a name="quoted-expressions"></a>Wyrażenia cytowane

*Wyrażenie cytowane* jest F# wyrażeniem w kodzie, które jest rozdzielane w taki sposób, że nie jest kompilowane jako część programu, ale zamiast tego jest kompilowane do obiektu, który reprezentuje F# wyrażenie. Wyrażenie ujęte w cudzysłów można oznaczyć na jeden z dwóch sposobów: z informacjami o typie lub bez informacji o typie. Jeśli chcesz dołączyć informacje o typie, Użyj symboli `<@` i `@>` , aby rozdzielić wyrażenie ujęte w cudzysłów. Jeśli nie potrzebujesz informacji o typie, Użyj symboli `<@@` i. `@@>` Poniższy kod przedstawia wpisane i niewpisywane cudzysłowy.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Przechodzenie przez duże drzewo wyrażeń jest szybsze, jeśli nie zostaną uwzględnione informacje o typie. Typ wyniku wyrażenia cytowanego za pomocą wpisanych symboli to `Expr<'T>`, gdzie parametr typu ma typ wyrażenia określony przez algorytm wnioskowania o typie F# kompilatora. W przypadku używania cudzysłowów kodu bez informacji o typie, typ wyrażenia w cudzysłowie jest wyrażeniem typu innego niż [](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65)ogólny. Można wywołać Właściwość [RAW](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) klasy z określonym `Expr` typem, aby uzyskać `Expr` obiekt bez typu.

Istnieją różne metody statyczne, które umożliwiają programowe generowanie F# obiektów wyrażeń w `Expr` klasie bez użycia wyrażeń ujętych w cudzysłów.

Należy zauważyć, że cytat kodu musi zawierać pełne wyrażenie. Na przykład dla powiązania, potrzebna jest zarówno definicja powiązanej nazwy, jak i dodatkowe wyrażenie, które używa powiązania. `let` W pełnej składni jest to wyrażenie zgodne ze `in` słowem kluczowym. Na najwyższego poziomu w module jest to tylko następne wyrażenie w module, ale w cudzysłowie jest to jawnie wymagane.

W związku z tym następujące wyrażenie jest nieprawidłowe.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Ale poniższe wyrażenia są prawidłowe.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Aby obliczyć F# oferty, należy użyć [ F# ewaluatora oferty](https://github.com/fsprojects/FSharp.Quotations.Evaluator). Zapewnia obsługę oceniania i wykonywania F# obiektów wyrażeń.

## <a name="expr-type"></a>Typ wyrażenia

Wystąpienie `Expr` typu reprezentuje F# wyrażenie. Typy ogólne i nieogólne `Expr` są udokumentowane w dokumentacji F# biblioteki. Aby uzyskać więcej informacji, zobacz [przestrzeń nazw Microsoft. FSharp. apostrofs](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) i [cudzysłów. Expr](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>Łączenie operatorów

Metoda łączenia umożliwia łączenie literałów kodu w znakach z wyrażeniami utworzonymi programowo lub z innej oferty kodu. Operatory `%` i `%%` umożliwiają dodawanie obiektu F# Expression do cytatu kodu. Możesz użyć `%` operatora, aby wstawić obiekt wyrażenia z wpisaną do wpisanej cudzysłowu. Użyj operatora `%%` , aby wstawić nieokreślony obiekt wyrażenia do cudzysłowu nietypu. Oba operatory są jednoargumentowymi operatorami prefiksu. W takim `expr` przypadku, jeśli jest wyrażeniem typu `Expr`untyped, poniższy kod jest prawidłowy.

```fsharp
<@@ 1 + %%expr @@>
```

A jeśli `expr` jest wpisanym cytatem typu `Expr<int>`, poniższy kod jest prawidłowy.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład ilustruje użycie cytatów kodu do umieszczenia F# kodu w obiekcie Expression, a następnie drukowanie F# kodu, który reprezentuje wyrażenie. Zdefiniowano `println` funkcję, która zawiera funkcję `print` cykliczną, która wyświetla F# obiekt wyrażenia (typu `Expr`) w przyjaznym formacie. Istnieje kilka aktywnych wzorców w modułach [Microsoft. FSharp. apostrofs. Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) i [Microsoft. FSharp. cytats. DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) , których można użyć do analizowania obiektów wyrażeń. Ten przykład nie obejmuje wszystkich możliwych wzorców, które mogą być wyświetlane w F# wyrażeniu. Każdy nierozpoznany wzorzec wyzwala dopasowanie do wzorca wieloznacznego`_`() i jest renderowany przy `ToString` użyciu metody `Expr` , która w typie, pozwala znać Aktywny wzorzec do dodania do wyrażenia dopasowania.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>Dane wyjściowe

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Można również użyć trzech aktywnych wzorców w [module ExprShape](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) do przechodzenia między drzewami wyrażeń i mniejszą liczbą aktywnych wzorców. Te aktywne wzorce mogą być przydatne, gdy chcesz przechodzenie przez drzewo, ale nie potrzebujesz wszystkich informacji w większości węzłów. W przypadku korzystania z tych wzorców każde F# wyrażenie pasuje do jednego z następujących trzech wzorców: `ShapeVar` Jeśli wyrażenie jest zmienną, `ShapeLambda` Jeśli wyrażenie jest wyrażeniem lambda lub `ShapeCombination` wyrażenie jest inne. Jeśli przejdziesz do drzewa wyrażenia przy użyciu aktywnych wzorców, jak w poprzednim przykładzie kodu, musisz użyć wielu innych wzorców do obsługi wszystkich możliwych F# typów wyrażeń, a kod będzie bardziej skomplikowany. Aby uzyskać więcej informacji, zobacz [ExprShape.&#124;ShapeVar&#124;ShapeLambda ShapeCombination — Active Pattern](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

Poniższy przykład kodu może służyć jako podstawa dla bardziej złożonych przechodzenia. W tym kodzie jest tworzone drzewo wyrażenia dla wyrażenia, które obejmuje wywołanie `add`funkcji. Aktywny wzorzec [SpecificCall —](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) jest używany do wykrywania dowolnego wywołania `add` w drzewie wyrażenia. Ten Aktywny wzorzec przypisuje argumenty wywołania do `exprList` wartości. W tym przypadku istnieją tylko dwa, więc są one ściągane i funkcja jest wywoływana cyklicznie na argumentach. Wyniki są wstawiane do cudzysłowu kodu, który reprezentuje wywołanie `mul` przy użyciu operatora splice (`%%`). `println` Funkcja z poprzedniego przykładu służy do wyświetlania wyników.

Kod w innych gałęziach aktywnego wzorca tylko generuje to samo drzewo wyrażenia, więc jedyną zmianą w wyrażeniu wynikiem jest zmiana z `add` na. `mul`

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Dane wyjściowe

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
