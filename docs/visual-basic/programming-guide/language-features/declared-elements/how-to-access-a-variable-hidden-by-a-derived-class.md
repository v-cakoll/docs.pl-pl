---
title: 'Instrukcje: Dostęp do zmiennej ukrytej przez klasę pochodną (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: a97a51d4570d87eaa873fb3152ad810f528dff46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832180"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Instrukcje: Dostęp do zmiennej ukrytej przez klasę pochodną (Visual Basic)
Gdy kod w klasie pochodnej uzyskuje dostęp do zmiennej, kompilator zwykle jest rozpoznawany jako odwołanie do najbliższej wersji dostępna, oznacza to, dostępnej wersji najmniejszą liczbą derivational kroki z poprzednimi wersjami z dostępu do klasy. Jeśli zmienna jest zdefiniowana w klasie pochodnej, kod zwykle uzyskuje dostęp do tej definicji.  
  
 Jeśli zmienna w klasie pochodnej cieni zmiennej w klasie bazowej, ukrywa wersją klasy bazowej. Jednak możesz mają dostęp do klasy bazowej zmiennej kwalifikując ją za pomocą `MyBase` — słowo kluczowe.  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Dostęp do zmiennej w klasie bazowej ukrytej przez klasę pochodną  
  
-   W wyrażeniu lub instrukcji przypisania, nazwę zmiennej należy poprzedzić `MyBase` — słowo kluczowe i okres (`.`).  
  
     Kompilator rozpoznaje odwołanie do zmiennej wersją klasy bazowej.  
  
     W poniższym przykładzie pokazano cieniowania przez dziedziczenie. Dzięki temu dwa odwołania, który uzyskuje dostęp do zmiennej przesłaniania i taki, który pomija cieniowania.  
  
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
 Aby zmniejszyć ryzyko odnoszące się do niezamierzonych wersję zasłonięte zmiennej, można pełnej kwalifikacji wszystkie odwołania do zmiennej zasłonięte. Przesłanianie wprowadza więcej niż jedna wersja zmienna o takiej samej nazwie. Instrukcja kodu odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołania zależy od czynników, takich jak lokalizacja instrukcja kodu i występowania ciągu kwalifikującym się. Może to zwiększyć ryzyko odnoszące się do niewłaściwej wersji zmiennej.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Różnice między przesłanianiem i zastępowaniem](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Instrukcje: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Instrukcje: Ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
