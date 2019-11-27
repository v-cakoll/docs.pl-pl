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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350821"
---
# <a name="inheritance-basics-visual-basic"></a>Podstawowe informacje o dziedziczeniu (Visual Basic)

Instrukcja `Inherits` służy do deklarowania nowej klasy, zwanej *klasą pochodną*, na podstawie istniejącej klasy, znanej jako *Klasa bazowa*. Klasy pochodne dziedziczą i mogą być rozszerzone, właściwości, metody, zdarzenia, pola i stałe zdefiniowane w klasie bazowej. W poniższej sekcji opisano niektóre reguły dziedziczenia oraz modyfikatory, których można użyć do zmiany metod dziedziczonych lub dziedziczonych przez klasy:

- Domyślnie wszystkie klasy są dziedziczone, chyba że oznaczono za pomocą słowa kluczowego `NotInheritable`. Klasy mogą dziedziczyć z innych klas w projekcie lub z klas w innych zestawach, do których odwołuje się projekt.

- W przeciwieństwie do języków, które zezwalają na wielokrotne dziedziczenie, Visual Basic zezwala tylko na jedno dziedziczenie w klasach. oznacza to, że klasy pochodne mogą mieć tylko jedną klasę bazową. Chociaż nie jest dozwolone wielokrotne dziedziczenie w klasach, klasy mogą implementować wiele interfejsów, co może efektywnie wykonywać te same punkty końcowe.

- Aby zapobiec ujawnieniu elementów z ograniczeniami w klasie bazowej, typ dostępu klasy pochodnej musi być równy lub bardziej restrykcyjny niż jego Klasa bazowa. Na przykład Klasa `Public` nie może dziedziczyć `Friend` lub klasy `Private`, a Klasa `Friend` nie może dziedziczyć klasy `Private`.

## <a name="inheritance-modifiers"></a>Modyfikatory dziedziczenia

Visual Basic wprowadza następujące instrukcje i Modyfikatory na poziomie klasy do obsługi dziedziczenia:

- Instrukcja `Inherits` — określa klasę bazową.

- modyfikator `NotInheritable` — uniemożliwia programistom Używanie klasy jako klasy bazowej.

- modyfikator `MustInherit` — określa, że Klasa jest przeznaczona do użycia tylko jako klasa bazowa. Wystąpienia klas `MustInherit` nie mogą być tworzone bezpośrednio; mogą być tworzone tylko jako wystąpienia klasy bazowej klasy pochodnej. (Inne języki programowania, takie jak C++ i C#, używają *klasy abstrakcyjnej* do opisywania takiej klasy).

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Zastępowanie właściwości i metod w klasach pochodnych

Domyślnie Klasa pochodna dziedziczy właściwości i metody z klasy bazowej. Jeśli dziedziczona właściwość lub metoda musi zachowywać się inaczej w klasie pochodnej, można ją *przesłonić*. Oznacza to, że można zdefiniować nową implementację metody w klasie pochodnej. Poniższe Modyfikatory służą do kontrolowania sposobu przesłania właściwości i metod:

- `Overridable` — umożliwia zastąpienie właściwości lub metody w klasie pochodnej w klasie.

- `Overrides` — przesłania Właściwość `Overridable` lub metodę zdefiniowaną w klasie bazowej.

- `NotOverridable` — zapobiega przesłanianiu przez właściwość lub metodę w klasie dziedziczenia. Domyślnie `NotOverridable`metody `Public` są.

- `MustOverride` — wymaga, aby Klasa pochodna przesłaniał właściwość lub metodę. Gdy używane jest słowo kluczowe `MustOverride`, definicja metody składa się tylko z instrukcji `Sub`, `Function`lub `Property`. Żadne inne instrukcje nie są dozwolone i nie ma żadnej instrukcji `End Sub` ani `End Function`. Metody `MustOverride` muszą być zadeklarowane w klasach `MustInherit`.

Załóżmy, że chcesz zdefiniować klasy do obsługi listy płac. Można zdefiniować generyczną klasę `Payroll`, która zawiera metodę `RunPayroll`, która oblicza listę płac dla typowego tygodnia. Następnie można użyć `Payroll` jako klasy bazowej dla bardziej wyspecjalizowanej klasy `BonusPayroll`, która może być używana do dystrybucji premii pracowników.

Klasa `BonusPayroll` może dziedziczyć i przesłonić metodę `PayEmployee` zdefiniowaną w klasie podstawowej `Payroll`.

W poniższym przykładzie zdefiniowano klasę bazową, `Payroll,` i klasę pochodną `BonusPayroll`, która zastępuje metodę dziedziczoną, `PayEmployee`. Procedura `RunPayroll`, tworzy, a następnie przekazuje obiekt `Payroll` i obiekt `BonusPayroll` do funkcji, `Pay`, która wykonuje metodę `PayEmployee` obu obiektów.

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>Słowo kluczowe MyBase

Słowo kluczowe `MyBase` zachowuje się jak zmienna obiektu odwołująca się do klasy podstawowej bieżącego wystąpienia klasy. `MyBase` jest często używana do uzyskiwania dostępu do składowych klasy bazowej, które są zastępowane lub zasłonięte w klasie pochodnej. W szczególności `MyBase.New` jest używany do jawnego wywoływania konstruktora klasy bazowej z konstruktora klasy pochodnej.

Załóżmy na przykład, że projektujesz klasę pochodną, która zastępuje metodę dziedziczoną z klasy bazowej. Zastąpiona metoda może wywołać metodę w klasie bazowej i zmodyfikować wartość zwracaną, jak pokazano w poniższym fragmencie kodu:

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

Poniższa lista zawiera opis ograniczeń dotyczących używania `MyBase`:

- `MyBase` odwołuje się do bezpośredniej klasy podstawowej i jej dziedziczonych elementów członkowskich. Nie można jej użyć w celu uzyskania dostępu do `Private` elementów członkowskich w klasie.

- `MyBase` jest słowem kluczowym, a nie obiektem rzeczywistym. `MyBase` nie można przypisać do zmiennej, przekazywać do procedur ani używać w porównaniu `Is`.

- Metoda, która `MyBase` kwalifikatory, nie musi być zdefiniowana w bezpośredniej klasie podstawowej; może być zdefiniowana w niejawnie dziedziczonej klasie bazowej. Aby dokumentacja kwalifikowana przez `MyBase` była skompilowana prawidłowo, pewna klasa bazowa musi zawierać metodę zgodną z nazwą i typami parametrów, które są wyświetlane w wywołaniu.

- Nie można użyć `MyBase` do wywołania `MustOverride` metod klasy bazowej.

- `MyBase` nie może być używana do kwalifikowania się samego siebie. W związku z tym następujący kod jest nieprawidłowy:

  `MyBase.MyBase.BtnOK_Click()`

- nie można używać `MyBase` w modułach.

- nie można użyć `MyBase`, aby uzyskać dostęp do składowych klasy bazowej, które są oznaczone jako `Friend`, jeśli klasa bazowa znajduje się w innym zestawie.

Aby uzyskać więcej informacji i inny przykład, zobacz [jak: dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).

## <a name="the-myclass-keyword"></a>Słowo kluczowe MyClass

Słowo kluczowe `MyClass` zachowuje się jak zmienna obiektu, która odwołuje się do bieżącego wystąpienia klasy jako pierwotnie zaimplementowane. `MyClass` przypomina `Me`, ale każde wywołanie metody i właściwości na `MyClass` jest traktowane jakby Metoda lub właściwość były [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). W związku z tym metoda lub właściwość nie ma wpływ na zastępowanie w klasie pochodnej.

- `MyClass` jest słowem kluczowym, a nie obiektem rzeczywistym. `MyClass` nie można przypisać do zmiennej, przekazywać do procedur ani używać w porównaniu `Is`.

- `MyClass` odwołuje się do klasy zawierającej i jej dziedziczonych elementów członkowskich.

- `MyClass` może służyć jako kwalifikator dla członków `Shared`.

- nie można użyć `MyClass` wewnątrz metody `Shared`, ale może być używana wewnątrz metody wystąpienia, aby uzyskać dostęp do współużytkowanej składowej klasy.

- nie można używać `MyClass` w modułach standardowych.

- `MyClass` może służyć do kwalifikowania metody, która jest zdefiniowana w klasie bazowej i która nie ma implementacji metody podanej w tej klasie. Takie odwołanie ma takie samo znaczenie jak *metoda*`MyBase.`.

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

Mimo że `derivedClass` przesłania `testMethod`, słowo kluczowe `MyClass` w `useMyClass` NULLIFIES efekty przesłaniania, a kompilator rozpoznaje wywołanie do wersji klasy bazowej programu `testMethod`.

## <a name="see-also"></a>Zobacz także

- [Inherits, instrukcja](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase i MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
