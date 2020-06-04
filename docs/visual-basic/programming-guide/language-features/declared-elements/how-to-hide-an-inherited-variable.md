---
title: 'Porady: ukrywanie dziedziczonej zmiennej'
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
ms.openlocfilehash: f49bba0497f9f4f2774b01284c815bba9aaed119
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357273"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Porady: ukrywanie dziedziczonej zmiennej (Visual Basic)

Klasa pochodna dziedziczy wszystkie definicje swojej klasy podstawowej. Jeśli chcesz zdefiniować zmienną przy użyciu takiej samej nazwy, jak element klasy bazowej, można ukryć lub *zaobserwować*ten element klasy bazowej podczas definiowania zmiennej w klasie pochodnej. W takim przypadku kod w klasie pochodnej uzyskuje dostęp do zmiennej, chyba że jawnie pomija mechanizm przesłaniania.

Kolejną przyczyną może być ukrycie dziedziczonej zmiennej jest ochrona przed poprawką klasy bazowej. Klasa bazowa może ulec zmianie, która zmienia element, który jest dziedziczony. W takim przypadku `Shadows` modyfikator wymusza odwołania z klasy pochodnej, aby można było je rozpoznać do zmiennej, a nie do elementu klasy bazowej.

## <a name="to-hide-an-inherited-variable"></a>Aby ukryć dziedziczoną zmienną

1. Upewnij się, że zmienna, która ma być ukryta, jest zadeklarowana na poziomie klasy (poza jakąkolwiek procedurą). W przeciwnym razie nie trzeba go ukrywać.
  
2. Wewnątrz klasy pochodnej Napisz [instrukcję Dim](../../../language-reference/statements/dim-statement.md) deklarującą zmienną. Użyj takiej samej nazwy, jak w przypadku zmiennej dziedziczonej.

3. Uwzględnij słowo kluczowe [Shadows](../../../language-reference/modifiers/shadows.md) w deklaracji.

     Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej.

     Poniższy przykład ilustruje cieniowanie zmiennej dziedziczonej:
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     Poprzedni przykład deklaruje zmienną `shadowString` w klasie bazowej i zasłania ją w klasie pochodnej. Procedura `ShowStrings` w klasie pochodnej wyświetla wersję przesłaniania ciągu, gdy nazwa `shadowString` nie jest kwalifikowana. Następnie wyświetla wersję w tle, gdy `shadowString` jest kwalifikowana za pomocą `MyBase` słowa kluczowego.  
  
## <a name="robust-programming"></a>Niezawodne programowanie

Przesłanianie zawiera więcej niż jedną wersję zmiennej o tej samej nazwie. Gdy instrukcja Code odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołanie, zależy od czynników, takich jak lokalizacja instrukcji Code i obecność ciągu uprawniającego. Może to zwiększyć ryzyko związane z odwołującymi się do niezamierzonej wersji zmiennej cieniowej. To ryzyko można obniżyć, w pełni kwalifikując wszystkie odwołania do zmiennej w tle.

## <a name="see-also"></a>Zobacz też

- [Odwołania do elementów zadeklarowanych](references-to-declared-elements.md)
- [Przesłanianie w Visual Basic](shadowing.md)
- [Różnice między przesłanianiem i zastępowaniem](differences-between-shadowing-and-overriding.md)
- [Instrukcje: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Instrukcje: dostęp do zmiennej ukrytej przez klasę pochodną](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Przesłonięcia](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase i MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../objects-and-classes/inheritance-basics.md)
