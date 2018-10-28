---
title: Właściwości indeksowane (F#)
description: Więcej informacji na temat właściwości indeksowanych w F#, które umożliwiają dostęp tablicy do danych uporządkowanych.
ms.date: 10/17/2018
ms.openlocfilehash: 3dac60eba3d9e7a9c3e76ad7ee051e6b30b88636
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452251"
---
# <a name="indexed-properties"></a>Właściwości indeksowane

Podczas definiowania klasy, która przenosi danych uporządkowanych, czasami może być przydatne do udostępnienia indeksowane dane bez narażania podstawowej implementacji. Jest to zrobić za pomocą `Index` elementu członkowskiego.

## <a name="syntax"></a>Składnia

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.Index
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property with get only
member self-identifier.Index
    with get(index-values) =
        get-member-body

// Indexed property that has set only.
member self-identifier.Index
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

## <a name="indexed-properties-with-multiple-index-variables"></a>Właściwości indeksowane, za pomocą wielu zmiennych indeksu

Właściwości indeksowane może mieć więcej niż jedną zmienną indeksu. W takim przypadku zmienne są oddzielone przecinkami, gdy jest używana. Metody set w takiej właściwości musi mieć dwa argumenty rozwinięte, pierwszy z nich jest krotkę zawierającą klucze, a drugi z nich jest wartość.

Poniższy przykład demonstruje użycie Właściwość indeksowana z wielu zmiennych indeksu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
