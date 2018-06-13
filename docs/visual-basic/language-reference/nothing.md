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
ms.openlocfilehash: fb1af7d748faac78b26177af453a0e858f9e97c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603993"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
Reprezentuje wartość domyślną każdego typu danych. Typy odwołań, wartością domyślną jest `null` odwołania. Dla typów wartości wartość domyślna zależy od tego, czy typ wartości jest null.  
  
> [!NOTE]
>  Dla typów wartości nie przyjmujące wartości `Nothing` w języku Visual Basic różni się od `null` w języku C#. W języku Visual Basic, jeśli wartość zmiennej typu niedopuszczający wartości null do `Nothing`, zmienna jest ustawiona na wartość domyślną dla deklarowanym typem. W języku C#, jeśli przypisano zmienną typu niedopuszczające wartości do `null`, występuje błąd kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 `Nothing` reprezentuje wartość domyślna typu danych. Wartość domyślna zależy od tego, czy zmienna jest typem wartości lub typu referencyjnego.  
  
 Zmienna *typu wartości* bezpośrednio zawiera wartość. Typy wartości obejmują wszystkie typy danych numerycznych, `Boolean`, `Char`, `Date`, wszystkie struktury i wszystkie wyliczenia. Zmienna *zawierają odwołania do typu* zawiera odwołanie do wystąpienia obiektu w pamięci. Typy odwołań obejmują klas, tablic obiektów delegowanych i ciągów. Aby uzyskać więcej informacji, zobacz [typów wartości i typy referencyjne](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Jeśli zmienna jest wartością typu, zachowanie `Nothing` zależy od tego, czy zmienna jest typem danych wartości null. Do reprezentowania typu wartości null, należy dodać `?` modyfikator nazwy typu. Przypisywanie `Nothing` do wartości null zmiennej ustawia wartość `null`. Aby uzyskać dodatkowe informacje i przykłady, zobacz [typy dopuszczające wartości zerowe wartości](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Jeśli zmienna jest typ wartości, który nie dopuszcza, przypisywanie `Nothing` do ustawia ją na wartość domyślną dla deklarowanym typem. Ten typ zawiera elementy członkowskie zmiennej, są ustawione wartości domyślne. Poniższy przykład przedstawia to dla typów skalarnych.  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 Jeśli zmienna jest typu referencyjnego, przypisywanie `Nothing` do zmiennej ustawia ją na `null` odwołanie typu zmienną. Zmienna, która ma ustawioną wartość `null` odwołania nie jest skojarzony z żadnym obiektem. W poniższym przykładzie pokazano to.  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 Podczas sprawdzania, czy odwołanie (lub wartość null, wpisz) zmienna jest `null`, nie używaj `= Nothing` lub `<> Nothing`. Zawsze używaj `Is Nothing` lub `IsNot Nothing`.  
  
 Ciągi w Visual Basic, pusty ciąg równa `Nothing`. W związku z tym `"" = Nothing` ma wartość true.  
  
 W poniższym przykładzie przedstawiono porównanie, które używają `Is` i `IsNot` operatorów.  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 Jeśli zmienna jest zadeklarowana bez użycia `As` klauzuli i ustaw ją na `Nothing`, zmienna ma typ `Object`. Na przykład jest `Dim something = Nothing`. Błąd kompilacji w takim przypadku występuje podczas `Option Strict` znajduje się na i `Option Infer` jest wyłączona.  
  
 Po przypisaniu `Nothing` zmiennej obiektu nie odwołuje się do dowolnego wystąpienia obiektu. Jeśli zmienna była wcześniej określone wystąpienie, ustawieniem dla niego `Nothing` nie kończy się wystąpienia. Wystąpienie zostanie zakończony i skojarzone z nim zasoby pamięci są wydawane tylko wtedy, gdy moduł garbage collector (GC) wykrywa, że nie ma żadnych aktywnych odwołań pozostałych.  
  
 `Nothing` różni się od <xref:System.DBNull> obiektu, który reprezentuje niezainicjowanej wariantu lub kolumną nieistniejącą bazy danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Dim, instrukcja](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Okres istnienia w Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Is, operator](../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot, operator](../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Typy wartości dopuszczających wartości null](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
