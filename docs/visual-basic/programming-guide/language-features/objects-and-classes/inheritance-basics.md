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
ms.openlocfilehash: 3bf1847f618a642d26df4aa1c5247a4ba2bd3b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411782"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="c9158-102">Podstawowe informacje o dziedziczeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9158-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="c9158-103">`Inherits`Instrukcja jest używana do deklarowania nowej klasy, zwanej *klasą pochodną*, na podstawie istniejącej klasy, znanej jako *Klasa bazowa*.</span><span class="sxs-lookup"><span data-stu-id="c9158-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="c9158-104">Klasy pochodne dziedziczą i mogą być rozszerzone, właściwości, metody, zdarzenia, pola i stałe zdefiniowane w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="c9158-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="c9158-105">W poniższej sekcji opisano niektóre reguły dziedziczenia oraz modyfikatory, których można użyć do zmiany metod dziedziczonych lub dziedziczonych przez klasy:</span><span class="sxs-lookup"><span data-stu-id="c9158-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="c9158-106">Domyślnie wszystkie klasy są dziedziczone, chyba że oznaczono za pomocą `NotInheritable` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="c9158-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="c9158-107">Klasy mogą dziedziczyć z innych klas w projekcie lub z klas w innych zestawach, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="c9158-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="c9158-108">W przeciwieństwie do języków, które zezwalają na wielokrotne dziedziczenie, Visual Basic zezwala tylko na jedno dziedziczenie w klasach. oznacza to, że klasy pochodne mogą mieć tylko jedną klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="c9158-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="c9158-109">Chociaż nie jest dozwolone wielokrotne dziedziczenie w klasach, klasy mogą implementować wiele interfejsów, co może efektywnie wykonywać te same punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="c9158-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="c9158-110">Aby zapobiec ujawnieniu elementów z ograniczeniami w klasie bazowej, typ dostępu klasy pochodnej musi być równy lub bardziej restrykcyjny niż jego Klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="c9158-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="c9158-111">Na przykład `Public` Klasa nie może dziedziczyć `Friend` `Private` klasy lub, a Klasa `Friend` nie może dziedziczyć `Private` klasy.</span><span class="sxs-lookup"><span data-stu-id="c9158-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="c9158-112">Modyfikatory dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="c9158-112">Inheritance Modifiers</span></span>

<span data-ttu-id="c9158-113">Visual Basic wprowadza następujące instrukcje i Modyfikatory na poziomie klasy do obsługi dziedziczenia:</span><span class="sxs-lookup"><span data-stu-id="c9158-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="c9158-114">`Inherits`Instrukcja — określa klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="c9158-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="c9158-115">`NotInheritable`Modyfikator — uniemożliwia programistom Używanie klasy jako klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c9158-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="c9158-116">`MustInherit`modyfikator — określa, że Klasa jest przeznaczona do użycia tylko jako klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="c9158-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="c9158-117">Wystąpienia `MustInherit` klas nie mogą być tworzone bezpośrednio; mogą być tworzone tylko jako wystąpienia klasy bazowej klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c9158-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="c9158-118">(Inne języki programowania, takie jak C++ i C#, używają *klasy abstrakcyjnej* do opisywania takiej klasy).</span><span class="sxs-lookup"><span data-stu-id="c9158-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="c9158-119">Zastępowanie właściwości i metod w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="c9158-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="c9158-120">Domyślnie Klasa pochodna dziedziczy właściwości i metody z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c9158-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="c9158-121">Jeśli dziedziczona właściwość lub metoda musi zachowywać się inaczej w klasie pochodnej, można ją *przesłonić*.</span><span class="sxs-lookup"><span data-stu-id="c9158-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="c9158-122">Oznacza to, że można zdefiniować nową implementację metody w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c9158-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="c9158-123">Poniższe Modyfikatory służą do kontrolowania sposobu przesłania właściwości i metod:</span><span class="sxs-lookup"><span data-stu-id="c9158-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="c9158-124">`Overridable`— Umożliwia zastąpienie właściwości lub metody w klasie pochodnej w klasie.</span><span class="sxs-lookup"><span data-stu-id="c9158-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="c9158-125">`Overrides`— Przesłania `Overridable` Właściwość lub metodę zdefiniowaną w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="c9158-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="c9158-126">`NotOverridable`— Zapobiega zastąpieniu właściwości lub metody w klasie dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="c9158-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="c9158-127">Domyślnie `Public` metody są `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="c9158-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="c9158-128">`MustOverride`— Wymaga, aby Klasa pochodna przesłaniał właściwość lub metodę.</span><span class="sxs-lookup"><span data-stu-id="c9158-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="c9158-129">Gdy `MustOverride` słowo kluczowe jest używane, definicja metody składa się z tylko `Sub` `Function` instrukcji,, lub `Property` .</span><span class="sxs-lookup"><span data-stu-id="c9158-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="c9158-130">Nie są dozwolone żadne inne instrukcje, a w przeciwnym razie nie ma `End Sub` `End Function` instrukcji or.</span><span class="sxs-lookup"><span data-stu-id="c9158-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="c9158-131">`MustOverride`metody muszą być zadeklarowane w `MustInherit` klasach.</span><span class="sxs-lookup"><span data-stu-id="c9158-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="c9158-132">Załóżmy, że chcesz zdefiniować klasy do obsługi listy płac.</span><span class="sxs-lookup"><span data-stu-id="c9158-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="c9158-133">Można zdefiniować klasę generyczną zawierającą `Payroll` `RunPayroll` metodę, która oblicza listę płac dla typowego tygodnia.</span><span class="sxs-lookup"><span data-stu-id="c9158-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="c9158-134">Można użyć `Payroll` jako klasy bazowej dla bardziej wyspecjalizowanej `BonusPayroll` klasy, która może być używana do dystrybucji premii pracowników.</span><span class="sxs-lookup"><span data-stu-id="c9158-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="c9158-135">`BonusPayroll`Klasa może dziedziczyć i przesłonić `PayEmployee` metodę zdefiniowaną w klasie bazowej `Payroll` .</span><span class="sxs-lookup"><span data-stu-id="c9158-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="c9158-136">W poniższym przykładzie zdefiniowano klasę bazową `Payroll,` i klasę pochodną, `BonusPayroll` która zastępuje metodę dziedziczoną `PayEmployee` .</span><span class="sxs-lookup"><span data-stu-id="c9158-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="c9158-137">Procedura, `RunPayroll` ,, tworzy, a następnie przekazuje `Payroll` obiekt i `BonusPayroll` obiekt do funkcji, `Pay` , która wykonuje `PayEmployee` metodę obu obiektów.</span><span class="sxs-lookup"><span data-stu-id="c9158-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="c9158-138">Słowo kluczowe MyBase</span><span class="sxs-lookup"><span data-stu-id="c9158-138">The MyBase Keyword</span></span>

<span data-ttu-id="c9158-139">`MyBase`Słowo kluczowe zachowuje się jak zmienna obiektu, która odwołuje się do klasy podstawowej bieżącego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="c9158-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="c9158-140">`MyBase`jest często używany do uzyskiwania dostępu do składowych klasy bazowej, które są zastępowane lub zasłonięte w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c9158-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="c9158-141">W szczególności `MyBase.New` jest używany do jawnego wywoływania konstruktora klasy bazowej z konstruktora klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c9158-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="c9158-142">Załóżmy na przykład, że projektujesz klasę pochodną, która zastępuje metodę dziedziczoną z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c9158-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="c9158-143">Zastąpiona metoda może wywołać metodę w klasie bazowej i zmodyfikować wartość zwracaną, jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="c9158-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="c9158-144">Na poniższej liście opisano ograniczenia dotyczące korzystania z programu `MyBase` :</span><span class="sxs-lookup"><span data-stu-id="c9158-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="c9158-145">`MyBase`odwołuje się do bezpośredniej klasy podstawowej i jej dziedziczonych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c9158-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="c9158-146">Nie można jej użyć w celu uzyskania dostępu do `Private` elementów członkowskich w klasie.</span><span class="sxs-lookup"><span data-stu-id="c9158-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="c9158-147">`MyBase`jest słowem kluczowym, a nie obiektem rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="c9158-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="c9158-148">`MyBase`nie można przypisać do zmiennej, przekazywać do procedur ani używać w `Is` porównaniu.</span><span class="sxs-lookup"><span data-stu-id="c9158-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="c9158-149">Metoda, która `MyBase` kwalifikuje się nie musi być zdefiniowana w bezpośredniej klasie podstawowej; może być zdefiniowana w pośrednio dziedziczonej klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="c9158-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="c9158-150">Aby odwołanie kwalifikowane przez `MyBase` program do prawidłowego kompilowania, pewna klasa bazowa musi zawierać metodę zgodną z nazwą i typami parametrów, które pojawiają się w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="c9158-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="c9158-151">Nie można użyć `MyBase` do wywołania `MustOverride` metod klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c9158-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="c9158-152">`MyBase`nie można jej użyć do zakwalifikowania się.</span><span class="sxs-lookup"><span data-stu-id="c9158-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="c9158-153">W związku z tym następujący kod jest nieprawidłowy:</span><span class="sxs-lookup"><span data-stu-id="c9158-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="c9158-154">`MyBase`nie można używać w modułach.</span><span class="sxs-lookup"><span data-stu-id="c9158-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="c9158-155">`MyBase`nie można użyć w celu uzyskania dostępu do składowych klasy bazowej, które są oznaczone jako, `Friend` Jeśli klasa bazowa znajduje się w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="c9158-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="c9158-156">Aby uzyskać więcej informacji i inny przykład, zobacz [jak: dostęp do zmiennej ukrytej przez klasę pochodną](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="c9158-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="c9158-157">Słowo kluczowe MyClass</span><span class="sxs-lookup"><span data-stu-id="c9158-157">The MyClass Keyword</span></span>

<span data-ttu-id="c9158-158">`MyClass`Słowo kluczowe zachowuje się jak zmienna obiektu, która odwołuje się do bieżącego wystąpienia klasy jako pierwotnie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="c9158-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="c9158-159">`MyClass`przypomina `Me` , ale każde wywołanie metody i właściwości `MyClass` jest traktowane jak, jeśli metoda lub właściwość zostały [NotOverridable](../../../language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="c9158-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="c9158-160">W związku z tym metoda lub właściwość nie ma wpływ na zastępowanie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c9158-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="c9158-161">`MyClass`jest słowem kluczowym, a nie obiektem rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="c9158-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="c9158-162">`MyClass`nie można przypisać do zmiennej, przekazywać do procedur ani używać w `Is` porównaniu.</span><span class="sxs-lookup"><span data-stu-id="c9158-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="c9158-163">`MyClass`odwołuje się do klasy zawierającej i jej dziedziczonych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c9158-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="c9158-164">`MyClass`może służyć jako kwalifikator dla `Shared` elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c9158-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="c9158-165">`MyClass`nie można użyć wewnątrz `Shared` metody, ale może być używana wewnątrz metody wystąpienia, aby uzyskać dostęp do współużytkowanej składowej klasy.</span><span class="sxs-lookup"><span data-stu-id="c9158-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="c9158-166">`MyClass`nie można używać w modułach standardowych.</span><span class="sxs-lookup"><span data-stu-id="c9158-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="c9158-167">`MyClass`może służyć do kwalifikowania metody, która jest zdefiniowana w klasie bazowej i która nie ma implementacji metody podanej w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="c9158-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="c9158-168">Takie odwołanie ma takie samo znaczenie jak `MyBase.` *Metoda*.</span><span class="sxs-lookup"><span data-stu-id="c9158-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="c9158-169">Poniższy przykład porówna `Me` i `MyClass` .</span><span class="sxs-lookup"><span data-stu-id="c9158-169">The following example compares `Me` and `MyClass`.</span></span>

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

<span data-ttu-id="c9158-170">Mimo że `derivedClass` zastąpień `testMethod` , `MyClass` słowo kluczowe w `useMyClass` NULLIFIES efekty przesłaniania, a kompilator rozpoznaje wywołanie do wersji klasy bazowej `testMethod` .</span><span class="sxs-lookup"><span data-stu-id="c9158-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9158-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9158-171">See also</span></span>

- [<span data-ttu-id="c9158-172">Inherits — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="c9158-172">Inherits Statement</span></span>](../../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="c9158-173">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="c9158-173">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
