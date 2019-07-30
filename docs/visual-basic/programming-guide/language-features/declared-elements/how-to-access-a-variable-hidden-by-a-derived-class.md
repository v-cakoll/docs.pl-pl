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
ms.openlocfilehash: 68f92142cdc435ebd82101eea83035e1d09dcf25
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630015"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Instrukcje: Dostęp do zmiennej ukrytej przez klasę pochodną (Visual Basic)

Gdy kod w klasie pochodnej uzyskuje dostęp do zmiennej, kompilator zwykle rozwiązuje odwołanie do najbliższej dostępnej wersji, czyli dostępnej wersji, którą można wykonać z tyłu od klasy dostępu. Jeśli zmienna jest zdefiniowana w klasie pochodnej, kod zwykle uzyskuje dostęp do tej definicji.

Jeśli zmienna klasy pochodnej zasłania zmienną w klasie bazowej, ukrywa wersję klasy bazowej. Można jednak uzyskać dostęp do zmiennej klasy bazowej, kwalifikując ją za pomocą `MyBase` słowa kluczowego.

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Aby uzyskać dostęp do zmiennej klasy bazowej ukrytej przez klasę pochodną

- W instrukcji wyrażenia lub przypisania poprzedź nazwę `MyBase` zmiennej słowem kluczowym i kropką (`.`).

    Kompilator rozpoznaje odwołanie do wersji klasy bazowej zmiennej.

    Poniższy przykład ilustruje przesłanianie przez dziedziczenie. Tworzy dwa odwołania, które uzyskują dostęp do zmiennej przesłaniania i jeden, który pomija przesłanianie.

    ```vb
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

    Poprzedni przykład deklaruje zmienną `shadowString` w klasie bazowej i zasłania ją w klasie pochodnej. Procedura `showStrings` w klasie pochodnej wyświetla wersję przesłaniania ciągu, gdy nazwa `shadowString` nie jest kwalifikowana. Następnie wyświetla wersję w tle, gdy `shadowString` jest kwalifikowana `MyBase` za pomocą słowa kluczowego.

## <a name="robust-programming"></a>Niezawodne programowanie

Aby zmniejszyć ryzyko związane z odwołującymi się do niezamierzonej wersji zmiennej w tle, można w pełni zakwalifikować wszystkie odwołania do zmiennej cieniowej. Przesłanianie zawiera więcej niż jedną wersję zmiennej o tej samej nazwie. Gdy instrukcja Code odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołanie, zależy od czynników, takich jak lokalizacja instrukcji Code i obecność ciągu uprawniającego. Może to zwiększyć ryzyko odwołania się do niewłaściwej wersji zmiennej.

## <a name="see-also"></a>Zobacz także

- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Obserwowanie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Różnice między przesłanianiem i zastępowaniem](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Instrukcje: Ukryj zmienną o takiej samej nazwie jak zmienna](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Instrukcje: Ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
