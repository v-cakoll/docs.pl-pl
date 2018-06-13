---
title: Key (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 92d54e3135142bc02a17f3ce5ac078a356c139be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599847"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
`Key` — Słowo kluczowe można określić zachowanie dla właściwości typu anonimowego. Tylko właściwości wyznaczone jako właściwości klucza brać udziału w testach równość wystąpień typu anonimowego lub obliczenia wartości skrótu kodu. Nie można zmienić wartości właściwości klucza.  
  
 Możesz określić właściwości typu anonimowego jako właściwość klucza przez umieszczenie słowo kluczowe `Key` przed jej deklaracją listy inicjowania. W poniższym przykładzie `Airline` i `FlightNo` są właściwościami klucza, ale `Gate` nie jest.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 Podczas tworzenia nowego typu anonimowego dziedziczy bezpośrednio z <xref:System.Object>. Kompilator zastępuje trzy dziedziczone elementy członkowskie: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, i <xref:System.Object.ToString%2A>. Kod zastąpienia, który jest tworzony dla <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> na podstawie właściwości klucza. Jeśli nie ma żadnych właściwości klucza w typie, <xref:System.Object.GetHashCode%2A> i <xref:System.Object.Equals%2A> nie zostaną zastąpione.  
  
## <a name="equality"></a>Równość  
 Dwa wystąpienia typu anonimowego są takie same, jeśli są one wystąpień tego samego typu i wartości ich właściwości klucza są takie same. W poniższych przykładach `flight2` jest równa `flight1` z poprzedniego przykładu ponieważ są one takie same anonimowego wystąpienia typu i mieć zgodne wartości dla ich właściwości klucza. Jednak `flight3` nie jest równa `flight1` , ponieważ ma ona inną wartość dla właściwości klucza, `FlightNo`. Wystąpienie `flight4` nie jest taki sam typ jak `flight1` ponieważ one określić różne właściwości jako właściwości klucza.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 Jeśli dwa wystąpienia został zadeklarowany z tylko niż właściwości klucza, takie same jak w nazwę, typ, kolejność i wartości, dwa wystąpienia nie są takie same. Wystąpienia bez właściwości klucza wynosi tylko do samego siebie.  
  
 Aby uzyskać więcej informacji o warunkach, w których dwa wystąpienia typu anonimowego są wystąpień tego samego typu anonimowego, zobacz [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Obliczanie kodu wyznaczania wartości skrótu  
 Podobnie jak <xref:System.Object.Equals%2A>, funkcji skrótu, który jest zdefiniowany w <xref:System.Object.GetHashCode%2A> dla typu anonimowego opiera się na typ właściwości klucza. W poniższych przykładach pokazano interakcji między właściwości klucza oraz skrót wartości kodów.  
  
 Wystąpienia typu anonimowego, które mają takie same wartości dla wszystkich właściwości klucza mają taką samą wartość kodu wyznaczania wartości skrótu, nawet jeśli niż właściwości klucza nie ma dopasowania wartości. Zwraca następująca instrukcja `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 Wystąpienia typu anonimowego, które mają różne wartości dla co najmniej jednej właściwości klucza mają różne skrótu kodu wartości. Zwraca następująca instrukcja `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 Wystąpień typów anonimowych, które określają różne właściwości jako właściwości klucza nie są wystąpień tego samego typu. Mają one wartości kodów różnych wyznaczania wartości skrótu, nawet wtedy, gdy nazwy i wartości wszystkich właściwości są takie same. Zwraca następująca instrukcja `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a>Wartości tylko do odczytu  
 Nie można zmienić wartości właściwości klucza. Na przykład w `flight1` w przykładach wcześniejszych `Airline` i `FlightNo` pola są tylko do odczytu, ale `Gate` można zmienić.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Definicja typu anonimowego](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
