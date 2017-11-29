---
title: "Przesłanianie w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cbfce3edc122ca875552b2d41ba876fe5cfcfc4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="d2145-102">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2145-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="d2145-103">Gdy dwa elementy programowania o tej samej nazwie, jeden z nich można ukryć, lub *tle*, jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="d2145-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="d2145-104">W takiej sytuacji zasłonięty element nie jest dostępna dla odwołania; Zamiast tego po kodzie używa nazwy elementu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora rozpoznaje ją do elementu przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="d2145-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="d2145-105">Cel</span><span class="sxs-lookup"><span data-stu-id="d2145-105">Purpose</span></span>  
 <span data-ttu-id="d2145-106">Głównym celem przesłanianie ma chronić definicji członkowie klasy.</span><span class="sxs-lookup"><span data-stu-id="d2145-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="d2145-107">Klasa podstawowa mogą być zmiany, która tworzy element o takiej samej nazwie jako jeden, który został już zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="d2145-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="d2145-108">W takim przypadku `Shadows` wymusza modyfikator odwołuje się do klasy mają zostać rozwiązane do elementu członkowskiego zdefiniowane, a nie nowy element klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d2145-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="d2145-109">Typy cieniowania</span><span class="sxs-lookup"><span data-stu-id="d2145-109">Types of Shadowing</span></span>  
 <span data-ttu-id="d2145-110">Element można obserwować inny element na dwa różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="d2145-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="d2145-111">Element przesłaniania mogą być deklarowane w regionu, regionu zawierający element zasłonięty, w którym odbywa się przypadku przesłanianie *przez zakres*.</span><span class="sxs-lookup"><span data-stu-id="d2145-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="d2145-112">Lub Klasa pochodna ponownie zdefiniować elementu członkowskiego klasy podstawowej, w którym odbywa się przypadku przesłanianie *poprzez dziedziczenie*.</span><span class="sxs-lookup"><span data-stu-id="d2145-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="d2145-113">Cieniowania przez zakres</span><span class="sxs-lookup"><span data-stu-id="d2145-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="d2145-114">Istnieje możliwość programowania elementów modułu, klasy lub struktury, poproś go o tej samej nazwie, ale inny zakres.</span><span class="sxs-lookup"><span data-stu-id="d2145-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="d2145-115">Gdy dwa elementy są zadeklarowane w ten sposób i kod odwołuje się do nazwy mają, element z zakresem mniejszą niż zasłania innego elementu (zakresie bloku jest najwęższym).</span><span class="sxs-lookup"><span data-stu-id="d2145-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="d2145-116">Na przykład można zdefiniować moduł `Public` zmiennej o nazwie `temp`, i procedury w module można zadeklarować zmiennej lokalnej o nazwie `temp`.</span><span class="sxs-lookup"><span data-stu-id="d2145-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="d2145-117">Odwołuje się do `temp` z poziomu procedury uzyskują dostęp do zmiennej lokalnej podczas odwołania do `temp` z poza dostępu procedury `Public` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d2145-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="d2145-118">W tym przypadku zmiennej procedury `temp` zasłania zmiennej modułu `temp`.</span><span class="sxs-lookup"><span data-stu-id="d2145-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="d2145-119">Na poniższej ilustracji przedstawiono dwie zmienne, o nazwie `temp`.</span><span class="sxs-lookup"><span data-stu-id="d2145-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="d2145-120">Zmienna lokalna `temp` zasłania zmiennej członkowskiej `temp` podczas uzyskiwania dostępu do z, w ramach własnej procedury `p`.</span><span class="sxs-lookup"><span data-stu-id="d2145-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="d2145-121">Jednak `MyClass` — słowo kluczowe pomija przesłanianie i uzyskuje dostęp do zmiennej członka.</span><span class="sxs-lookup"><span data-stu-id="d2145-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 <span data-ttu-id="d2145-122">![Graficzny diagram cieniowania przez zakres](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span><span class="sxs-lookup"><span data-stu-id="d2145-122">![Graphic diagram of shadowing through scope](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span></span>  
<span data-ttu-id="d2145-123">Cieniowania przez zakres</span><span class="sxs-lookup"><span data-stu-id="d2145-123">Shadowing through scope</span></span>  
  
 <span data-ttu-id="d2145-124">Na przykład cieniowania przez zakres zobacz [porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej Your](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="d2145-124">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="d2145-125">Przesłanianie poprzez dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="d2145-125">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="d2145-126">Jeśli klasa pochodna ponownie definiuje elementu programistycznego dziedziczona z klasy podstawowej, redefining element zasłania oryginalnego elementu.</span><span class="sxs-lookup"><span data-stu-id="d2145-126">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="d2145-127">Można obserwować dowolnego typu zadeklarowany element lub zbiór przeciążone elementy z żadnym innym typem.</span><span class="sxs-lookup"><span data-stu-id="d2145-127">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="d2145-128">Na przykład `Integer` zmiennej można obserwować `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="d2145-128">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="d2145-129">Jeśli w tle procedury z innej procedury można użyć inną listą parametrów i innym typie zwracanym.</span><span class="sxs-lookup"><span data-stu-id="d2145-129">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="d2145-130">Na poniższej ilustracji przedstawiono klasę podstawową `b` i Klasa pochodna `d` dziedziczący po `b`.</span><span class="sxs-lookup"><span data-stu-id="d2145-130">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="d2145-131">Klasa podstawowa definiuje procedurę o nazwie `proc`, a klasa pochodna zasłania go z innej procedury o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="d2145-131">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="d2145-132">Pierwszy `Call` instrukcji uzyskuje dostęp do cieniowania `proc` w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="d2145-132">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="d2145-133">Jednak `MyBase` — słowo kluczowe pomija przesłanianie i uzyskuje dostęp do zasłonięty procedury w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d2145-133">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 <span data-ttu-id="d2145-134">![Diagram graficzny cieniowania przez dziedziczenie](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span><span class="sxs-lookup"><span data-stu-id="d2145-134">![Graphic diagram of shadowing through inheritance](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span></span>  
<span data-ttu-id="d2145-135">Przesłanianie poprzez dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="d2145-135">Shadowing through inheritance</span></span>  
  
 <span data-ttu-id="d2145-136">Na przykład cieniowania przez dziedziczenie, zobacz [porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej Your](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) i [porady: ukrywanie odziedziczonych zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="d2145-136">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="d2145-137">Przesłanianie i poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="d2145-137">Shadowing and Access Level</span></span>  
 <span data-ttu-id="d2145-138">Element przesłaniania nie jest zawsze dostępne z kodu przy użyciu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="d2145-138">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="d2145-139">Na przykład może być zadeklarowana `Private`.</span><span class="sxs-lookup"><span data-stu-id="d2145-139">For example, it might be declared `Private`.</span></span> <span data-ttu-id="d2145-140">W takim przypadku przesłanianie jest bezcelowe i kompilator usuwa wszelkie odwołania do tego samego elementu miałoby Jeśli nie był nie przesłanianie.</span><span class="sxs-lookup"><span data-stu-id="d2145-140">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="d2145-141">Ten element jest dostępny element najmniejszą liczbę derivational kroki wstecz od klasy przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="d2145-141">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="d2145-142">Jeśli element zasłonięty jest procedurą, rozwiązanie jest najbliższy dostępny wersji o takiej samej nazwie, lista parametrów i typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="d2145-142">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="d2145-143">Poniższy przykład przedstawia hierarchię dziedziczenia trzech klas.</span><span class="sxs-lookup"><span data-stu-id="d2145-143">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="d2145-144">Każda klasa definiuje `Sub` procedury `display`, i zostały opracowane na każdej klasy shadows `display` procedury w swojej klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d2145-144">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```  
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
  
 <span data-ttu-id="d2145-145">W powyższym przykładzie Klasa pochodna `secondClass` shadows `display` z `Private` procedury.</span><span class="sxs-lookup"><span data-stu-id="d2145-145">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="d2145-146">Gdy moduł `callDisplay` wywołania `display` w `secondClass`, kod wywołujący znajduje się poza `secondClass` i dlatego nie można uzyskać dostępu prywatnego `display` procedury.</span><span class="sxs-lookup"><span data-stu-id="d2145-146">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="d2145-147">Przesłanianie jest bezcelowe i kompilator usuwa odwołanie do klasy podstawowej `display` procedury.</span><span class="sxs-lookup"><span data-stu-id="d2145-147">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="d2145-148">Jednak dalszy pochodnej klasy `thirdClass` deklaruje `display` jako `Public`, więc kod w `callDisplay` do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="d2145-148">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="d2145-149">Przesłanianiem i zastępowaniem</span><span class="sxs-lookup"><span data-stu-id="d2145-149">Shadowing and Overriding</span></span>  
 <span data-ttu-id="d2145-150">Nie należy mylić przesłanianie z zastępowanie.</span><span class="sxs-lookup"><span data-stu-id="d2145-150">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="d2145-151">Zarówno są używane, gdy klasa pochodna dziedziczy z klasy podstawowej, a jednocześnie ponownie definiować jeden element zadeklarowany z innym.</span><span class="sxs-lookup"><span data-stu-id="d2145-151">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="d2145-152">Ale są istotne różnice między nimi.</span><span class="sxs-lookup"><span data-stu-id="d2145-152">But there are significant differences between the two.</span></span> <span data-ttu-id="d2145-153">Porównanie, zobacz [różnice pomiędzy przesłanianiem i przesłanianie](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="d2145-153">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="d2145-154">Przesłanianie i przeciążeniu</span><span class="sxs-lookup"><span data-stu-id="d2145-154">Shadowing and Overloading</span></span>  
 <span data-ttu-id="d2145-155">Jeśli cień tego samego elementu klasy podstawowej z więcej niż jeden element w klasie pochodnej przesłaniania elementy stają się zastąpionej wersji tego elementu.</span><span class="sxs-lookup"><span data-stu-id="d2145-155">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="d2145-156">Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="d2145-156">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="d2145-157">Uzyskiwanie dostępu do elementu zasłonięty</span><span class="sxs-lookup"><span data-stu-id="d2145-157">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="d2145-158">Gdy uzyskujesz dostęp do elementu z klasy pochodnej, należy zwykle to zrobić przez bieżące wystąpienie tej klasy pochodnej, kwalifikujących się z nazwy elementu `Me` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d2145-158">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="d2145-159">Klasy pochodne zasłania element w klasie podstawowej, można przejść do elementu klasy podstawowej przez kwalifikującego się za pomocą `MyBase` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d2145-159">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="d2145-160">Na przykład uzyskiwania dostępu do elementu zasłonięty zobacz [porady: dostęp do zmiennej ukrytej przez klasę pochodnych](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="d2145-160">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="d2145-161">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="d2145-161">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="d2145-162">Jak utworzyć zmienną obiektu może wpłynąć na czy klasy pochodnej uzyskuje dostęp do elementu przesłaniania lub element zasłonięty.</span><span class="sxs-lookup"><span data-stu-id="d2145-162">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="d2145-163">Poniższy przykład tworzy dwa obiekty z klasy pochodnej, ale jeden obiekt jest zadeklarowany jako klasa podstawowa, a drugi jako klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="d2145-163">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```  
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
  
 <span data-ttu-id="d2145-164">W powyższym przykładzie zmienna `basObj` jest zadeklarowany jako klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d2145-164">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="d2145-165">Przypisywanie `dervCls` obiekt do niego stanowi konwersję rozszerzającą i dlatego jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d2145-165">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="d2145-166">Jednak klasy podstawowej nie może uzyskać dostępu wersja przesłaniania w zmiennej `z` w klasie pochodnej, dlatego kompilator rozpoznaje `basObj.z` do wartości oryginalnej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d2145-166">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2145-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2145-167">See Also</span></span>  
 [<span data-ttu-id="d2145-168">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="d2145-168">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="d2145-169">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2145-169">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="d2145-170">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="d2145-170">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="d2145-171">Shadows</span><span class="sxs-lookup"><span data-stu-id="d2145-171">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="d2145-172">Zastąpienia</span><span class="sxs-lookup"><span data-stu-id="d2145-172">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="d2145-173">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="d2145-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="d2145-174">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="d2145-174">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
