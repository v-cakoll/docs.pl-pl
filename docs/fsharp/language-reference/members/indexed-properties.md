---
title: "Właściwości indeksowane (F#)"
description: "Więcej informacji na temat F # indeksowane właściwości, które są właściwości, które zapewniają dostęp tablicy do danych uporządkowanych."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f1266b8b-e2e3-4f49-9332-65c6d34dc0f3
ms.openlocfilehash: 78a09a70621e82f073346471e68ec826359641d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="indexed-properties"></a>Właściwości indeksowane

*Właściwości indeksowanych* są uporządkowane właściwości, które zapewniają dostęp tablicy do danych.


## <a name="syntax"></a>Składnia

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.PropertyName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.PropertyName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.PropertyName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.PropertyName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a>Uwagi
Trzech rodzajów poprzedniej składni pokazują, jak zdefiniować właściwości indeksowanych, które mają zarówno `get` i `set` metody, ma `get` tylko metody lub ma `set` tylko metody. Można także połączyć oba składni pokazano tylko polecenie get i składni pokazano tylko zestawu i tworzy właściwość, która ma zarówno get i set. Ten ostatni formularz umożliwia zawiesić modyfikatory dostępności różnych i atrybuty get i ustaw metody.

Gdy *PropertyName* jest `Item`, kompilator traktuje właściwość jako domyślnie indeksowanej właściwości. A *Właściwość indeksowana domyślnie* jest właściwością, której będziesz mieć dostęp za pomocą składni tablicy w wystąpieniu obiektu. Na przykład jeśli `obj` jest obiektem typu, który definiuje tę właściwość, składnia `obj.[index]` służy do dostępu do właściwości.

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
