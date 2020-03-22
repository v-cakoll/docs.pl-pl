---
title: Podstawowe informacje o dziedziczeniu
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
ms.openlocfilehash: 89fcf2a14d8938d536aa72628218242811baa1a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400884"
---
# <a name="inheritance-basics-visual-basic"></a>Podstawowe informacje o dziedziczeniu (Visual Basic)

Instrukcja `Inherits` jest używana do deklarowania nowej klasy, zwanej *klasą pochodną,* na podstawie istniejącej klasy, znanej jako *klasa podstawowa.* Klasy pochodne dziedziczą i mogą rozszerzać właściwości, metody, zdarzenia, pola i stałe zdefiniowane w klasie podstawowej. W poniższej sekcji opisano niektóre reguły dziedziczenia i modyfikatory, których można użyć do zmiany sposobu dziedziczenia lub dziedziczenia klas:

- Domyślnie wszystkie klasy są dziedziczone, `NotInheritable` chyba że oznaczone słowem kluczowym. Klasy mogą dziedziczyć z innych klas w projekcie lub z klas w innych zestawach, które odwołuje się do projektu.

- W przeciwieństwie do języków, które zezwalają na wielokrotne dziedziczenie Visual Basic zezwala tylko na pojedyncze dziedziczenie w klasach; oznacza to, że klasy pochodne mogą mieć tylko jedną klasę podstawową. Mimo że wiele dziedziczenia nie jest dozwolone w klasach, klasy można zaimplementować wiele interfejsów, które mogą skutecznie osiągnąć te same cele.

- Aby zapobiec uwidacznianiu elementów podlegających ograniczeniom w klasie podstawowej, typ dostępu klasy pochodnej musi być równy lub bardziej restrykcyjny niż jego klasa podstawowa. Na przykład `Public` klasa nie `Friend` może `Private` dziedziczyć `Friend` klasy lub `Private` klasy, a klasa nie może dziedziczyć klasy.

## <a name="inheritance-modifiers"></a>Modyfikatory dziedziczenia

Visual Basic wprowadza następujące instrukcje na poziomie klasy i modyfikatory do obsługi dziedziczenia:

- `Inherits`instrukcja — określa klasę podstawową.

- `NotInheritable`modyfikator — uniemożliwia programistom używanie klasy jako klasy podstawowej.

- `MustInherit`modyfikator — określa, że klasa jest przeznaczona tylko do użytku jako klasa podstawowa. Wystąpienia `MustInherit` klas nie mogą być tworzone bezpośrednio; mogą być tworzone tylko jako wystąpienia klasy podstawowej klasy pochodnej. (Inne języki programowania, takie jak C++ i C#, używają terminu *klasy abstrakcyjnej* do opisania takiej klasy.)

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Zastępowanie właściwości i metod w klasach pochodnych

Domyślnie klasa pochodna dziedziczy właściwości i metody z klasy podstawowej. Jeśli dziedziczona właściwość lub metoda musi zachowywać się inaczej w klasie pochodnej, może zostać *zastąpiona.* Oznacza to, że można zdefiniować nową implementację metody w klasie pochodnej. Następujące modyfikatory są używane do kontrolowania, jak właściwości i metody są zastępowane:

- `Overridable`— Umożliwia właściwość lub metodę w klasie, która ma zostać zastąpiona w klasie pochodnej.

- `Overrides`— Zastępuje właściwość lub metodę zdefiniowaną `Overridable` w klasie podstawowej.

- `NotOverridable`— Zapobiega nadpisywania właściwości lub metody w klasie dziedziczącej. Domyślnie `Public` metody `NotOverridable`są .

- `MustOverride`— Wymaga, aby klasa pochodna zastępowała właściwość lub metodę. Gdy `MustOverride` słowo kluczowe jest używane, definicja `Sub` `Function`metody `Property` składa się tylko z , lub instrukcji. Żadne inne instrukcje nie są dozwolone, `End Sub` `End Function` a w szczególności nie ma ani nie ma instrukcji. `MustOverride`metody muszą być `MustInherit` zadeklarowane w klasach.

Załóżmy, że chcesz zdefiniować klasy do obsługi listy płac. Można zdefiniować `Payroll` klasę rodzajową, która zawiera metodę obliczającą `RunPayroll` listę płac dla typowego tygodnia. Następnie można `Payroll` użyć jako klasy podstawowej `BonusPayroll` dla bardziej wyspecjalizowanej klasy, która może być używana podczas dystrybucji premii pracowniczych.

Klasa `BonusPayroll` może dziedziczyć i zastępować metodę zdefiniowaną `PayEmployee` w klasie podstawowej. `Payroll`

Poniższy przykład definiuje klasę `Payroll,` podstawową i klasę `BonusPayroll`pochodną, która zastępuje metodę `PayEmployee`dziedziczoną, . Procedura , `RunPayroll`tworzy, a `Payroll` następnie przekazuje `BonusPayroll` obiekt i `Pay`obiekt do funkcji, która wykonuje `PayEmployee` metodę obu obiektów.

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>Słowo kluczowe MyBase

Słowo `MyBase` kluczowe zachowuje się jak zmienna obiektu, która odwołuje się do klasy podstawowej bieżącego wystąpienia klasy. `MyBase`jest często używany do uzyskiwania dostępu do elementów członkowskich klasy podstawowej, które są zastępowane lub cieniowane w klasie pochodnej. W szczególności `MyBase.New` jest używany do jawnego wywołania konstruktora klasy podstawowej z konstruktora klas pochodnych.

Załóżmy na przykład, że projektujesz klasę pochodną, która zastępuje metodę dziedziczoną z klasy podstawowej. Zastąpiona metoda może wywołać metodę w klasie podstawowej i zmodyfikować wartość zwracaną, jak pokazano w następującym fragmencie kodu:

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

Na poniższej liście opisano `MyBase`ograniczenia dotyczące używania:

- `MyBase`odnosi się do natychmiastowej klasy podstawowej i jej odziedziczonych członków. Nie można użyć `Private` dostępu do elementów członkowskich w klasie.

- `MyBase`jest słowem kluczowym, a nie prawdziwym obiektem. `MyBase`nie można przypisać do zmiennej, przejść do `Is` procedur lub użyć w porównaniu.

- Metoda, `MyBase` która kwalifikuje się nie musi być zdefiniowana w natychmiastowej klasie podstawowej; zamiast tego może być zdefiniowany w pośrednio dziedziczonej klasie podstawowej. Aby odwołanie kwalifikowane `MyBase` przez do poprawnego skompilowania, niektóre klasy podstawowej musi zawierać metodę pasującą do nazwy i typów parametrów, które pojawiają się w wywołaniu.

- Nie można `MyBase` wywołać metody klasy `MustOverride` podstawowej.

- `MyBase`nie mogą być wykorzystane do zakwalifikowania się. W związku z tym następujący kod jest nieprawidłowy:

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase`nie mogą być używane w modułach.

- `MyBase`nie można użyć do uzyskania dostępu `Friend` do elementów członkowskich klasy podstawowej, które są oznaczone tak, jakby klasa podstawowa znajduje się w innym zestawie.

Aby uzyskać więcej informacji i inny przykład, zobacz [Jak: Dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).

## <a name="the-myclass-keyword"></a>Słowo kluczowe MyClass

Słowo `MyClass` kluczowe zachowuje się jak zmienna obiektu, która odwołuje się do bieżącego wystąpienia klasy, jak pierwotnie zaimplementowano. `MyClass`przypomina `Me`, ale każda metoda `MyClass` i właściwość wywołać na jest traktowana tak, jakby metoda lub właściwość [były NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). W związku z tym metoda lub właściwość nie ma wpływu na zastąpienie w klasie pochodnej.

- `MyClass`jest słowem kluczowym, a nie prawdziwym obiektem. `MyClass`nie można przypisać do zmiennej, przejść do `Is` procedur lub użyć w porównaniu.

- `MyClass`odnosi się do klasy zawierającej i jej odziedziczonych członków.

- `MyClass`może służyć jako kwalifikator dla `Shared` członków.

- `MyClass`nie można użyć `Shared` wewnątrz metody, ale może służyć wewnątrz metody wystąpienia, aby uzyskać dostęp do udostępnionego elementu członkowskiego klasy.

- `MyClass`nie mogą być stosowane w standardowych modułach.

- `MyClass`może służyć do zakwalifikowania metody, która jest zdefiniowana w klasie podstawowej i która nie ma implementacji metody przewidzianej w tej klasie. Takie odniesienie ma takie `MyBase.`samo znaczenie jak *metoda*.

Poniższy przykład `Me` porównuje `MyClass`i .

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

Mimo `derivedClass` że zastępuje `testMethod`, `MyClass` słowo `useMyClass` kluczowe w unieważnia skutki zastąpienia, a kompilator rozwiązuje wywołanie `testMethod`do wersji klasy podstawowej .

## <a name="see-also"></a>Zobacz też

- [Inherits, instrukcja](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
