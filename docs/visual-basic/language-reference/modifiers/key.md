---
title: Klucz
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 5b060f5fa0042dfb8ffa6876f5e172d3bcda67a3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396223"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
`Key`Słowo kluczowe umożliwia określenie zachowania właściwości typów anonimowych. Tylko właściwości, które należy wyznaczyć jako właściwości klucza, uczestniczą w testach równości między wystąpieniami typu anonimowego lub obliczeń wartości kodów skrótu. Nie można zmienić wartości właściwości klucza.  
  
 Właściwość typu anonimowego należy wyznaczyć jako właściwość klucza poprzez umieszczenie słowa kluczowego `Key` przed deklaracją na liście inicjalizacji. W poniższym przykładzie `Airline` i `FlightNo` są właściwościami klucza, ale `Gate` nie jest.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 Po utworzeniu nowego typu anonimowego dziedziczy on bezpośrednio z <xref:System.Object> . Kompilator przesłania trzy dziedziczone elementy członkowskie: <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> , i <xref:System.Object.ToString%2A> . Kod przesłonięcia, który jest tworzony dla <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> jest oparty na właściwościach klucza. Jeśli w typie nie ma właściwości klucza <xref:System.Object.GetHashCode%2A> i <xref:System.Object.Equals%2A> nie są one zastępowane.  
  
## <a name="equality"></a>Równość  
 Dwa wystąpienia typu anonimowego są równe, jeśli są wystąpieniami tego samego typu, a wartości ich właściwości klucza są równe. W poniższych przykładach `flight2` jest równe `flight1` z poprzedniego przykładu, ponieważ są wystąpieniami tego samego typu anonimowego i mają pasujące wartości właściwości klucza. Jednak `flight3` nie jest równe, `flight1` ponieważ ma inną wartość właściwości klucza `FlightNo` . Wystąpienie `flight4` nie jest tego samego typu, `flight1` ponieważ wyznaczy różne właściwości jako właściwości klucza.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 Jeśli dwa wystąpienia są zadeklarowane tylko z właściwościami niebędącymi kluczowymi, takimi jak nazwa, typ, kolejność i wartość, dwa wystąpienia nie są równe. Wystąpienie bez właściwości klucza jest równe tylko dla siebie.  
  
 Aby uzyskać więcej informacji na temat warunków, w których dwa wystąpienia typu anonimowego są wystąpieniami tego samego typu anonimowego, zobacz [Typy anonimowe](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Obliczanie kodu skrótu  
 Podobnie jak <xref:System.Object.Equals%2A> Funkcja skrótu zdefiniowana w <xref:System.Object.GetHashCode%2A> dla typu anonimowego jest oparta na właściwościach klucza typu. W poniższych przykładach przedstawiono interakcje między właściwościami klucza i wartościami kodu skrótu.  
  
 Wystąpienia typu anonimowego, które mają takie same wartości dla wszystkich właściwości klucza mają tę samą wartość kodu skrótu, nawet jeśli właściwości nieklucza nie mają pasujących wartości. Poniższa instrukcja zwraca wartość `True` .  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 Wystąpienia typu anonimowego, które mają różne wartości dla co najmniej jednej właściwości klucza mają różne wartości kodu skrótu. Poniższa instrukcja zwraca wartość `False` .  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 Wystąpienia typów anonimowych, które wyznaczają różne właściwości jako właściwości klucza, nie są wystąpieniami tego samego typu. Mają różne wartości kodu skrótu, nawet gdy nazwy i wartości wszystkich właściwości są takie same. Poniższa instrukcja zwraca wartość `False` .  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>Wartości tylko do odczytu  
 Nie można zmienić wartości właściwości klucza. Na przykład w `flight1` poprzednich przykładach `Airline` i `FlightNo` pola są tylko do odczytu, ale `Gate` można je zmienić.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>Zobacz też

- [Definicja typu anonimowego](../../programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Typy anonimowe](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
