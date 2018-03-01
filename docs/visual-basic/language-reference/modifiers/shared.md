---
title: Shared (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fce13c308a449e63eacc2bc4c94c274c7e25506a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="shared-visual-basic"></a><span data-ttu-id="f123d-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f123d-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="f123d-103">Określa, że co najmniej jeden zadeklarowany element programistyczny skojarzonych z klasy lub struktury w dużych, a nie z konkretnym wystąpieniem klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f123d-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f123d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f123d-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="f123d-105">Kiedy należy używać udostępnionych</span><span class="sxs-lookup"><span data-stu-id="f123d-105">When to Use Shared</span></span>  
 <span data-ttu-id="f123d-106">Udostępnianie elementem członkowskim klasy lub struktury udostępnia go do każdego wystąpienia, a nie *udostępniana*, gdzie każde wystąpienie zachowuje własną kopię.</span><span class="sxs-lookup"><span data-stu-id="f123d-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="f123d-107">Jest to przydatne, na przykład, jeśli wartość zmiennej, która ma zastosowanie do całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f123d-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="f123d-108">Deklarowanie zmiennej jako `Shared`, następnie wszystkie wystąpienia dostęp do tej samej lokalizacji magazynu, a jeśli jedno wystąpienie zmieni wartość zmiennej, wszystkich wystąpień dostęp zaktualizowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="f123d-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="f123d-109">Udostępnianie nie zmienia poziom dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f123d-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="f123d-110">Na przykład może być udostępniony element członkowski klasy i prywatny (dostępny tylko w obrębie klasy), lub udostępniana, jak i publicznych.</span><span class="sxs-lookup"><span data-stu-id="f123d-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="f123d-111">Aby uzyskać więcej informacji, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f123d-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f123d-112">Reguły</span><span class="sxs-lookup"><span data-stu-id="f123d-112">Rules</span></span>  
  
-   <span data-ttu-id="f123d-113">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="f123d-113">**Declaration Context.**</span></span> <span data-ttu-id="f123d-114">Można użyć `Shared` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="f123d-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="f123d-115">Oznacza to, że w kontekście deklaracji `Shared` elementu musi być klasy lub struktury i nie może być plik źródłowy, przestrzeni nazw lub procedury.</span><span class="sxs-lookup"><span data-stu-id="f123d-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="f123d-116">**Łączna modyfikatorów.**</span><span class="sxs-lookup"><span data-stu-id="f123d-116">**Combined Modifiers.**</span></span> <span data-ttu-id="f123d-117">Nie można określić `Shared` razem z [zastępuje](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), lub [ Statyczne](../../../visual-basic/language-reference/modifiers/static.md) w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="f123d-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
-   <span data-ttu-id="f123d-118">**Uzyskiwanie dostępu do.**</span><span class="sxs-lookup"><span data-stu-id="f123d-118">**Accessing.**</span></span> <span data-ttu-id="f123d-119">Dostęp do udostępnionego elementu przy kwalifikujące go z nazwą klasy lub struktury, a nie z nazwę zmiennej określonego wystąpienia klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f123d-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="f123d-120">Nawet nie trzeba tworzyć wystąpienia klasy lub struktury, dostęp do jego udostępniane elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="f123d-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="f123d-121">Poniższy przykład wywołuje procedurę udostępnionego <xref:System.Double.IsNaN%2A> udostępnianych przez <xref:System.Double> struktury.</span><span class="sxs-lookup"><span data-stu-id="f123d-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   <span data-ttu-id="f123d-122">**Niejawne udostępniania.**</span><span class="sxs-lookup"><span data-stu-id="f123d-122">**Implicit Sharing.**</span></span> <span data-ttu-id="f123d-123">Nie można użyć `Shared` modyfikator w [instrukcja Const](../../../visual-basic/language-reference/statements/const-statement.md), ale stałe niejawnie są udostępnione.</span><span class="sxs-lookup"><span data-stu-id="f123d-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="f123d-124">Podobnie, nie można zadeklarować członka modułu lub interfejs `Shared`, ale niejawnie są one udostępniane.</span><span class="sxs-lookup"><span data-stu-id="f123d-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="f123d-125">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="f123d-125">Behavior</span></span>  
  
-   <span data-ttu-id="f123d-126">**Magazyn.**</span><span class="sxs-lookup"><span data-stu-id="f123d-126">**Storage.**</span></span> <span data-ttu-id="f123d-127">Udostępniona zmienna lub zdarzenia jest przechowywany w pamięci tylko raz, niezależnie od tego, ile lub kilka wystąpień utworzyć jej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f123d-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="f123d-128">Podobnie współdzielonej procedury lub właściwości zawiera tylko jeden zestaw zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="f123d-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
-   <span data-ttu-id="f123d-129">**Uzyskiwanie dostępu za pośrednictwem zmiennej wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="f123d-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="f123d-130">Istnieje możliwość uzyskania dostępu do udostępnionego elementu przy kwalifikujących się on na nazwę zmiennej, która zawiera określone wystąpienia klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f123d-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="f123d-131">Chociaż to zwykle działa zgodnie z oczekiwaniami, kompilator generuje ostrzeżenie i umożliwia dostęp za pośrednictwem Nazwa klasy lub struktury, zamiast zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f123d-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
-   <span data-ttu-id="f123d-132">**Uzyskiwanie dostępu za pomocą wyrażenia wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="f123d-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="f123d-133">Jeśli dostęp do udostępnionego elementu przez wyrażenie, które zwraca wystąpienie klasy lub struktury, kompilator sprawia, że dostęp za pośrednictwem Nazwa klasy lub struktury, zamiast obliczenie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f123d-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="f123d-134">Tworzy nieoczekiwane wyniki, jeśli przeznaczony wyrażenie, które ma wykonywać inne akcje, a także zwracanie wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="f123d-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="f123d-135">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="f123d-135">The following example illustrates this.</span></span>  
  
    ```  
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     <span data-ttu-id="f123d-136">W powyższym przykładzie kompilator generuje ostrzeżenie razem kod uzyskuje dostęp do współdzielonej zmiennej `total` za pomocą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f123d-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="f123d-137">W każdym przypadku ułatwia dostępu bezpośrednio za pomocą klasy `shareTotal` i nie należy używać wszystkie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f123d-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="f123d-138">W przypadku zamierzonej wywołanie procedury `returnClass`, oznacza to, że nie generuje nawet wywołanie `returnClass`, więc dodatkowych akcji wyświetlanie "returnClass() funkcji o nazwie" nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="f123d-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="f123d-139">`Shared` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="f123d-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f123d-140">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f123d-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="f123d-141">Event — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f123d-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="f123d-142">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f123d-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="f123d-143">Operator — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f123d-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="f123d-144">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f123d-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="f123d-145">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f123d-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f123d-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f123d-146">See Also</span></span>  
 [<span data-ttu-id="f123d-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="f123d-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="f123d-148">Statyczne</span><span class="sxs-lookup"><span data-stu-id="f123d-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="f123d-149">Okres istnienia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f123d-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="f123d-150">Procedury</span><span class="sxs-lookup"><span data-stu-id="f123d-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="f123d-151">Struktury</span><span class="sxs-lookup"><span data-stu-id="f123d-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="f123d-152">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="f123d-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
