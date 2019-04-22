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
ms.openlocfilehash: e13a773f0b585a5c8803a77c7aaad441d90dfe75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842307"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
`Key` — Słowo kluczowe pozwala na określenie zachowania w przypadku właściwości anonimowych typów. Tylko właściwości wyznaczone jako właściwości klucza wziąć udział w testach równości pomiędzy wystąpień typu anonimowego lub obliczania wartości Kod skrótu. Nie można zmienić wartości właściwości klucza.  
  
 Właściwości typu anonimowego wyznaczyć jako właściwość klucza poprzez umieszczenie słowa kluczowego `Key` przed jej deklaracją listy inicjowania. W poniższym przykładzie `Airline` i `FlightNo` są właściwościami klucza, ale `Gate` nie jest.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 Po utworzeniu nowego typu anonimowego dziedziczy bezpośrednio z <xref:System.Object>. Kompilator zastępuje trzy dziedziczone elementy członkowskie: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, i <xref:System.Object.ToString%2A>. Kod zastąpienia, który jest generowany dla <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> na podstawie właściwości klucza. Jeśli nie ma żadnych kluczy właściwości w typie <xref:System.Object.GetHashCode%2A> i <xref:System.Object.Equals%2A> nie są zastępowane.  
  
## <a name="equality"></a>Równości  
 Dwa wystąpienia typu anonimowego są takie same, jeśli są one wystąpień tego samego typu i wartości ich właściwości klucza są takie same. W poniższych przykładach `flight2` jest równa `flight1` z poprzedniego przykładu, ponieważ są one wystąpień tego samego anonimowy typ i mają pasujących wartości ich właściwości klucza. Jednak `flight3` nie jest równa `flight1` ponieważ ma ona inną wartość dla klucza właściwości `FlightNo`. Wystąpienie `flight4` nie jest taki sam jak `flight1` ponieważ one wyznaczyć różnych właściwości jako właściwości klucza.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 Jeśli dwa wystąpienia są uznane za pomocą tylko niekluczowych właściwości, identyczne nazwę, typ, kolejność i wartości, dwa wystąpienia nie są równe. Wystąpienie bez właściwości klucza jest równe tylko do samego siebie.  
  
 Aby uzyskać więcej informacji o warunkach, w których dwa wystąpienia typu anonimowego są wystąpieniami tego samego typu anonimowego, zobacz [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Obliczanie kodu wyznaczania wartości skrótu  
 Podobnie jak <xref:System.Object.Equals%2A>, funkcję mieszania, która jest zdefiniowana w <xref:System.Object.GetHashCode%2A> dla typu anonimowego opiera się na kluczowych właściwości typu. W poniższych przykładach pokazano interakcji między właściwościami klucza i wyznaczania wartości skrótu wartości kodu.  
  
 Wystąpienia typu anonimowego, które mają takie same wartości wszystkich właściwości klucza mają taką samą wartość kodu wyznaczania wartości skrótu, nawet jeśli niekluczowych właściwości nie mają pasujących wartości. Poniższa instrukcja zwraca `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 Wystąpienia typu anonimowego, które mają różne wartości dla co najmniej jedną właściwość klucza mają wartości kodu inny skrót. Poniższa instrukcja zwraca `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 Wystąpienia typów anonimowych, które określają różne właściwości jako właściwości klucza nie są wystąpieniami tego samego typu. Mają one różne wartości skrótów kodu wartości, nawet wtedy, gdy nazwy i wartości wszystkich właściwości są takie same. Poniższa instrukcja zwraca `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>Wartości tylko do odczytu  
 Nie można zmienić wartości właściwości klucza. Na przykład w `flight1` w wcześniejszych przykładach `Airline` i `FlightNo` pola są tylko do odczytu, ale `Gate` można zmienić.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>Zobacz także

- [Definicja typu anonimowego](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Instrukcje: Wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
