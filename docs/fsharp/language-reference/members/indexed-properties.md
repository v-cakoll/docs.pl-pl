---
title: Właściwości indeksowane
description: Dowiedz się więcej na F#temat właściwości indeksowanych w programie, które umożliwiają dostęp do danych uporządkowanych w postaci zbliżonej do tablic.
ms.date: 11/04/2019
ms.openlocfilehash: f6cf3bfa737d2bf458e379594be5884696cee3e1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976609"
---
# <a name="indexed-properties"></a>Właściwości indeksowane

Podczas definiowania klasy, która jest abstrakcyjna względem uporządkowanych danych, może być czasem przydatna do zapewnienia indeksowanego dostępu do tych danych bez uwidaczniania podstawowej implementacji. Jest to realizowane z `Item` członkiem.

## <a name="syntax"></a>Składnia

```fsharp
// Indexed property that can be read and written to
member self-identifier.Item
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property can only be read
member self-identifier.Item
    with get(index-values) =
        get-member-body

// Indexed property that can only be set
member self-identifier.Item
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a>Uwagi

Formy poprzedniej składni pokazują, jak definiować indeksowane właściwości, które mają zarówno `get`, jak i `set`, mają tylko metodę `get` lub mają tylko metodę `set`. Można również połączyć składnię pokazaną tylko do pobrania i składnię wyświetlaną tylko dla zestawu i utworzyć właściwość, która ma oba metody get i Set. Ten ostatni formularz umożliwia umieszczenie różnych modyfikatorów dostępności i atrybutów w metodach get i Set.

Przy użyciu nazwy `Item`, kompilator traktuje właściwość jako domyślną właściwość indeksowaną. *Domyślną indeksowaną właściwością* jest właściwość, do której można uzyskać dostęp za pomocą składni podobnej do tablic w wystąpieniu obiektu. Na przykład jeśli `o` jest obiektem typu, który definiuje tę właściwość, `o.[index]` składnia jest używana w celu uzyskania dostępu do właściwości.

Składnia służąca do uzyskiwania dostępu do właściwości indeksowanej innej niż domyślna to podanie nazwy właściwości i indeksu w nawiasach, podobnie jak zwykłego elementu członkowskiego. Na przykład jeśli właściwość na `o` jest nazywana `Ordinal`, należy napisać `o.Ordinal(index)`, aby uzyskać do niej dostęp.

Niezależnie od tego, który formularz jest używany, należy zawsze używać formularza rozwinięte dla metody Set dla właściwości indeksowanej. Aby uzyskać informacje o funkcjach rozwinięte, zobacz [Functions](../functions/index.md).

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje definicję i użycie domyślnych i niedomyślnych właściwości indeksowanych, które mają metody get i Set.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Dane wyjściowe

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>Właściwości indeksowane z wieloma wartościami indeksu

Indeksowane właściwości mogą mieć więcej niż jedną wartość indeksu. W takim przypadku wartości są oddzielane przecinkami, gdy właściwość jest używana. Metoda Set w takiej właściwości musi mieć dwa argumenty rozwinięte, z których pierwszy jest krotką zawierającą klucze, a druga wartość do ustawienia.

Poniższy kod ilustruje użycie właściwości indeksowanej z wieloma wartościami indeksu.

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member _.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
