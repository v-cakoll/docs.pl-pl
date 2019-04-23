---
title: 'Instrukcje: Ukrywanie dziedziczonej zmiennej (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: ee147ecd00b88b538ace32844c42ac9c5022b2ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331705"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Instrukcje: Ukrywanie dziedziczonej zmiennej (Visual Basic)
Klasa pochodna dziedziczy wszystkie definicje klasy bazowej. Jeśli chcesz zdefiniować zmienną przy użyciu tej samej nazwie jako element klasy podstawowej, można ukryć, lub *w tle*, ten element klasy bazowej podczas definiowania zmiennej w klasie pochodnej. Jeśli to zrobisz, kod w klasie pochodnej uzyskuje dostęp do zmiennej, chyba że jawnie pomija mechanizm przesłaniania.  
  
 Jest kolejnym powodem, że możesz chcieć ukrywanie dziedziczonej zmiennej do ochrony przed poprawki klasy bazowej. Klasy bazowej może zostać poddane zmianę, która modyfikuje element, do którego są dziedziczone. W takim przypadku `Shadows` modyfikator wymusza odwołania z klasy pochodnej jest rozpoznawana do zmiennej, zamiast elementu klasy podstawowej.  
  
### <a name="to-hide-an-inherited-variable"></a>Aby ukrywanie dziedziczonej zmiennej  
  
1. Upewnij się, że zmiennej, którą chcesz ukryć zadeklarowano na poziomie klasy (poza dowolnej procedury). W przeciwnym razie nie trzeba je ukryć.  
  
2. Wewnątrz klasy pochodnej, należy napisać [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarowanie zmiennej. Użyj takiej samej nazwie, jak w przypadku dziedziczonej zmiennej.  
  
3. Obejmują [cieni](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w deklaracji.  
  
     Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej.  
  
     Poniższy przykład ilustruje przesłanianie dziedziczonej zmiennej.  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     Poprzedni przykład deklaruje zmienną `shadowString` w klasie bazowej i przesłania go w klasie pochodnej. Procedura `showStrings` w klasie pochodnej Wyświetla przesłaniania wersję ciągu podczas nazwę `shadowString` nie jest kwalifikowana. Następnie wyświetla tekst z cieniem wersji podczas `shadowString` jest kwalifikowany za pomocą `MyBase` — słowo kluczowe.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Przesłanianie wprowadza więcej niż jedna wersja zmienna o takiej samej nazwie. Instrukcja kodu odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołania zależy od czynników, takich jak lokalizacja instrukcja kodu i występowania ciągu kwalifikującym się. Może to zwiększyć ryzyko odnoszące się do niezamierzonych wersję zasłonięte zmiennej. Możesz obniżyć ryzyko kwalifikując pełni wszystkie odwołania do zmiennej zasłonięte.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Różnice między przesłanianiem i zastępowaniem](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Instrukcje: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Instrukcje: Dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
