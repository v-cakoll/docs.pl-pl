---
title: Const, instrukcja
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 1411e019058e7aac8249b7a50ecd295885a74177
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354128"
---
# <a name="const-statement-visual-basic"></a>Const — Instrukcja (Visual Basic)

Deklaruje i definiuje co najmniej jedną stałą.

## <a name="syntax"></a>Składnia

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ]
Const constantlist
```

## <a name="parts"></a>Części

`attributelist`  
Opcjonalna. Lista atrybutów, które są stosowane do wszystkich stałych zadeklarowanych w tej instrukcji. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasach kątowych ("`<`" i "`>`").

`accessmodifier`  
Opcjonalna. Użyj tego, aby określić, jaki kod może uzyskać dostęp do tych stałych. Może być [publiczna](../../../visual-basic/language-reference/modifiers/public.md), [chroniona](../../../visual-basic/language-reference/modifiers/protected.md), [zaprzyjaźniona](../../../visual-basic/language-reference/modifiers/friend.md), [chroniona zaprzyjaźniona](../modifiers/protected-friend.md), [prywatna](../../../visual-basic/language-reference/modifiers/private.md)lub [prywatna](../../language-reference/modifiers/private-protected.md).

`Shadows`  
Opcjonalna. Użyj tego, aby ponownie zadeklarować i ukryć element programowania w klasie bazowej. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

`constantlist`  
Wymagana. Lista stałych, które są zadeklarowane w tej instrukcji.

`constant` `[ ,` `constant` `... ]`

Każda `constant` ma następującą składnię i części:

`constantname` `[ As` `datatype` `] =` `initializer`

|Części|Opis|
|----------|-----------------|
|`constantname`|Wymagana. Nazwa stałej. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`datatype`|Wymagane, jeśli `Option Strict` jest `On`. Typ danych stałej.|
|`initializer`|Wymagana. Wyrażenie, które jest oceniane w czasie kompilacji i przypisane do stałej.|

## <a name="remarks"></a>Uwagi

Jeśli masz wartość, która nigdy nie zmienia się w aplikacji, można zdefiniować nazwaną stałą i użyć jej zamiast wartości literału. Nazwa jest łatwiejsza do zapamiętania niż wartość. Możesz zdefiniować stałą tylko raz i użyć jej w wielu miejscach w kodzie. Jeśli w nowszej wersji należy ponownie zdefiniować wartość, instrukcja `Const` jest jedynym miejscem, w którym należy wprowadzić zmianę.

`Const` można użyć tylko na poziomie modułu lub procedury. Oznacza to, że *kontekst deklaracji* dla zmiennej musi być klasą, strukturą, modułem, procedurą lub blokiem i nie może być plikiem źródłowym, przestrzenią nazw ani interfejsem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Lokalne stałe (wewnątrz procedury) domyślnie mają dostęp publiczny i nie można używać żadnych modyfikatorów dostępu. Stałe elementu członkowskiego klasy i modułu (poza jakąkolwiek procedurą) domyślnie są dostępem prywatnym, a stałe elementów członkowskich struktury domyślnie mają dostęp publiczny. Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu.

## <a name="rules"></a>Reguły

- **Kontekst deklaracji.** Stała zadeklarowana na poziomie modułu, poza żadną procedurą, jest *stałą członkowską*; jest członkiem klasy, struktury lub modułu, który go deklaruje.

  Stała zadeklarowana na poziomie procedury jest *stałą lokalną*; jest on lokalny dla procedury lub bloku, który deklaruje go.

- **Attributes.** Atrybuty można stosować tylko do stałych elementów członkowskich, nie do stałych lokalnych. Atrybut zawiera informacje dotyczące metadanych zestawu, który nie ma znaczenia dla tymczasowego magazynu, takiego jak stałe lokalne.

- **Modyfikatory.** Domyślnie wszystkie stałe są `Shared`, `Static`i `ReadOnly`. Nie można użyć żadnego z tych słów kluczowych podczas deklarowania stałej.

  Na poziomie procedury nie można używać `Shadows` ani modyfikatorów dostępu do deklarowania stałych lokalnych.

- **Wiele stałych.** Można zadeklarować kilka stałych w tej samej instrukcji deklaracji, określając `constantname` część dla każdej z nich. Wiele stałych jest oddzielonych przecinkami.

## <a name="data-type-rules"></a>Reguły typu danych

- **Typy danych.** Instrukcja `Const` może deklarować typ danych zmiennej. Można określić dowolny typ danych lub nazwę wyliczenia.

- **Typ domyślny.** Jeśli nie określisz `datatype`, stała Pobiera typ danych `initializer`. Jeśli określisz zarówno `datatype` i `initializer`, typ danych `initializer` musi być konwertowany na `datatype`. Jeśli nie `datatype` ani `initializer` nie istnieje, typ danych jest wartością domyślną `Object`.

- **Różne typy.** Można określić różne typy danych dla różnych stałych przy użyciu oddzielnej klauzuli `As` dla każdej zadeklarowanej zmiennej. Nie można jednak zadeklarować kilku stałych jako tego samego typu przy użyciu wspólnej klauzuli `As`.

- **Zainicjować.** Należy zainicjować wartość każdej stałej w `constantlist`. Użyj `initializer`, aby podać wyrażenie, które ma zostać przypisane do stałej. Wyrażenie może być dowolną kombinacją literałów, innych stałych, które są już zdefiniowane, oraz składowych wyliczenia, które są już zdefiniowane. Do łączenia takich elementów można używać operatorów arytmetycznych i logicznych.

  Nie można używać zmiennych ani funkcji w `initializer`. Można jednak użyć słów kluczowych konwersji, takich jak `CByte` i `CShort`. Możesz również użyć `AscW`, jeśli wywołasz go za pomocą stałej `String` lub argumentu `Char`, ponieważ może być oceniane w czasie kompilacji.

## <a name="behavior"></a>Zachowanie

- **Scope.** Stałe lokalne są dostępne tylko z poziomu ich procedury lub bloku. Stałe składowe są dostępne z dowolnego miejsca w swojej klasie, strukturze lub module.

- **Branego.** Kod poza klasą, strukturą lub modułem musi kwalifikować nazwę stałej elementu członkowskiego o nazwie tej klasy, struktury lub modułu. Kod poza procedurą lub blok nie może odwoływać się do żadnych stałych lokalnych w ramach tej procedury lub bloku.

## <a name="example"></a>Przykład

W poniższym przykładzie użyto instrukcji `Const`, aby zadeklarować stałe do użycia zamiast wartości literału.

[!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]

## <a name="example"></a>Przykład

W przypadku zdefiniowania stałej z typem danych `Object`, kompilator Visual Basic udostępnia typ `initializer`, a nie `Object`. W poniższym przykładzie, stały `naturalLogBase` ma `Decimal`typu czasu wykonywania.

[!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]

W poprzednim przykładzie użyto metody <xref:System.Type.ToString%2A> na obiekcie <xref:System.Type> zwróconym przez [operator GetType](../../../visual-basic/language-reference/operators/gettype-operator.md), ponieważ <xref:System.Type> nie można przekonwertować na `String` przy użyciu `CStr`.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)
- [#Const, dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)
- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
- [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Stałe i wyliczenia](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Stałe i wyliczenia](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
