---
title: Nothing — Słowo kluczowe
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 3bd4681341a33cc8db4ecbc2b284be243db56549
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344162"
---
# <a name="nothing-keyword-visual-basic"></a>Nothing — słowo kluczowe (Visual Basic)

Reprezentuje wartość domyślną każdego typu danych. W przypadku typów referencyjnych wartością domyślną jest odwołanie `null`. W przypadku typów wartości wartość domyślna zależy od tego, czy typ wartości dopuszcza wartość null.

> [!NOTE]
> W przypadku typów wartości niedopuszczających wartości null `Nothing` w Visual Basic różni się C#od `null` w. W Visual Basic, jeśli ustawisz zmienną typu wartości, która nie dopuszcza wartości null do `Nothing`, zmienna jest ustawiona na wartość domyślną dla zadeklarowanego typu. W C#programie, Jeśli przypiszesz zmienną typu wartości niedopuszczających wartości null do `null`, wystąpi błąd w czasie kompilacji.

## <a name="remarks"></a>Uwagi

`Nothing` reprezentuje wartość domyślną typu danych. Wartość domyślna zależy od tego, czy zmienna jest typu wartości lub typu odwołania.

Zmienna *typu wartości* bezpośrednio zawiera jej wartość. Typy wartości obejmują wszystkie typy danych liczbowych, `Boolean`, `Char`, `Date`, wszystkie struktury i wszystkie wyliczenia. Zmienna *typu referencyjnego* przechowuje odwołanie do wystąpienia obiektu w pamięci. Typy odwołań obejmują klasy, tablice, Delegaty i ciągi. Aby uzyskać więcej informacji, zobacz [typy wartości i typy odwołań](../programming-guide/language-features/data-types/value-types-and-reference-types.md).

Jeśli zmienna ma typ wartości, zachowanie `Nothing` zależy od tego, czy zmienna ma typ danych dopuszczający wartości null. Aby reprezentować typ wartości null, Dodaj modyfikator `?` do nazwy typu. Przypisanie `Nothing` do zmiennej dopuszczanej do wartości null ustawia wartość do `null`. Aby uzyskać więcej informacji i przykładów, zobacz [dopuszczanie typów wartości null](../programming-guide/language-features/data-types/nullable-value-types.md).

Jeśli zmienna ma typ wartości, który nie dopuszcza wartości null, przypisanie `Nothing` do niego ustawia wartość domyślną dla zadeklarowanego typu. Jeśli ten typ zawiera zmienne składowe, są one ustawione na wartości domyślne. Poniższy przykład ilustruje tę wartość dla typów skalarnych.

[!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]

Jeśli zmienna jest typu referencyjnego, przypisanie `Nothing` do zmiennej ustawia ją na `null` odwołanie do typu zmiennej. Zmienna, która jest ustawiona na odwołanie `null` nie jest skojarzona z żadnym obiektem. Poniższy przykład ilustruje:

[!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]

Podczas sprawdzania, czy zmienna odwołania (lub typ wartości null) jest `null`, nie należy używać `= Nothing` lub `<> Nothing`. Zawsze używaj `Is Nothing` lub `IsNot Nothing`.

W przypadku ciągów w Visual Basic pusty ciąg jest równy `Nothing`. W związku z tym `"" = Nothing` ma wartość true.

W poniższym przykładzie przedstawiono porównania wykorzystujące operatory `Is` i `IsNot`:

[!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]

Jeśli deklarujesz zmienną bez użycia klauzuli `As` i ustawisz ją na `Nothing`, zmienna ma typ `Object`. Przykładem tego jest `Dim something = Nothing`. W tym przypadku występuje błąd czasu kompilacji, gdy `Option Strict` jest włączona, a `Option Infer` jest wyłączona.

Przypisanie `Nothing` do zmiennej obiektu nie odwołuje się już do żadnego wystąpienia obiektu. Jeśli zmienna była wcześniej nazywana wystąpieniem, ustawienie jej na `Nothing` nie przerywa działania samego wystąpienia. Wystąpienie zostanie przerwane, a zasoby pamięci i systemu skojarzone z nim zostaną wydane dopiero po wykryciu przez moduł wyrzucania elementów bezużytecznych, że nie ma aktywnych odwołań.

`Nothing` różni się od obiektu <xref:System.DBNull>, który reprezentuje niezainicjowany wariant lub nieistniejącą kolumnę bazy danych.

## <a name="see-also"></a>Zobacz także

- [Dim, instrukcja](./statements/dim-statement.md)
- [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Okres istnienia w Visual Basic](../programming-guide/language-features/declared-elements/lifetime.md)
- [Is, operator](./operators/is-operator.md)
- [IsNot, operator](./operators/isnot-operator.md)
- [Typy wartości dopuszczających wartości null](../programming-guide/language-features/data-types/nullable-value-types.md)
