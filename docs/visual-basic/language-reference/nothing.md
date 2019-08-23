---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 12c88db49dc7723fc269195e7d174bfa822c64d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963760"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
Reprezentuje wartość domyślną każdego typu danych. W przypadku typów referencyjnych wartością domyślną jest `null` odwołanie. W przypadku typów wartości wartość domyślna zależy od tego, czy typ wartości dopuszcza wartość null.  
  
> [!NOTE]
> W przypadku typów wartości niedopuszczających `Nothing` wartości null, w `null` Visual Basic C#różni się od elementu w. W Visual Basic, jeśli ustawisz zmienną typu wartości, która nie dopuszcza wartości null do `Nothing`, zmienna jest ustawiona na wartość domyślną dla zadeklarowanego typu. W C#programie, Jeśli przypiszesz zmienną typu wartości niedopuszczające wartości null `null`do, wystąpi błąd w czasie kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 `Nothing`reprezentuje wartość domyślną typu danych. Wartość domyślna zależy od tego, czy zmienna jest typu wartości lub typu odwołania.  
  
 Zmienna *typu wartości* bezpośrednio zawiera jej wartość. Typy wartości obejmują wszystkie typy danych liczbowych `Boolean`, `Char` `Date`,,, wszystkie struktury i wszystkie wyliczenia. Zmienna *typu referencyjnego* przechowuje odwołanie do wystąpienia obiektu w pamięci. Typy odwołań obejmują klasy, tablice, Delegaty i ciągi. Aby uzyskać więcej informacji, zobacz [typy wartości i typy odwołań](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Jeśli zmienna ma typ wartości, zachowanie `Nothing` jest zależne od tego, czy zmienna ma typ danych dopuszczający wartości null. Aby reprezentować typ wartości null, Dodaj `?` modyfikator do nazwy typu. Przypisanie `Nothing` do zmiennej dopuszczanej do wartości null ustawia `null`wartość na. Aby uzyskać więcej informacji i przykładów, zobacz [dopuszczanie typów wartości null](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Jeśli zmienna ma typ wartości, który nie dopuszcza wartości null, przypisanie `Nothing` do niego ustawia wartość domyślną dla zadeklarowanego typu. Jeśli ten typ zawiera zmienne składowe, są one ustawione na wartości domyślne. Poniższy przykład ilustruje tę wartość dla typów skalarnych.  
  
 [!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]  
  
 Jeśli zmienna jest typu referencyjnego, przypisanie `Nothing` do zmiennej ustawia ją `null` na odwołanie do typu zmiennej. Zmienna, która jest ustawiona na `null` odwołanie, nie jest skojarzona z żadnym obiektem. Poniższy przykład ilustruje to.  
  
 [!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]  
  
 Podczas sprawdzania, czy zmienna odwołania (lub typ wartości null) ma `null`wartość, nie używaj `= Nothing` ani `<> Nothing`. Zawsze używaj `Is Nothing` lub `IsNot Nothing`.  
  
 W przypadku ciągów w Visual Basic pusty ciąg równa `Nothing`się. W związku `"" = Nothing` z tym, ma wartość true.  
  
 W poniższym przykładzie przedstawiono porównania `Is` wykorzystujące operatory i. `IsNot`  
  
 [!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]  
  
 Jeśli deklarujesz zmienną bez użycia `As` klauzuli i ustawisz ją na `Nothing`, `Object`zmienna ma typ. Przykładem jest `Dim something = Nothing`. W takim przypadku występuje błąd czasu kompilacji, gdy `Option Strict` jest on włączony i `Option Infer` jest wyłączony.  
  
 Przypisanie `Nothing` do zmiennej obiektu nie odwołuje się już do żadnego wystąpienia obiektu. Jeśli zmienna była wcześniej nazywana wystąpieniem, ustawienie go na `Nothing` nie kończy działanie samego wystąpienia. Wystąpienie zostanie przerwane, a zasoby pamięci i systemu skojarzone z nim zostaną wydane dopiero po wykryciu przez moduł wyrzucania elementów bezużytecznych, że nie ma aktywnych odwołań.  
  
 `Nothing`różni się <xref:System.DBNull> od obiektu, który reprezentuje niezainicjowany wariant lub nieistniejącą kolumnę bazy danych.  
  
## <a name="see-also"></a>Zobacz także

- [Dim, instrukcja](../../visual-basic/language-reference/statements/dim-statement.md)
- [Okres istnienia obiektu: Jak obiekty są tworzone i niszczone](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Okres istnienia w Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Is, operator](../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot, operator](../../visual-basic/language-reference/operators/isnot-operator.md)
- [Typy wartości dopuszczających wartości null](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
