---
title: Właściwości indeksowane
description: Więcej informacji na temat właściwości indeksowanych w F#, które umożliwiają dostęp tablicy do danych uporządkowanych.
ms.date: 10/17/2018
ms.openlocfilehash: 7fc8f46e029255c6ed985a43b92c8f7c2908c428
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489490"
---
# <a name="indexed-properties"></a>Właściwości indeksowane

Podczas definiowania klasy, która przenosi danych uporządkowanych, czasami może być przydatne do udostępnienia indeksowane dane bez narażania podstawowej implementacji. Jest to zrobić za pomocą `Item` elementu członkowskiego.

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

Formy składnia poprzednich pokazują, jak zdefiniować właściwości indeksowanych mających zarówno `get` i `set` metody mają `get` tylko metody lub `set` tylko metody. Można także połączyć oba te składni przedstawionej tylko polecenie get i składni przedstawionej tylko zestaw i generuje właściwości, która ma zarówno get i set. Ten formularz, ostatnie pozwala umieścić modyfikatory dostępności różnych i atrybuty w get i ustawianie metody.

Przy użyciu nazwy `Item`, kompilator traktuje właściwości jako domyślnie indeksowanej właściwości. A *Właściwość indeksowana domyślnie* jest właściwością, która może uzyskać dostęp za pomocą składni tablicy na wystąpienie obiektu. Na przykład jeśli `o` jest obiektem typu, który definiuje tę właściwość, składnia `o.[index]` umożliwia dostęp do właściwości.

Składnia służąca do uzyskiwania dostępu do właściwości indeksowanych innych niż domyślne jest do podania nazwy właściwości i indeksu w nawiasach, podobnie jak regularny członek. Na przykład jeśli właściwość `o` nosi nazwę `Ordinal`, piszesz `o.Ordinal(index)` do niego dostęp.

Niezależnie od tego formularza, którego używasz należy zawsze używać rozwinięte formularza metody set dla właściwości indeksowanych. Aby uzyskać informacje na temat funkcji rozwinięte zobacz [funkcji](../functions/index.md).

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje definicja oraz wykorzystanie domyślnej i właściwości indeksowanych innych niż domyślne, które get i ustawianie metody.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Dane wyjściowe

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>Właściwości indeksowane, za pomocą wielu wartości indeksu

Właściwości indeksowane może mieć więcej niż jedną wartość indeksu. W takim przypadku wartości są oddzielone przecinkami, gdy jest używana. Metody set w takiej właściwości musi mieć dwa argumenty rozwinięte, pierwszy z nich jest krotkę zawierającą klucze, a drugi z nich jest wartość do ustawienia.

Poniższy przykład demonstruje użycie właściwości indeksowanej z wieloma wartościami indeksu.

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
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
