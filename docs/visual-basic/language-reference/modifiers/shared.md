---
title: Udostępniona
ms.date: 07/20/2015
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
ms.openlocfilehash: 98fa25d2283408dfb80e82fbc620a1b284e5c530
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349118"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="2e7cc-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e7cc-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="2e7cc-103">Określa, że co najmniej jeden zadeklarowany element programistyczny jest skojarzony z klasą lub strukturą w dużej, a nie z określonym wystąpieniem klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e7cc-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e7cc-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="2e7cc-105">Kiedy używać udostępnionego</span><span class="sxs-lookup"><span data-stu-id="2e7cc-105">When to Use Shared</span></span>  
 <span data-ttu-id="2e7cc-106">Udostępnienie składowej klasy lub struktury sprawia, że jest ona dostępna dla każdego wystąpienia, a nie bez *udziału*, gdzie każde wystąpienie zachowuje własną kopię.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="2e7cc-107">Jest to przydatne, na przykład jeśli wartość zmiennej dotyczy całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="2e7cc-108">Jeśli zadeklarujesz tę zmienną do `Shared`, wszystkie wystąpienia uzyskują dostęp do tej samej lokalizacji magazynu, a jeśli jedno wystąpienie zmieni wartość zmiennej, wszystkie wystąpienia uzyskują dostęp do zaktualizowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="2e7cc-109">Udostępnianie nie zmienia poziomu dostępu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="2e7cc-110">Na przykład element członkowski klasy może być współużytkowany i prywatny (dostępny tylko w ramach klasy) lub nieudostępniony i publiczny.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="2e7cc-111">Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2e7cc-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2e7cc-112">Reguły</span><span class="sxs-lookup"><span data-stu-id="2e7cc-112">Rules</span></span>  
  
- <span data-ttu-id="2e7cc-113">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="2e7cc-113">**Declaration Context.**</span></span> <span data-ttu-id="2e7cc-114">`Shared` można używać tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="2e7cc-115">Oznacza to, że kontekst deklaracji dla elementu `Shared` musi być klasą lub strukturą i nie może być plikiem źródłowym, przestrzenią nazw ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
- <span data-ttu-id="2e7cc-116">**Połączone modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="2e7cc-116">**Combined Modifiers.**</span></span> <span data-ttu-id="2e7cc-117">Nie można określić `Shared` razem z [zastąpień](../../../visual-basic/language-reference/modifiers/overrides.md), [zastąpienia](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)lub [static](../../../visual-basic/language-reference/modifiers/static.md) w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
- <span data-ttu-id="2e7cc-118">**Korzystając.**</span><span class="sxs-lookup"><span data-stu-id="2e7cc-118">**Accessing.**</span></span> <span data-ttu-id="2e7cc-119">Dostęp do elementu udostępnionego można uzyskać, uprawniając do jego nazwy klasy lub struktury, a nie nazwy zmiennej określonego wystąpienia jego klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="2e7cc-120">Nie trzeba nawet utworzyć wystąpienia klasy lub struktury, aby uzyskać dostęp do jego udostępnionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="2e7cc-121">Poniższy przykład wywołuje procedurę udostępnioną <xref:System.Double.IsNaN%2A> uwidocznioną przez strukturę <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- <span data-ttu-id="2e7cc-122">**Niejawne udostępnianie.**</span><span class="sxs-lookup"><span data-stu-id="2e7cc-122">**Implicit Sharing.**</span></span> <span data-ttu-id="2e7cc-123">Nie można użyć modyfikatora `Shared` w [instrukcji const](../../../visual-basic/language-reference/statements/const-statement.md), ale stałe są niejawnie udostępnione.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="2e7cc-124">Podobnie nie można zadeklarować elementu członkowskiego modułu lub interfejsu do `Shared`, ale są one niejawnie udostępnione.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2e7cc-125">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="2e7cc-125">Behavior</span></span>  
  
- <span data-ttu-id="2e7cc-126">**Chowan.**</span><span class="sxs-lookup"><span data-stu-id="2e7cc-126">**Storage.**</span></span> <span data-ttu-id="2e7cc-127">Współdzielona zmienna lub zdarzenie jest przechowywane w pamięci tylko raz, niezależnie od tego, jak wiele lub kilka wystąpień utworzonych przez siebie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="2e7cc-128">Podobnie wspólna procedura lub właściwość zawiera tylko jeden zestaw zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
- <span data-ttu-id="2e7cc-129">**Uzyskiwanie dostępu za za poorednictwem zmiennej wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="2e7cc-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="2e7cc-130">Istnieje możliwość uzyskania dostępu do elementu udostępnionego przez zakwalifikowanie go o nazwę zmiennej, która zawiera określone wystąpienie jego klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="2e7cc-131">Chociaż zwykle działa to w oczekiwany sposób, kompilator generuje komunikat ostrzegawczy i zapewnia dostęp za pomocą nazwy klasy lub struktury zamiast zmiennej.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
- <span data-ttu-id="2e7cc-132">**Uzyskiwanie dostępu za poorednictwem wyrażenia wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="2e7cc-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="2e7cc-133">Jeśli uzyskujesz dostęp do udostępnionego elementu za pomocą wyrażenia, które zwraca wystąpienie jego klasy lub struktury, kompilator uzyskuje dostęp poprzez nazwę klasy lub struktury zamiast oceniania wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="2e7cc-134">Daje to nieoczekiwane wyniki, jeśli zamierzasz wykonać wyrażenie do wykonania innych czynności, a także zwracające wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="2e7cc-135">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-135">The following example illustrates this.</span></span>  
  
    ```vb
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
  
     <span data-ttu-id="2e7cc-136">W poprzednim przykładzie kompilator generuje komunikat ostrzegawczy, gdy kod uzyskuje dostęp do zmiennej udostępnionej `total` za pomocą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="2e7cc-137">W każdym przypadku uzyskuje dostęp bezpośrednio za pomocą klasy `shareTotal` i nie korzysta z żadnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="2e7cc-138">W przypadku zamierzonego wywołania procedury `returnClass`oznacza to, że nie generuje nawet wywołania do `returnClass`, więc dodatkowa akcja przedstawiająca "Function returnClass () wywołana" nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="2e7cc-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="2e7cc-139">Modyfikator `Shared` może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="2e7cc-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2e7cc-140">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2e7cc-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="2e7cc-141">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2e7cc-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="2e7cc-142">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2e7cc-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="2e7cc-143">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2e7cc-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="2e7cc-144">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2e7cc-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="2e7cc-145">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2e7cc-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2e7cc-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e7cc-146">See also</span></span>

- [<span data-ttu-id="2e7cc-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="2e7cc-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="2e7cc-148">Static</span><span class="sxs-lookup"><span data-stu-id="2e7cc-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="2e7cc-149">Okres istnienia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e7cc-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="2e7cc-150">Procedury</span><span class="sxs-lookup"><span data-stu-id="2e7cc-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="2e7cc-151">Struktury</span><span class="sxs-lookup"><span data-stu-id="2e7cc-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="2e7cc-152">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="2e7cc-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
