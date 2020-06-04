---
title: 'Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika'
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
ms.openlocfilehash: c1f4c2fbf339358be77e76468b1db94616bf04a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357235"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)

Można ukryć zmienną przez jej *obserwowanie* , czyli przez ponowne zdefiniowanie jej przy użyciu zmiennej o tej samej nazwie. Można zaobserwować zmienną, która ma być ukryta na dwa sposoby:

- **Przesłanianie przez zakres.** Można obsłużyć ten zakres przez Zadeklaruj go wewnątrz podregionu regionu zawierającego zmienną, którą chcesz ukryć.

- **Przesłanianie przez dziedziczenie.** Jeśli zmienna, która ma być ukryta, jest zdefiniowana na poziomie klasy, można ją utworzyć w tle przez dziedziczenie, ponownie deklarując ją za pomocą słowa kluczowego [Shadows](../../../language-reference/modifiers/shadows.md) w klasie pochodnej.

## <a name="two-ways-to-hide-a-variable"></a>Dwa sposoby ukrywania zmiennej

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Aby ukryć zmienną przez Zacień jej w zakresie

1. Określ region definiujący zmienną, która ma być ukryta, i określ podregion, w którym ma zostać zmieniona jego zmiana.

    |Region zmiennej|Dozwolony podregion na potrzeby jego ponownego definiowania|
    |-----------------------|-------------------------------------------|
    |Moduł|Klasa w module|
    |Klasa|Podklasa w klasie<br /><br /> Procedura w klasie|

    Nie można ponownie zdefiniować zmiennej procedury w bloku w ramach tej procedury, na przykład w `If` pętli... `End If` konstrukcja lub `For` pętla.

2. Utwórz podregion, jeśli jeszcze nie istnieje.

3. W obszarze podregionu Napisz [instrukcję Dim](../../../language-reference/statements/dim-statement.md) deklarującą zmienną cieniowania.

    Gdy kod wewnątrz podregionu odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej przesłaniania.

    Poniższy przykład ilustruje przesłanianie przez zakres, a także odwołanie, które pomija przesłanianie.

    ```vb
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

    Powyższy przykład deklaruje zmienną `num` zarówno na poziomie modułu, jak i na poziomie procedury (w procedurze `show` ). Zmienna lokalna `num` zasłania zmienną na poziomie modułu `num` w `show` , więc zmienna lokalna jest ustawiona na 2. Nie istnieje jednak żadna zmienna lokalna do przesłania `num` w `useModuleLevelNum` procedurze. W związku z tym `useModuleLevelNum` ustawia wartość zmiennej poziomu modułu na 1.

    `MsgBox`Wywołanie wewnątrz `show` pomija mechanizm przesłaniania przez zakwalifikowanie `num` się do nazwy modułu. W związku z tym wyświetla zmienną na poziomie modułu zamiast zmiennej lokalnej.

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Aby ukryć zmienną przez przesłonięcie jej przez dziedziczenie

1. Upewnij się, że zmienna, która ma być ukryta, jest zadeklarowana w klasie i na poziomie klasy (poza jakąkolwiek procedurą). W przeciwnym razie nie można zasłaniać go przez dziedziczenie.

2. Zdefiniuj klasę pochodną klasy, jeśli jeszcze nie istnieje.

3. W klasie pochodnej Napisz `Dim` instrukcję deklarującą zmienną. Uwzględnij słowo kluczowe [Shadows](../../../language-reference/modifiers/shadows.md) w deklaracji.

    Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej.

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

Przesłanianie zawiera więcej niż jedną wersję zmiennej o tej samej nazwie. Gdy instrukcja Code odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołanie, zależy od czynników, takich jak lokalizacja instrukcji Code i obecność ciągu uprawniającego. Może to zwiększyć ryzyko związane z odwołującymi się do niezamierzonej wersji zmiennej cieniowej. To ryzyko można obniżyć, w pełni kwalifikując wszystkie odwołania do zmiennej w tle.

## <a name="see-also"></a>Zobacz też

- [Odwołania do elementów zadeklarowanych](references-to-declared-elements.md)
- [Przesłanianie w Visual Basic](shadowing.md)
- [Różnice między przesłanianiem i zastępowaniem](differences-between-shadowing-and-overriding.md)
- [Instrukcje: ukrywanie dziedziczonej zmiennej](how-to-hide-an-inherited-variable.md)
- [Instrukcje: dostęp do zmiennej ukrytej przez klasę pochodną](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Przesłonięcia](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase i MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../objects-and-classes/inheritance-basics.md)
