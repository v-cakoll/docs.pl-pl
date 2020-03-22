---
title: Zasłanianie
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 20a33478f622fca6d3183772f53dcb3e72f79409
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266888"
---
# <a name="shadowing-in-visual-basic"></a>Przesłanianie w Visual Basic
Gdy dwa elementy programowania mają tę samą nazwę, jeden z nich może ukryć lub *cień,* drugi. W takiej sytuacji element cieniowany nie jest dostępny do odwołania; Zamiast tego gdy kod używa nazwy elementu, kompilator języka Visual Basic rozwiązuje go do elementu cieniowania.  
  
## <a name="purpose"></a>Przeznaczenie  
 Głównym celem cieniowania jest ochrona definicji członków klasy. Klasa podstawowa może zostać poddana zmianom, które tworzą element o takiej samej nazwie, jak ta, która została już zdefiniowana. W takim przypadku `Shadows` modyfikator wymusza odwołania za pośrednictwem klasy, które mają zostać rozpoznane do zdefiniowanego elementu członkowskiego, a nie do nowego elementu klasy podstawowej.  
  
## <a name="types-of-shadowing"></a>Rodzaje cieniowania  
 Element może cień inny element na dwa różne sposoby. Element cieniowania można zadeklarować wewnątrz podregionu regionu zawierającego element cieniowany, w którym to przypadku cieniowanie odbywa się *za pośrednictwem zakresu*. Lub klasy pochodnej można przedefiniować członka klasy podstawowej, w którym to przypadku cieniowanie odbywa się *za pośrednictwem dziedziczenia*.  
  
### <a name="shadowing-through-scope"></a>Cieniowanie przez zakres  
 Jest możliwe dla programowania elementów w tym samym module, klasy lub struktury, aby mieć taką samą nazwę, ale inny zakres. Gdy dwa elementy są zadeklarowane w ten sposób, a kod odwołuje się do nazwy, którą współużytkują, element o węższym zakresie cieniuje inny element (zakres bloku jest najwęższy).  
  
 Na przykład moduł może `Public` zdefiniować `temp`zmienną o nazwie , a procedura `temp`w module może zadeklarować zmienną lokalną również o nazwie . Odwołania do `temp` z wewnątrz procedury dostęp do zmiennej lokalnej, podczas gdy odwołania do spoza procedury dostęp do `temp` zmiennej. `Public` W takim przypadku zmienna `temp` procedury `temp`cieniuje zmienną modułu .  
  
 Na poniższej ilustracji przedstawiono `temp`dwie zmienne o nazwie . Zmienna `temp` lokalna cieniuje `temp` zmienną elementu członkowskiego, `p`gdy uzyskuje się do niej dostęp z poziomu własnej procedury . Jednak `MyClass` słowo kluczowe omija cieniowanie i uzyskuje dostęp do zmiennej elementu członkowskiego.  
  
 ![Grafika przedstawiająca cieniowanie przez zakres.](./media/shadowing/shadow-scope-diagram.gif)
  
 Na przykład cieniowania przez zakres, zobacz [Jak: Ukryć zmienną o takiej samej nazwie jak zmienna](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Cieniowanie przez dziedziczenie  
 Jeśli klasa pochodna ponownie definiuje element programowania dziedziczony z klasy podstawowej, element ponownego definiowania cienie oryginalnego elementu. Można cieniować dowolny typ zadeklarowanego elementu lub zestaw przeciążonych elementów z dowolnym innym typem. Na przykład `Integer` zmienna może `Function` cieniować procedurę. Jeśli procedura jest cieniowana z inną procedurą, można użyć innej listy parametrów i innego typu zwracanego.  
  
 Na poniższej ilustracji `b` przedstawiono klasę `d` podstawową `b`i klasę pochodną, która dziedziczy po . Klasa podstawowa definiuje procedurę `proc`o nazwie , a klasa pochodna cieniuje ją inną procedurą o tej samej nazwie. Pierwsza `Call` instrukcja uzyskuje dostęp `proc` do cieniowania w klasie pochodnej. Jednak `MyBase` słowo kluczowe omija cieniowanie i uzyskuje dostęp do procedury cieniowanej w klasie podstawowej.  
  
 ![Graficzny diagram cieniowania przez dziedziczenie](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Na przykład cieniowania przez dziedziczenie, zobacz [Jak: Ukryć zmienną o takiej samej nazwie jak zmienna](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) i [Jak: Ukryć dziedziczoną zmienną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Poziom cieniowania i dostępu  
 Element cieniowania nie zawsze jest dostępny z kodu przy użyciu klasy pochodnej. Na przykład może być `Private`zadeklarowany . W takim przypadku cieniowanie jest pokonany i kompilator rozwiązuje wszelkie odwołania do tego samego elementu, który miałby, gdyby nie było cieniowania. Ten element jest dostępny element najmniej pochodnych kroków wstecz od klasy cieniowania. Jeśli element cieniowany jest procedurą, rozdzielczość jest do najbliższej dostępnej wersji o tej samej nazwie, liście parametrów i typu zwracanego.  
  
 W poniższym przykładzie przedstawiono hierarchię dziedziczenia trzech klas. Każda klasa definiuje `Sub` `display`procedurę , a każda klasa `display` pochodna cieniuje procedurę w swojej klasie podstawowej.  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 W poprzednim przykładzie klasy `secondClass` pochodnej `display` cienie `Private` z procedurą. Gdy `callDisplay` moduł `display` `secondClass`wywołuje w , `secondClass` kod wywołujący jest `display` na zewnątrz i dlatego nie można uzyskać dostępu do procedury prywatnej. Shadowing jest pokonany, a kompilator rozwiązuje odwołanie `display` do procedury klasy podstawowej.  
  
 Jednak dalsze pochodne `thirdClass` klasy `display` deklaruje `Public`jako , `callDisplay` więc kod w można uzyskać do niego dostęp.  
  
## <a name="shadowing-and-overriding"></a>Cieniowanie i zastępowanie  
 Nie należy mylić cieniowania z nadpisaniem. Oba są używane, gdy klasa pochodna dziedziczy z klasy podstawowej i oba ponownie zdefiniować jeden zadeklarowany element z innym. Ale istnieją znaczne różnice między nimi. Dla porównania zobacz [Różnice między cieniowania i zastępowania](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Cieniowanie i przeciążanie  
 Jeśli cień tego samego elementu klasy podstawowej z więcej niż jeden element w klasie pochodnej, elementy cieniowania stają się przeciążonymi wersjami tego elementu. Aby uzyskać więcej informacji, zobacz [Przeciążanie procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Uzyskiwanie dostępu do elementu cienia  
 Podczas uzyskiwania dostępu do elementu z klasy pochodnej, zwykle można to zrobić za pośrednictwem bieżącego `Me` wystąpienia tej klasy pochodnej, kwalifikując nazwę elementu ze słowem kluczowym. Jeśli klasa pochodna cienie element w klasie podstawowej, można uzyskać dostęp do `MyBase` elementu klasy podstawowej, kwalifikując go za pomocą słowa kluczowego.  
  
 Na przykład uzyskiwania dostępu do elementu cieniowanego zobacz [Jak: Dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Deklaracja zmiennej obiektu  
 Sposób tworzenia zmiennej obiektu może również mieć wpływ na to, czy klasa pochodna uzyskuje dostęp do elementu cieniowania lub elementu cieniowanego. Poniższy przykład tworzy dwa obiekty z klasy pochodnej, ale jeden obiekt jest zadeklarowany jako klasa podstawowa, a drugi jako klasa pochodna.  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 W poprzednim przykładzie zmienna `basObj` jest zadeklarowana jako klasa podstawowa. Przypisanie `dervCls` do niego obiektu stanowi konwersję rozszerzającą i dlatego jest prawidłowe. Jednak klasa podstawowa nie może uzyskać dostępu `z` do wersji cieniowania zmiennej w `basObj.z` klasie pochodnej, więc kompilator rozpoznaje oryginalną wartość klasy podstawowej.  
  
## <a name="see-also"></a>Zobacz też

- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
