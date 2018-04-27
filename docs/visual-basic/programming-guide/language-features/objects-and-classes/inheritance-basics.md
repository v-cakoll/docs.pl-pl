---
title: Podstawowe informacje o dziedziczeniu (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e37dabefcbda48144af910298dd4d82c13b7042
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="inheritance-basics-visual-basic"></a>Podstawowe informacje o dziedziczeniu (Visual Basic)
`Inherits` Instrukcji służy do deklarowania nową klasę o nazwie *klasy*, oparte na istniejącej klasy, znany jako *klasa podstawowa*. Klasy pochodne dziedziczą i można rozszerzyć, właściwości, metody, zdarzenia, pól i stałe zdefiniowana w klasie podstawowej. W poniższej sekcji opisano niektóre zasady dotyczące dziedziczenia, a modyfikatorów, których można użyć, aby zmienić sposób klasy dziedziczą lub są dziedziczone:  
  
-   Domyślnie wszystkie klasy są dziedziczone, o ile nie jest oznaczony atrybutem `NotInheritable` — słowo kluczowe. Klasy mogą dziedziczyć z innych klas do projektu lub z klas w innych zestawów, do których odwołuje się projekt.  
  
-   W odróżnieniu od języków, które umożliwiają dziedziczenie wielokrotne Visual Basic umożliwia tylko pojedyncze dziedziczenie klas; oznacza to klasy pochodne mogą mieć tylko jedną klasę podstawową. Mimo że wielokrotne dziedziczenie nie jest dozwolona w klasy, klasy można zaimplementować wiele interfejsów, które można skutecznie wykonać zakończenia tego samego.  
  
-   Aby uniemożliwić udostępnianie ograniczeniami elementy w klasie podstawowej, typ dostępu do klasy pochodnej musi być większy lub bardziej restrykcyjne od swojej klasy podstawowej. Na przykład `Public` klasa nie dziedziczy `Friend` lub `Private` klasy, a `Friend` klasa nie dziedziczy `Private` klasy.  
  
## <a name="inheritance-modifiers"></a>Modyfikatory dziedziczenia  
 Visual Basic wprowadza następujące instrukcje poziomie klasy i Modyfikatory do obsługi dziedziczenia:  
  
-   `Inherits` Instrukcja — określa klasę podstawową.  
  
-   `NotInheritable` Modyfikator — uniemożliwia używanie klasy jako klasę podstawową programistów.  
  
-   `MustInherit` Modyfikator — Określa, że klasa jest przeznaczona do użycia jako klasę podstawową tylko. Wystąpienia `MustInherit` klasy nie można bezpośrednio utworzyć; ich można tworzyć tylko podstawowego wystąpień klasy pochodnej klasy. (Innych języków programowania, takich jak C++ i C#, używany jest termin *klasy abstrakcyjnej* do opisania tych klas.)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>Zastępowanie właściwości i metod w klasach pochodnych  
 Domyślnie Klasa pochodna dziedziczy właściwości i metody swojej klasy podstawowej. Jeśli właściwość dziedziczona lub metoda ma zachowywać się inaczej w klasie pochodnej może być *przesłonięcia*. Oznacza to można zdefiniować nowej implementacji metody w klasie pochodnej. Następujących modyfikatorów są używane do kontrolowania sposobu przesłonięcia właściwości i metody:  
  
-   `Overridable` — Umożliwia właściwości lub metody w klasie do zastąpienia w klasie pochodnej.  
  
-   `Overrides` — Zastępuje `Overridable` właściwości lub metody zdefiniowanej w klasie podstawowej.  
  
-   `NotOverridable` — Uniemożliwia właściwości lub metody przesłaniana klasy dziedziczące. Domyślnie `Public` metody są `NotOverridable`.  
  
-   `MustOverride` — Wymaga się, że klasa pochodna zastąpienie właściwości lub metody. Gdy `MustOverride` słowo kluczowe jest używane, definicja metody składa się z tylko `Sub`, `Function`, lub `Property` instrukcji. Nie inne instrukcje są dozwolone, a w szczególności jest nie `End Sub` lub `End Function` instrukcji. `MustOverride` metody musi być zadeklarowana w `MustInherit` klasy.  
  
 Załóżmy, że chcesz zdefiniować klasy do obsługi płacowego. Można zdefiniować ogólnego `Payroll` klasę, która zawiera `RunPayroll` metodę, która oblicza płacowego typowe tygodnia. Następnie można użyć `Payroll` jako klasę podstawową dla bardziej wyspecjalizowanych `BonusPayroll` klasy, która może służyć do rozpowszechniania dodatki pracownika.  
  
 `BonusPayroll` Klasy mogą dziedziczyć i zastąpić, `PayEmployee` metody zdefiniowanej w podstawowym `Payroll` klasy.  
  
 W poniższym przykładzie zdefiniowano klasę podstawową `Payroll,` i Klasa pochodna `BonusPayroll`, która zastępuje dziedziczonej metody `PayEmployee`. W procedurze `RunPayroll`, tworzy, a następnie przekazuje `Payroll` obiektu i `BonusPayroll` obiektu do funkcji, `Pay`, który jest wykonywany `PayEmployee` metody zarówno do obiektów.  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a>MyBase — słowo kluczowe  
 `MyBase` — Słowo kluczowe zachowuje się jak zmienna obiektu, który odwołuje się do klasy bazowej bieżącego wystąpienia klasy. `MyBase` często umożliwia dostęp do elementów członkowskich klasy podstawowej, które są zastępowane lub cieniowanie w klasie pochodnej. W szczególności `MyBase.New` służy do jawnego wywołania konstruktora klasy podstawowej z konstruktora klasy pochodnej.  
  
 Na przykład załóżmy, że projektowania klasy pochodnej, który przesłania metodę dziedziczona z klasy podstawowej. Przeciążonej można wywołać metody w klasie podstawowej i zmodyfikować zwracanej wartości, jak pokazano w poniższy fragment kodu:  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 Na poniższej liście wymieniono ograniczenia dotyczące używania `MyBase`:  
  
-   `MyBase` odnosi się do natychmiastowego klasy podstawowej i jej dziedziczonych elementów członkowskich. Nie można użyć do dostępu `Private` elementów członkowskich w klasie.  
  
-   `MyBase` jest słowem kluczowym rzeczywistego obiektu. `MyBase` nie może być przypisany do zmiennej, przekazany do procedury lub używane w `Is` porównania.  
  
-   Metoda który `MyBase` kwalifikuje się nie musi być zdefiniowana w klasie podstawowej natychmiastowego; zamiast tego może być zdefiniowana w klasie podstawowej pośrednio dziedziczone. Aby kwalifikowana przez odwołanie `MyBase` do poprawnej kompilacji niektóre klasy podstawowej musi zawierać nazwę i typy parametrów, które pojawiają się w wywołaniu metody.  
  
-   Nie można użyć `MyBase` do wywołania `MustOverride` metod klasy podstawowej.  
  
-   `MyBase` Nie można użyć, aby zakwalifikować się. W związku z tym następujący kod jest nieprawidłowy:  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase` Nie można używać w modułach.  
  
-   `MyBase` Nie można uzyskać dostępu do elementów członkowskich klasy podstawowej, które są oznaczone jako `Friend` Jeśli klasą podstawową jest w innym zestawie.  
  
 Więcej informacji oraz innym przykładem, zobacz [porady: dostęp do zmiennej ukrytej przez klasę pochodnych](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
## <a name="the-myclass-keyword"></a>MyClass — słowo kluczowe  
 `MyClass` — Słowo kluczowe zachowuje się jak zmienna obiektu, który odwołuje się do bieżącego wystąpienia klasy pierwotnie zaimplementowanych. `MyClass` podobny `Me`, ale każdy metody i właściwości wywołać w `MyClass` jest traktowana tak, jakby był metody lub właściwości [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). W związku z tym ta metoda lub właściwość nie ma wpływu na zastępowanie w klasie pochodnej.  
  
-   `MyClass` jest słowem kluczowym rzeczywistego obiektu. `MyClass` nie może być przypisany do zmiennej, przekazany do procedury lub używane w `Is` porównania.  
  
-   `MyClass` odnosi się do klasy zawierającej i jego dziedziczone elementy członkowskie.  
  
-   `MyClass` mogą być używane jako kwalifikator dla `Shared` elementów członkowskich.  
  
-   `MyClass` Nie można używać wewnątrz `Shared` metody, ale można uzyskać dostępu do udostępnionego elementu członkowskiego klasy można używać wewnątrz metody wystąpienia.  
  
-   `MyClass` Nie można używać w modułach standardowych.  
  
-   `MyClass` może służyć do kwalifikowania metody, który jest zdefiniowany w klasie podstawowej, na którym jest żadnej implementacji metody podane w tej klasie. Odniesienie ma takie samo znaczenie jak `MyBase.` *metody*.  
  
 Poniższy przykład porównuje `Me` i `MyClass`.  
  
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
  
 Mimo że `derivedClass` zastępuje `testMethod`, `MyClass` — słowo kluczowe w `useMyClass` nullifies skutki zastępowanie i rozwiązuje kompilatora wywołania do klasy podstawowej wersji `testMethod`.  
  
## <a name="see-also"></a>Zobacz też  
 [Inherits, instrukcja](../../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
