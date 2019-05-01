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
ms.openlocfilehash: 9ad992a53618fa2f410e0b0fb23886c30136384f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917920"
---
# <a name="shadowing-in-visual-basic"></a>Przesłanianie w Visual Basic
Gdy dwa elementy programowania mają taką samą nazwę, jeden z nich można ukryć, lub *w tle*, jeden z nich. W takiej sytuacji zasłonięte element nie jest dostępne do użytku; Zamiast tego gdy kod używa nazwy elementu, kompilator Visual Basic jest rozpoznawany jako jej przesłaniania elementu.  
  
## <a name="purpose"></a>Cel  
 Głównym celem przesłanianie jest ochrona definicji usługi składowych klasy. Klasy bazowej może przechodzić zmianę, która tworzy element o takiej samej nazwie jako jeden, który został już zdefiniowany. W takim przypadku `Shadows` wymusza modyfikator odwołuje się do swojej klasy, które mają zostać rozwiązane do elementu członkowskiego zdefiniowane, zamiast na nowy element klasy bazowej.  
  
## <a name="types-of-shadowing"></a>Typy cieniowania  
 Element można w tle innego elementu na dwa różne sposoby. Można zadeklarować elementu przesłaniania wewnątrz Podobszar regionu zawierającego element zasłonięte, w której odbywa sprawy przesłanianie *przez zakres*. I Klasa pochodna można ponownie zdefiniować składowej klasy bazowej, w którym odbywa sprawy przesłanianie *poprzez dziedziczenie*.  
  
### <a name="shadowing-through-scope"></a>Cieniowania przez zakres  
 Istnieje możliwość programowania elementów w tej samej modułu, klasy lub struktury, aby mieć takiej samej nazwie, ale inny zakres. Jeśli dwa elementy są deklarowane w ten sposób, kod odwołuje się do nazwy mają element z węższy zakres zasłania innego elementu (zakres bloku jest najmniejsza).  
  
 Na przykład można zdefiniować moduł `Public` zmiennej o nazwie `temp`, oraz procedury w module można zadeklarować zmiennej lokalnej o nazwie `temp`. Odwołuje się do `temp` z poziomu procedury dostępu do zmiennej lokalnej podczas odwołania do `temp` z poza dostępu procedury `Public` zmiennej. W tym przypadku zmienna procedury `temp` zasłania zmiennej modułu `temp`.  
  
 Na poniższej ilustracji przedstawiono dwie zmienne, o nazwie `temp`. Zmienna lokalna `temp` zasłania zmiennej składowej `temp` podczas uzyskiwania dostępu do z, w ramach własnej procedury `p`. Jednak `MyClass` — słowo kluczowe pomija przesłanianiem i uzyskuje dostęp do zmiennej elementu członkowskiego.  
  
 ![Grafika przedstawiająca cieniowania przez zakres.](./media/shadowing/shadow-scope-diagram.gif)
  
 Na przykład cieniowania przez zakres zobacz [jak: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Przesłanianie poprzez dziedziczenie  
 Jeśli klasa pochodna redefiniuje elementu programistycznego dziedziczone z klasy bazowej, redefining element zasłania oryginalnego elementu. Można w tle dowolnego typu element zadeklarowany lub zestaw przeciążonych elementów z żadnym innym typem. Na przykład `Integer` zmiennej może w tle `Function` procedury. Jeśli w tle procedury z innej procedury można użyć inną listą parametrów i innym typie zwracanym.  
  
 Na poniższej ilustracji przedstawiono klasę bazową `b` i Klasa pochodna `d` tej, która dziedziczy `b`. Klasa bazowa definiuje procedurę o nazwie `proc`, i Klasa pochodna zasłania go przy użyciu innej procedury o takiej samej nazwie. Pierwszy `Call` uzyskuje dostęp do instrukcji, przesłanianie `proc` w klasie pochodnej. Jednak `MyBase` — słowo kluczowe pomija przesłanianiem i uzyskuje dostęp do zasłonięte procedury w klasie bazowej.  
  
 ![Diagram graficzny cieniowania poprzez dziedziczenie](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Na przykład cieniowania przez dziedziczenie zobacz [jak: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) i [jak: Ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Przesłanianie i poziom dostępu  
 Element przesłaniania nie zawsze jest dostępne z kodu za pomocą klasy pochodnej. Na przykład może być zadeklarowana `Private`. W takim przypadku przesłanianie jest bezcelowe i kompilator rozwiązuje wszelkie odwołania do tego samego elementu, gdyż miałoby Jeśli nastąpiła nie przesłanianie. Ten element jest dostępnego elementu najmniejszą liczbę derivational kroki wstecz od klasy przesłaniania. Jeśli element zasłonięte jest procedurą, rozwiązanie jest do najbliższej dostępnej wersji o takiej samej nazwie, lista parametrów i zwracany typ.  
  
 Poniższy przykład pokazuje hierarchię dziedziczenia trzech klas. Każda klasa definiuje `Sub` procedury `display`, i każdy pochodne klasy cieni `display` procedury w swojej klasie bazowej.  
  
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
  
 W poprzednim przykładzie Klasa pochodna `secondClass` cieni `display` z `Private` procedury. Gdy moduł `callDisplay` wywołania `display` w `secondClass`, kod wywołujący znajduje się poza `secondClass` i dlatego nie może uzyskiwać dostęp do prywatnego `display` procedury. Przesłanianie jest bezcelowe, a kompilator jest rozpoznawana jako odwołanie do klasy bazowej `display` procedury.  
  
 Jednak dalsze klasy pochodnej `thirdClass` deklaruje `display` jako `Public`, dlatego ten kod w `callDisplay` do niego dostęp.  
  
## <a name="shadowing-and-overriding"></a>Przesłanianiem i zastępowaniem  
 Nie należy mylić przesłanianie z nadpisaniem. Oba są używane, gdy klasa pochodna dziedziczy z klasy bazowej, a jednocześnie ponownie zdefiniować jeden element zadeklarowany z innym. Jednak istnieją znaczne różnice między nimi. Dla porównania, zobacz [różnice między przesłanianiem i przesłanianie](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Przesłanianie i przeciążenie  
 Jeśli w klasie pochodnej w tle tego samego elementu klasy bazowej z więcej niż jeden element, przesłaniania elementy stają się przeciążone wersje tego elementu. Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Uzyskiwanie dostępu do elementu tekst z cieniem  
 Gdy uzyskujesz dostęp do elementu z klasy pochodnej, możesz normalnie to zrobić przez bieżące wystąpienie tej klasy pochodnej kwalifikując nazwę elementu z `Me` — słowo kluczowe. Klasy pochodne cieni elementów w klasie bazowej, można przejść do elementu klasy podstawowej kwalifikując ją za pomocą `MyBase` — słowo kluczowe.  
  
 Na przykład uzyskiwania dostępu do elementu zasłonięte zobacz [jak: Dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Deklaracja zmiennej obiektu  
 Jak utworzyć zmienną obiektu może również wpływać na czy klasy pochodnej uzyskuje dostęp do przesłaniania element lub tekst z cieniem elementu. Poniższy przykład tworzy dwa obiekty z klasy pochodnej, ale jeden obiekt jest zadeklarowany jako klasę bazową, a drugi jako klasy pochodnej.  
  
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
  
 W poprzednim przykładzie, zmienna `basObj` jest zadeklarowany jako klasa bazowa. Przypisywanie `dervCls` obiektu do niego stanowi konwersją rozszerzającą, a w związku z tym jest prawidłowy. Jednak klasy bazowej nie może uzyskiwać dostęp do wersji przesłaniania w zmiennej `z` w klasie pochodnej, dlatego kompilator rozpoznaje `basObj.z` do oryginalnej wartości klasy bazowej.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
