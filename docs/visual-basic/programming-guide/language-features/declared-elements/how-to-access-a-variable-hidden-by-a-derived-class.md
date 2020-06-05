---
title: 'Porady: dostęp do zmiennej ukrytej przez klasę pochodną'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: c5ff802a0f6e081acd00d7cdfab4a8296b4daad9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392860"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Porady: dostęp do zmiennej ukrytej przez klasę pochodną (Visual Basic)

Gdy kod w klasie pochodnej uzyskuje dostęp do zmiennej, kompilator zwykle rozwiązuje odwołanie do najbliższej dostępnej wersji, czyli dostępnej wersji, którą można wykonać z tyłu od klasy dostępu. Jeśli zmienna jest zdefiniowana w klasie pochodnej, kod zwykle uzyskuje dostęp do tej definicji.

Jeśli zmienna klasy pochodnej zasłania zmienną w klasie bazowej, ukrywa wersję klasy bazowej. Można jednak uzyskać dostęp do zmiennej klasy bazowej, kwalifikując ją za pomocą `MyBase` słowa kluczowego.

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Aby uzyskać dostęp do zmiennej klasy bazowej ukrytej przez klasę pochodną

- W instrukcji wyrażenia lub przypisania poprzedź nazwę zmiennej `MyBase` słowem kluczowym i kropką ( `.` ).

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

    Poprzedni przykład deklaruje zmienną `shadowString` w klasie bazowej i zasłania ją w klasie pochodnej. Procedura `showStrings` w klasie pochodnej wyświetla wersję przesłaniania ciągu, gdy nazwa `shadowString` nie jest kwalifikowana. Następnie wyświetla wersję w tle, gdy `shadowString` jest kwalifikowana za pomocą `MyBase` słowa kluczowego.

## <a name="robust-programming"></a>Niezawodne programowanie

Aby zmniejszyć ryzyko związane z odwołującymi się do niezamierzonej wersji zmiennej w tle, można w pełni zakwalifikować wszystkie odwołania do zmiennej cieniowej. Przesłanianie zawiera więcej niż jedną wersję zmiennej o tej samej nazwie. Gdy instrukcja Code odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołanie, zależy od czynników, takich jak lokalizacja instrukcji Code i obecność ciągu uprawniającego. Może to zwiększyć ryzyko odwołania się do niewłaściwej wersji zmiennej.

## <a name="see-also"></a>Zobacz też

- [Odwołania do elementów zadeklarowanych](references-to-declared-elements.md)
- [Przesłanianie w Visual Basic](shadowing.md)
- [Różnice między przesłanianiem i zastępowaniem](differences-between-shadowing-and-overriding.md)
- [Instrukcje: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Instrukcje: ukrywanie dziedziczonej zmiennej](how-to-hide-an-inherited-variable.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [Przesłonięcia](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase i MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../objects-and-classes/inheritance-basics.md)
