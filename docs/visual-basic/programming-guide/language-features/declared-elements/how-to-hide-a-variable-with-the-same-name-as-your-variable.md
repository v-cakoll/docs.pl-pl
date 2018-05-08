---
title: 'Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)'
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
ms.openlocfilehash: a7ebc4eb44592800decd5ef943750f0cd845afb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)
Można ukryć zmiennej przez *przesłanianie* go, czyli przy ponownym zdefiniowaniem go za pomocą zmiennych o takiej samej nazwie. Można obserwować zmiennej, którą chcesz ukryć na dwa sposoby:  
  
-   **Cieniowania przez zakres.** Można obserwować go za pomocą zakresu przez ponownego deklarowania go wewnątrz regionu, regionu zawierający zmiennej, którą chcesz ukryć.  
  
-   **Przesłanianie przez dziedziczenie.** Jeśli chcesz ukryć zmienna jest zdefiniowana na poziomie klasy, można obserwować go poprzez dziedziczenie przez ponownego deklarowania go przy użyciu [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w klasie pochodnej.  
  
## <a name="two-ways-to-hide-a-variable"></a>Dwa sposoby ukrywanie zmiennej  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Aby ukryć przez przesłanianie go za pomocą zakresu zmiennej  
  
1.  Określanie obszaru Definiowanie zmiennej, którą chcesz ukryć i określ dla regionu, w którym można zdefiniować ją ponownie do zmiennej.  
  
    |Region zmiennej|Podregion dopuszczalny dla ponownym zdefiniowaniem go|  
    |-----------------------|-------------------------------------------|  
    |Moduł|Klasa modułu|  
    |Class|Podklasa klasy<br /><br /> Procedury w ramach klasy|  
  
     Nie można zmienić procedury zmiennej w bloku, w ramach tej procedury, na przykład w `If`... `End If` konstrukcji lub `For` pętli.  
  
2.  Jeśli jeszcze nie istnieje, należy utworzyć regionu.  
  
3.  W obrębie regionu, zapisać [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarowanie zmiennej przesłaniania.  
  
     Gdy kodu wewnątrz regionu odwołuje się do nazwy zmiennej, kompilator usuwa odwołanie do zmiennej przesłaniania.  
  
     Poniższy przykład przedstawia cieniowania przez zakres, a także omija przesłanianie odwołanie.  
  
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
  
     Powyższy przykład deklaruje zmienną `num` zarówno na poziomie modułu, jak i na poziomie procedury (w procedurze `show`). Zmienna lokalna `num` zasłania zmiennej poziom modułu `num` w `show`, więc zmiennej lokalnej jest równa 2. Jednak nie ma żadnych zmiennej lokalnej na tle `num` w `useModuleLevelNum` procedury. W związku z tym `useModuleLevelNum` ustawia wartość zmiennej modułu poziomu 1.  
  
     `MsgBox` Wywołać wewnątrz `show` pomija przesłaniania mechanizm przez kwalifikowanie `num` z nazwą modułu. W związku z tym Wyświetla zmiennej poziom modułu zamiast zmiennej lokalnej.  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Aby ukryć zmiennej przez przesłanianie go poprzez dziedziczenie  
  
1.  Upewnij się, że zmiennej, którą chcesz ukryć jest zadeklarowana w klasie i na poziomie klasy (poza dowolnej procedury). W przeciwnym razie nie można go cienia przez dziedziczenie.  
  
2.  Zdefiniuj klasę pochodzącą od klasy zmiennej, jeśli już nie istnieje.  
  
3.  W klasie pochodnej zapisu `Dim` instrukcji deklarowanie zmiennej użytkownika. Obejmują [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w deklaracji.  
  
     Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator usuwa odwołanie do zmiennej użytkownika.  
  
     Poniższy przykład przedstawia cieniowania przez dziedziczenie. Powoduje to dodanie dwa odwołania, który uzyskuje dostęp do zmiennej przesłaniania i jedną omija cieniowania.  
  
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
  
     Powyższy przykład deklaruje zmienną `shadowString` w klasie podstawowej i przesłania go w klasie pochodnej. Procedura `showStrings` w klasie pochodnej Wyświetla wersję przesłaniania ciągu gdy nazwa `shadowString` nie jest kwalifikowana. Następnie wyświetla zasłonięty wersji podczas `shadowString` jest kwalifikowana z `MyBase` — słowo kluczowe.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Przesłanianie wprowadza więcej niż jedną wersję zmienna o takiej samej nazwie. Gdy instrukcję kodu odwołuje się do nazwy zmiennej, wersji, do którego kompilator usuwa odwołanie zależy od czynników, takich jak lokalizacja instrukcji kodu oraz występowania ciągu kwalifikujących. Może to zwiększyć ryzyko wystąpienia odwołujących się do wersji niezamierzone zmiennej zasłonięty. Można zmniejszyć ryzyko przez pełni kwalifikowanie wszystkie odwołania do zmiennej zasłonięty.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Różnice między przesłanianiem i zastępowaniem](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Instrukcje: ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Instrukcje: dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
