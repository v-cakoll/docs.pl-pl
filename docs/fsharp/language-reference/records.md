---
title: Rekordy
description: Dowiedz się, jak F# rekordów reprezentują prostych wartości zagregowanych nazwanych wartości opcjonalnie wraz z elementów członkowskich.
ms.date: 06/09/2019
ms.openlocfilehash: cfb8de8272b479571119ae4cf91ea1d6fd5db73c
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816192"
---
# <a name="records"></a>Rekordy

Rekordy reprezentują prostych wartości zagregowanych nazwanych wartości opcjonalnie wraz z elementów członkowskich. Mogą to być albo typu struktury lub odwołania.  Są one domyślnie typami odwołań.

## <a name="syntax"></a>Składnia

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *typename* jest nazwą typu rekordu *label1* i *etykiety 2* nazwy wartości, nazywane są *etykiety*, i *type1* i *type2* typy tych wartości. *Lista elementów członkowskich* jest opcjonalna lista elementów członkowskich typu.  Możesz użyć `[<Struct>]` atrybutu do utworzenia rekordu struktury, a nie rekord, który jest typem referencyjnym.

Poniżej przedstawiono kilka przykładów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

Po każdej etykiety w osobnym wierszu średnik jest opcjonalne.

Można ustawić wartości w wyrażeniach, znane jako *rejestrowania wyrażenia*. Kompilator wnioskuje typ z etykiet, używane (Jeśli etykiety wystarczająco różnią się od tych innych typów rekordów). Nawiasy klamrowe ({}) powinno być rekord. Poniższy kod pokazuje wyrażenie rekordów, które inicjuje rekord za pomocą trzech elementów float z etykietami `x`, `y` i `z`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

Nie należy używać formy skróconej, jeśli może być innym typem, który ma również tej samej etykiety.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

Etykiety najbardziej niedawno zadeklarowanym typem pierwszeństwo wcześniej zadeklarowanej typu, więc w powyższym przykładzie `mypoint3D` jest `Point3D`. Można jawnie określić typ rekordu, tak jak w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Metody mogą być definiowane dla typów rekordów, podobnie jak w przypadku typu klasy.

## <a name="creating-records-by-using-record-expressions"></a>Tworzenie rekordów za pomocą wyrażeń rekordów

Rekordy można zainicjować za pomocą etykiet, które są zdefiniowane w rekordzie. Wyrażenie, które ten jest nazywany *rejestrowania wyrażenie*. Powinno być rekord i użyj średnika jako ogranicznika, należy użyć nawiasów klamrowych.

Poniższy przykład pokazuje, jak utworzyć rekord.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

Średnikami po ostatnim polu w wyrażeniu rekordu i w definicji typu są opcjonalne, niezależnie od tego, czy pola są wszystko w jednym wierszu.

Podczas tworzenia rekordu należy podać wartości dla każdego pola. Nie można odwołać się do wartości innych pól w wyrażeniu inicjowania dla dowolnego pola.

W poniższym kodzie typ `myRecord2` wynika z nazwy pól. Opcjonalnie można jawnie określić nazwę typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Inna forma konstrukcji rekord może być przydatne, kiedy trzeba skopiować istniejący rekord, a być może zmienić niektóre wartości pól. Następujący wiersz kodu ilustruje to.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Ta forma wyrażenia rekordu jest nazywany *kopiowanie i aktualizacja wyrażeń rekordów*.

Rekordy, które są niezmienne domyślnie; jednak można łatwo utworzyć zmodyfikowanych rekordów przy użyciu wyrażenia Kopiuj i Aktualizuj. Można również jawnie określić mutable pola.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

Nie używaj atrybutu DefaultValue przy użyciu pól rekordu. Lepszym rozwiązaniem jest zdefiniowanie wystąpieniami domyślnymi rekordów z polami, które są inicjowane do wartości domyślnych, a następnie użyć kopii i zaktualizować rekord wyrażenia, aby ustawić wszystkie pola, które różnią się od wartości domyślne.

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="creating-mutually-recursive-records"></a>Tworzenie wzajemnie rekordów cykliczne

Później, podczas tworzenia rekordu, możesz go są zależne od innego typu, który chcesz zdefiniować później. Jest to błąd kompilacji, chyba że zdefiniujesz typów rekordów, które wzajemnie się jako cykliczne.

Definiowanie wzajemnie rekordów cyklicznego jest przeprowadzane za pomocą `and` — słowo kluczowe. Dzięki temu można połączyć ze sobą typy 2 lub więcej rekordów.

Na przykład, poniższy kod definiuje `Person` i `Address` typ jako wzajemnie cyklicznej:

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string }
```

Jeśli potrzeba zdefiniowania poprzedniego przykładu bez `and` — słowo kluczowe, a następnie ją będzie niemożliwa. `and` — Słowo kluczowe jest wymagany dla wzajemnie definicje cykliczne.

## <a name="pattern-matching-with-records"></a>Dopasowywanie wzorca z rekordów

Rekordy można łączyć z dopasowywania do wzorca. Można jawnie określić niektóre pola i podać zmienne dla innych pól, które zostaną przypisane po wystąpieniu dopasowania. Pokazano to w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

Dane wyjściowe tego kodu jest w następujący sposób.

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>Różnice między rekordami i klasy

Pola rekordu różnią się od klas są one automatycznie dostępne jako właściwości i są one używane do tworzenia i kopiowania rekordów. Konstrukcja rekordów również różni się od konstrukcji klasy. W polu Typ rekordu nie można zdefiniować Konstruktor. Zamiast tego składni konstrukcji opisane w tym temacie mają zastosowanie. Klasy nie mają bezpośredniego relacji między parametry konstruktora, pola i właściwości.

Podobnie jak typy Unii i struktury rekordy mają semantykę porównania strukturalnego. Klasy mają odniesienie równości semantyki. Poniższy przykład kodu pokazuje to.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

Dane wyjściowe tego kodu jest następująca:

```
The records are equal.
```

Jeśli piszesz ten sam kod z klasami, obiektów dwóch klas będzie nierówne, ponieważ dwie wartości reprezentuje dwa obiekty na stosie i będzie można porównać tylko adresy (o ile nie zastępuje typ klasy `System.Object.Equals` metody).

Jeśli potrzebujesz odwołać równości dla rekordów, Dodaj atrybut `[<ReferenceEquality>]` powyżej rekordu.

## <a name="see-also"></a>Zobacz także

- [Typy F#](fsharp-types.md)
- [Klasy](classes.md)
- [Dokumentacja języka F#](index.md)
- [Równość odniesienia](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [Dopasowanie do wzorca](pattern-matching.md)
