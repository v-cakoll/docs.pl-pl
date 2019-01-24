---
title: Podstawowe informacje o dziedziczeniu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: ae6b53db3a2cdcefa2b05d68ed953c5e17b279dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551790"
---
# <a name="inheritance-basics-visual-basic"></a>Podstawowe informacje o dziedziczeniu (Visual Basic)
`Inherits` Instrukcja jest używane do deklarowania nową klasę o nazwie *klasy pochodnej*zgodnie z istniejącej klasy, znane jako *klasy bazowej*. Klasy pochodne dziedziczenie i można rozszerzyć, właściwości, metody, zdarzenia, pola i stałe zdefiniowane w klasie bazowej. W poniższej sekcji opisano niektóre z reguł do obsługi dziedziczenia i modyfikatorów, których można użyć, aby zmienić sposób klasy dziedziczą lub są dziedziczone:  
  
-   Domyślnie wszystkie klasy są dziedziczone, o ile nie jest oznaczona za pomocą `NotInheritable` — słowo kluczowe. Klasy mogą dziedziczyć z innych klas w projekcie lub klas w innych zestawach, do których odwołuje się do projektu.  
  
-   W odróżnieniu od języków, które umożliwiają wielokrotne dziedziczenie Visual Basic umożliwia tylko pojedyncze dziedziczenie w klasach; oznacza to klasy pochodne mogą mieć tylko jedną klasę bazową. Mimo że wielokrotne dziedziczenie jest niedozwolona w klasach i klas można zaimplementować wiele interfejsów, które skutecznie można osiągnąć ten sam kończy się.  
  
-   Aby uniemożliwić udostępnianie ograniczonych elementów w klasie bazowej, typ dostępu dla klasy pochodnej musi być większa lub równa bardziej restrykcyjny niż jej klasy bazowej. Na przykład `Public` klasa nie może dziedziczyć `Friend` lub `Private` klasy, a `Friend` klasa nie może dziedziczyć `Private` klasy.  
  
## <a name="inheritance-modifiers"></a>Modyfikatory dziedziczenia  
 Visual Basic wprowadza następujące instrukcje na poziomie klasy i Modyfikatory do obsługi dziedziczenia:  
  
-   `Inherits` Instrukcja — określa klasę bazową.  
  
-   `NotInheritable` Modyfikator — powstrzymuje programistów przed za pomocą klasy jako klasę bazową.  
  
-   `MustInherit` Modyfikator — Określa, że klasa jest przeznaczona do użytku jako klasę bazową tylko. Wystąpienia elementu `MustInherit` klasy nie można utworzyć bezpośrednio; one mogą być tworzone tylko podstawowego wystąpienia klasy pochodnej klasy. (Innych języków programowania, takich jak C++ i C#, używany jest termin *abstrakcyjna klasa* do opisania tych klas.)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>Zastępowanie właściwości i metod w klasach pochodnych  
 Domyślnie Klasa pochodna dziedziczy właściwości i metody w swojej klasie podstawowej. Jeśli właściwość dziedziczona lub metoda ma zachowują się odmiennie w klasie pochodnej może być *zastąpione*. Oznacza to można zdefiniować nową metodę implementacji metody w klasie pochodnej. Następujące Modyfikatory są używane do kontrolowania, jak zastąpić właściwości i metod:  
  
-   `Overridable` — Umożliwia właściwość lub metoda klasy został nadpisany w klasie pochodnej.  
  
-   `Overrides` — Zastępuje `Overridable` właściwości lub metody zdefiniowanej w klasie bazowej.  
  
-   `NotOverridable` — Uniemożliwia właściwości lub metody są przesłonięcia w klasie dziedziczącej. Domyślnie `Public` metody są `NotOverridable`.  
  
-   `MustOverride` — Wymaga, że klasa pochodna zastąpienie właściwości lub metody. Gdy `MustOverride` słowo kluczowe jest używane, definicję metody składa się z tylko `Sub`, `Function`, lub `Property` instrukcji. Są dozwolone nie inne instrukcje, a w szczególności istnieje nie `End Sub` lub `End Function` instrukcji. `MustOverride` metody musi być zadeklarowana w `MustInherit` klasy.  
  
 Załóżmy, że chcesz zdefiniować klasy do obsługi płac. Można zdefiniować ogólnego `Payroll` klasę, która zawiera `RunPayroll` metodę, która oblicza płac dla typowych tygodnia. Następnie można użyć `Payroll` jako klasę bazową dla bardziej wyspecjalizowane `BonusPayroll` klasy, który może być używany podczas dystrybucji premie pracownika.  
  
 `BonusPayroll` Klasy mogą dziedziczyć i zastąpić, `PayEmployee` metody zdefiniowane w bazowym `Payroll` klasy.  
  
 W poniższym przykładzie zdefiniowano klasę bazową `Payroll,` i Klasa pochodna `BonusPayroll`, który zastępuje metody dziedziczonej, `PayEmployee`. W procedurze `RunPayroll`, tworzy, a następnie przekazuje `Payroll` obiektu i `BonusPayroll` obiektu do funkcji, `Pay`, który wykonuje `PayEmployee` metoda obu obiektów.  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a>MyBase — słowo kluczowe  
 `MyBase` — Słowo kluczowe zachowuje się jak zmienna obiektu, który odwołuje się do klasy bazowej bieżącego wystąpienia klasy. `MyBase` często używane do dostępu do składowych klasy bazowej, które zostały zastąpione lub pada w klasie pochodnej. W szczególności `MyBase.New` służy do jawnie wywołać konstruktora klasy bazowej w konstruktorze klasy pochodnej.  
  
 Na przykład załóżmy, że projektujesz Klasa pochodna, która zastępuje metodę dziedziczone z klasy podstawowej. Zastąpione metody można wywołać metodę w klasie bazowej i zmodyfikować zwracanej wartości, jak pokazano na następujący fragment kodu:  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 Na poniższej liście opisano ograniczenia dotyczące używania `MyBase`:  
  
-   `MyBase` odnosi się do natychmiastowego klasy podstawowej i jej dziedziczone elementy członkowskie. Nie można użyć do dostępu `Private` elementów członkowskich w klasie.  
  
-   `MyBase` jest słowem kluczowym rzeczywistego obiektu. `MyBase` Nie można przypisać do zmiennej, przekazany do procedury ani wykorzystywać w `Is` porównania.  
  
-   Metoda, `MyBase` kwalifikuje się nie musi być zdefiniowany w klasie bazowej natychmiastowego; zamiast tego może być zdefiniowana w klasie bazowej pośrednio dziedziczone. Aby odwołanie kwalifikowana przez `MyBase` skompilować poprawnie, niektóre klasa bazowa musi zawierać pasujących do nazwy i typy parametrów, które pojawiają się w wywołaniu metody.  
  
-   Nie można użyć `MyBase` do wywołania `MustOverride` metody klasy bazowej.  
  
-   `MyBase` nie może służyć do samego zakwalifikowania. W związku z tym poniższy kod jest nieprawidłowy:  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase` Nie można używać w modułach.  
  
-   `MyBase` Nie można użyć do dostępu do składowych klasy bazowej, które są oznaczone jako `Friend` Jeśli klasa podstawowa jest w innym zestawie.  
  
 Aby uzyskać więcej informacji i inny przykład, zobacz [jak: Dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
## <a name="the-myclass-keyword"></a>MyClass — słowo kluczowe  
 `MyClass` — Słowo kluczowe zachowuje się jak zmienna obiektu, który odwołuje się do bieżącego wystąpienia klasy pierwotnie zaimplementowanych. `MyClass` przypomina `Me`, ale co metod i właściwości wywołać w `MyClass` jest traktowany tak, jakby były metodę lub właściwość [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). W związku z tym metody lub właściwości nie występuje przez zastąpienie w klasie pochodnej.  
  
-   `MyClass` jest słowem kluczowym rzeczywistego obiektu. `MyClass` Nie można przypisać do zmiennej, przekazany do procedury ani wykorzystywać w `Is` porównania.  
  
-   `MyClass` odnosi się do klasy zawierającego i jego dziedziczone elementy członkowskie.  
  
-   `MyClass` mogą być używane jako kwalifikator dla `Shared` elementów członkowskich.  
  
-   `MyClass` Nie można używać wewnątrz `Shared` metody, ale mogą być używane do dostępu do udostępnionej składowej klasy wewnątrz metody wystąpienia.  
  
-   `MyClass` Nie można używać w modułach standardowych.  
  
-   `MyClass` może służyć do kwalifikowania metodę, która jest zdefiniowana w klasie bazowej, a która nie ma implementacji metody dostarczone przez tę klasę. Takie odwołanie, ma takie samo znaczenie jak `MyBase.` *metoda*.  
  
 W poniższym przykładzie porównano `Me` i `MyClass`.  
  
```vb
Class baseClass  
    Public Overridable Sub testMethod()  
        MsgBox("Base class string")  
    End Sub  
    Public Sub useMe()  
        ' The following call uses the calling class's method, even if   
        ' that method is an override.  
        Me.testMethod()  
    End Sub  
    Public Sub useMyClass()  
        ' The following call uses this instance's method and not any  
        ' override.  
        MyClass.testMethod()  
    End Sub  
End Class  
Class derivedClass : Inherits baseClass  
    Public Overrides Sub testMethod()  
        MsgBox("Derived class string")  
    End Sub  
End Class  
Class testClasses  
    Sub startHere()  
        Dim testObj As derivedClass = New derivedClass()  
        ' The following call displays "Derived class string".  
        testObj.useMe()  
        ' The following call displays "Base class string".  
        testObj.useMyClass()  
    End Sub  
End Class  
```  
  
 Mimo że `derivedClass` zastępuje `testMethod`, `MyClass` — słowo kluczowe w `useMyClass` nullifies skutki zastępowanie i rozwiązuje kompilatora wywołanie klasy bazowej wersję `testMethod`.  
  
## <a name="see-also"></a>Zobacz także
- [Inherits, instrukcja](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
