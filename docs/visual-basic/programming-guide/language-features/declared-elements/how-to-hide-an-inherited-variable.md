---
title: 'Porady: ukrywanie dziedziczonej zmiennej (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d2059da873f8b9ec9ea51191139c652a9e01d92b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Porady: ukrywanie dziedziczonej zmiennej (Visual Basic)
Klasa pochodna dziedziczy wszystkie definicje klasy podstawowej. Jeśli chcesz zdefiniować zmienną przy użyciu takiej samej nazwie jako element klasy podstawowej, można ukryć, lub *tle*, podczas definiowania do zmiennej w klasie pochodnej elementu klasy podstawowej. Jeśli to zrobisz, kod w klasie pochodnej uzyskuje dostęp do zmiennej użytkownika, chyba że jawnie pomija mechanizmu przesłaniania.  
  
 Kolejny powód, czy może chcesz ukrywanie dziedziczonej zmiennej jest ochrona przed poprawki klasy podstawowej. Klasa podstawowa może podlegają zmianom zmieniającą elementu, które są dziedziczone. W takim przypadku `Shadows` modyfikator wymusza odwołań z klasy pochodnej w celu można rozwiązać do zmiennej, a nie do elementu klasy podstawowej.  
  
### <a name="to-hide-an-inherited-variable"></a>Aby ukrywanie dziedziczonej zmiennej  
  
1.  Upewnij się, że zmiennej, którą chcesz ukryć jest zadeklarowane na poziomie klasy (poza dowolnej procedury). W przeciwnym razie nie należy je ukryć.  
  
2.  W klasie pochodnej zapisu [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarowanie zmiennej użytkownika. Użyj takiej samej nazwie jak dziedziczonej zmiennej.  
  
3.  Obejmują [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w deklaracji.  
  
     Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator usuwa odwołanie do zmiennej użytkownika.  
  
     Poniższy przykład przedstawia przesłanianie dziedziczonej zmiennej.  
  
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
 [Różnice pomiędzy przesłanianiem i zastępowaniem](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Porady: dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Zastąpienia](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
