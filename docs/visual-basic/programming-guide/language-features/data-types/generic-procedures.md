---
title: Procedury ogólne w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 0f2a0c646b5af91d5296bafb01f5261d7ee6b9fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574316"
---
# <a name="generic-procedures-in-visual-basic"></a>Procedury ogólne w Visual Basic
A *ogólna procedura*, nazywane również *metody ogólnej*, jest to procedura zdefiniowany co najmniej jednego parametru typu. Dzięki temu kod wywołujący, aby dostosować typy danych do ich wymagania dotyczące zawsze wywołuje procedurę.  
  
 Procedura nie jest ogólna po prostu wynoszącą definiowanego wewnątrz Ogólna klasa lub Struktura ogólna. Aby być ogólna, procedurę należy wykonać co najmniej jeden parametr typu, oprócz normalnych parametrów, może to potrwać. Ogólna klasa lub struktura może zawierać procedury nierodzajowymi i nierodzajowymi klasy, struktury lub modułu może zawierać procedury ogólne.  
  
 Procedury ogólne użyć jego parametrów typu w jego listę parametrów normalne, jego typem zwracanym, jeśli ma on jeden, a w jego procedury kodu.  
  
## <a name="type-inference"></a>Wnioskowanie o typie  
 Ogólna procedura można wywołać bez podawania żadnych argumentów typu w ogóle. Jeśli wywołasz ją w ten sposób, kompilator spróbuje określić typy odpowiednie dane do przekazania do procedury argumentów typu. Jest to nazywane *wnioskowanie o typie*. Poniższy kod ilustruje sposób wywoływania, w którym kompilator ustala, powinna przekazać typ `String` na parametr typu `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 Jeśli kompilator nie można wywnioskować argumentów typu z kontekstu wywołania, zgłasza błąd. Jedną z możliwych przyczyn takiego komunikatu o błędzie jest niezgodność rangi tablicy. Na przykład załóżmy, że zdefiniujesz normalne parametr jako tablicę z parametrem typu. Jeśli wywołanie procedury ogólne dostarczanie tablicy o innej randze (liczba wymiarów), niezgodność powoduje, że wnioskowanie o typie nie powiedzie się. Poniższy kod ilustruje sposób wywoływania, w którym tablicy dwuwymiarowej jest przekazywany do procedury, która oczekuje Jednowymiarowa tablica.  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 Wnioskowanie o typie można wywoływać, pomijając wszystkich argumentów typu. Jeśli podasz jeden argument typu, należy podać je wszystkie.  
  
 Wnioskowanie o typie jest obsługiwana tylko w przypadku ogólnych procedurach. Nie można wywołać wnioskowanie o typie na klasy ogólne, struktur, interfejsów i delegatów.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie zdefiniowano ogólnego `Function` procedurze, aby znaleźć określony element w tablicy. On definiuje jeden parametr typu i używa ich do utworzenia dwóch parametrów na liście parametrów.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a>Komentarze  
 Poprzedni przykład wymaga możliwości porównywania `searchValue` względem każdego elementu `searchArray`. Aby zagwarantować tę możliwość, jego ogranicza parametr typu `T` do zaimplementowania <xref:System.IComparable%601> interfejsu. Kod używa <xref:System.IComparable%601.CompareTo%2A> zamiast metody `=` operatora, ponieważ nie ma żadnej gwarancji, że argument typu dostarczane na potrzeby `T` obsługuje `=` operatora.  
  
 Możesz przetestować `findElement` procedury z następującym kodem.  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 Poprzedniego wywołania `MsgBox` odpowiednio wyświetlane "0", "1" i "-1".  
  
## <a name="see-also"></a>Zobacz także
- [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Instrukcje: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Instrukcje: używanie klasy ogólnej](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Procedury](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Parametry i argumenty procedur](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Lista typów](../../../../visual-basic/language-reference/statements/type-list.md)
- [Lista parametrów](../../../../visual-basic/language-reference/statements/parameter-list.md)
