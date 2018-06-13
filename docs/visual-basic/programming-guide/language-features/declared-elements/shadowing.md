---
title: Przesłanianie w Visual Basic
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
ms.openlocfilehash: fde6259b67a8d963ed8c30b87c94029fb2658664
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656074"
---
# <a name="shadowing-in-visual-basic"></a>Przesłanianie w Visual Basic
Gdy dwa elementy programowania o tej samej nazwie, jeden z nich można ukryć, lub *tle*, jeden z nich. W takiej sytuacji zasłonięty element nie jest dostępna dla odwołania; Zamiast tego po kodzie używa nazwy elementu, kompilator Visual Basic rozpoznaje ją do przesłaniania elementu.  
  
## <a name="purpose"></a>Cel  
 Głównym celem przesłanianie ma chronić definicji członkowie klasy. Klasa podstawowa mogą być zmiany, która tworzy element o takiej samej nazwie jako jeden, który został już zdefiniowany. W takim przypadku `Shadows` wymusza modyfikator odwołuje się do klasy mają zostać rozwiązane do elementu członkowskiego zdefiniowane, a nie nowy element klasy podstawowej.  
  
## <a name="types-of-shadowing"></a>Typy cieniowania  
 Element można obserwować inny element na dwa różne sposoby. Element przesłaniania mogą być deklarowane w regionu, regionu zawierający element zasłonięty, w którym odbywa się przypadku przesłanianie *przez zakres*. Lub Klasa pochodna ponownie zdefiniować elementu członkowskiego klasy podstawowej, w którym odbywa się przypadku przesłanianie *poprzez dziedziczenie*.  
  
### <a name="shadowing-through-scope"></a>Cieniowania przez zakres  
 Istnieje możliwość programowania elementów modułu, klasy lub struktury, poproś go o tej samej nazwie, ale inny zakres. Gdy dwa elementy są zadeklarowane w ten sposób i kod odwołuje się do nazwy mają, element z zakresem mniejszą niż zasłania innego elementu (zakresie bloku jest najwęższym).  
  
 Na przykład można zdefiniować moduł `Public` zmiennej o nazwie `temp`, i procedury w module można zadeklarować zmiennej lokalnej o nazwie `temp`. Odwołuje się do `temp` z poziomu procedury uzyskują dostęp do zmiennej lokalnej podczas odwołania do `temp` z poza dostępu procedury `Public` zmiennej. W tym przypadku zmiennej procedury `temp` zasłania zmiennej modułu `temp`.  
  
 Na poniższej ilustracji przedstawiono dwie zmienne, o nazwie `temp`. Zmienna lokalna `temp` zasłania zmiennej członkowskiej `temp` podczas uzyskiwania dostępu do z, w ramach własnej procedury `p`. Jednak `MyClass` — słowo kluczowe pomija przesłanianie i uzyskuje dostęp do zmiennej członka.  
  
 ![Graficzny diagram cieniowania przez zakres](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")  
Cieniowania przez zakres  
  
 Na przykład cieniowania przez zakres zobacz [porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej Your](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Przesłanianie poprzez dziedziczenie  
 Jeśli klasa pochodna ponownie definiuje elementu programistycznego dziedziczona z klasy podstawowej, redefining element zasłania oryginalnego elementu. Można obserwować dowolnego typu zadeklarowany element lub zbiór przeciążone elementy z żadnym innym typem. Na przykład `Integer` zmiennej można obserwować `Function` procedury. Jeśli w tle procedury z innej procedury można użyć inną listą parametrów i innym typie zwracanym.  
  
 Na poniższej ilustracji przedstawiono klasę podstawową `b` i Klasa pochodna `d` dziedziczący po `b`. Klasa podstawowa definiuje procedurę o nazwie `proc`, a klasa pochodna zasłania go z innej procedury o takiej samej nazwie. Pierwszy `Call` instrukcji uzyskuje dostęp do cieniowania `proc` w klasie pochodnej. Jednak `MyBase` — słowo kluczowe pomija przesłanianie i uzyskuje dostęp do zasłonięty procedury w klasie podstawowej.  
  
 ![Diagram graficzny cieniowania przez dziedziczenie](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")  
Przesłanianie poprzez dziedziczenie  
  
 Na przykład cieniowania przez dziedziczenie, zobacz [porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej Your](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) i [porady: ukrywanie odziedziczonych zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Przesłanianie i poziom dostępu  
 Element przesłaniania nie jest zawsze dostępne z kodu przy użyciu klasy pochodnej. Na przykład może być zadeklarowana `Private`. W takim przypadku przesłanianie jest bezcelowe i kompilator usuwa wszelkie odwołania do tego samego elementu miałoby Jeśli nie był nie przesłanianie. Ten element jest dostępny element najmniejszą liczbę derivational kroki wstecz od klasy przesłaniania. Jeśli element zasłonięty jest procedurą, rozwiązanie jest najbliższy dostępny wersji o takiej samej nazwie, lista parametrów i typ zwracany.  
  
 Poniższy przykład przedstawia hierarchię dziedziczenia trzech klas. Każda klasa definiuje `Sub` procedury `display`, i zostały opracowane na każdej klasy shadows `display` procedury w swojej klasie podstawowej.  
  
```  
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
  
 W powyższym przykładzie Klasa pochodna `secondClass` shadows `display` z `Private` procedury. Gdy moduł `callDisplay` wywołania `display` w `secondClass`, kod wywołujący znajduje się poza `secondClass` i dlatego nie można uzyskać dostępu prywatnego `display` procedury. Przesłanianie jest bezcelowe i kompilator usuwa odwołanie do klasy podstawowej `display` procedury.  
  
 Jednak dalszy pochodnej klasy `thirdClass` deklaruje `display` jako `Public`, więc kod w `callDisplay` do niego dostęp.  
  
## <a name="shadowing-and-overriding"></a>Przesłanianiem i zastępowaniem  
 Nie należy mylić przesłanianie z zastępowanie. Zarówno są używane, gdy klasa pochodna dziedziczy z klasy podstawowej, a jednocześnie ponownie definiować jeden element zadeklarowany z innym. Ale są istotne różnice między nimi. Porównanie, zobacz [różnice pomiędzy przesłanianiem i przesłanianie](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Przesłanianie i przeciążeniu  
 Jeśli cień tego samego elementu klasy podstawowej z więcej niż jeden element w klasie pochodnej przesłaniania elementy stają się zastąpionej wersji tego elementu. Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Uzyskiwanie dostępu do elementu zasłonięty  
 Gdy uzyskujesz dostęp do elementu z klasy pochodnej, należy zwykle to zrobić przez bieżące wystąpienie tej klasy pochodnej, kwalifikujących się z nazwy elementu `Me` — słowo kluczowe. Klasy pochodne zasłania element w klasie podstawowej, można przejść do elementu klasy podstawowej przez kwalifikującego się za pomocą `MyBase` — słowo kluczowe.  
  
 Na przykład uzyskiwania dostępu do elementu zasłonięty zobacz [porady: dostęp do zmiennej ukrytej przez klasę pochodnych](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Deklaracja zmiennej obiektu  
 Jak utworzyć zmienną obiektu może wpłynąć na czy klasy pochodnej uzyskuje dostęp do elementu przesłaniania lub element zasłonięty. Poniższy przykład tworzy dwa obiekty z klasy pochodnej, ale jeden obiekt jest zadeklarowany jako klasa podstawowa, a drugi jako klasy pochodnej.  
  
```  
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
  
 W powyższym przykładzie zmienna `basObj` jest zadeklarowany jako klasy podstawowej. Przypisywanie `dervCls` obiekt do niego stanowi konwersję rozszerzającą i dlatego jest nieprawidłowy. Jednak klasy podstawowej nie może uzyskać dostępu wersja przesłaniania w zmiennej `z` w klasie pochodnej, dlatego kompilator rozpoznaje `basObj.z` do wartości oryginalnej klasy podstawowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
