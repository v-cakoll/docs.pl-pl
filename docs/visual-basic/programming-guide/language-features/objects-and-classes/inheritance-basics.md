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
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="98de6-102">Podstawowe informacje o dziedziczeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98de6-102">Inheritance Basics (Visual Basic)</span></span>
<span data-ttu-id="98de6-103">`Inherits` Instrukcji służy do deklarowania nową klasę o nazwie *klasy*, oparte na istniejącej klasy, znany jako *klasa podstawowa*.</span><span class="sxs-lookup"><span data-stu-id="98de6-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="98de6-104">Klasy pochodne dziedziczą i można rozszerzyć, właściwości, metody, zdarzenia, pól i stałe zdefiniowana w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="98de6-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="98de6-105">W poniższej sekcji opisano niektóre zasady dotyczące dziedziczenia, a modyfikatorów, których można użyć, aby zmienić sposób klasy dziedziczą lub są dziedziczone:</span><span class="sxs-lookup"><span data-stu-id="98de6-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>  
  
-   <span data-ttu-id="98de6-106">Domyślnie wszystkie klasy są dziedziczone, o ile nie jest oznaczony atrybutem `NotInheritable` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="98de6-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="98de6-107">Klasy mogą dziedziczyć z innych klas do projektu lub z klas w innych zestawów, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="98de6-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>  
  
-   <span data-ttu-id="98de6-108">W odróżnieniu od języków, które umożliwiają dziedziczenie wielokrotne Visual Basic umożliwia tylko pojedyncze dziedziczenie klas; oznacza to klasy pochodne mogą mieć tylko jedną klasę podstawową.</span><span class="sxs-lookup"><span data-stu-id="98de6-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="98de6-109">Mimo że wielokrotne dziedziczenie nie jest dozwolona w klasy, klasy można zaimplementować wiele interfejsów, które można skutecznie wykonać zakończenia tego samego.</span><span class="sxs-lookup"><span data-stu-id="98de6-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>  
  
-   <span data-ttu-id="98de6-110">Aby uniemożliwić udostępnianie ograniczeniami elementy w klasie podstawowej, typ dostępu do klasy pochodnej musi być większy lub bardziej restrykcyjne od swojej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="98de6-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="98de6-111">Na przykład `Public` klasa nie dziedziczy `Friend` lub `Private` klasy, a `Friend` klasa nie dziedziczy `Private` klasy.</span><span class="sxs-lookup"><span data-stu-id="98de6-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>  
  
## <a name="inheritance-modifiers"></a><span data-ttu-id="98de6-112">Modyfikatory dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="98de6-112">Inheritance Modifiers</span></span>  
 <span data-ttu-id="98de6-113">Visual Basic wprowadza następujące instrukcje poziomie klasy i Modyfikatory do obsługi dziedziczenia:</span><span class="sxs-lookup"><span data-stu-id="98de6-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>  
  
-   <span data-ttu-id="98de6-114">`Inherits` Instrukcja — określa klasę podstawową.</span><span class="sxs-lookup"><span data-stu-id="98de6-114">`Inherits` statement — Specifies the base class.</span></span>  
  
-   <span data-ttu-id="98de6-115">`NotInheritable` Modyfikator — uniemożliwia używanie klasy jako klasę podstawową programistów.</span><span class="sxs-lookup"><span data-stu-id="98de6-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>  
  
-   <span data-ttu-id="98de6-116">`MustInherit` Modyfikator — Określa, że klasa jest przeznaczona do użycia jako klasę podstawową tylko.</span><span class="sxs-lookup"><span data-stu-id="98de6-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="98de6-117">Wystąpienia `MustInherit` klasy nie można bezpośrednio utworzyć; ich można tworzyć tylko podstawowego wystąpień klasy pochodnej klasy.</span><span class="sxs-lookup"><span data-stu-id="98de6-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="98de6-118">(Innych języków programowania, takich jak C++ i C#, używany jest termin *klasy abstrakcyjnej* do opisania tych klas.)</span><span class="sxs-lookup"><span data-stu-id="98de6-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="98de6-119">Zastępowanie właściwości i metod w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="98de6-119">Overriding Properties and Methods in Derived Classes</span></span>  
 <span data-ttu-id="98de6-120">Domyślnie Klasa pochodna dziedziczy właściwości i metody swojej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="98de6-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="98de6-121">Jeśli właściwość dziedziczona lub metoda ma zachowywać się inaczej w klasie pochodnej może być *przesłonięcia*.</span><span class="sxs-lookup"><span data-stu-id="98de6-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="98de6-122">Oznacza to można zdefiniować nowej implementacji metody w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="98de6-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="98de6-123">Następujących modyfikatorów są używane do kontrolowania sposobu przesłonięcia właściwości i metody:</span><span class="sxs-lookup"><span data-stu-id="98de6-123">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
-   <span data-ttu-id="98de6-124">`Overridable` — Umożliwia właściwości lub metody w klasie do zastąpienia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="98de6-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>  
  
-   <span data-ttu-id="98de6-125">`Overrides` — Zastępuje `Overridable` właściwości lub metody zdefiniowanej w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="98de6-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>  
  
-   <span data-ttu-id="98de6-126">`NotOverridable` — Uniemożliwia właściwości lub metody przesłaniana klasy dziedziczące.</span><span class="sxs-lookup"><span data-stu-id="98de6-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="98de6-127">Domyślnie `Public` metody są `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="98de6-127">By default, `Public` methods are `NotOverridable`.</span></span>  
  
-   <span data-ttu-id="98de6-128">`MustOverride` — Wymaga się, że klasa pochodna zastąpienie właściwości lub metody.</span><span class="sxs-lookup"><span data-stu-id="98de6-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="98de6-129">Gdy `MustOverride` słowo kluczowe jest używane, definicja metody składa się z tylko `Sub`, `Function`, lub `Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="98de6-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="98de6-130">Nie inne instrukcje są dozwolone, a w szczególności jest nie `End Sub` lub `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="98de6-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="98de6-131">`MustOverride` metody musi być zadeklarowana w `MustInherit` klasy.</span><span class="sxs-lookup"><span data-stu-id="98de6-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>  
  
 <span data-ttu-id="98de6-132">Załóżmy, że chcesz zdefiniować klasy do obsługi płacowego.</span><span class="sxs-lookup"><span data-stu-id="98de6-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="98de6-133">Można zdefiniować ogólnego `Payroll` klasę, która zawiera `RunPayroll` metodę, która oblicza płacowego typowe tygodnia.</span><span class="sxs-lookup"><span data-stu-id="98de6-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="98de6-134">Następnie można użyć `Payroll` jako klasę podstawową dla bardziej wyspecjalizowanych `BonusPayroll` klasy, która może służyć do rozpowszechniania dodatki pracownika.</span><span class="sxs-lookup"><span data-stu-id="98de6-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>  
  
 <span data-ttu-id="98de6-135">`BonusPayroll` Klasy mogą dziedziczyć i zastąpić, `PayEmployee` metody zdefiniowanej w podstawowym `Payroll` klasy.</span><span class="sxs-lookup"><span data-stu-id="98de6-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>  
  
 <span data-ttu-id="98de6-136">W poniższym przykładzie zdefiniowano klasę podstawową `Payroll,` i Klasa pochodna `BonusPayroll`, która zastępuje dziedziczonej metody `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="98de6-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="98de6-137">W procedurze `RunPayroll`, tworzy, a następnie przekazuje `Payroll` obiektu i `BonusPayroll` obiektu do funkcji, `Pay`, który jest wykonywany `PayEmployee` metody zarówno do obiektów.</span><span class="sxs-lookup"><span data-stu-id="98de6-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a><span data-ttu-id="98de6-138">MyBase — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="98de6-138">The MyBase Keyword</span></span>  
 <span data-ttu-id="98de6-139">`MyBase` — Słowo kluczowe zachowuje się jak zmienna obiektu, który odwołuje się do klasy bazowej bieżącego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="98de6-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="98de6-140">`MyBase` często umożliwia dostęp do elementów członkowskich klasy podstawowej, które są zastępowane lub cieniowanie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="98de6-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="98de6-141">W szczególności `MyBase.New` służy do jawnego wywołania konstruktora klasy podstawowej z konstruktora klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="98de6-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
 <span data-ttu-id="98de6-142">Na przykład załóżmy, że projektowania klasy pochodnej, który przesłania metodę dziedziczona z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="98de6-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="98de6-143">Przeciążonej można wywołać metody w klasie podstawowej i zmodyfikować zwracanej wartości, jak pokazano w poniższy fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="98de6-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 <span data-ttu-id="98de6-144">Na poniższej liście wymieniono ograniczenia dotyczące używania `MyBase`:</span><span class="sxs-lookup"><span data-stu-id="98de6-144">The following list describes restrictions on using `MyBase`:</span></span>  
  
-   <span data-ttu-id="98de6-145">`MyBase` odnosi się do natychmiastowego klasy podstawowej i jej dziedziczonych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="98de6-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="98de6-146">Nie można użyć do dostępu `Private` elementów członkowskich w klasie.</span><span class="sxs-lookup"><span data-stu-id="98de6-146">It cannot be used to access `Private` members in the class.</span></span>  
  
-   <span data-ttu-id="98de6-147">`MyBase` jest słowem kluczowym rzeczywistego obiektu.</span><span class="sxs-lookup"><span data-stu-id="98de6-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="98de6-148">`MyBase` nie może być przypisany do zmiennej, przekazany do procedury lub używane w `Is` porównania.</span><span class="sxs-lookup"><span data-stu-id="98de6-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="98de6-149">Metoda który `MyBase` kwalifikuje się nie musi być zdefiniowana w klasie podstawowej natychmiastowego; zamiast tego może być zdefiniowana w klasie podstawowej pośrednio dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="98de6-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="98de6-150">Aby kwalifikowana przez odwołanie `MyBase` do poprawnej kompilacji niektóre klasy podstawowej musi zawierać nazwę i typy parametrów, które pojawiają się w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="98de6-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>  
  
-   <span data-ttu-id="98de6-151">Nie można użyć `MyBase` do wywołania `MustOverride` metod klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="98de6-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>  
  
-   <span data-ttu-id="98de6-152">`MyBase` Nie można użyć, aby zakwalifikować się.</span><span class="sxs-lookup"><span data-stu-id="98de6-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="98de6-153">W związku z tym następujący kod jest nieprawidłowy:</span><span class="sxs-lookup"><span data-stu-id="98de6-153">Therefore, the following code is not valid:</span></span>  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   <span data-ttu-id="98de6-154">`MyBase` Nie można używać w modułach.</span><span class="sxs-lookup"><span data-stu-id="98de6-154">`MyBase` cannot be used in modules.</span></span>  
  
-   <span data-ttu-id="98de6-155">`MyBase` Nie można uzyskać dostępu do elementów członkowskich klasy podstawowej, które są oznaczone jako `Friend` Jeśli klasą podstawową jest w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="98de6-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>  
  
 <span data-ttu-id="98de6-156">Więcej informacji oraz innym przykładem, zobacz [porady: dostęp do zmiennej ukrytej przez klasę pochodnych](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="98de6-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
## <a name="the-myclass-keyword"></a><span data-ttu-id="98de6-157">MyClass — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="98de6-157">The MyClass Keyword</span></span>  
 <span data-ttu-id="98de6-158">`MyClass` — Słowo kluczowe zachowuje się jak zmienna obiektu, który odwołuje się do bieżącego wystąpienia klasy pierwotnie zaimplementowanych.</span><span class="sxs-lookup"><span data-stu-id="98de6-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="98de6-159">`MyClass` podobny `Me`, ale każdy metody i właściwości wywołać w `MyClass` jest traktowana tak, jakby był metody lub właściwości [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="98de6-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="98de6-160">W związku z tym ta metoda lub właściwość nie ma wpływu na zastępowanie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="98de6-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>  
  
-   <span data-ttu-id="98de6-161">`MyClass` jest słowem kluczowym rzeczywistego obiektu.</span><span class="sxs-lookup"><span data-stu-id="98de6-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="98de6-162">`MyClass` nie może być przypisany do zmiennej, przekazany do procedury lub używane w `Is` porównania.</span><span class="sxs-lookup"><span data-stu-id="98de6-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="98de6-163">`MyClass` odnosi się do klasy zawierającej i jego dziedziczone elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="98de6-163">`MyClass` refers to the containing class and its inherited members.</span></span>  
  
-   <span data-ttu-id="98de6-164">`MyClass` mogą być używane jako kwalifikator dla `Shared` elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="98de6-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>  
  
-   <span data-ttu-id="98de6-165">`MyClass` Nie można używać wewnątrz `Shared` metody, ale można uzyskać dostępu do udostępnionego elementu członkowskiego klasy można używać wewnątrz metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="98de6-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>  
  
-   <span data-ttu-id="98de6-166">`MyClass` Nie można używać w modułach standardowych.</span><span class="sxs-lookup"><span data-stu-id="98de6-166">`MyClass` cannot be used in standard modules.</span></span>  
  
-   <span data-ttu-id="98de6-167">`MyClass` może służyć do kwalifikowania metody, który jest zdefiniowany w klasie podstawowej, na którym jest żadnej implementacji metody podane w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="98de6-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="98de6-168">Odniesienie ma takie samo znaczenie jak `MyBase.` *metody*.</span><span class="sxs-lookup"><span data-stu-id="98de6-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>  
  
 <span data-ttu-id="98de6-169">Poniższy przykład porównuje `Me` i `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="98de6-169">The following example compares `Me` and `MyClass`.</span></span>  
  
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
  
 <span data-ttu-id="98de6-170">Mimo że `derivedClass` zastępuje `testMethod`, `MyClass` — słowo kluczowe w `useMyClass` nullifies skutki zastępowanie i rozwiązuje kompilatora wywołania do klasy podstawowej wersji `testMethod`.</span><span class="sxs-lookup"><span data-stu-id="98de6-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98de6-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98de6-171">See Also</span></span>  
 [<span data-ttu-id="98de6-172">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="98de6-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="98de6-173">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="98de6-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
