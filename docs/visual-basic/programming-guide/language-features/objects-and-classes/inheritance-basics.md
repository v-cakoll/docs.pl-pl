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
ms.openlocfilehash: 5e4b8511145e758bf3d6328141be0e526965dccf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826577"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="1cc48-102">Podstawowe informacje o dziedziczeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cc48-102">Inheritance Basics (Visual Basic)</span></span>
<span data-ttu-id="1cc48-103">`Inherits` Instrukcja jest używane do deklarowania nową klasę o nazwie *klasy pochodnej*zgodnie z istniejącej klasy, znane jako *klasy bazowej*.</span><span class="sxs-lookup"><span data-stu-id="1cc48-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="1cc48-104">Klasy pochodne dziedziczenie i można rozszerzyć, właściwości, metody, zdarzenia, pola i stałe zdefiniowane w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="1cc48-105">W poniższej sekcji opisano niektóre z reguł do obsługi dziedziczenia i modyfikatorów, których można użyć, aby zmienić sposób klasy dziedziczą lub są dziedziczone:</span><span class="sxs-lookup"><span data-stu-id="1cc48-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>  
  
-   <span data-ttu-id="1cc48-106">Domyślnie wszystkie klasy są dziedziczone, o ile nie jest oznaczona za pomocą `NotInheritable` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1cc48-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="1cc48-107">Klasy mogą dziedziczyć z innych klas w projekcie lub klas w innych zestawach, do których odwołuje się do projektu.</span><span class="sxs-lookup"><span data-stu-id="1cc48-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>  
  
-   <span data-ttu-id="1cc48-108">W odróżnieniu od języków, które umożliwiają wielokrotne dziedziczenie Visual Basic umożliwia tylko pojedyncze dziedziczenie w klasach; oznacza to klasy pochodne mogą mieć tylko jedną klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="1cc48-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="1cc48-109">Mimo że wielokrotne dziedziczenie jest niedozwolona w klasach i klas można zaimplementować wiele interfejsów, które skutecznie można osiągnąć ten sam kończy się.</span><span class="sxs-lookup"><span data-stu-id="1cc48-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>  
  
-   <span data-ttu-id="1cc48-110">Aby uniemożliwić udostępnianie ograniczonych elementów w klasie bazowej, typ dostępu dla klasy pochodnej musi być większa lub równa bardziej restrykcyjny niż jej klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="1cc48-111">Na przykład `Public` klasa nie może dziedziczyć `Friend` lub `Private` klasy, a `Friend` klasa nie może dziedziczyć `Private` klasy.</span><span class="sxs-lookup"><span data-stu-id="1cc48-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>  
  
## <a name="inheritance-modifiers"></a><span data-ttu-id="1cc48-112">Modyfikatory dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="1cc48-112">Inheritance Modifiers</span></span>  
 <span data-ttu-id="1cc48-113">Visual Basic wprowadza następujące instrukcje na poziomie klasy i Modyfikatory do obsługi dziedziczenia:</span><span class="sxs-lookup"><span data-stu-id="1cc48-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>  
  
-   <span data-ttu-id="1cc48-114">`Inherits` Instrukcja — określa klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="1cc48-114">`Inherits` statement — Specifies the base class.</span></span>  
  
-   <span data-ttu-id="1cc48-115">`NotInheritable` Modyfikator — powstrzymuje programistów przed za pomocą klasy jako klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="1cc48-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>  
  
-   <span data-ttu-id="1cc48-116">`MustInherit` Modyfikator — Określa, że klasa jest przeznaczona do użytku jako klasę bazową tylko.</span><span class="sxs-lookup"><span data-stu-id="1cc48-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="1cc48-117">Wystąpienia elementu `MustInherit` klasy nie można utworzyć bezpośrednio; one mogą być tworzone tylko podstawowego wystąpienia klasy pochodnej klasy.</span><span class="sxs-lookup"><span data-stu-id="1cc48-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="1cc48-118">(Innych języków programowania, takich jak C++ i C#, używany jest termin *abstrakcyjna klasa* do opisania tych klas.)</span><span class="sxs-lookup"><span data-stu-id="1cc48-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="1cc48-119">Zastępowanie właściwości i metod w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="1cc48-119">Overriding Properties and Methods in Derived Classes</span></span>  
 <span data-ttu-id="1cc48-120">Domyślnie Klasa pochodna dziedziczy właściwości i metody w swojej klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="1cc48-121">Jeśli właściwość dziedziczona lub metoda ma zachowują się odmiennie w klasie pochodnej może być *zastąpione*.</span><span class="sxs-lookup"><span data-stu-id="1cc48-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="1cc48-122">Oznacza to można zdefiniować nową metodę implementacji metody w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="1cc48-123">Następujące Modyfikatory są używane do kontrolowania, jak zastąpić właściwości i metod:</span><span class="sxs-lookup"><span data-stu-id="1cc48-123">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
-   <span data-ttu-id="1cc48-124">`Overridable` — Umożliwia właściwość lub metoda klasy został nadpisany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>  
  
-   <span data-ttu-id="1cc48-125">`Overrides` — Zastępuje `Overridable` właściwości lub metody zdefiniowanej w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>  
  
-   <span data-ttu-id="1cc48-126">`NotOverridable` — Uniemożliwia właściwości lub metody są przesłonięcia w klasie dziedziczącej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="1cc48-127">Domyślnie `Public` metody są `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="1cc48-127">By default, `Public` methods are `NotOverridable`.</span></span>  
  
-   <span data-ttu-id="1cc48-128">`MustOverride` — Wymaga, że klasa pochodna zastąpienie właściwości lub metody.</span><span class="sxs-lookup"><span data-stu-id="1cc48-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="1cc48-129">Gdy `MustOverride` słowo kluczowe jest używane, definicję metody składa się z tylko `Sub`, `Function`, lub `Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1cc48-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="1cc48-130">Są dozwolone nie inne instrukcje, a w szczególności istnieje nie `End Sub` lub `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1cc48-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="1cc48-131">`MustOverride` metody musi być zadeklarowana w `MustInherit` klasy.</span><span class="sxs-lookup"><span data-stu-id="1cc48-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>  
  
 <span data-ttu-id="1cc48-132">Załóżmy, że chcesz zdefiniować klasy do obsługi płac.</span><span class="sxs-lookup"><span data-stu-id="1cc48-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="1cc48-133">Można zdefiniować ogólnego `Payroll` klasę, która zawiera `RunPayroll` metodę, która oblicza płac dla typowych tygodnia.</span><span class="sxs-lookup"><span data-stu-id="1cc48-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="1cc48-134">Następnie można użyć `Payroll` jako klasę bazową dla bardziej wyspecjalizowane `BonusPayroll` klasy, który może być używany podczas dystrybucji premie pracownika.</span><span class="sxs-lookup"><span data-stu-id="1cc48-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>  
  
 <span data-ttu-id="1cc48-135">`BonusPayroll` Klasy mogą dziedziczyć i zastąpić, `PayEmployee` metody zdefiniowane w bazowym `Payroll` klasy.</span><span class="sxs-lookup"><span data-stu-id="1cc48-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>  
  
 <span data-ttu-id="1cc48-136">W poniższym przykładzie zdefiniowano klasę bazową `Payroll,` i Klasa pochodna `BonusPayroll`, który zastępuje metody dziedziczonej, `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="1cc48-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="1cc48-137">W procedurze `RunPayroll`, tworzy, a następnie przekazuje `Payroll` obiektu i `BonusPayroll` obiektu do funkcji, `Pay`, który wykonuje `PayEmployee` metoda obu obiektów.</span><span class="sxs-lookup"><span data-stu-id="1cc48-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>  
  
 [!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]  
  
## <a name="the-mybase-keyword"></a><span data-ttu-id="1cc48-138">MyBase — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="1cc48-138">The MyBase Keyword</span></span>  
 <span data-ttu-id="1cc48-139">`MyBase` — Słowo kluczowe zachowuje się jak zmienna obiektu, który odwołuje się do klasy bazowej bieżącego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="1cc48-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="1cc48-140">`MyBase` często używane do dostępu do składowych klasy bazowej, które zostały zastąpione lub pada w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="1cc48-141">W szczególności `MyBase.New` służy do jawnie wywołać konstruktora klasy bazowej w konstruktorze klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
 <span data-ttu-id="1cc48-142">Na przykład załóżmy, że projektujesz Klasa pochodna, która zastępuje metodę dziedziczone z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="1cc48-143">Zastąpione metody można wywołać metodę w klasie bazowej i zmodyfikować zwracanej wartości, jak pokazano na następujący fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="1cc48-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]  
  
 <span data-ttu-id="1cc48-144">Na poniższej liście opisano ograniczenia dotyczące używania `MyBase`:</span><span class="sxs-lookup"><span data-stu-id="1cc48-144">The following list describes restrictions on using `MyBase`:</span></span>  
  
-   <span data-ttu-id="1cc48-145">`MyBase` odnosi się do natychmiastowego klasy podstawowej i jej dziedziczone elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="1cc48-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="1cc48-146">Nie można użyć do dostępu `Private` elementów członkowskich w klasie.</span><span class="sxs-lookup"><span data-stu-id="1cc48-146">It cannot be used to access `Private` members in the class.</span></span>  
  
-   <span data-ttu-id="1cc48-147">`MyBase` jest słowem kluczowym rzeczywistego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1cc48-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="1cc48-148">`MyBase` Nie można przypisać do zmiennej, przekazany do procedury ani wykorzystywać w `Is` porównania.</span><span class="sxs-lookup"><span data-stu-id="1cc48-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="1cc48-149">Metoda, `MyBase` kwalifikuje się nie musi być zdefiniowany w klasie bazowej natychmiastowego; zamiast tego może być zdefiniowana w klasie bazowej pośrednio dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="1cc48-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="1cc48-150">Aby odwołanie kwalifikowana przez `MyBase` skompilować poprawnie, niektóre klasa bazowa musi zawierać pasujących do nazwy i typy parametrów, które pojawiają się w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="1cc48-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>  
  
-   <span data-ttu-id="1cc48-151">Nie można użyć `MyBase` do wywołania `MustOverride` metody klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>  
  
-   <span data-ttu-id="1cc48-152">`MyBase` nie może służyć do samego zakwalifikowania.</span><span class="sxs-lookup"><span data-stu-id="1cc48-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="1cc48-153">W związku z tym poniższy kod jest nieprawidłowy:</span><span class="sxs-lookup"><span data-stu-id="1cc48-153">Therefore, the following code is not valid:</span></span>  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   <span data-ttu-id="1cc48-154">`MyBase` Nie można używać w modułach.</span><span class="sxs-lookup"><span data-stu-id="1cc48-154">`MyBase` cannot be used in modules.</span></span>  
  
-   <span data-ttu-id="1cc48-155">`MyBase` Nie można użyć do dostępu do składowych klasy bazowej, które są oznaczone jako `Friend` Jeśli klasa podstawowa jest w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="1cc48-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>  
  
 <span data-ttu-id="1cc48-156">Aby uzyskać więcej informacji i inny przykład, zobacz [jak: Dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="1cc48-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
## <a name="the-myclass-keyword"></a><span data-ttu-id="1cc48-157">MyClass — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="1cc48-157">The MyClass Keyword</span></span>  
 <span data-ttu-id="1cc48-158">`MyClass` — Słowo kluczowe zachowuje się jak zmienna obiektu, który odwołuje się do bieżącego wystąpienia klasy pierwotnie zaimplementowanych.</span><span class="sxs-lookup"><span data-stu-id="1cc48-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="1cc48-159">`MyClass` przypomina `Me`, ale co metod i właściwości wywołać w `MyClass` jest traktowany tak, jakby były metodę lub właściwość [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="1cc48-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="1cc48-160">W związku z tym metody lub właściwości nie występuje przez zastąpienie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1cc48-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>  
  
-   <span data-ttu-id="1cc48-161">`MyClass` jest słowem kluczowym rzeczywistego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1cc48-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="1cc48-162">`MyClass` Nie można przypisać do zmiennej, przekazany do procedury ani wykorzystywać w `Is` porównania.</span><span class="sxs-lookup"><span data-stu-id="1cc48-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="1cc48-163">`MyClass` odnosi się do klasy zawierającego i jego dziedziczone elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="1cc48-163">`MyClass` refers to the containing class and its inherited members.</span></span>  
  
-   <span data-ttu-id="1cc48-164">`MyClass` mogą być używane jako kwalifikator dla `Shared` elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="1cc48-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>  
  
-   <span data-ttu-id="1cc48-165">`MyClass` Nie można używać wewnątrz `Shared` metody, ale mogą być używane do dostępu do udostępnionej składowej klasy wewnątrz metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1cc48-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>  
  
-   <span data-ttu-id="1cc48-166">`MyClass` Nie można używać w modułach standardowych.</span><span class="sxs-lookup"><span data-stu-id="1cc48-166">`MyClass` cannot be used in standard modules.</span></span>  
  
-   <span data-ttu-id="1cc48-167">`MyClass` może służyć do kwalifikowania metodę, która jest zdefiniowana w klasie bazowej, a która nie ma implementacji metody dostarczone przez tę klasę.</span><span class="sxs-lookup"><span data-stu-id="1cc48-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="1cc48-168">Takie odwołanie, ma takie samo znaczenie jak `MyBase.` *metoda*.</span><span class="sxs-lookup"><span data-stu-id="1cc48-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>  
  
 <span data-ttu-id="1cc48-169">W poniższym przykładzie porównano `Me` i `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="1cc48-169">The following example compares `Me` and `MyClass`.</span></span>  
  
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
  
 <span data-ttu-id="1cc48-170">Mimo że `derivedClass` zastępuje `testMethod`, `MyClass` — słowo kluczowe w `useMyClass` nullifies skutki zastępowanie i rozwiązuje kompilatora wywołanie klasy bazowej wersję `testMethod`.</span><span class="sxs-lookup"><span data-stu-id="1cc48-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc48-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cc48-171">See also</span></span>

- [<span data-ttu-id="1cc48-172">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1cc48-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="1cc48-173">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="1cc48-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
