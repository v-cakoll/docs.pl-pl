---
title: Zasłanianie
ms.date: 07/20/2015
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
ms.openlocfilehash: 20a33478f622fca6d3183772f53dcb3e72f79409
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266888"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="3cbff-102">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3cbff-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="3cbff-103">Gdy dwa elementy programowania mają tę samą nazwę, jeden z nich może ukryć lub *cień,* drugi.</span><span class="sxs-lookup"><span data-stu-id="3cbff-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="3cbff-104">W takiej sytuacji element cieniowany nie jest dostępny do odwołania; Zamiast tego gdy kod używa nazwy elementu, kompilator języka Visual Basic rozwiązuje go do elementu cieniowania.</span><span class="sxs-lookup"><span data-stu-id="3cbff-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="3cbff-105">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="3cbff-105">Purpose</span></span>  
 <span data-ttu-id="3cbff-106">Głównym celem cieniowania jest ochrona definicji członków klasy.</span><span class="sxs-lookup"><span data-stu-id="3cbff-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="3cbff-107">Klasa podstawowa może zostać poddana zmianom, które tworzą element o takiej samej nazwie, jak ta, która została już zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="3cbff-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="3cbff-108">W takim przypadku `Shadows` modyfikator wymusza odwołania za pośrednictwem klasy, które mają zostać rozpoznane do zdefiniowanego elementu członkowskiego, a nie do nowego elementu klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3cbff-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="3cbff-109">Rodzaje cieniowania</span><span class="sxs-lookup"><span data-stu-id="3cbff-109">Types of Shadowing</span></span>  
 <span data-ttu-id="3cbff-110">Element może cień inny element na dwa różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="3cbff-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="3cbff-111">Element cieniowania można zadeklarować wewnątrz podregionu regionu zawierającego element cieniowany, w którym to przypadku cieniowanie odbywa się *za pośrednictwem zakresu*.</span><span class="sxs-lookup"><span data-stu-id="3cbff-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="3cbff-112">Lub klasy pochodnej można przedefiniować członka klasy podstawowej, w którym to przypadku cieniowanie odbywa się *za pośrednictwem dziedziczenia*.</span><span class="sxs-lookup"><span data-stu-id="3cbff-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="3cbff-113">Cieniowanie przez zakres</span><span class="sxs-lookup"><span data-stu-id="3cbff-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="3cbff-114">Jest możliwe dla programowania elementów w tym samym module, klasy lub struktury, aby mieć taką samą nazwę, ale inny zakres.</span><span class="sxs-lookup"><span data-stu-id="3cbff-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="3cbff-115">Gdy dwa elementy są zadeklarowane w ten sposób, a kod odwołuje się do nazwy, którą współużytkują, element o węższym zakresie cieniuje inny element (zakres bloku jest najwęższy).</span><span class="sxs-lookup"><span data-stu-id="3cbff-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="3cbff-116">Na przykład moduł może `Public` zdefiniować `temp`zmienną o nazwie , a procedura `temp`w module może zadeklarować zmienną lokalną również o nazwie .</span><span class="sxs-lookup"><span data-stu-id="3cbff-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="3cbff-117">Odwołania do `temp` z wewnątrz procedury dostęp do zmiennej lokalnej, podczas gdy odwołania do spoza procedury dostęp do `temp` zmiennej. `Public`</span><span class="sxs-lookup"><span data-stu-id="3cbff-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="3cbff-118">W takim przypadku zmienna `temp` procedury `temp`cieniuje zmienną modułu .</span><span class="sxs-lookup"><span data-stu-id="3cbff-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="3cbff-119">Na poniższej ilustracji przedstawiono `temp`dwie zmienne o nazwie .</span><span class="sxs-lookup"><span data-stu-id="3cbff-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="3cbff-120">Zmienna `temp` lokalna cieniuje `temp` zmienną elementu członkowskiego, `p`gdy uzyskuje się do niej dostęp z poziomu własnej procedury .</span><span class="sxs-lookup"><span data-stu-id="3cbff-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="3cbff-121">Jednak `MyClass` słowo kluczowe omija cieniowanie i uzyskuje dostęp do zmiennej elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="3cbff-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Grafika przedstawiająca cieniowanie przez zakres.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="3cbff-123">Na przykład cieniowania przez zakres, zobacz [Jak: Ukryć zmienną o takiej samej nazwie jak zmienna](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="3cbff-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="3cbff-124">Cieniowanie przez dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="3cbff-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="3cbff-125">Jeśli klasa pochodna ponownie definiuje element programowania dziedziczony z klasy podstawowej, element ponownego definiowania cienie oryginalnego elementu.</span><span class="sxs-lookup"><span data-stu-id="3cbff-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="3cbff-126">Można cieniować dowolny typ zadeklarowanego elementu lub zestaw przeciążonych elementów z dowolnym innym typem.</span><span class="sxs-lookup"><span data-stu-id="3cbff-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="3cbff-127">Na przykład `Integer` zmienna może `Function` cieniować procedurę.</span><span class="sxs-lookup"><span data-stu-id="3cbff-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="3cbff-128">Jeśli procedura jest cieniowana z inną procedurą, można użyć innej listy parametrów i innego typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="3cbff-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="3cbff-129">Na poniższej ilustracji `b` przedstawiono klasę `d` podstawową `b`i klasę pochodną, która dziedziczy po .</span><span class="sxs-lookup"><span data-stu-id="3cbff-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="3cbff-130">Klasa podstawowa definiuje procedurę `proc`o nazwie , a klasa pochodna cieniuje ją inną procedurą o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3cbff-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="3cbff-131">Pierwsza `Call` instrukcja uzyskuje dostęp `proc` do cieniowania w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="3cbff-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="3cbff-132">Jednak `MyBase` słowo kluczowe omija cieniowanie i uzyskuje dostęp do procedury cieniowanej w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3cbff-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![Graficzny diagram cieniowania przez dziedziczenie](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="3cbff-134">Na przykład cieniowania przez dziedziczenie, zobacz [Jak: Ukryć zmienną o takiej samej nazwie jak zmienna](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) i [Jak: Ukryć dziedziczoną zmienną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="3cbff-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="3cbff-135">Poziom cieniowania i dostępu</span><span class="sxs-lookup"><span data-stu-id="3cbff-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="3cbff-136">Element cieniowania nie zawsze jest dostępny z kodu przy użyciu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="3cbff-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="3cbff-137">Na przykład może być `Private`zadeklarowany .</span><span class="sxs-lookup"><span data-stu-id="3cbff-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="3cbff-138">W takim przypadku cieniowanie jest pokonany i kompilator rozwiązuje wszelkie odwołania do tego samego elementu, który miałby, gdyby nie było cieniowania.</span><span class="sxs-lookup"><span data-stu-id="3cbff-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="3cbff-139">Ten element jest dostępny element najmniej pochodnych kroków wstecz od klasy cieniowania.</span><span class="sxs-lookup"><span data-stu-id="3cbff-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="3cbff-140">Jeśli element cieniowany jest procedurą, rozdzielczość jest do najbliższej dostępnej wersji o tej samej nazwie, liście parametrów i typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="3cbff-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="3cbff-141">W poniższym przykładzie przedstawiono hierarchię dziedziczenia trzech klas.</span><span class="sxs-lookup"><span data-stu-id="3cbff-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="3cbff-142">Każda klasa definiuje `Sub` `display`procedurę , a każda klasa `display` pochodna cieniuje procedurę w swojej klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3cbff-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```vb  
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
  
 <span data-ttu-id="3cbff-143">W poprzednim przykładzie klasy `secondClass` pochodnej `display` cienie `Private` z procedurą.</span><span class="sxs-lookup"><span data-stu-id="3cbff-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="3cbff-144">Gdy `callDisplay` moduł `display` `secondClass`wywołuje w , `secondClass` kod wywołujący jest `display` na zewnątrz i dlatego nie można uzyskać dostępu do procedury prywatnej.</span><span class="sxs-lookup"><span data-stu-id="3cbff-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="3cbff-145">Shadowing jest pokonany, a kompilator rozwiązuje odwołanie `display` do procedury klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3cbff-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="3cbff-146">Jednak dalsze pochodne `thirdClass` klasy `display` deklaruje `Public`jako , `callDisplay` więc kod w można uzyskać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="3cbff-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="3cbff-147">Cieniowanie i zastępowanie</span><span class="sxs-lookup"><span data-stu-id="3cbff-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="3cbff-148">Nie należy mylić cieniowania z nadpisaniem.</span><span class="sxs-lookup"><span data-stu-id="3cbff-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="3cbff-149">Oba są używane, gdy klasa pochodna dziedziczy z klasy podstawowej i oba ponownie zdefiniować jeden zadeklarowany element z innym.</span><span class="sxs-lookup"><span data-stu-id="3cbff-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="3cbff-150">Ale istnieją znaczne różnice między nimi.</span><span class="sxs-lookup"><span data-stu-id="3cbff-150">But there are significant differences between the two.</span></span> <span data-ttu-id="3cbff-151">Dla porównania zobacz [Różnice między cieniowania i zastępowania](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="3cbff-151">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="3cbff-152">Cieniowanie i przeciążanie</span><span class="sxs-lookup"><span data-stu-id="3cbff-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="3cbff-153">Jeśli cień tego samego elementu klasy podstawowej z więcej niż jeden element w klasie pochodnej, elementy cieniowania stają się przeciążonymi wersjami tego elementu.</span><span class="sxs-lookup"><span data-stu-id="3cbff-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="3cbff-154">Aby uzyskać więcej informacji, zobacz [Przeciążanie procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="3cbff-154">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="3cbff-155">Uzyskiwanie dostępu do elementu cienia</span><span class="sxs-lookup"><span data-stu-id="3cbff-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="3cbff-156">Podczas uzyskiwania dostępu do elementu z klasy pochodnej, zwykle można to zrobić za pośrednictwem bieżącego `Me` wystąpienia tej klasy pochodnej, kwalifikując nazwę elementu ze słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="3cbff-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="3cbff-157">Jeśli klasa pochodna cienie element w klasie podstawowej, można uzyskać dostęp do `MyBase` elementu klasy podstawowej, kwalifikując go za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="3cbff-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="3cbff-158">Na przykład uzyskiwania dostępu do elementu cieniowanego zobacz [Jak: Dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="3cbff-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="3cbff-159">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="3cbff-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="3cbff-160">Sposób tworzenia zmiennej obiektu może również mieć wpływ na to, czy klasa pochodna uzyskuje dostęp do elementu cieniowania lub elementu cieniowanego.</span><span class="sxs-lookup"><span data-stu-id="3cbff-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="3cbff-161">Poniższy przykład tworzy dwa obiekty z klasy pochodnej, ale jeden obiekt jest zadeklarowany jako klasa podstawowa, a drugi jako klasa pochodna.</span><span class="sxs-lookup"><span data-stu-id="3cbff-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```vb  
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
  
 <span data-ttu-id="3cbff-162">W poprzednim przykładzie zmienna `basObj` jest zadeklarowana jako klasa podstawowa.</span><span class="sxs-lookup"><span data-stu-id="3cbff-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="3cbff-163">Przypisanie `dervCls` do niego obiektu stanowi konwersję rozszerzającą i dlatego jest prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="3cbff-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="3cbff-164">Jednak klasa podstawowa nie może uzyskać dostępu `z` do wersji cieniowania zmiennej w `basObj.z` klasie pochodnej, więc kompilator rozpoznaje oryginalną wartość klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3cbff-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cbff-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3cbff-165">See also</span></span>

- [<span data-ttu-id="3cbff-166">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="3cbff-166">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="3cbff-167">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3cbff-167">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="3cbff-168">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="3cbff-168">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="3cbff-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="3cbff-169">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="3cbff-170">Overrides</span><span class="sxs-lookup"><span data-stu-id="3cbff-170">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="3cbff-171">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="3cbff-171">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="3cbff-172">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="3cbff-172">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
