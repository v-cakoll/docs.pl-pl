---
title: Cytaty kodu
description: Dowiedz się więcej o F# cytaty kodu, funkcji języka, który umożliwia generowanie i pracować z F# programowo kodu wyrażenia.
ms.date: 05/16/2016
ms.openlocfilehash: 30fd5b575fa59d78c3e70c1a94cd921a6a655ace
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402126"
---
# <a name="code-quotations"></a>Cytaty kodu

> [!NOTE]
> Łącze odwołania API spowoduje przejście do MSDN.  Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.

W tym temacie opisano *kodu ofert*, funkcji języka, który umożliwia generowanie i pracować z F# programowo kodu wyrażenia. Ta funkcja umożliwia generowanie drzewo abstrakcyjnej składni, która reprezentuje F# kodu. Drzewo abstrakcyjnej składni można następnie przesunięta i przetwarzane odpowiednio do potrzeb aplikacji. Na przykład, można użyć drzewa do generowania F# kod lub wygenerować kod w inny język.

## <a name="quoted-expressions"></a>Wyrażenia w cudzysłowach

A *wyrażenia w cudzysłowach* jest F# wyrażenia w kodzie, które są rozdzielane w taki sposób, że nie jest kompilowana jako część programu, ale zamiast tego jest skompilowany w obiekt, który reprezentuje F# wyrażenia. Można oznaczać cudzysłowach wyrażeń w jeden z dwóch sposobów: za pomocą informacji o typie lub bez informacji o typie. Jeśli chcesz uwzględnić informacje o typie, użyj symboli `<@` i `@>` ograniczającej wyrażenie w cudzysłowie. Jeśli nie potrzebujesz informacji o typie, użyj symboli `<@@` i `@@>`. Poniższy kod przedstawia ofert typizowane i nietypizowane.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Przechodzenie drzewa wyrażenie dużych jest szybsze, ponieważ nie zawiera informacji o typie. Wynikowy typ wyrażenia z symbolami wpisane w cudzysłowach jest `Expr<'T>`, gdzie parametr typu ma typ wyrażenia zgodnie z ustaleniami F# algorytm wnioskowanie o typie kompilatora. Gdy używasz cytaty kodu bez informacji o typie, typ wyrażenia w cudzysłowach jest typu nieogólnego [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Możesz wywołać [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) właściwość wpisanego `Expr` klasy w celu uzyskania danych `Expr` obiektu.

Istnieją różne metody statyczne, które umożliwiają generowanie F# wyrażenia obiektów programowo w `Expr` klasy bez użycia wyrażenia w cudzysłowach.

Należy pamiętać, że oferty kod musi zawierać pełne wyrażenie. Aby uzyskać `let` powiązania, na przykład potrzebujesz definicji powiązanej nazwy i wyrażenie dodatkowe, które używa powiązania. Pełne składnię, to wyrażenie, który następuje po `in` — słowo kluczowe. Na najwyższym poziomie w module to po prostu następnego wyrażenia w module, ale w ofercie, jest wyraźnie wymagane.

W związku z tym poniższe wyrażenie jest nieprawidłowe.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Ale następujących wyrażeń są prawidłowe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Aby ocenić F# ofert, należy użyć [ F# ewaluatora oferty](https://github.com/fsprojects/FSharp.Quotations.Evaluator). Udostępnia obsługę oceniania i wykonywania F# obiektów wyrażeń.

## <a name="expr-type"></a>Wyrażenie typu

Wystąpienie `Expr` wpisz reprezentuje F# wyrażenia. Zarówno ogólnego ogólnych i nieogólnych `Expr` typy są udokumentowane w artykule F# dokumentacji biblioteki. Aby uzyskać więcej informacji, zobacz [Namespace Microsoft.fsharp.quotations —](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) i [quotations.Expr — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>Łączenie operatorów

Łączenie umożliwia łączenie cytaty kodu literału z wyrażeniami, które zostały utworzone programowo, albo z innej oferty kodu. `%` i `%%` operatory umożliwiają dodawanie F# obiektu będącego wyrażeniem w cudzysłowie kodu. Możesz użyć `%` operatora, aby wstawić obiektu wpisane wyrażenie do typizowanych oferty; użyj `%%` operatora, aby wstawić obiektu niewpisanych wyrażeń do bez typu oferty. Oba operatory są operatorami przedrostkowymi jednoargumentowy. Dlatego jeśli `expr` jest bez typu wyrażenia typu `Expr`, poniższy kod jest nieprawidłowy.

```fsharp
<@@ 1 + %%expr @@>
```

Jeśli `expr` jest wpisane oferty typu `Expr<int>`, poniższy kod jest nieprawidłowy.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład ilustruje użycie cytaty kodu, aby umieścić F# kodu do obiektu będącego wyrażeniem, a następnie wydrukuj F# kod, który reprezentuje wyrażenie. Funkcja `println` zdefiniowano zawierający funkcji recursive `print` wyświetlającą F# obiektu będącego wyrażeniem (typu `Expr`) w formacie przyjazna. Istnieje kilka wzorców, które znajdują się w [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) i [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) modułów, które mogą służyć do analizowania obiekty wyrażeń. W tym przykładzie nie obejmują wszystkich możliwych wzorców, które mogą być wyświetlane w F# wyrażenia. Dowolny Nierozpoznany wzorzec wyzwala dopasowania do wzorca symbolu wieloznacznego (`_`) i jest renderowany przy użyciu `ToString` metody, która na `Expr` wpisz informuje Cię do dodania do w wyrażeniu dopasowania — aktywny wzorzec.

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

Można również użyć trzy wzorce aktywne w [exprshape — moduł](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) przechodzenie drzewa wyrażeń przy użyciu mniejszej liczby wzorców. Te wzorce aktywne może być przydatne, gdy chcesz przenoszenie drzewa, ale nie są wszystkie informacje w większości węzłów. Kiedy używać tych wzorców wszystkie F# wyrażenie pasuje do jednej z następujących trzech wzorców: `ShapeVar` Jeśli wyrażenie jest zmienną, `ShapeLambda` Jeśli wyrażenie jest wyrażeniem lambda lub `ShapeCombination` Jeśli wyrażenie jest inny. Jeśli przy użyciu wzorców, tak jak w poprzednim przykładzie kodu przechodzić przez drzewo wyrażenia, będzie konieczne użycie wielu więcej wzorców w celu obsługi wszystkich możliwych F# typy wyrażenia, a Twój kod będzie bardziej złożone. Aby uzyskać więcej informacji, zobacz [ExprShape.ShapeVar&#124;shapelambda —&#124;shapecombination — aktywny wzorzec](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

Poniższy przykład kodu może służyć jako podstawa dla bardziej złożonych przejścia. W tym kodzie drzewa wyrażenie jest tworzony dla wyrażenie, które polega na wywołanie funkcji `add`. [Specificcall —](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) — aktywny wzorzec jest używany do wykrywania wszelkich wywołanie `add` drzewa wyrażeń. To — aktywny wzorzec przypisuje argumenty wywołanie `exprList` wartość. W tym przypadku istnieją tylko dwa, więc te są pobierane w i funkcja jest wywoływana cyklicznie w argumenty. Wyniki są wstawiane do oferty kod, który reprezentuje wywołanie `mul` za pomocą operatora splice (`%%`). `println` Funkcja z poprzedniego przykładu jest używana do wyświetlania wyników.

Kod w inne gałęzie — aktywny wzorzec po prostu ponownie generuje tym samym drzewie wyrażeń, więc tylko zmiana wyrażenie wynikowe zmiany z `add` do `mul`.

### <a name="code"></a>Kod

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Dane wyjściowe

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
