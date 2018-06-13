---
title: Właściwości indeksowane (F#)
description: 'Więcej informacji na temat F # indeksowane właściwości, które są właściwości, które zapewniają dostęp tablicy do danych uporządkowanych.'
ms.date: 05/16/2016
ms.openlocfilehash: 503cef9693cfe5e13d4e2d19a721d65bff1ce749
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235944"
---
# <a name="indexed-properties"></a>Właściwości indeksowane

*Właściwości indeksowanych* są uporządkowane właściwości, które zapewniają dostęp tablicy do danych. Pochodzą w trzech formularzach:

* `Item`
* `Ordinal`
* `Cardinal`

Element członkowski F # musi mieć nazwę jednej z tych trzech nazw zapewnienie dostępu do tablicy. `IndexerName` jest używana do reprezentowania żadnego z trzech poniższych opcji:


## <a name="syntax"></a>Składnia

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.IndexerName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.IndexerName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.IndexerName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.IndexerName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a>Uwagi
Formularze poprzedniej składni pokazują, jak zdefiniować właściwości indeksowanych, które mają zarówno `get` i `set` metody, ma `get` metody tylko, lub ma `set` tylko metody. Można także połączyć oba składni pokazano tylko polecenie get i składni pokazano tylko zestawu i tworzy właściwość, która ma zarówno get i set. Ten ostatni formularz umożliwia zawiesić modyfikatory dostępności różnych i atrybuty get i ustaw metody.

Gdy *IndexerName* jest `Item`, kompilator traktuje właściwość jako domyślnie indeksowanej właściwości. A *Właściwość indeksowana domyślnie* jest właściwością, której będziesz mieć dostęp za pomocą składni tablicy w wystąpieniu obiektu. Na przykład jeśli `obj` jest obiektem typu, który definiuje tę właściwość, składnia `obj.[index]` służy do dostępu do właściwości.

Składnia do uzyskiwania dostępu do właściwości indeksowanych niestandardowy jest zapewnienie nazwy właściwości oraz indeksu w nawiasach. Na przykład, jeśli właściwość jest `Ordinal`, możesz zapisać `obj.Ordinal(index)` do niego dostęp.

Niezależnie od tego formularza, którego używasz, zawsze należy używać rozwinięte forma `set` metody dla właściwości indeksowanej. Aby uzyskać informacje o funkcje rozwinięte, zobacz [funkcji](../functions/index.md).

## <a name="example"></a>Przykład

Poniższy przykładowy kod przedstawia definicja oraz wykorzystanie domyślnych i właściwości indeksowanych innych niż domyślne, które i ustaw metody get.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Dane wyjściowe

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a>Właściwości indeksowane wiele zmiennych indeksu
Właściwości indeksowane może mieć więcej niż jedną zmienną indeksu. W takim przypadku zmienne są oddzielone przecinkami, gdy jest używana. W takich właściwości metody zestaw musi mieć dwa argumenty curried, z których pierwszy jest spójnych kolekcji zawierający klucze, a drugi z nich jest wartość.

Poniższy kod przedstawia użycie właściwości indeksowanych wiele zmiennych indeksu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a>Zobacz też
[Elementy członkowskie](index.md)
