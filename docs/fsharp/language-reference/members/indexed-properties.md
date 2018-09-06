---
title: Właściwości indeksowane (F#)
description: 'Więcej informacji na temat F # indeksowane właściwości, które są właściwościami, które zapewnia dostęp tablicy do danych uporządkowanych.'
ms.date: 05/16/2016
ms.openlocfilehash: e56e4e2ea3f35df4c8ec46012357242cb6ce69f3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749598"
---
# <a name="indexed-properties"></a>Właściwości indeksowane

*Właściwości indeksowanych* są uporządkowane właściwości, które zapewniają dostęp tablicy do danych. Pochodzą one w trzech formach:

* `Item`
* `Ordinal`
* `Cardinal`

Element członkowski F #, musi nosić jedna z tych trzech nazw, aby zapewnić dostęp tablicy. `IndexerName` jest używana do reprezentowania dowolne trzy poniższe opcje:

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

Formy składnia poprzednich pokazują, jak zdefiniować właściwości indeksowanych mających zarówno `get` i `set` metody mają `get` tylko metody lub `set` tylko metody. Można także połączyć oba te składni przedstawionej tylko polecenie get i składni przedstawionej tylko zestaw i generuje właściwości, która ma zarówno get i set. Ten formularz, ostatnie pozwala umieścić modyfikatory dostępności różnych i atrybuty w get i ustawianie metody.

Gdy *IndexerName* jest `Item`, kompilator traktuje właściwości jako domyślnie indeksowanej właściwości. A *Właściwość indeksowana domyślnie* jest właściwością, która może uzyskać dostęp za pomocą składni tablicy na wystąpienie obiektu. Na przykład jeśli `obj` jest obiektem typu, który definiuje tę właściwość, składnia `obj.[index]` umożliwia dostęp do właściwości.

Składnia służąca do uzyskiwania dostępu do właściwości indeksowanych inną niż domyślna jest podać nazwę właściwości i indeksu w nawiasach. Na przykład, jeśli właściwość jest `Ordinal`, piszesz `obj.Ordinal(index)` do niego dostęp.

Niezależnie od tego formularza, którego używasz, należy zawsze używać rozwinięte formularz `set` metody właściwości indeksowanej. Aby uzyskać informacje na temat funkcji rozwinięte zobacz [funkcji](../functions/index.md).

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje definicja oraz wykorzystanie domyślnej i właściwości indeksowanych innych niż domyślne, które get i ustawianie metody.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Dane wyjściowe

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a>Właściwości indeksowane, za pomocą wielu zmiennych indeksu

Właściwości indeksowane może mieć więcej niż jedną zmienną indeksu. W takim przypadku zmienne są oddzielone przecinkami, gdy jest używana. Metody set w takiej właściwości musi mieć dwa argumenty rozwinięte, pierwszy z nich jest krotkę zawierającą klucze, a drugi z nich jest wartość.

Poniższy przykład demonstruje użycie Właściwość indeksowana z wielu zmiennych indeksu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
