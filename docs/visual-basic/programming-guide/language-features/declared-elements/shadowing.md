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
ms.openlocfilehash: 7d76e2e7398c2f954ff4274f77ffa350efbd3617
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410750"
---
# <a name="shadowing-in-visual-basic"></a>Przesłanianie w Visual Basic
Gdy dwa elementy programistyczne współdzielą tę samą nazwę, jeden z nich może ukryć lub *Zacień*, drugi. W takiej sytuacji cień elementu nie jest dostępny do celów referencyjnych. Zamiast tego, gdy kod używa nazwy elementu, kompilator Visual Basic rozpoznaje ją jako element przesłaniania.  
  
## <a name="purpose"></a>Przeznaczenie  
 Głównym celem przesłaniania jest ochrona definicji elementów członkowskich klasy. Klasa bazowa może ulec zmianie, która tworzy element o takiej samej nazwie jak już zdefiniowany. W takim przypadku `Shadows` modyfikator wymusza odwołania za pomocą klasy, aby można było rozpoznać element członkowski zdefiniowany przez użytkownika, a nie do nowego elementu klasy bazowej.  
  
## <a name="types-of-shadowing"></a>Typy przesłaniania  
 Element może zasłaniać inny element na dwa różne sposoby. Element shadower może być zadeklarowany wewnątrz podregionu regionu zawierającego element shadowd, w takim przypadku przesłanianie jest realizowane *przez zakres*. Lub Klasa pochodna może przedefiniować składową klasy bazowej, w tym przypadku przesłanianie odbywa się *przez dziedziczenie*.  
  
### <a name="shadowing-through-scope"></a>Przesłanianie przez zakres  
 Istnieje możliwość, że elementy programistyczne w tym samym module, klasie lub strukturze mają taką samą nazwę, ale różne zakresy. Gdy dwa elementy są zadeklarowane w ten sposób, a kod odnosi się do współużytkowanej nazwy, element z węższym zakresem zasłania inny element (zakres blokowy jest najwęższy).  
  
 Na przykład moduł może zdefiniować `Public` zmienną o nazwie `temp` , a procedura w module może zadeklarować zmienną lokalną również o nazwie `temp` . Odwołania do `temp` z procedury uzyskują dostęp do zmiennej lokalnej, natomiast odwołania do `temp` spoza procedury uzyskują dostęp do `Public` zmiennej. W takim przypadku zmienna procedura `temp` zasłania zmienną modułu `temp` .  
  
 Na poniższej ilustracji przedstawiono dwie zmienne: o nazwie `temp` . Zmienna lokalna `temp` zasłania zmienną elementu członkowskiego, `temp` gdy jest dostępny z własnej procedury `p` . Jednak `MyClass` słowo kluczowe pomija cieniowanie i uzyskuje dostęp do zmiennej składowej.  
  
 ![Grafika pokazująca cieniowanie przez zakres.](./media/shadowing/shadow-scope-diagram.gif)
  
 Aby zapoznać się z przykładem przesłaniania przez zakres, zobacz [How to: Hide a Variable o takiej samej nazwie jak zmienna](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Przesłanianie przez dziedziczenie  
 Jeśli klasa pochodna ponownie definiuje element programistyczny Dziedziczony z klasy bazowej, element, który ponownie definiuje, zasłania element oryginalny. Można obsłużyć dowolny typ zadeklarowanego elementu lub zestawu przeciążonych elementów przy użyciu dowolnego innego typu. Na przykład `Integer` zmienna może zasłaniać `Function` procedurę. W przypadku wykonania procedury z inną procedurą można użyć innej listy parametrów i innego typu zwracanego.  
  
 Na poniższej ilustracji przedstawiono klasę bazową `b` i klasę pochodną `d` , która dziedziczy z `b` . Klasa bazowa definiuje procedurę o nazwie `proc` , a Klasa pochodna zasłania ją z inną procedurą o tej samej nazwie. Pierwsza `Call` instrukcja uzyskuje dostęp do przesłaniania `proc` w klasie pochodnej. Jednak `MyBase` słowo kluczowe pomija cieniowanie i uzyskuje dostęp do procedury obserwowania w klasie bazowej.  
  
 ![Diagram grafiki przesłaniania przez dziedziczenie](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Aby zapoznać się z przykładem przesłaniania poprzez dziedziczenie, zobacz [jak: ukrywanie zmiennej o tej samej nazwie co zmienna](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) i [instrukcje: ukrywanie dziedziczonej zmiennej](how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Cień i poziom dostępu  
 Element Shadow nie zawsze jest dostępny z kodu przy użyciu klasy pochodnej. Na przykład może być zadeklarowany `Private` . W takim przypadku przesłanianie jest zakłócane, a kompilator rozpoznaje wszelkie odwołania do tego samego elementu, jeśli nie wystąpiły żadne cieniowanie. Ten element jest dostępnym elementem z najmniejszą liczbą czynności pochodnych z tyłu klasy przesłaniania. Jeśli element Shadow jest procedurą, rozdzielczość jest do najbliższej dostępnej wersji z tą samą nazwą, listą parametrów i zwracanym typem.  
  
 W poniższym przykładzie przedstawiono hierarchię dziedziczenia trzech klas. Każda klasa definiuje `Sub` procedurę `display` , a każda klasa pochodna zasłania `display` procedurę w jej klasie bazowej.  
  
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
  
 W poprzednim przykładzie `secondClass` zaciemnienie klasy pochodnej `display` z `Private` procedurą. Gdy moduł `callDisplay` wywołuje `display` w `secondClass` , kod wywołujący jest poza `secondClass` i w związku z tym nie może uzyskać dostępu do prywatnej `display` procedury. Trwa obniżanie poziomu przesłaniania, a kompilator rozpoznaje odwołanie do procedury klasy bazowej `display` .  
  
 Jednak dodatkowo Klasa pochodna `thirdClass` deklaruje `display` jako `Public` , więc kod w `callDisplay` może uzyskać do niej dostęp.  
  
## <a name="shadowing-and-overriding"></a>Przesłanianie i zastępowanie  
 Nie należy mylić przesłaniania z zastępowaniem. Oba są używane, gdy Klasa pochodna dziedziczy z klasy bazowej, i obie przedefiniują jeden zadeklarowany element z innym. Istnieją jednak znaczące różnice między nimi. Aby zapoznać się z porównaniem, zobacz [różnice między przesłanianiem i zastępowaniem](differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Przesłanianie i Przeciążenie  
 Jeśli ten sam element klasy bazowej zostanie zasłonięty przez więcej niż jeden element w klasie pochodnej, elementy przesłaniania staną się przeciążonymi wersjami tego elementu. Aby uzyskać więcej informacji, zobacz [przeciążanie procedur](../procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Uzyskiwanie dostępu do obserwowania elementu  
 Gdy uzyskujesz dostęp do elementu z klasy pochodnej, zazwyczaj odbywa się to za pośrednictwem bieżącego wystąpienia tej klasy pochodnej, kwalifikując nazwę elementu za pomocą `Me` słowa kluczowego. Jeśli klasa pochodna zasłania element w klasie bazowej, można uzyskać dostęp do elementu klasy bazowej poprzez kwalifikowanie go za pomocą `MyBase` słowa kluczowego.  
  
 Aby zapoznać się z przykładem uzyskiwania dostępu do obserwowania elementu, zobacz [How to: Access a zmienna ukryta przez klasę pochodną](how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
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
  
 W poprzednim przykładzie zmienna `basObj` jest zadeklarowana jako klasa bazowa. Przypisanie `dervCls` obiektu do niego stanowi konwersję rozszerzającą i dlatego jest prawidłowy. Jednak Klasa bazowa nie może uzyskać dostępu do wersji przesłania zmiennej `z` w klasie pochodnej, więc kompilator rozpoznaje `basObj.z` do oryginalnej wartości klasy bazowej.  
  
## <a name="see-also"></a>Zobacz też

- [Odwołania do elementów zadeklarowanych](references-to-declared-elements.md)
- [Zakres w Visual Basic](scope.md)
- [Rozszerzanie i zwężanie konwersji](../data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [Przesłonięcia](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase i MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../objects-and-classes/inheritance-basics.md)
