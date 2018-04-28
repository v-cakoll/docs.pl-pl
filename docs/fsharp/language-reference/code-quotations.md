---
title: Cytaty kodu (F#)
description: 'Dowiedz się więcej o F # cytaty kodu, funkcja języka, która umożliwia generowanie i pracować z wyrażenia kodu języka F # programowo.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: cfa2e4b9a4ad1776315dfa8ea82fb8fc3f13a552
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="code-quotations"></a>Cytaty kodu

> [!NOTE]
Łącze odwołania API spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

W tym temacie opisano *kodu ofert*, funkcja języka, która umożliwia generowanie i pracować z wyrażenia kodu języka F # programowo. Ta funkcja umożliwia wygenerowanie drzewa składni abstrakcyjnej, który reprezentuje kodzie języka F #. Następnie można przechodzić drzewa składni abstrakcyjnej i przetwarzane odpowiednio do potrzeb aplikacji. Na przykład można użyć drzewa, aby wygenerować kod w języku F # lub wygenerować kod w inny język.


## <a name="quoted-expressions"></a>Wyrażenia ujętego w cudzysłów
A *podane wyrażenie* wyrażenie F # w kodzie rozdzielana w taki sposób, że nie jest on skompilowany w ramach programu, ale zamiast tego jest kompilowany do obiektu, który reprezentuje wyrażenie F #. Można oznaczyć wyrażenia ujętego w cudzysłów w jeden z dwóch sposobów: informacji o typach lub bez informacji o typie. Jeśli chcesz uwzględnić informacje o typie, użyj symboli `<@` i `@>` ograniczającej wyrażenia ujętego w cudzysłów. Jeśli informacje o typie nie jest wymagane, użyj symboli `<@@` i `@@>`. Poniższy kod przedstawia ofert maszynowy i bez typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Przeglądanie drzewa wyrażenia dużych jest szybsze, jeśli nie ma informacji o typie. Wynikowy typ wyrażenia z symbolami typu w cudzysłowach jest `Expr<'T>`, gdzie parametr typu ma typ wyrażenia zgodnie z ustaleniami algorytm wnioskowania typu kompilator języka F #. Gdy używasz cytaty kodu bez informacji o typie typ wyrażenia ujętego w cudzysłów jest typu nieogólnego [wyrażenie](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Możesz wywołać [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) właściwość wpisanego `Expr` klasy w celu uzyskania bez typu `Expr` obiektu.

Istnieją różne metody statyczne, które umożliwiają generowanie F # obiektów wyrażeń programowo w `Expr` klasy bez użycia wyrażeń w cudzysłowach.

Należy pamiętać, że oferty kodu musi zawierać pełne wyrażenie. Aby uzyskać `let` powiązanie, na przykład należy definicji powiązania nazwy i dodatkowe wyrażenie używające powiązania. W Pełna składnia jest to wyrażenie, które wykonuje `in` — słowo kluczowe. Na najwyższym poziomie w module to po prostu następnego wyrażenia w module, ale w cudzysłowie, jest wyraźnie wymagane.

W związku z tym następujące wyrażenie jest nieprawidłowe.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Ale następujące wyrażenia są prawidłowe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Aby użyć cytaty kodu, należy dodać deklaracja importu (przy użyciu `open` — słowo kluczowe) który otwiera [Microsoft.fsharp.quotations —](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) przestrzeni nazw.

PowerPack F # obsługuje ocenianie i wykonywania obiektów wyrażeń F #.


## <a name="expr-type"></a>Wyrażenie typu
Wystąpienie `Expr` typu reprezentuje wyrażenie F #. Rodzajowa i nieogólnego `Expr` typy są opisane w dokumentacji biblioteki F #. Aby uzyskać więcej informacji, zobacz [Namespace Microsoft.fsharp.quotations —](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) i [quotations.Expr — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).


## <a name="splicing-operators"></a>Operatory łączenia
Łączenia umożliwia łączenie cytaty kodu literału z wyrażeń, które zostały utworzone programowo lub z innego kodu oferty. `%` i `%%` operatory umożliwiają dodanie obiektu będącego wyrażeniem F # w cudzysłowie kodu. Możesz użyć `%` operatora, aby wstawić obiektu typu wyrażenia do typu oferty; możesz użyć `%%` operatora, aby wstawić obiekt bez typu wyrażenia do oferty bez typu. Oba operatory są operatory jednoargumentowe prefiks. W związku z tym jeśli `expr` jest bez typu wyrażenia typu `Expr`, następujący kod jest nieprawidłowy.

```fsharp
<@@ 1 + %%expr @@>
```

A jeśli `expr` jest typu oferty typu `Expr<int>`, następujący kod jest nieprawidłowy.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis
Poniższy przykład przedstawia użycie cytaty kodu, aby umieścić kodzie języka F # w wyrażeniu obiektu, a następnie wydrukuj kodzie języka F #, który reprezentuje wyrażenie. Funkcja `println` zdefiniowano zawierający funkcję rekursywną `print` wyświetlający obiekt expression F # (typu `Expr`) w formacie przyjazne. Istnieje kilka aktywne wzorce w [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) i [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) modułów, które mogą służyć do analizowania obiektów wyrażeń. W tym przykładzie nie obejmuje wszystkich możliwych wzorców, które mogą być wyświetlane w wyrażeniu F #. Wszelkie Nierozpoznany wzorzec wyzwala dopasowania wzorca symbolu wieloznacznego (`_`) i jest renderowany przy użyciu `ToString` — metoda, która na `Expr` wpisz informuje Cię o aktywny wzorzec do dodania do wyrażenie dopasowania.


### <a name="code"></a>Kod
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]
    
### <a name="output"></a>Dane wyjściowe

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis
Można również użyć trzy wzorce aktywne w [exprshape — moduł](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) przechodzenia drzewa wyrażeń z mniej aktywne wzorce. Te wzorce aktywne mogą być przydatne, gdy chcesz przenoszenie drzewa, ale nie są wszystkie informacje w większości węzłów. Korzystając z tych wzorców, dowolne wyrażenie F # pasuje do jednej z następujących trzech wzorców: `ShapeVar` Jeśli wyrażenie jest zmienną, `ShapeLambda` Jeśli wyrażenie jest wyrażenia lambda lub `ShapeCombination` Jeśli wyrażenie jest inny. Jeśli przy użyciu aktywne wzorce co w poprzednim przykładzie kodu przechodzą przez drzewo wyrażenia, należy użyć wielu wzorców więcej do obsługi wszystkich możliwych typów wyrażenie F #, a Twój kod będzie bardziej złożonych. Aby uzyskać więcej informacji, zobacz [ExprShape.ShapeVar&#124;shapelambda —&#124;shapecombination — aktywny wzorzec](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

Poniższy przykład kodu może służyć jako podstawa dla traversals bardziej złożonych. W tym kodzie drzewo wyrażeń jest tworzona dla wyrażenie, które polega na wywołanie funkcji `add`. [Specificcall —](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) — aktywny wzorzec jest używana do wykrywania każde wywołanie `add` drzewa wyrażenia. Argumenty wywołania przypisuje tego — aktywny wzorzec `exprList` wartość. W takim przypadku istnieją tylko dwa, dzięki czemu są one pobierane i funkcja jest wywoływana rekursywnie na argumenty. Wyniki są wstawiane do oferty kodu, który reprezentuje wywołanie `mul` za pomocą operatora łączenia (`%%`). `println` Funkcji z poprzedniego przykładu służy do wyświetlania wyników.

Kod w innych działów — aktywny wzorzec generuje tylko tym samym drzewie wyrażenie, tak tylko zmianę wynikowe wyrażenie jest zmiana z `add` do `mul`.


### <a name="code"></a>Kod
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]
    
### <a name="output"></a>Dane wyjściowe

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

