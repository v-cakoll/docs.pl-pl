---
title: Zakres w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: d6692379626d787b728d6e92bd447c4a96e6680e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="c8ec1-102">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8ec1-102">Scope in Visual Basic</span></span>
<span data-ttu-id="c8ec1-103">*Zakres* elementu zadeklarowane to zbiór wszystkich kod, który może odwoływać się do niego bez kwalifikujących się jego nazwę lub udostępnianie przy [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="c8ec1-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="c8ec1-104">Element może mieć zakresu w jednej z następujących poziomach:</span><span class="sxs-lookup"><span data-stu-id="c8ec1-104">An element can have scope at one of the following levels:</span></span>  
  
|<span data-ttu-id="c8ec1-105">Poziom</span><span class="sxs-lookup"><span data-stu-id="c8ec1-105">Level</span></span>|<span data-ttu-id="c8ec1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c8ec1-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c8ec1-107">Zakres bloku</span><span class="sxs-lookup"><span data-stu-id="c8ec1-107">Block scope</span></span>|<span data-ttu-id="c8ec1-108">Dostępne tylko w kodzie bloku, w którym zadeklarowano</span><span class="sxs-lookup"><span data-stu-id="c8ec1-108">Available only within the code block in which it is declared</span></span>|  
|<span data-ttu-id="c8ec1-109">Zakres procedury</span><span class="sxs-lookup"><span data-stu-id="c8ec1-109">Procedure scope</span></span>|<span data-ttu-id="c8ec1-110">Dostępne dla całego kodu w ramach procedury, w którym jest zadeklarowana</span><span class="sxs-lookup"><span data-stu-id="c8ec1-110">Available to all code within the procedure in which it is declared</span></span>|  
|<span data-ttu-id="c8ec1-111">Zakres modułu</span><span class="sxs-lookup"><span data-stu-id="c8ec1-111">Module scope</span></span>|<span data-ttu-id="c8ec1-112">Dostępne dla wszystkich kodu w module, klasy lub struktury, w którym jest zadeklarowana</span><span class="sxs-lookup"><span data-stu-id="c8ec1-112">Available to all code within the module, class, or structure in which it is declared</span></span>|  
|<span data-ttu-id="c8ec1-113">Zakres Namespace</span><span class="sxs-lookup"><span data-stu-id="c8ec1-113">Namespace scope</span></span>|<span data-ttu-id="c8ec1-114">Dostępne dla całego kodu w przestrzeni nazw, w którym jest zadeklarowana</span><span class="sxs-lookup"><span data-stu-id="c8ec1-114">Available to all code in the namespace in which it is declared</span></span>|  
  
 <span data-ttu-id="c8ec1-115">Te poziomy postęp zakresu najwęższym (Blokuj) do uzyskiwania (przestrzeni nazw), gdzie *najwęższy zakres* oznacza, że najmniejszy zestaw kod, który może odwoływać się do elementu bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="c8ec1-116">Aby uzyskać więcej informacji zobacz "Poziomy zakresu" na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-116">For more information, see "Levels of Scope" on this page.</span></span>  
  
## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="c8ec1-117">Określanie zakresu i definiowanie zmiennych</span><span class="sxs-lookup"><span data-stu-id="c8ec1-117">Specifying Scope and Defining Variables</span></span>  
 <span data-ttu-id="c8ec1-118">Możesz określić zakres elementu przy deklarowaniu go.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="c8ec1-119">Zakres może zależeć od następujących czynników:</span><span class="sxs-lookup"><span data-stu-id="c8ec1-119">The scope can depend on the following factors:</span></span>  
  
-   <span data-ttu-id="c8ec1-120">Region (bloku, procedury, modułu, klasy lub struktury), w którym można zadeklarować elementu</span><span class="sxs-lookup"><span data-stu-id="c8ec1-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>  
  
-   <span data-ttu-id="c8ec1-121">Przestrzeń nazw zawierająca deklaracji elementu</span><span class="sxs-lookup"><span data-stu-id="c8ec1-121">The namespace containing the element's declaration</span></span>  
  
-   <span data-ttu-id="c8ec1-122">Poziom dostępu, który został zadeklarowany dla elementu</span><span class="sxs-lookup"><span data-stu-id="c8ec1-122">The access level you declare for the element</span></span>  
  
 <span data-ttu-id="c8ec1-123">Należy dopilnować, podczas definiowania zmiennych o tej samej nazwie, ale inny zakres, ponieważ w ten sposób może prowadzić do nieoczekiwanych wyników.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="c8ec1-124">Aby uzyskać więcej informacji, zobacz [odwołania do elementów zadeklarowany](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="c8ec1-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="levels-of-scope"></a><span data-ttu-id="c8ec1-125">Poziomy zakresu</span><span class="sxs-lookup"><span data-stu-id="c8ec1-125">Levels of Scope</span></span>  
 <span data-ttu-id="c8ec1-126">Element programowania są dostępne w całej region ją zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="c8ec1-127">Cały kod w tym samym regionie mogą odwoływać się do elementu bez kwalifikujących się jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-127">All code in the same region can refer to the element without qualifying its name.</span></span>  
  
### <a name="block-scope"></a><span data-ttu-id="c8ec1-128">Zasięg bloku</span><span class="sxs-lookup"><span data-stu-id="c8ec1-128">Block Scope</span></span>  
 <span data-ttu-id="c8ec1-129">Blok jest zestaw instrukcji ujętą w nawiasy klamrowe inicjowanie i kończenie instrukcji deklaracji, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="c8ec1-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>  
  
-   <span data-ttu-id="c8ec1-130">`Do` I `Loop`</span><span class="sxs-lookup"><span data-stu-id="c8ec1-130">`Do` and `Loop`</span></span>  
  
-   <span data-ttu-id="c8ec1-131">`For` [`Each`] i `Next`</span><span class="sxs-lookup"><span data-stu-id="c8ec1-131">`For` [`Each`] and `Next`</span></span>  
  
-   <span data-ttu-id="c8ec1-132">`If` I `End If`</span><span class="sxs-lookup"><span data-stu-id="c8ec1-132">`If` and `End If`</span></span>  
  
-   <span data-ttu-id="c8ec1-133">`Select` I `End Select`</span><span class="sxs-lookup"><span data-stu-id="c8ec1-133">`Select` and `End Select`</span></span>  
  
-   <span data-ttu-id="c8ec1-134">`SyncLock` I `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="c8ec1-134">`SyncLock` and `End SyncLock`</span></span>  
  
-   <span data-ttu-id="c8ec1-135">`Try` I `End Try`</span><span class="sxs-lookup"><span data-stu-id="c8ec1-135">`Try` and `End Try`</span></span>  
  
-   <span data-ttu-id="c8ec1-136">`While` I `End While`</span><span class="sxs-lookup"><span data-stu-id="c8ec1-136">`While` and `End While`</span></span>  
  
-   <span data-ttu-id="c8ec1-137">`With` I `End With`</span><span class="sxs-lookup"><span data-stu-id="c8ec1-137">`With` and `End With`</span></span>  
  
 <span data-ttu-id="c8ec1-138">Jeżeli można zadeklarować zmiennej w bloku, możesz używać go tylko w tym bloku.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="c8ec1-139">W poniższym przykładzie zakres zmienna całkowitoliczbowa `cube` bloku między `If` i `End If`, a nie mogą odwoływać się do `cube` podczas wykonywania przekazuje poza blokiem.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  <span data-ttu-id="c8ec1-140">Nawet jeśli zakresu zmiennej jest ograniczona do bloku, jego okres istnienia jest nadal całej procedury.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="c8ec1-141">Po wprowadzeniu bloku w więcej niż raz podczas wykonywania procedury każdej zmiennej w bloku zachowuje jego poprzednią wartość.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="c8ec1-142">Aby uniknąć nieoczekiwanych wyników w takim przypadku, jest rozsądnego zainicjować zmienne bloku na początku bloku.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>  
  
### <a name="procedure-scope"></a><span data-ttu-id="c8ec1-143">Zakres procedury</span><span class="sxs-lookup"><span data-stu-id="c8ec1-143">Procedure Scope</span></span>  
 <span data-ttu-id="c8ec1-144">Element zadeklarowany w obrębie procedury nie jest dostępna spoza tej procedury.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="c8ec1-145">Można go używać tylko tej procedury, która zawiera deklarację.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="c8ec1-146">Zmienne na tym poziomie są również znane jako *zmiennych lokalnych*.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="c8ec1-147">Deklarowanie je za pomocą [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), z lub bez [statycznych](../../../../visual-basic/language-reference/modifiers/static.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>  
  
 <span data-ttu-id="c8ec1-148">Zakres procedury i bloku są ściśle powiązane.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="c8ec1-149">Jeśli należy zadeklarować zmienną wewnątrz procedury, ale spoza bloku w ramach tej procedury, można traktować jako o zakresie bloku, w którym bloku jest całą procedurę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8ec1-150">Wszystkie elementy lokalne, nawet jeśli są one `Static` zmienne, są prywatne dla procedury, w jakiej widnieją.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="c8ec1-151">Nie można zadeklarować przy użyciu dowolnego elementu [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe w procedurze.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>  
  
### <a name="module-scope"></a><span data-ttu-id="c8ec1-152">Zakres modułu</span><span class="sxs-lookup"><span data-stu-id="c8ec1-152">Module Scope</span></span>  
 <span data-ttu-id="c8ec1-153">Dla wygody pojedynczy termin *poziom modułu* dotyczą modułów, klasy i struktury.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="c8ec1-154">Elementy na tym poziomie można zadeklarować przez umieszczenie instrukcji deklaracji poza żadnych procedurę lub blok, ale w ramach modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>  
  
 <span data-ttu-id="c8ec1-155">Po wprowadzeniu deklaracji na poziomie modułu, należy wybrać poziom dostępu określa zakres.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="c8ec1-156">Przestrzeń nazw, który zawiera modułu, klasy lub struktury dotyczy również zakres.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>  
  
 <span data-ttu-id="c8ec1-157">Elementy, dla których należy zadeklarować [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) poziom dostępu są dostępne do każdej procedury w module, ale nie do żadnego kodu w innym module.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="c8ec1-158">`Dim` Domyślnie instrukcji na poziomie modułu `Private` Jeśli nie używasz dowolnego słowa kluczowe do poziomu dostępu.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="c8ec1-159">Jednak można tworzyć poziom dostępu i zakres bardziej oczywistymi, przy użyciu `Private` — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>  
  
 <span data-ttu-id="c8ec1-160">W poniższym przykładzie wszystkie procedury zdefiniowane w module mogą odwoływać się do zmiennej ciągu `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="c8ec1-161">Druga procedura jest wywoływana, wyświetla zawartość zmiennej ciągu `strMsg` w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a><span data-ttu-id="c8ec1-162">Zakres Namespace</span><span class="sxs-lookup"><span data-stu-id="c8ec1-162">Namespace Scope</span></span>  
 <span data-ttu-id="c8ec1-163">W przypadku elementu w poziomie przy użyciu modułu [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) lub [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe, staje się dostępny dla wszystkich procedur w całej przestrzeni nazw, w którym zadeklarowano ten element.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="c8ec1-164">Z następującą modyfikacją jak w poprzednim przykładzie zmienna string `strMsg` mogą być przywoływane przez kod w dowolnym miejscu jego deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 <span data-ttu-id="c8ec1-165">Zakres Namespace zawiera zagnieżdżone przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="c8ec1-166">Element dostępne w przestrzeni nazw jest również dostępne w przestrzeni nazw zagnieżdżone wewnątrz tego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>  
  
 <span data-ttu-id="c8ec1-167">Jeśli projekt nie zawiera żadnych [instrukcji Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md), wszystko w projekcie jest w tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="c8ec1-168">W takim przypadku zakresie przestrzeni nazw można traktować jako zakres projektu.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="c8ec1-169">`Public` elementy w module, klasy lub struktury są również dostępne dla każdego projektu, który odwołuje się do swojego projektu.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>  
  
## <a name="choice-of-scope"></a><span data-ttu-id="c8ec1-170">Wybór zakresu</span><span class="sxs-lookup"><span data-stu-id="c8ec1-170">Choice of Scope</span></span>  
 <span data-ttu-id="c8ec1-171">Deklaracja zmiennej możesz należy mieć na uwadze następujące kwestie podczas wybierania jej zakres.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>  
  
### <a name="advantages-of-local-variables"></a><span data-ttu-id="c8ec1-172">Zalety zmiennych lokalnych</span><span class="sxs-lookup"><span data-stu-id="c8ec1-172">Advantages of Local Variables</span></span>  
 <span data-ttu-id="c8ec1-173">Zmienne lokalne są dobrym rozwiązaniem w przypadku dowolnych tymczasowego obliczeń z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="c8ec1-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>  
  
-   <span data-ttu-id="c8ec1-174">**Unikanie konfliktów nazw.**</span><span class="sxs-lookup"><span data-stu-id="c8ec1-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="c8ec1-175">Nazwy zmiennych lokalnych nie są podatne na konflikt.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="c8ec1-176">Na przykład można utworzyć kilka różne procedury zawierające zmiennej o nazwie `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="c8ec1-177">Tak długo, jak każdy `intTemp` jest zadeklarowany jako zmienną lokalną każdej procedury rozpoznaje tylko własną wersję z `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="c8ec1-178">Wszelkie jednej procedury można zmienić wartości w jego lokalnej `intTemp` bez wpływu na `intTemp` zmiennych w innych procedur.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>  
  
-   <span data-ttu-id="c8ec1-179">**Zużycie pamięci.**</span><span class="sxs-lookup"><span data-stu-id="c8ec1-179">**Memory Consumption.**</span></span> <span data-ttu-id="c8ec1-180">Zmienne lokalne używa pamięci tylko wtedy, gdy ich procedura jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="c8ec1-181">Ich pamięci jest likwidowany, gdy procedura powróci do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="c8ec1-182">Z kolei [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) i [statycznych](../../../../visual-basic/language-reference/modifiers/static.md) zmienne zużywają zasoby pamięci, dopóki aplikacja przestanie działać, należy więc je tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="c8ec1-183">*Wystąpienie zmienne* używa pamięci podczas ich wystąpienia nadal istnieje, dzięki czemu ich mniej wydajne niż zmiennych lokalnych, ale potencjalnie bardziej efektywne niż `Shared` lub `Static` zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>  
  
### <a name="minimizing-scope"></a><span data-ttu-id="c8ec1-184">Minimalizowanie zakresu</span><span class="sxs-lookup"><span data-stu-id="c8ec1-184">Minimizing Scope</span></span>  
 <span data-ttu-id="c8ec1-185">Ogólnie rzecz biorąc, przy deklarowaniu dowolną zmienną lub stałą, jest dobrym programowania rozwiązań, aby zakres jak to możliwe (zakresie bloku jest najwęższym).</span><span class="sxs-lookup"><span data-stu-id="c8ec1-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="c8ec1-186">Pomaga zachować pamięci i minimalizuje ryzyko błędnego odwołujących się do zmiennej niewłaściwy kod.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="c8ec1-187">Podobnie, należy zadeklarować zmiennej jako [statycznych](../../../../visual-basic/language-reference/modifiers/static.md) tylko gdy jest konieczne w celu zachowania jego wartość z zakresu od wywołań procedur.</span><span class="sxs-lookup"><span data-stu-id="c8ec1-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ec1-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8ec1-188">See Also</span></span>  
 [<span data-ttu-id="c8ec1-189">Charakterystyka zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="c8ec1-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="c8ec1-190">Instrukcje: kontrolowanie zakresu zmiennej</span><span class="sxs-lookup"><span data-stu-id="c8ec1-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [<span data-ttu-id="c8ec1-191">Okres istnienia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8ec1-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="c8ec1-192">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8ec1-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="c8ec1-193">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="c8ec1-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="c8ec1-194">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="c8ec1-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
