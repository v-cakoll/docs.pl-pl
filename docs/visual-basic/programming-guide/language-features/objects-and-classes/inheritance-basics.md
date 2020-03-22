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
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="b8383-102">Podstawowe informacje o dziedziczeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8383-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="b8383-103">Instrukcja `Inherits` jest używana do deklarowania nowej klasy, zwanej *klasą pochodną,* na podstawie istniejącej klasy, znanej jako *klasa podstawowa.*</span><span class="sxs-lookup"><span data-stu-id="b8383-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="b8383-104">Klasy pochodne dziedziczą i mogą rozszerzać właściwości, metody, zdarzenia, pola i stałe zdefiniowane w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b8383-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="b8383-105">W poniższej sekcji opisano niektóre reguły dziedziczenia i modyfikatory, których można użyć do zmiany sposobu dziedziczenia lub dziedziczenia klas:</span><span class="sxs-lookup"><span data-stu-id="b8383-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="b8383-106">Domyślnie wszystkie klasy są dziedziczone, `NotInheritable` chyba że oznaczone słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="b8383-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="b8383-107">Klasy mogą dziedziczyć z innych klas w projekcie lub z klas w innych zestawach, które odwołuje się do projektu.</span><span class="sxs-lookup"><span data-stu-id="b8383-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="b8383-108">W przeciwieństwie do języków, które zezwalają na wielokrotne dziedziczenie Visual Basic zezwala tylko na pojedyncze dziedziczenie w klasach; oznacza to, że klasy pochodne mogą mieć tylko jedną klasę podstawową.</span><span class="sxs-lookup"><span data-stu-id="b8383-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="b8383-109">Mimo że wiele dziedziczenia nie jest dozwolone w klasach, klasy można zaimplementować wiele interfejsów, które mogą skutecznie osiągnąć te same cele.</span><span class="sxs-lookup"><span data-stu-id="b8383-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="b8383-110">Aby zapobiec uwidacznianiu elementów podlegających ograniczeniom w klasie podstawowej, typ dostępu klasy pochodnej musi być równy lub bardziej restrykcyjny niż jego klasa podstawowa.</span><span class="sxs-lookup"><span data-stu-id="b8383-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="b8383-111">Na przykład `Public` klasa nie `Friend` może `Private` dziedziczyć `Friend` klasy lub `Private` klasy, a klasa nie może dziedziczyć klasy.</span><span class="sxs-lookup"><span data-stu-id="b8383-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="b8383-112">Modyfikatory dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="b8383-112">Inheritance Modifiers</span></span>

<span data-ttu-id="b8383-113">Visual Basic wprowadza następujące instrukcje na poziomie klasy i modyfikatory do obsługi dziedziczenia:</span><span class="sxs-lookup"><span data-stu-id="b8383-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="b8383-114">`Inherits`instrukcja — określa klasę podstawową.</span><span class="sxs-lookup"><span data-stu-id="b8383-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="b8383-115">`NotInheritable`modyfikator — uniemożliwia programistom używanie klasy jako klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b8383-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="b8383-116">`MustInherit`modyfikator — określa, że klasa jest przeznaczona tylko do użytku jako klasa podstawowa.</span><span class="sxs-lookup"><span data-stu-id="b8383-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="b8383-117">Wystąpienia `MustInherit` klas nie mogą być tworzone bezpośrednio; mogą być tworzone tylko jako wystąpienia klasy podstawowej klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b8383-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="b8383-118">(Inne języki programowania, takie jak C++ i C#, używają terminu *klasy abstrakcyjnej* do opisania takiej klasy.)</span><span class="sxs-lookup"><span data-stu-id="b8383-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="b8383-119">Zastępowanie właściwości i metod w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="b8383-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="b8383-120">Domyślnie klasa pochodna dziedziczy właściwości i metody z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b8383-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="b8383-121">Jeśli dziedziczona właściwość lub metoda musi zachowywać się inaczej w klasie pochodnej, może zostać *zastąpiona.*</span><span class="sxs-lookup"><span data-stu-id="b8383-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="b8383-122">Oznacza to, że można zdefiniować nową implementację metody w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b8383-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="b8383-123">Następujące modyfikatory są używane do kontrolowania, jak właściwości i metody są zastępowane:</span><span class="sxs-lookup"><span data-stu-id="b8383-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="b8383-124">`Overridable`— Umożliwia właściwość lub metodę w klasie, która ma zostać zastąpiona w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b8383-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="b8383-125">`Overrides`— Zastępuje właściwość lub metodę zdefiniowaną `Overridable` w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b8383-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="b8383-126">`NotOverridable`— Zapobiega nadpisywania właściwości lub metody w klasie dziedziczącej.</span><span class="sxs-lookup"><span data-stu-id="b8383-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="b8383-127">Domyślnie `Public` metody `NotOverridable`są .</span><span class="sxs-lookup"><span data-stu-id="b8383-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="b8383-128">`MustOverride`— Wymaga, aby klasa pochodna zastępowała właściwość lub metodę.</span><span class="sxs-lookup"><span data-stu-id="b8383-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="b8383-129">Gdy `MustOverride` słowo kluczowe jest używane, definicja `Sub` `Function`metody `Property` składa się tylko z , lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b8383-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="b8383-130">Żadne inne instrukcje nie są dozwolone, `End Sub` `End Function` a w szczególności nie ma ani nie ma instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b8383-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="b8383-131">`MustOverride`metody muszą być `MustInherit` zadeklarowane w klasach.</span><span class="sxs-lookup"><span data-stu-id="b8383-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="b8383-132">Załóżmy, że chcesz zdefiniować klasy do obsługi listy płac.</span><span class="sxs-lookup"><span data-stu-id="b8383-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="b8383-133">Można zdefiniować `Payroll` klasę rodzajową, która zawiera metodę obliczającą `RunPayroll` listę płac dla typowego tygodnia.</span><span class="sxs-lookup"><span data-stu-id="b8383-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="b8383-134">Następnie można `Payroll` użyć jako klasy podstawowej `BonusPayroll` dla bardziej wyspecjalizowanej klasy, która może być używana podczas dystrybucji premii pracowniczych.</span><span class="sxs-lookup"><span data-stu-id="b8383-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="b8383-135">Klasa `BonusPayroll` może dziedziczyć i zastępować metodę zdefiniowaną `PayEmployee` w klasie podstawowej. `Payroll`</span><span class="sxs-lookup"><span data-stu-id="b8383-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="b8383-136">Poniższy przykład definiuje klasę `Payroll,` podstawową i klasę `BonusPayroll`pochodną, która zastępuje metodę `PayEmployee`dziedziczoną, .</span><span class="sxs-lookup"><span data-stu-id="b8383-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="b8383-137">Procedura , `RunPayroll`tworzy, a `Payroll` następnie przekazuje `BonusPayroll` obiekt i `Pay`obiekt do funkcji, która wykonuje `PayEmployee` metodę obu obiektów.</span><span class="sxs-lookup"><span data-stu-id="b8383-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="b8383-138">Słowo kluczowe MyBase</span><span class="sxs-lookup"><span data-stu-id="b8383-138">The MyBase Keyword</span></span>

<span data-ttu-id="b8383-139">Słowo `MyBase` kluczowe zachowuje się jak zmienna obiektu, która odwołuje się do klasy podstawowej bieżącego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="b8383-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="b8383-140">`MyBase`jest często używany do uzyskiwania dostępu do elementów członkowskich klasy podstawowej, które są zastępowane lub cieniowane w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b8383-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="b8383-141">W szczególności `MyBase.New` jest używany do jawnego wywołania konstruktora klasy podstawowej z konstruktora klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="b8383-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="b8383-142">Załóżmy na przykład, że projektujesz klasę pochodną, która zastępuje metodę dziedziczoną z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b8383-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="b8383-143">Zastąpiona metoda może wywołać metodę w klasie podstawowej i zmodyfikować wartość zwracaną, jak pokazano w następującym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="b8383-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="b8383-144">Na poniższej liście opisano `MyBase`ograniczenia dotyczące używania:</span><span class="sxs-lookup"><span data-stu-id="b8383-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="b8383-145">`MyBase`odnosi się do natychmiastowej klasy podstawowej i jej odziedziczonych członków.</span><span class="sxs-lookup"><span data-stu-id="b8383-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="b8383-146">Nie można użyć `Private` dostępu do elementów członkowskich w klasie.</span><span class="sxs-lookup"><span data-stu-id="b8383-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="b8383-147">`MyBase`jest słowem kluczowym, a nie prawdziwym obiektem.</span><span class="sxs-lookup"><span data-stu-id="b8383-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="b8383-148">`MyBase`nie można przypisać do zmiennej, przejść do `Is` procedur lub użyć w porównaniu.</span><span class="sxs-lookup"><span data-stu-id="b8383-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="b8383-149">Metoda, `MyBase` która kwalifikuje się nie musi być zdefiniowana w natychmiastowej klasie podstawowej; zamiast tego może być zdefiniowany w pośrednio dziedziczonej klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b8383-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="b8383-150">Aby odwołanie kwalifikowane `MyBase` przez do poprawnego skompilowania, niektóre klasy podstawowej musi zawierać metodę pasującą do nazwy i typów parametrów, które pojawiają się w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="b8383-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="b8383-151">Nie można `MyBase` wywołać metody klasy `MustOverride` podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b8383-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="b8383-152">`MyBase`nie mogą być wykorzystane do zakwalifikowania się.</span><span class="sxs-lookup"><span data-stu-id="b8383-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="b8383-153">W związku z tym następujący kod jest nieprawidłowy:</span><span class="sxs-lookup"><span data-stu-id="b8383-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="b8383-154">`MyBase`nie mogą być używane w modułach.</span><span class="sxs-lookup"><span data-stu-id="b8383-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="b8383-155">`MyBase`nie można użyć do uzyskania dostępu `Friend` do elementów członkowskich klasy podstawowej, które są oznaczone tak, jakby klasa podstawowa znajduje się w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="b8383-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="b8383-156">Aby uzyskać więcej informacji i inny przykład, zobacz [Jak: Dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="b8383-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="b8383-157">Słowo kluczowe MyClass</span><span class="sxs-lookup"><span data-stu-id="b8383-157">The MyClass Keyword</span></span>

<span data-ttu-id="b8383-158">Słowo `MyClass` kluczowe zachowuje się jak zmienna obiektu, która odwołuje się do bieżącego wystąpienia klasy, jak pierwotnie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="b8383-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="b8383-159">`MyClass`przypomina `Me`, ale każda metoda `MyClass` i właściwość wywołać na jest traktowana tak, jakby metoda lub właściwość [były NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="b8383-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="b8383-160">W związku z tym metoda lub właściwość nie ma wpływu na zastąpienie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b8383-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="b8383-161">`MyClass`jest słowem kluczowym, a nie prawdziwym obiektem.</span><span class="sxs-lookup"><span data-stu-id="b8383-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="b8383-162">`MyClass`nie można przypisać do zmiennej, przejść do `Is` procedur lub użyć w porównaniu.</span><span class="sxs-lookup"><span data-stu-id="b8383-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="b8383-163">`MyClass`odnosi się do klasy zawierającej i jej odziedziczonych członków.</span><span class="sxs-lookup"><span data-stu-id="b8383-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="b8383-164">`MyClass`może służyć jako kwalifikator dla `Shared` członków.</span><span class="sxs-lookup"><span data-stu-id="b8383-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="b8383-165">`MyClass`nie można użyć `Shared` wewnątrz metody, ale może służyć wewnątrz metody wystąpienia, aby uzyskać dostęp do udostępnionego elementu członkowskiego klasy.</span><span class="sxs-lookup"><span data-stu-id="b8383-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="b8383-166">`MyClass`nie mogą być stosowane w standardowych modułach.</span><span class="sxs-lookup"><span data-stu-id="b8383-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="b8383-167">`MyClass`może służyć do zakwalifikowania metody, która jest zdefiniowana w klasie podstawowej i która nie ma implementacji metody przewidzianej w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="b8383-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="b8383-168">Takie odniesienie ma takie `MyBase.`samo znaczenie jak *metoda*.</span><span class="sxs-lookup"><span data-stu-id="b8383-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="b8383-169">Poniższy przykład `Me` porównuje `MyClass`i .</span><span class="sxs-lookup"><span data-stu-id="b8383-169">The following example compares `Me` and `MyClass`.</span></span>

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

<span data-ttu-id="b8383-170">Mimo `derivedClass` że zastępuje `testMethod`, `MyClass` słowo `useMyClass` kluczowe w unieważnia skutki zastąpienia, a kompilator rozwiązuje wywołanie `testMethod`do wersji klasy podstawowej .</span><span class="sxs-lookup"><span data-stu-id="b8383-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8383-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8383-171">See also</span></span>

- [<span data-ttu-id="b8383-172">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b8383-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="b8383-173">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="b8383-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
