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
ms.openlocfilehash: 30c02cf367c461c3896a01538d03380627de294f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004855"
---
# <a name="shadowing-in-visual-basic"></a>Przesłanianie w Visual Basic
Gdy dwa elementy programistyczne współdzielą tę samą nazwę, jeden z nich może ukryć lub *Zacień*, drugi. W takiej sytuacji cień elementu nie jest dostępny do celów referencyjnych. Zamiast tego, gdy kod używa nazwy elementu, kompilator Visual Basic rozpoznaje ją jako element przesłaniania.  
  
## <a name="purpose"></a>Cel  
 Głównym celem przesłaniania jest ochrona definicji elementów członkowskich klasy. Klasa bazowa może ulec zmianie, która tworzy element o takiej samej nazwie jak już zdefiniowany. W takim przypadku modyfikator `Shadows` wymusza odwołania za pomocą klasy, aby można było rozpoznać element członkowski zdefiniowany przez użytkownika, a nie do nowego elementu klasy bazowej.  
  
## <a name="types-of-shadowing"></a>Typy przesłaniania  
 Element może zasłaniać inny element na dwa różne sposoby. Element shadower może być zadeklarowany wewnątrz podregionu regionu zawierającego element shadowd, w takim przypadku przesłanianie jest realizowane *przez zakres*. Lub Klasa pochodna może przedefiniować składową klasy bazowej, w tym przypadku przesłanianie odbywa się *przez dziedziczenie*.  
  
### <a name="shadowing-through-scope"></a>Przesłanianie przez zakres  
 Istnieje możliwość, że elementy programistyczne w tym samym module, klasie lub strukturze mają taką samą nazwę, ale różne zakresy. Gdy dwa elementy są zadeklarowane w ten sposób, a kod odnosi się do współużytkowanej nazwy, element z węższym zakresem zasłania inny element (zakres blokowy jest najwęższy).  
  
 Na przykład moduł może zdefiniować zmienną `Public` o nazwie `temp`, a procedura w module może zadeklarować zmienną lokalną także o nazwie `temp`. Odwołania do `temp` z procedury uzyskują dostęp do zmiennej lokalnej, natomiast odwołania do `temp` z zewnątrz procedury uzyskują dostęp do zmiennej `Public`. W takim przypadku zmienna procedury `temp` Cieniuje zmienną modułu `temp`.  
  
 Na poniższej ilustracji przedstawiono dwie zmienne: o nazwie `temp`. Zmienna lokalna `temp` Cieniuje zmienną członkowską `temp` w przypadku dostępu z własnej procedury `p`. Jednak słowo kluczowe `MyClass` pomija cieniowanie i uzyskuje dostęp do zmiennej składowej.  
  
 ![Grafika pokazująca cieniowanie przez zakres.](./media/shadowing/shadow-scope-diagram.gif)
  
 Aby zapoznać się z przykładem przesłaniania przez zakres, zobacz [How to: Hide a Variable o takiej samej nazwie jak zmienna](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Przesłanianie przez dziedziczenie  
 Jeśli klasa pochodna ponownie definiuje element programistyczny Dziedziczony z klasy bazowej, element, który ponownie definiuje, zasłania element oryginalny. Można obsłużyć dowolny typ zadeklarowanego elementu lub zestawu przeciążonych elementów przy użyciu dowolnego innego typu. Na przykład zmienna `Integer` może obsłużyć procedurę `Function`. W przypadku wykonania procedury z inną procedurą można użyć innej listy parametrów i innego typu zwracanego.  
  
 Na poniższej ilustracji przedstawiono klasę bazową `b` i klasę pochodną `d`, która dziedziczy po `b`. Klasa bazowa definiuje procedurę o nazwie `proc`, a Klasa pochodna zasłania ją z inną procedurą o tej samej nazwie. Pierwsza instrukcja `Call` uzyskuje dostęp do obserwowania `proc` w klasie pochodnej. Jednak słowo kluczowe `MyBase` pomija cieniowanie i uzyskuje dostęp do procedury obserwowania w klasie bazowej.  
  
 ![Diagram grafiki przesłaniania przez dziedziczenie](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Aby zapoznać się z przykładem przesłaniania poprzez dziedziczenie, zobacz [jak: ukrywanie zmiennej o tej samej nazwie co zmienna](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) i [instrukcje: ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Cień i poziom dostępu  
 Element Shadow nie zawsze jest dostępny z kodu przy użyciu klasy pochodnej. Na przykład może być zadeklarowany `Private`. W takim przypadku przesłanianie jest zakłócane, a kompilator rozpoznaje wszelkie odwołania do tego samego elementu, jeśli nie wystąpiły żadne cieniowanie. Ten element jest dostępnym elementem z najmniejszą liczbą czynności pochodnych z tyłu klasy przesłaniania. Jeśli element Shadow jest procedurą, rozdzielczość jest do najbliższej dostępnej wersji z tą samą nazwą, listą parametrów i zwracanym typem.  
  
 W poniższym przykładzie przedstawiono hierarchię dziedziczenia trzech klas. Każda klasa definiuje procedurę `Sub` `display`, a każda klasa pochodna zasłania procedurę `display` w swojej klasie podstawowej.  
  
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
  
 W poprzednim przykładzie Klasa pochodna `secondClass` Cieniuje `display` za pomocą procedury `Private`. Gdy moduł `callDisplay` wywołuje `display` w `secondClass`, kod wywołujący jest poza `secondClass` i w związku z tym nie może uzyskać dostępu do prywatnej procedury `display`. Trwa obniżanie poziomu przesłaniania, a kompilator rozpoznaje odwołanie do klasy bazowej `display` procedury.  
  
 Jednak dodatkowo Klasa pochodna `thirdClass` deklaruje `display` jako `Public`, więc kod w `callDisplay` może uzyskać do niego dostęp.  
  
## <a name="shadowing-and-overriding"></a>Przesłanianie i zastępowanie  
 Nie należy mylić przesłaniania z zastępowaniem. Oba są używane, gdy Klasa pochodna dziedziczy z klasy bazowej, i obie przedefiniują jeden zadeklarowany element z innym. Istnieją jednak znaczące różnice między nimi. Aby zapoznać się z porównaniem, zobacz [różnice między przesłanianiem i zastępowaniem](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Przesłanianie i Przeciążenie  
 Jeśli ten sam element klasy bazowej zostanie zasłonięty przez więcej niż jeden element w klasie pochodnej, elementy przesłaniania staną się przeciążonymi wersjami tego elementu. Aby uzyskać więcej informacji, zobacz [przeciążanie procedur](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Uzyskiwanie dostępu do obserwowania elementu  
 Gdy uzyskujesz dostęp do elementu z klasy pochodnej, zazwyczaj odbywa się to za pośrednictwem bieżącego wystąpienia tej klasy pochodnej, kwalifikując nazwę elementu za pomocą słowa kluczowego `Me`. Jeśli klasa pochodna zasłania element w klasie bazowej, można uzyskać dostęp do elementu klasy bazowej poprzez kwalifikowanie go za pomocą słowa kluczowego `MyBase`.  
  
 Aby zapoznać się z przykładem uzyskiwania dostępu do obserwowania elementu, zobacz [How to: Access a zmienna ukryta przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Deklaracja zmiennej obiektu  
 Sposób tworzenia zmiennej obiektu może również mieć wpływ na to, czy Klasa pochodna uzyskuje dostęp do elementu obserwowania lub cieniowania. Poniższy przykład tworzy dwa obiekty z klasy pochodnej, ale jeden obiekt jest zadeklarowany jako klasa bazowa, a drugi jako Klasa pochodna.  
  
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
  
 W poprzednim przykładzie zmienna `basObj` jest zadeklarowana jako klasa bazowa. Przypisanie do niego obiektu `dervCls` stanowi konwersję rozszerzającą i dlatego jest prawidłowy. Jednak Klasa bazowa nie może uzyskać dostępu do wersji przesłaniania zmiennej `z` w klasie pochodnej, więc kompilator rozpoznaje `basObj.z` do oryginalnej wartości klasy bazowej.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
