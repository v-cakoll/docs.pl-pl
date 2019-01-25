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
ms.openlocfilehash: b4a9acb5a43898ef616bbc6bb97f2f4f96d206b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496952"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
Reprezentuje wartość domyślną każdego typu danych. Dla typów odwołań, wartość domyślna to `null` odwołania. Dla typów wartości wartość domyślna zależy od tego, czy typ wartości ma wartość null.  
  
> [!NOTE]
>  W przypadku typów wartości niedopuszczającym wartości `Nothing` w języku Visual Basic różni się od `null` w C#. W języku Visual Basic, jeśli zostanie ustawiona zmienna typu wartości niedopuszczającym wartości do `Nothing`, zmienna jest ustawiana na wartość domyślną dla deklarowanym typem. W C#, jeśli przypiszesz zmienną typu wartości niedopuszczającym wartości do `null`, wystąpi błąd kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 `Nothing` reprezentuje wartość domyślną typu danych. Wartość domyślna zależy od tego, czy zmienna jest typem wartości lub typem referencyjnym.  
  
 Zmienna *typu wartości* bezpośrednio zawiera wartość. Typy wartości obejmują wszystkie typy danych liczbowych, `Boolean`, `Char`, `Date`, wszystkie struktury i wszystkie wyliczenia. Zmienna *odwołania do typu* przechowuje odwołania do wystąpienia obiektu w pamięci. Typy odwołań zawierają klasy, tablice, delegaty i ciągi. Aby uzyskać więcej informacji, zobacz [typy wartości i odwołań](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Jeśli zmienna jest wartość typu, zachowanie `Nothing` zależy od tego, czy zmienna jest typu danych dopuszczających wartość null. Do reprezentowania typem wartościowym, Dodaj `?` modyfikator do nazwy typu. Przypisywanie `Nothing` dopuszcza wartości null zmiennej ustawia wartość `null`. Aby uzyskać więcej informacji i przykładów, zobacz [typów wartości dopuszczających wartości zerowe](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Jeśli zmienna jest typem wartości, która nie jest dopuszczalna, przypisując `Nothing` do ustawia ją na wartość domyślną dla deklarowanym typem. Jeśli ten typ zawiera składowe zmiennych, są gotowi do wartości domyślnych. W poniższym przykładzie pokazano to w przypadku typów skalarnych.  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 Jeśli zmienna jest typem referencyjnym, przypisując `Nothing` do zmiennej ustawia ją na `null` odwołanie do zmiennej typu. Zmienna, która jest równa `null` odwołania nie jest skojarzony z żadnym obiektem. Poniższy przykład przedstawia to.  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 Podczas sprawdzania, czy odwołanie (lub typ dopuszczający wartość null wartości) zmienna jest `null`, nie używaj `= Nothing` lub `<> Nothing`. Zawsze używaj `Is Nothing` lub `IsNot Nothing`.  
  
 Ciągi w języku Visual Basic, równa się pustym ciągiem `Nothing`. W związku z tym `"" = Nothing` ma wartość true.  
  
 W poniższym przykładzie pokazano porównania, które używają `Is` i `IsNot` operatorów.  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 Jeśli zmienna jest zadeklarowana bez użycia `As` klauzuli i ustaw ją na `Nothing`, zmienna posiada typ `Object`. Na przykład `Dim something = Nothing`. Występuje błąd kompilacji, w tym przypadku podczas `Option Strict` znajduje się na i `Option Infer` jest wyłączona.  
  
 Po przypisaniu `Nothing` zmienną obiektu nie jest już odwołuje się do dowolnego wystąpienia obiektu. Jeśli zmienna wcześniej odnosił się do wystąpienia, ustawieniem dla niego `Nothing` nie kończy samego wystąpienia. Wystąpienie zostanie zakończony i skojarzone z nią zasoby pamięci są zwalniane, tylko wtedy, gdy moduł odśmiecania pamięci (GC) wykrywa żadnych aktywnych odwołań pozostałe.  
  
 `Nothing` różni się od <xref:System.DBNull> obiektu, który reprezentuje niezainicjowanej wariantu lub kolumny nieistniejącej bazy danych.  
  
## <a name="see-also"></a>Zobacz także
- [Dim, instrukcja](../../visual-basic/language-reference/statements/dim-statement.md)
- [Okres istnienia obiektów: Jak obiekty są tworzone i niszczone](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Okres istnienia w Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Is, operator](../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot, operator](../../visual-basic/language-reference/operators/isnot-operator.md)
- [Typy wartości dopuszczających wartości null](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
