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
ms.openlocfilehash: 9ad992a53618fa2f410e0b0fb23886c30136384f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839395"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="eef46-102">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eef46-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="eef46-103">Gdy dwa elementy programowania mają taką samą nazwę, jeden z nich można ukryć, lub *w tle*, jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="eef46-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="eef46-104">W takiej sytuacji zasłonięte element nie jest dostępne do użytku; Zamiast tego gdy kod używa nazwy elementu, kompilator Visual Basic jest rozpoznawany jako jej przesłaniania elementu.</span><span class="sxs-lookup"><span data-stu-id="eef46-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="eef46-105">Cel</span><span class="sxs-lookup"><span data-stu-id="eef46-105">Purpose</span></span>  
 <span data-ttu-id="eef46-106">Głównym celem przesłanianie jest ochrona definicji usługi składowych klasy.</span><span class="sxs-lookup"><span data-stu-id="eef46-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="eef46-107">Klasy bazowej może przechodzić zmianę, która tworzy element o takiej samej nazwie jako jeden, który został już zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="eef46-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="eef46-108">W takim przypadku `Shadows` wymusza modyfikator odwołuje się do swojej klasy, które mają zostać rozwiązane do elementu członkowskiego zdefiniowane, zamiast na nowy element klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="eef46-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="eef46-109">Typy cieniowania</span><span class="sxs-lookup"><span data-stu-id="eef46-109">Types of Shadowing</span></span>  
 <span data-ttu-id="eef46-110">Element można w tle innego elementu na dwa różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="eef46-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="eef46-111">Można zadeklarować elementu przesłaniania wewnątrz Podobszar regionu zawierającego element zasłonięte, w której odbywa sprawy przesłanianie *przez zakres*.</span><span class="sxs-lookup"><span data-stu-id="eef46-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="eef46-112">I Klasa pochodna można ponownie zdefiniować składowej klasy bazowej, w którym odbywa sprawy przesłanianie *poprzez dziedziczenie*.</span><span class="sxs-lookup"><span data-stu-id="eef46-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="eef46-113">Cieniowania przez zakres</span><span class="sxs-lookup"><span data-stu-id="eef46-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="eef46-114">Istnieje możliwość programowania elementów w tej samej modułu, klasy lub struktury, aby mieć takiej samej nazwie, ale inny zakres.</span><span class="sxs-lookup"><span data-stu-id="eef46-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="eef46-115">Jeśli dwa elementy są deklarowane w ten sposób, kod odwołuje się do nazwy mają element z węższy zakres zasłania innego elementu (zakres bloku jest najmniejsza).</span><span class="sxs-lookup"><span data-stu-id="eef46-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="eef46-116">Na przykład można zdefiniować moduł `Public` zmiennej o nazwie `temp`, oraz procedury w module można zadeklarować zmiennej lokalnej o nazwie `temp`.</span><span class="sxs-lookup"><span data-stu-id="eef46-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="eef46-117">Odwołuje się do `temp` z poziomu procedury dostępu do zmiennej lokalnej podczas odwołania do `temp` z poza dostępu procedury `Public` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="eef46-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="eef46-118">W tym przypadku zmienna procedury `temp` zasłania zmiennej modułu `temp`.</span><span class="sxs-lookup"><span data-stu-id="eef46-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="eef46-119">Na poniższej ilustracji przedstawiono dwie zmienne, o nazwie `temp`.</span><span class="sxs-lookup"><span data-stu-id="eef46-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="eef46-120">Zmienna lokalna `temp` zasłania zmiennej składowej `temp` podczas uzyskiwania dostępu do z, w ramach własnej procedury `p`.</span><span class="sxs-lookup"><span data-stu-id="eef46-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="eef46-121">Jednak `MyClass` — słowo kluczowe pomija przesłanianiem i uzyskuje dostęp do zmiennej elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="eef46-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Grafika przedstawiająca cieniowania przez zakres.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="eef46-123">Na przykład cieniowania przez zakres zobacz [jak: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="eef46-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="eef46-124">Przesłanianie poprzez dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="eef46-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="eef46-125">Jeśli klasa pochodna redefiniuje elementu programistycznego dziedziczone z klasy bazowej, redefining element zasłania oryginalnego elementu.</span><span class="sxs-lookup"><span data-stu-id="eef46-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="eef46-126">Można w tle dowolnego typu element zadeklarowany lub zestaw przeciążonych elementów z żadnym innym typem.</span><span class="sxs-lookup"><span data-stu-id="eef46-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="eef46-127">Na przykład `Integer` zmiennej może w tle `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="eef46-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="eef46-128">Jeśli w tle procedury z innej procedury można użyć inną listą parametrów i innym typie zwracanym.</span><span class="sxs-lookup"><span data-stu-id="eef46-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="eef46-129">Na poniższej ilustracji przedstawiono klasę bazową `b` i Klasa pochodna `d` tej, która dziedziczy `b`.</span><span class="sxs-lookup"><span data-stu-id="eef46-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="eef46-130">Klasa bazowa definiuje procedurę o nazwie `proc`, i Klasa pochodna zasłania go przy użyciu innej procedury o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="eef46-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="eef46-131">Pierwszy `Call` uzyskuje dostęp do instrukcji, przesłanianie `proc` w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="eef46-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="eef46-132">Jednak `MyBase` — słowo kluczowe pomija przesłanianiem i uzyskuje dostęp do zasłonięte procedury w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="eef46-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![Diagram graficzny cieniowania poprzez dziedziczenie](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="eef46-134">Na przykład cieniowania przez dziedziczenie zobacz [jak: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) i [jak: Ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="eef46-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="eef46-135">Przesłanianie i poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="eef46-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="eef46-136">Element przesłaniania nie zawsze jest dostępne z kodu za pomocą klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="eef46-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="eef46-137">Na przykład może być zadeklarowana `Private`.</span><span class="sxs-lookup"><span data-stu-id="eef46-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="eef46-138">W takim przypadku przesłanianie jest bezcelowe i kompilator rozwiązuje wszelkie odwołania do tego samego elementu, gdyż miałoby Jeśli nastąpiła nie przesłanianie.</span><span class="sxs-lookup"><span data-stu-id="eef46-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="eef46-139">Ten element jest dostępnego elementu najmniejszą liczbę derivational kroki wstecz od klasy przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="eef46-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="eef46-140">Jeśli element zasłonięte jest procedurą, rozwiązanie jest do najbliższej dostępnej wersji o takiej samej nazwie, lista parametrów i zwracany typ.</span><span class="sxs-lookup"><span data-stu-id="eef46-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="eef46-141">Poniższy przykład pokazuje hierarchię dziedziczenia trzech klas.</span><span class="sxs-lookup"><span data-stu-id="eef46-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="eef46-142">Każda klasa definiuje `Sub` procedury `display`, i każdy pochodne klasy cieni `display` procedury w swojej klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="eef46-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
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
  
 <span data-ttu-id="eef46-143">W poprzednim przykładzie Klasa pochodna `secondClass` cieni `display` z `Private` procedury.</span><span class="sxs-lookup"><span data-stu-id="eef46-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="eef46-144">Gdy moduł `callDisplay` wywołania `display` w `secondClass`, kod wywołujący znajduje się poza `secondClass` i dlatego nie może uzyskiwać dostęp do prywatnego `display` procedury.</span><span class="sxs-lookup"><span data-stu-id="eef46-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="eef46-145">Przesłanianie jest bezcelowe, a kompilator jest rozpoznawana jako odwołanie do klasy bazowej `display` procedury.</span><span class="sxs-lookup"><span data-stu-id="eef46-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="eef46-146">Jednak dalsze klasy pochodnej `thirdClass` deklaruje `display` jako `Public`, dlatego ten kod w `callDisplay` do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="eef46-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="eef46-147">Przesłanianiem i zastępowaniem</span><span class="sxs-lookup"><span data-stu-id="eef46-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="eef46-148">Nie należy mylić przesłanianie z nadpisaniem.</span><span class="sxs-lookup"><span data-stu-id="eef46-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="eef46-149">Oba są używane, gdy klasa pochodna dziedziczy z klasy bazowej, a jednocześnie ponownie zdefiniować jeden element zadeklarowany z innym.</span><span class="sxs-lookup"><span data-stu-id="eef46-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="eef46-150">Jednak istnieją znaczne różnice między nimi.</span><span class="sxs-lookup"><span data-stu-id="eef46-150">But there are significant differences between the two.</span></span> <span data-ttu-id="eef46-151">Dla porównania, zobacz [różnice między przesłanianiem i przesłanianie](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="eef46-151">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="eef46-152">Przesłanianie i przeciążenie</span><span class="sxs-lookup"><span data-stu-id="eef46-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="eef46-153">Jeśli w klasie pochodnej w tle tego samego elementu klasy bazowej z więcej niż jeden element, przesłaniania elementy stają się przeciążone wersje tego elementu.</span><span class="sxs-lookup"><span data-stu-id="eef46-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="eef46-154">Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="eef46-154">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="eef46-155">Uzyskiwanie dostępu do elementu tekst z cieniem</span><span class="sxs-lookup"><span data-stu-id="eef46-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="eef46-156">Gdy uzyskujesz dostęp do elementu z klasy pochodnej, możesz normalnie to zrobić przez bieżące wystąpienie tej klasy pochodnej kwalifikując nazwę elementu z `Me` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="eef46-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="eef46-157">Klasy pochodne cieni elementów w klasie bazowej, można przejść do elementu klasy podstawowej kwalifikując ją za pomocą `MyBase` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="eef46-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="eef46-158">Na przykład uzyskiwania dostępu do elementu zasłonięte zobacz [jak: Dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="eef46-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="eef46-159">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="eef46-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="eef46-160">Jak utworzyć zmienną obiektu może również wpływać na czy klasy pochodnej uzyskuje dostęp do przesłaniania element lub tekst z cieniem elementu.</span><span class="sxs-lookup"><span data-stu-id="eef46-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="eef46-161">Poniższy przykład tworzy dwa obiekty z klasy pochodnej, ale jeden obiekt jest zadeklarowany jako klasę bazową, a drugi jako klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="eef46-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
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
  
 <span data-ttu-id="eef46-162">W poprzednim przykładzie, zmienna `basObj` jest zadeklarowany jako klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="eef46-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="eef46-163">Przypisywanie `dervCls` obiektu do niego stanowi konwersją rozszerzającą, a w związku z tym jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="eef46-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="eef46-164">Jednak klasy bazowej nie może uzyskiwać dostęp do wersji przesłaniania w zmiennej `z` w klasie pochodnej, dlatego kompilator rozpoznaje `basObj.z` do oryginalnej wartości klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="eef46-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef46-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eef46-165">See also</span></span>

- [<span data-ttu-id="eef46-166">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="eef46-166">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="eef46-167">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eef46-167">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="eef46-168">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="eef46-168">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="eef46-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="eef46-169">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="eef46-170">Overrides</span><span class="sxs-lookup"><span data-stu-id="eef46-170">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="eef46-171">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="eef46-171">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="eef46-172">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="eef46-172">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
