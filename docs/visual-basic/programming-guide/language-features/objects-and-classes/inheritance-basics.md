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
ms.openlocfilehash: 8a75b75ef9acb4c89f4c7d05f1410d4ca70e680b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582744"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="cd27c-102">Podstawowe informacje o dziedziczeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd27c-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="cd27c-103">Instrukcja `Inherits` służy do deklarowania nowej klasy, zwanej *klasą pochodną*, na podstawie istniejącej klasy, znanej jako *Klasa bazowa*.</span><span class="sxs-lookup"><span data-stu-id="cd27c-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="cd27c-104">Klasy pochodne dziedziczą i mogą być rozszerzone, właściwości, metody, zdarzenia, pola i stałe zdefiniowane w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="cd27c-105">W poniższej sekcji opisano niektóre reguły dziedziczenia oraz modyfikatory, których można użyć do zmiany metod dziedziczonych lub dziedziczonych przez klasy:</span><span class="sxs-lookup"><span data-stu-id="cd27c-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="cd27c-106">Domyślnie wszystkie klasy są dziedziczone, chyba że oznaczono za pomocą słowa kluczowego `NotInheritable`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="cd27c-107">Klasy mogą dziedziczyć z innych klas w projekcie lub z klas w innych zestawach, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="cd27c-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="cd27c-108">W przeciwieństwie do języków, które zezwalają na wielokrotne dziedziczenie, Visual Basic zezwala tylko na jedno dziedziczenie w klasach. oznacza to, że klasy pochodne mogą mieć tylko jedną klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="cd27c-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="cd27c-109">Chociaż nie jest dozwolone wielokrotne dziedziczenie w klasach, klasy mogą implementować wiele interfejsów, co może efektywnie wykonywać te same punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="cd27c-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="cd27c-110">Aby zapobiec ujawnieniu elementów z ograniczeniami w klasie bazowej, typ dostępu klasy pochodnej musi być równy lub bardziej restrykcyjny niż jego Klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="cd27c-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="cd27c-111">Na przykład Klasa `Public` nie może dziedziczyć `Friend` lub klasy `Private`, a Klasa `Friend` nie może dziedziczyć klasy `Private`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="cd27c-112">Modyfikatory dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="cd27c-112">Inheritance Modifiers</span></span>

<span data-ttu-id="cd27c-113">Visual Basic wprowadza następujące instrukcje i Modyfikatory na poziomie klasy do obsługi dziedziczenia:</span><span class="sxs-lookup"><span data-stu-id="cd27c-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="cd27c-114">Instrukcja `Inherits` — określa klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="cd27c-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="cd27c-115">modyfikator `NotInheritable` — uniemożliwia programistom Używanie klasy jako klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="cd27c-116">modyfikator `MustInherit` — określa, że Klasa jest przeznaczona do użycia tylko jako klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="cd27c-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="cd27c-117">Wystąpienia klas `MustInherit` nie mogą być tworzone bezpośrednio; mogą być tworzone tylko jako wystąpienia klasy bazowej klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="cd27c-118">(Inne języki programowania, takie jak C++ i C#, używają *klasy abstrakcyjnej* do opisywania takiej klasy).</span><span class="sxs-lookup"><span data-stu-id="cd27c-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="cd27c-119">Zastępowanie właściwości i metod w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="cd27c-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="cd27c-120">Domyślnie Klasa pochodna dziedziczy właściwości i metody z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="cd27c-121">Jeśli dziedziczona właściwość lub metoda musi zachowywać się inaczej w klasie pochodnej, można ją *przesłonić*.</span><span class="sxs-lookup"><span data-stu-id="cd27c-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="cd27c-122">Oznacza to, że można zdefiniować nową implementację metody w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="cd27c-123">Poniższe Modyfikatory służą do kontrolowania sposobu przesłania właściwości i metod:</span><span class="sxs-lookup"><span data-stu-id="cd27c-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="cd27c-124">`Overridable` — umożliwia zastąpienie właściwości lub metody w klasie pochodnej w klasie.</span><span class="sxs-lookup"><span data-stu-id="cd27c-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="cd27c-125">`Overrides` — przesłania Właściwość `Overridable` lub metodę zdefiniowaną w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="cd27c-126">`NotOverridable` — zapobiega przesłanianiu przez właściwość lub metodę w klasie dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="cd27c-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="cd27c-127">Domyślnie `NotOverridable` metody `Public` są.</span><span class="sxs-lookup"><span data-stu-id="cd27c-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="cd27c-128">`MustOverride` — wymaga, aby Klasa pochodna przesłaniał właściwość lub metodę.</span><span class="sxs-lookup"><span data-stu-id="cd27c-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="cd27c-129">Gdy używane jest słowo kluczowe `MustOverride`, definicja metody składa się tylko z instrukcji `Sub`, `Function` lub `Property`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="cd27c-130">Żadne inne instrukcje nie są dozwolone i nie ma żadnej instrukcji `End Sub` ani `End Function`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="cd27c-131">Metody `MustOverride` muszą być zadeklarowane w klasach `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="cd27c-132">Załóżmy, że chcesz zdefiniować klasy do obsługi listy płac.</span><span class="sxs-lookup"><span data-stu-id="cd27c-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="cd27c-133">Można zdefiniować generyczną klasę `Payroll`, która zawiera metodę `RunPayroll`, która oblicza listę płac dla typowego tygodnia.</span><span class="sxs-lookup"><span data-stu-id="cd27c-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="cd27c-134">Następnie można użyć `Payroll` jako klasy bazowej dla bardziej wyspecjalizowanej klasy `BonusPayroll`, która może być używana do dystrybucji premii pracowników.</span><span class="sxs-lookup"><span data-stu-id="cd27c-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="cd27c-135">Klasa `BonusPayroll` może dziedziczyć i przesłonić metodę `PayEmployee` zdefiniowaną w klasie podstawowej `Payroll`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="cd27c-136">W poniższym przykładzie zdefiniowano klasę bazową, `Payroll,` i klasę pochodną `BonusPayroll`, która zastępuje metodę dziedziczoną, `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="cd27c-137">Procedura `RunPayroll`, tworzy, a następnie przekazuje obiekt `Payroll` i obiekt `BonusPayroll` do funkcji, `Pay`, która wykonuje metodę `PayEmployee` obu obiektów.</span><span class="sxs-lookup"><span data-stu-id="cd27c-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="cd27c-138">Słowo kluczowe MyBase</span><span class="sxs-lookup"><span data-stu-id="cd27c-138">The MyBase Keyword</span></span>

<span data-ttu-id="cd27c-139">Słowo kluczowe `MyBase` zachowuje się jak zmienna obiektu odwołująca się do klasy podstawowej bieżącego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="cd27c-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="cd27c-140">`MyBase` jest często używana do uzyskiwania dostępu do składowych klasy bazowej, które są zastępowane lub zasłonięte w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="cd27c-141">W szczególności `MyBase.New` jest używany do jawnego wywoływania konstruktora klasy bazowej z konstruktora klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="cd27c-142">Załóżmy na przykład, że projektujesz klasę pochodną, która zastępuje metodę dziedziczoną z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="cd27c-143">Zastąpiona metoda może wywołać metodę w klasie bazowej i zmodyfikować wartość zwracaną, jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="cd27c-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="cd27c-144">Poniższa lista zawiera opis ograniczeń dotyczących używania `MyBase`:</span><span class="sxs-lookup"><span data-stu-id="cd27c-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="cd27c-145">`MyBase` odwołuje się do bezpośredniej klasy podstawowej i jej dziedziczonych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="cd27c-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="cd27c-146">Nie można jej użyć w celu uzyskania dostępu do `Private` elementów członkowskich w klasie.</span><span class="sxs-lookup"><span data-stu-id="cd27c-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="cd27c-147">`MyBase` jest słowem kluczowym, a nie obiektem rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="cd27c-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="cd27c-148">`MyBase` nie można przypisać do zmiennej, przekazywać do procedur ani używać w porównaniu `Is`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="cd27c-149">Metoda, która `MyBase` kwalifikatory, nie musi być zdefiniowana w bezpośredniej klasie podstawowej; może być zdefiniowana w niejawnie dziedziczonej klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="cd27c-150">Aby dokumentacja kwalifikowana przez `MyBase` była skompilowana prawidłowo, pewna klasa bazowa musi zawierać metodę zgodną z nazwą i typami parametrów, które są wyświetlane w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="cd27c-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="cd27c-151">Nie można użyć `MyBase` do wywołania `MustOverride` metod klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="cd27c-152">`MyBase` nie może być używana do kwalifikowania się samego siebie.</span><span class="sxs-lookup"><span data-stu-id="cd27c-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="cd27c-153">W związku z tym następujący kod jest nieprawidłowy:</span><span class="sxs-lookup"><span data-stu-id="cd27c-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="cd27c-154">nie można używać `MyBase` w modułach.</span><span class="sxs-lookup"><span data-stu-id="cd27c-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="cd27c-155">nie można użyć `MyBase`, aby uzyskać dostęp do składowych klasy bazowej, które są oznaczone jako `Friend`, jeśli klasa bazowa znajduje się w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="cd27c-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="cd27c-156">Aby uzyskać więcej informacji i inny przykład, zobacz [jak: dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="cd27c-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="cd27c-157">Słowo kluczowe MyClass</span><span class="sxs-lookup"><span data-stu-id="cd27c-157">The MyClass Keyword</span></span>

<span data-ttu-id="cd27c-158">Słowo kluczowe `MyClass` zachowuje się jak zmienna obiektu, która odwołuje się do bieżącego wystąpienia klasy jako pierwotnie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="cd27c-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="cd27c-159">`MyClass` przypomina `Me`, ale każde wywołanie metody i właściwości na `MyClass` jest traktowane jakby Metoda lub właściwość były [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="cd27c-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="cd27c-160">W związku z tym metoda lub właściwość nie ma wpływ na zastępowanie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cd27c-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="cd27c-161">`MyClass` jest słowem kluczowym, a nie obiektem rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="cd27c-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="cd27c-162">`MyClass` nie można przypisać do zmiennej, przekazywać do procedur ani używać w porównaniu `Is`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="cd27c-163">`MyClass` odwołuje się do klasy zawierającej i jej dziedziczonych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="cd27c-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="cd27c-164">`MyClass` może służyć jako kwalifikator dla członków `Shared`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="cd27c-165">nie można użyć `MyClass` wewnątrz metody `Shared`, ale może być używana wewnątrz metody wystąpienia, aby uzyskać dostęp do współużytkowanej składowej klasy.</span><span class="sxs-lookup"><span data-stu-id="cd27c-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="cd27c-166">nie można używać `MyClass` w modułach standardowych.</span><span class="sxs-lookup"><span data-stu-id="cd27c-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="cd27c-167">`MyClass` może służyć do kwalifikowania metody, która jest zdefiniowana w klasie bazowej i która nie ma implementacji metody podanej w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="cd27c-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="cd27c-168">Takie odwołanie ma takie samo znaczenie jak*metoda*`MyBase.`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="cd27c-169">Poniższy przykład porównuje `Me` i `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-169">The following example compares `Me` and `MyClass`.</span></span>

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

<span data-ttu-id="cd27c-170">Mimo że `derivedClass` przesłania `testMethod`, słowo kluczowe `MyClass` w `useMyClass` NULLIFIES efekty przesłaniania, a kompilator rozpoznaje wywołanie do wersji klasy bazowej programu `testMethod`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd27c-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd27c-171">See also</span></span>

- [<span data-ttu-id="cd27c-172">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd27c-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="cd27c-173">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="cd27c-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
