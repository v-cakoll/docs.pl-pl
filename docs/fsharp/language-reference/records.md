---
title: Rekordy (F#)
description: 'Dowiedz się, jak F # rekordów reprezentują proste agreguje nazwanych wartości, opcjonalnie z elementami członkowskimi.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1270bf4eaeba99a15b0f81b5477f4c3b98644f66
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="records"></a>Rekordy

Rejestruje reprezentują proste agreguje nazwanych wartości, opcjonalnie z elementami członkowskimi.  Począwszy od 4.1 F #, może to być typy struktur lub odwołanie.  Są one typy referencyjne domyślnie.

## <a name="syntax"></a>Składnia

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a>Uwagi
W poprzednich składni *typename* jest nazwa typu rekordu *label1* i *label2* nazwy wartości, nazywane są *etykiety*, i *type1* i *type2* typy tych wartości. *Lista elementów członkowskich* jest opcjonalna lista elementów członkowskich typu.  Można użyć `[<Struct>]` atrybutu, aby utworzyć rekord struktury, a nie rekordu, który jest typem referencyjnym.

Poniżej przedstawiono kilka przykładów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

W przypadku każdej etykiety w osobnym wierszu, średnik jest opcjonalna.

Można ustawić wartości w wyrażeniach znany jako *rekordów wyrażenia*. Kompilator wnioskuje typ z etykiety używane (Jeśli etykiety są wystarczająco różne inne typy rekordów). Nawiasy klamrowe ({}) należy ująć wyrażenia rekordu. Poniższy kod przedstawia wyrażenia rekordu, który inicjuje rekord z trzech elementów typu float z etykietami `x`, `y` i `z`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

Skrócona forma nie należy używać, jeśli może istnieć inny typ, który również ma takie same etykiety.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

Etykiety najbardziej ostatnio deklarowanego typu pierwszeństwo wcześniej zadeklarowanego typu tak w powyższym przykładzie `mypoint3D` jest wywnioskowany jako `Point3D`. Można jawnie określić typ rekordu, zgodnie z poniższym kodem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Metody mogą być definiowane dla typów rekordów, podobnie jak w przypadku typu klasy.

## <a name="creating-records-by-using-record-expressions"></a>Tworzenie rekordów przy użyciu wyrażenia rekordu
Rekordy można zainicjować za pomocą etykiet, które są zdefiniowane w rekordzie. To wyrażenie jest określany jako *rekordów wyrażenia*. Użyj nawiasów klamrowych ujmij wyrażenie rekordu i użyj średnika jako ogranicznik.

Poniższy przykład przedstawia sposób tworzenia rekordu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

Średnikami po ostatnim pola w wyrażeniu rekordu i w definicji typu są opcjonalne, niezależnie od tego, czy pola są wszystko w jednym wierszu.

Po utworzeniu rekordu, należy podać wartości dla każdego pola. Nie można odwołać się do wartości innych pól w wyrażeniu inicjowania dla dowolnego pola.

W poniższym kodzie typ `myRecord2` jest wywnioskowany na podstawie nazwy pól. Opcjonalnie można jawnie określić nazwę typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Innej formy konstrukcji rekordu może być przydatne podczas kopiowania istniejącego rekordu i prawdopodobnie zmieniania wartości pól. Następujący wiersz kodu ilustruje to.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Ta postać wyrażenia rekordu jest nazywany *kopiowanie i aktualizację wyrażenia rekordu*.

Rekordy są niezmienne domyślnie; można jednak łatwo utworzyć zmodyfikowanych rekordów przy użyciu wyrażenia Kopiuj i Aktualizuj. Można również jawnie określić pola modyfikowalnego.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

Nie używaj atrybutu DefaultValue z pola rekordu. Lepszym rozwiązaniem jest zdefiniuj wystąpień rekordy z pola, które są inicjowane wartości domyślne, a następnie użyj kopii i zaktualizuj wyrażenia rekordu, aby ustawić wszystkie pola, które różnią się od wartości domyślne.

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a>Dopasowywanie do wzorca z rekordów
Rekordy można łączyć z dopasowywania do wzorca. Można jawnie określić niektórych pól i podaj zmienne inne pola, które zostaną przypisane, jeśli pasują do. Pokazano to w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

Poniżej przedstawiono dane wyjściowe tego kodu.

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>Różnice między rekordów i klasy
Pola rekordu różnią się od klasy automatycznie są one widoczne jako właściwości, oraz są one używane do tworzenia i kopiowania rekordów. Konstrukcja rekordów również różni się od klasy konstrukcji. W polu Typ rekordu nie można definiować konstruktora. Zamiast tego stosuje składni konstrukcji opisanych w tym temacie. Klasy nie mają bezpośredniego relacji między parametrami konstruktora, pól i właściwości.

Jak typy Unii i struktury rekordów mają semantykę równości strukturalnej. Klasy mają odwołania semantykę równości. W poniższym przykładzie kodu pokazano to.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

Jeśli piszesz ten sam kod z klasy obiektów dwóch klas może być nierówne dwóch wartości będzie reprezentować dwóch obiektów na stercie i czy można porównywać tylko adresy (o ile nie zastępuje typu klasy `System.Object.Equals` metody).

Jeśli konieczne odwołanie równości dla rekordów, Dodaj atrybut `[<ReferenceEquality>]` powyżej rekordu.

## <a name="see-also"></a>Zobacz też
[Typy F#](fsharp-types.md)

[Klasy](classes.md)

[Dokumentacja języka F#](index.md)

[Równości odwołań](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[Dopasowanie do wzorca](pattern-matching.md)
