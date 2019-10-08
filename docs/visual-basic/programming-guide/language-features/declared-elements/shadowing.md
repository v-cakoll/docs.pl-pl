---
title: Przesłanianie w Visual Basic
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
ms.openlocfilehash: 30c02cf367c461c3896a01538d03380627de294f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004855"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="106fb-102">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="106fb-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="106fb-103">Gdy dwa elementy programistyczne współdzielą tę samą nazwę, jeden z nich może ukryć lub *Zacień*, drugi.</span><span class="sxs-lookup"><span data-stu-id="106fb-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="106fb-104">W takiej sytuacji cień elementu nie jest dostępny do celów referencyjnych. Zamiast tego, gdy kod używa nazwy elementu, kompilator Visual Basic rozpoznaje ją jako element przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="106fb-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="106fb-105">Cel</span><span class="sxs-lookup"><span data-stu-id="106fb-105">Purpose</span></span>  
 <span data-ttu-id="106fb-106">Głównym celem przesłaniania jest ochrona definicji elementów członkowskich klasy.</span><span class="sxs-lookup"><span data-stu-id="106fb-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="106fb-107">Klasa bazowa może ulec zmianie, która tworzy element o takiej samej nazwie jak już zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="106fb-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="106fb-108">W takim przypadku modyfikator `Shadows` wymusza odwołania za pomocą klasy, aby można było rozpoznać element członkowski zdefiniowany przez użytkownika, a nie do nowego elementu klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="106fb-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="106fb-109">Typy przesłaniania</span><span class="sxs-lookup"><span data-stu-id="106fb-109">Types of Shadowing</span></span>  
 <span data-ttu-id="106fb-110">Element może zasłaniać inny element na dwa różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="106fb-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="106fb-111">Element shadower może być zadeklarowany wewnątrz podregionu regionu zawierającego element shadowd, w takim przypadku przesłanianie jest realizowane *przez zakres*.</span><span class="sxs-lookup"><span data-stu-id="106fb-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="106fb-112">Lub Klasa pochodna może przedefiniować składową klasy bazowej, w tym przypadku przesłanianie odbywa się *przez dziedziczenie*.</span><span class="sxs-lookup"><span data-stu-id="106fb-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="106fb-113">Przesłanianie przez zakres</span><span class="sxs-lookup"><span data-stu-id="106fb-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="106fb-114">Istnieje możliwość, że elementy programistyczne w tym samym module, klasie lub strukturze mają taką samą nazwę, ale różne zakresy.</span><span class="sxs-lookup"><span data-stu-id="106fb-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="106fb-115">Gdy dwa elementy są zadeklarowane w ten sposób, a kod odnosi się do współużytkowanej nazwy, element z węższym zakresem zasłania inny element (zakres blokowy jest najwęższy).</span><span class="sxs-lookup"><span data-stu-id="106fb-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="106fb-116">Na przykład moduł może zdefiniować zmienną `Public` o nazwie `temp`, a procedura w module może zadeklarować zmienną lokalną także o nazwie `temp`.</span><span class="sxs-lookup"><span data-stu-id="106fb-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="106fb-117">Odwołania do `temp` z procedury uzyskują dostęp do zmiennej lokalnej, natomiast odwołania do `temp` z zewnątrz procedury uzyskują dostęp do zmiennej `Public`.</span><span class="sxs-lookup"><span data-stu-id="106fb-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="106fb-118">W takim przypadku zmienna procedury `temp` Cieniuje zmienną modułu `temp`.</span><span class="sxs-lookup"><span data-stu-id="106fb-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="106fb-119">Na poniższej ilustracji przedstawiono dwie zmienne: o nazwie `temp`.</span><span class="sxs-lookup"><span data-stu-id="106fb-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="106fb-120">Zmienna lokalna `temp` Cieniuje zmienną członkowską `temp` w przypadku dostępu z własnej procedury `p`.</span><span class="sxs-lookup"><span data-stu-id="106fb-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="106fb-121">Jednak słowo kluczowe `MyClass` pomija cieniowanie i uzyskuje dostęp do zmiennej składowej.</span><span class="sxs-lookup"><span data-stu-id="106fb-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Grafika pokazująca cieniowanie przez zakres.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="106fb-123">Aby zapoznać się z przykładem przesłaniania przez zakres, zobacz [How to: Hide a Variable o takiej samej nazwie jak zmienna](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="106fb-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="106fb-124">Przesłanianie przez dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="106fb-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="106fb-125">Jeśli klasa pochodna ponownie definiuje element programistyczny Dziedziczony z klasy bazowej, element, który ponownie definiuje, zasłania element oryginalny.</span><span class="sxs-lookup"><span data-stu-id="106fb-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="106fb-126">Można obsłużyć dowolny typ zadeklarowanego elementu lub zestawu przeciążonych elementów przy użyciu dowolnego innego typu.</span><span class="sxs-lookup"><span data-stu-id="106fb-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="106fb-127">Na przykład zmienna `Integer` może obsłużyć procedurę `Function`.</span><span class="sxs-lookup"><span data-stu-id="106fb-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="106fb-128">W przypadku wykonania procedury z inną procedurą można użyć innej listy parametrów i innego typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="106fb-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="106fb-129">Na poniższej ilustracji przedstawiono klasę bazową `b` i klasę pochodną `d`, która dziedziczy po `b`.</span><span class="sxs-lookup"><span data-stu-id="106fb-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="106fb-130">Klasa bazowa definiuje procedurę o nazwie `proc`, a Klasa pochodna zasłania ją z inną procedurą o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="106fb-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="106fb-131">Pierwsza instrukcja `Call` uzyskuje dostęp do obserwowania `proc` w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="106fb-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="106fb-132">Jednak słowo kluczowe `MyBase` pomija cieniowanie i uzyskuje dostęp do procedury obserwowania w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="106fb-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![Diagram grafiki przesłaniania przez dziedziczenie](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="106fb-134">Aby zapoznać się z przykładem przesłaniania poprzez dziedziczenie, zobacz [jak: ukrywanie zmiennej o tej samej nazwie co zmienna](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) i [instrukcje: ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="106fb-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="106fb-135">Cień i poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="106fb-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="106fb-136">Element Shadow nie zawsze jest dostępny z kodu przy użyciu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="106fb-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="106fb-137">Na przykład może być zadeklarowany `Private`.</span><span class="sxs-lookup"><span data-stu-id="106fb-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="106fb-138">W takim przypadku przesłanianie jest zakłócane, a kompilator rozpoznaje wszelkie odwołania do tego samego elementu, jeśli nie wystąpiły żadne cieniowanie.</span><span class="sxs-lookup"><span data-stu-id="106fb-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="106fb-139">Ten element jest dostępnym elementem z najmniejszą liczbą czynności pochodnych z tyłu klasy przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="106fb-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="106fb-140">Jeśli element Shadow jest procedurą, rozdzielczość jest do najbliższej dostępnej wersji z tą samą nazwą, listą parametrów i zwracanym typem.</span><span class="sxs-lookup"><span data-stu-id="106fb-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="106fb-141">W poniższym przykładzie przedstawiono hierarchię dziedziczenia trzech klas.</span><span class="sxs-lookup"><span data-stu-id="106fb-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="106fb-142">Każda klasa definiuje procedurę `Sub` `display`, a każda klasa pochodna zasłania procedurę `display` w swojej klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="106fb-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
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
  
 <span data-ttu-id="106fb-143">W poprzednim przykładzie Klasa pochodna `secondClass` Cieniuje `display` za pomocą procedury `Private`.</span><span class="sxs-lookup"><span data-stu-id="106fb-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="106fb-144">Gdy moduł `callDisplay` wywołuje `display` w `secondClass`, kod wywołujący jest poza `secondClass` i w związku z tym nie może uzyskać dostępu do prywatnej procedury `display`.</span><span class="sxs-lookup"><span data-stu-id="106fb-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="106fb-145">Trwa obniżanie poziomu przesłaniania, a kompilator rozpoznaje odwołanie do klasy bazowej `display` procedury.</span><span class="sxs-lookup"><span data-stu-id="106fb-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="106fb-146">Jednak dodatkowo Klasa pochodna `thirdClass` deklaruje `display` jako `Public`, więc kod w `callDisplay` może uzyskać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="106fb-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="106fb-147">Przesłanianie i zastępowanie</span><span class="sxs-lookup"><span data-stu-id="106fb-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="106fb-148">Nie należy mylić przesłaniania z zastępowaniem.</span><span class="sxs-lookup"><span data-stu-id="106fb-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="106fb-149">Oba są używane, gdy Klasa pochodna dziedziczy z klasy bazowej, i obie przedefiniują jeden zadeklarowany element z innym.</span><span class="sxs-lookup"><span data-stu-id="106fb-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="106fb-150">Istnieją jednak znaczące różnice między nimi.</span><span class="sxs-lookup"><span data-stu-id="106fb-150">But there are significant differences between the two.</span></span> <span data-ttu-id="106fb-151">Aby zapoznać się z porównaniem, zobacz [różnice między przesłanianiem i zastępowaniem](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="106fb-151">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="106fb-152">Przesłanianie i Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="106fb-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="106fb-153">Jeśli ten sam element klasy bazowej zostanie zasłonięty przez więcej niż jeden element w klasie pochodnej, elementy przesłaniania staną się przeciążonymi wersjami tego elementu.</span><span class="sxs-lookup"><span data-stu-id="106fb-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="106fb-154">Aby uzyskać więcej informacji, zobacz [przeciążanie procedur](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="106fb-154">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="106fb-155">Uzyskiwanie dostępu do obserwowania elementu</span><span class="sxs-lookup"><span data-stu-id="106fb-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="106fb-156">Gdy uzyskujesz dostęp do elementu z klasy pochodnej, zazwyczaj odbywa się to za pośrednictwem bieżącego wystąpienia tej klasy pochodnej, kwalifikując nazwę elementu za pomocą słowa kluczowego `Me`.</span><span class="sxs-lookup"><span data-stu-id="106fb-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="106fb-157">Jeśli klasa pochodna zasłania element w klasie bazowej, można uzyskać dostęp do elementu klasy bazowej poprzez kwalifikowanie go za pomocą słowa kluczowego `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="106fb-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="106fb-158">Aby zapoznać się z przykładem uzyskiwania dostępu do obserwowania elementu, zobacz [How to: Access a zmienna ukryta przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="106fb-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="106fb-159">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="106fb-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="106fb-160">Sposób tworzenia zmiennej obiektu może również mieć wpływ na to, czy Klasa pochodna uzyskuje dostęp do elementu obserwowania lub cieniowania.</span><span class="sxs-lookup"><span data-stu-id="106fb-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="106fb-161">Poniższy przykład tworzy dwa obiekty z klasy pochodnej, ale jeden obiekt jest zadeklarowany jako klasa bazowa, a drugi jako Klasa pochodna.</span><span class="sxs-lookup"><span data-stu-id="106fb-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
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
  
 <span data-ttu-id="106fb-162">W poprzednim przykładzie zmienna `basObj` jest zadeklarowana jako klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="106fb-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="106fb-163">Przypisanie do niego obiektu `dervCls` stanowi konwersję rozszerzającą i dlatego jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="106fb-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="106fb-164">Jednak Klasa bazowa nie może uzyskać dostępu do wersji przesłaniania zmiennej `z` w klasie pochodnej, więc kompilator rozpoznaje `basObj.z` do oryginalnej wartości klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="106fb-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="106fb-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="106fb-165">See also</span></span>

- [<span data-ttu-id="106fb-166">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="106fb-166">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="106fb-167">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="106fb-167">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="106fb-168">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="106fb-168">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="106fb-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="106fb-169">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="106fb-170">Overrides</span><span class="sxs-lookup"><span data-stu-id="106fb-170">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="106fb-171">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="106fb-171">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="106fb-172">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="106fb-172">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
