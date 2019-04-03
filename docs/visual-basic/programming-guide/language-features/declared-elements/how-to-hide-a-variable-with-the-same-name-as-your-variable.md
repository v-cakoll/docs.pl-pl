---
title: 'Instrukcje: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: a8a7eda2a636d7f89131d140c82ad4f3c4743211
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826681"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Instrukcje: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)
Można ukryć zmiennej przez *przesłanianie* go, oznacza to poprzez zmianę definicji go ze zmienną o takiej samej nazwie. Można w tle zmienną, którą chcesz ukryć na dwa sposoby:  
  
-   **Cieniowania przez zakres.** Można go cienia przez zakres przez redeclaring go wewnątrz Podobszar regionu zawierającego zmienną, którą chcesz ukryć.  
  
-   **Przesłanianie poprzez dziedziczenie.** Jeśli nie zdefiniowano zmiennej, którą chcesz ukryć na poziomie klasy, można cień go poprzez dziedziczenie przez redeclaring ją za pomocą [cieni](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w klasie pochodnej.  
  
## <a name="two-ways-to-hide-a-variable"></a>Ukrywanie zmiennej na dwa sposoby  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Aby ukryć zmiennej przez przesłanianie go przy użyciu zakresu  
  
1.  Określić region Definiowanie zmiennej, którą chcesz ukryć i określ Podobszar, w której ma zostać przedefiniować go za pomocą zmiennej.  
  
    |Region zmiennej|Dozwolone Podobszar dla ponownego definiowania go|  
    |-----------------------|-------------------------------------------|  
    |Moduł|Klasa modułu|  
    |Class|Podklasa klasy<br /><br /> Procedury w klasie|  
  
     Nie można przedefiniować procedury zmiennej w bloku, w ramach tej procedury, na przykład w `If`... `End If` konstrukcji lub `For` pętli.  
  
2.  Utwórz regionu, jeśli jeszcze nie istnieje.  
  
3.  W regionie zapisu [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) zadeklarowanie zmiennej przesłaniania.  
  
     Gdy kod wewnątrz regionu odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej przesłaniania.  
  
     W poniższym przykładzie pokazano cieniowania przez zakres, a także odwołania omija cieniowania.  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     Poprzedni przykład deklaruje zmienną `num` zarówno na poziomie modułu, jak i na poziomie procedury (w ramach procedury `show`). Zmienna lokalna `num` zasłania zmiennej poziom modułu `num` w ramach `show`, więc zmiennej lokalnej jest równa 2. Jednak nie ma żadnych zmienną lokalną, aby w tle `num` w `useModuleLevelNum` procedury. W związku z tym `useModuleLevelNum` ustawia wartość zmiennej modułu poziomu 1.  
  
     `MsgBox` Wywołać wewnątrz `show` pomija przesłaniania mechanizm kwalifikując `num` z nazwą modułu. W związku z tym Wyświetla zmiennej na poziomie modułu, zamiast zmiennej lokalnej.  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Aby ukryć zmiennej przez przesłanianie go poprzez dziedziczenie  
  
1.  Upewnij się, że zmiennej, którą chcesz ukryć jest zadeklarowana w klasie i na poziomie klasy (poza dowolnej procedury). W przeciwnym razie nie można go cienia poprzez dziedziczenie.  
  
2.  Zdefiniuj klasę pochodną klasy zmiennej, jeśli już nie istnieje.  
  
3.  W klasie pochodnej zapisu `Dim` instrukcji deklarowania zmiennej. Obejmują [cieni](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w deklaracji.  
  
     Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej.  
  
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
 Przesłanianie wprowadza więcej niż jedna wersja zmienna o takiej samej nazwie. Instrukcja kodu odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołania zależy od czynników, takich jak lokalizacja instrukcja kodu i występowania ciągu kwalifikującym się. Może to zwiększyć ryzyko odnoszące się do niezamierzonych wersję zasłonięte zmiennej. Możesz obniżyć ryzyko kwalifikując pełni wszystkie odwołania do zmiennej zasłonięte.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Różnice między przesłanianiem i zastępowaniem](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Instrukcje: Ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Instrukcje: Dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
