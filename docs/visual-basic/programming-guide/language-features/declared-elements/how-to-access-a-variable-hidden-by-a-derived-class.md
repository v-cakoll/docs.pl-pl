---
title: "Porady: dostęp do zmiennej ukrytej przez klasę pochodną (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f94e45fcb0a26b0d59789e101c37aceba219250
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Porady: dostęp do zmiennej ukrytej przez klasę pochodną (Visual Basic)
Gdy kod w klasie pochodnej uzyskuje dostęp do zmiennej, kompilator zwykle usuwa odwołania do najbliższej wersji dostępny, oznacza to, że dostępna wersja najmniejszej derivational kroki z poprzednimi wersjami z uzyskiwaniem dostępu do klasy. Jeśli zmienna jest zdefiniowana w klasie pochodnej, kod zwykle uzyskuje dostęp do tej definicji.  
  
 Jeśli zmienna klasy pochodnej cieni zmienna w klasie podstawowej, ukrywa wersja klasy podstawowej. Jednak mają dostęp do zmiennej klasy podstawowej przez kwalifikującego się za pomocą `MyBase` — słowo kluczowe.  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Dostęp do zmiennej klasy podstawowej ukryty przez klasę pochodną  
  
-   Wyrażenia lub instrukcji przypisania, poprzedź nazwę zmiennej o `MyBase` — słowo kluczowe i kropkę (`.`).  
  
     Kompilator usuwa odwołanie do klasy podstawowej wersji zmiennej.  
  
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
 Aby zmniejszyć ryzyko odwołujących się do wersji niezamierzone zasłonięty zmiennej, mogą pełnej kwalifikacji wszystkie odwołania do zmiennej zasłonięty. Przesłanianie wprowadza więcej niż jedną wersję zmienna o takiej samej nazwie. Gdy instrukcję kodu odwołuje się do nazwy zmiennej, wersji, do którego kompilator usuwa odwołanie zależy od czynników, takich jak lokalizacja instrukcji kodu oraz występowania ciągu kwalifikujących. Może to zwiększyć ryzyko wystąpienia odwołujących się do niewłaściwej wersji zmiennej.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Różnice pomiędzy przesłanianiem i zastępowaniem](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Porady: ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Zastąpienia](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
