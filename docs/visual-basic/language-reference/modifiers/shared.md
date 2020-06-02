---
title: Shared
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
ms.openlocfilehash: bc63de4bda1e8e605e25fbe293686c187dd4d005
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290996"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="0d978-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d978-102">Shared (Visual Basic)</span></span>

<span data-ttu-id="0d978-103">Określa, że co najmniej jeden zadeklarowany element programistyczny jest skojarzony z klasą lub strukturą w dużej, a nie z określonym wystąpieniem klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0d978-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>

## <a name="when-to-use-shared"></a><span data-ttu-id="0d978-104">Kiedy używać udostępnionego</span><span class="sxs-lookup"><span data-stu-id="0d978-104">When to Use Shared</span></span>

<span data-ttu-id="0d978-105">Udostępnienie składowej klasy lub struktury sprawia, że jest ona dostępna dla każdego wystąpienia, a nie jako *nieudostępnione*, gdzie każde wystąpienie zachowuje własną kopię.</span><span class="sxs-lookup"><span data-stu-id="0d978-105">Sharing a member of a class or structure makes it available to every instance, rather than *non-shared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="0d978-106">Jest to przydatne, na przykład jeśli wartość zmiennej dotyczy całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d978-106">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="0d978-107">Jeśli ta zmienna jest zadeklarowana `Shared` , wszystkie wystąpienia uzyskują dostęp do tej samej lokalizacji magazynu, a jeśli jedno wystąpienie zmieni wartość zmiennej, wszystkie wystąpienia uzyskują dostęp do zaktualizowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="0d978-107">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>

<span data-ttu-id="0d978-108">Udostępnianie nie zmienia poziomu dostępu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0d978-108">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="0d978-109">Na przykład element członkowski klasy może być współużytkowany i prywatny (dostępny tylko w ramach klasy) lub nieudostępniony i publiczny.</span><span class="sxs-lookup"><span data-stu-id="0d978-109">For example, a class member can be shared and private (accessible only from within the class), or non-shared and public.</span></span> <span data-ttu-id="0d978-110">Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0d978-110">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

## <a name="rules"></a><span data-ttu-id="0d978-111">Reguły</span><span class="sxs-lookup"><span data-stu-id="0d978-111">Rules</span></span>

- <span data-ttu-id="0d978-112">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="0d978-112">**Declaration Context.**</span></span> <span data-ttu-id="0d978-113">Można używać `Shared` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="0d978-113">You can use `Shared` only at module level.</span></span> <span data-ttu-id="0d978-114">Oznacza to, że kontekst deklaracji dla `Shared` elementu musi być klasą lub strukturą i nie może być plikiem źródłowym, przestrzenią nazw ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="0d978-114">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="0d978-115">**Połączone modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="0d978-115">**Combined Modifiers.**</span></span> <span data-ttu-id="0d978-116">Nie można określić `Shared` razem z [zastąpień](../../../visual-basic/language-reference/modifiers/overrides.md), [zastąpienia](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)lub [static](../../../visual-basic/language-reference/modifiers/static.md) w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="0d978-116">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>

- <span data-ttu-id="0d978-117">**Korzystając.**</span><span class="sxs-lookup"><span data-stu-id="0d978-117">**Accessing.**</span></span> <span data-ttu-id="0d978-118">Dostęp do elementu udostępnionego można uzyskać, uprawniając do jego nazwy klasy lub struktury, a nie nazwy zmiennej określonego wystąpienia jego klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0d978-118">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="0d978-119">Nie trzeba nawet utworzyć wystąpienia klasy lub struktury, aby uzyskać dostęp do jego udostępnionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="0d978-119">You do not even have to create an instance of a class or structure to access its shared members.</span></span>

     <span data-ttu-id="0d978-120">Poniższy przykład wywołuje procedurę udostępnioną <xref:System.Double.IsNaN%2A> uwidocznioną przez <xref:System.Double> strukturę.</span><span class="sxs-lookup"><span data-stu-id="0d978-120">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- <span data-ttu-id="0d978-121">**Niejawne udostępnianie.**</span><span class="sxs-lookup"><span data-stu-id="0d978-121">**Implicit Sharing.**</span></span> <span data-ttu-id="0d978-122">Nie można użyć `Shared` modyfikatora w [instrukcji const](../../../visual-basic/language-reference/statements/const-statement.md), ale stałe są niejawnie udostępnione.</span><span class="sxs-lookup"><span data-stu-id="0d978-122">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="0d978-123">Podobnie nie można zadeklarować elementu członkowskiego modułu lub interfejsu jako `Shared` , ale są one niejawnie udostępnione.</span><span class="sxs-lookup"><span data-stu-id="0d978-123">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>

## <a name="behavior"></a><span data-ttu-id="0d978-124">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="0d978-124">Behavior</span></span>

- <span data-ttu-id="0d978-125">**Chowan.**</span><span class="sxs-lookup"><span data-stu-id="0d978-125">**Storage.**</span></span> <span data-ttu-id="0d978-126">Współdzielona zmienna lub zdarzenie jest przechowywane w pamięci tylko raz, niezależnie od tego, jak wiele lub kilka wystąpień utworzonych przez siebie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0d978-126">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="0d978-127">Podobnie wspólna procedura lub właściwość zawiera tylko jeden zestaw zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0d978-127">Similarly, a shared procedure or property holds only one set of local variables.</span></span>

- <span data-ttu-id="0d978-128">**Uzyskiwanie dostępu za za poorednictwem zmiennej wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="0d978-128">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="0d978-129">Istnieje możliwość uzyskania dostępu do elementu udostępnionego przez zakwalifikowanie go o nazwę zmiennej, która zawiera określone wystąpienie jego klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0d978-129">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="0d978-130">Chociaż zwykle działa to w oczekiwany sposób, kompilator generuje komunikat ostrzegawczy i zapewnia dostęp za pomocą nazwy klasy lub struktury zamiast zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0d978-130">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>

- <span data-ttu-id="0d978-131">**Uzyskiwanie dostępu za poorednictwem wyrażenia wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="0d978-131">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="0d978-132">Jeśli uzyskujesz dostęp do udostępnionego elementu za pomocą wyrażenia, które zwraca wystąpienie jego klasy lub struktury, kompilator uzyskuje dostęp poprzez nazwę klasy lub struktury zamiast oceniania wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="0d978-132">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="0d978-133">Daje to nieoczekiwane wyniki, jeśli zamierzasz wykonać wyrażenie do wykonania innych czynności, a także zwracające wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="0d978-133">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="0d978-134">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0d978-134">The following example illustrates this.</span></span>
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     <span data-ttu-id="0d978-135">W poprzednim przykładzie kompilator generuje komunikat ostrzegawczy, gdy kod uzyskuje dostęp do właściwości udostępnionej `Total` za pomocą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0d978-135">In the preceding example, the compiler generates a warning message both times the code accesses the shared property `Total` through an instance.</span></span> <span data-ttu-id="0d978-136">W każdym przypadku uzyskuje dostęp bezpośrednio za pomocą klasy `ShareTotal` i nie korzysta z żadnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0d978-136">In each case it makes the access directly through the class `ShareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="0d978-137">W przypadku zamierzonego wywołania procedury `ReturnClass` oznacza to, że nie generuje nawet wywołania do `ReturnClass` , więc dodatkowa akcja wyświetlania "Function ReturnClass () wywołana" nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="0d978-137">In the case of the intended call to the procedure `ReturnClass`, this means it does not even generate a call to `ReturnClass`, so the additional action of displaying "Function ReturnClass() called" is not performed.</span></span>

<span data-ttu-id="0d978-138">`Shared`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="0d978-138">The `Shared` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="0d978-139">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0d978-139">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="0d978-140">Event — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="0d978-140">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="0d978-141">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0d978-141">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="0d978-142">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="0d978-142">Operator Statement</span></span>](../operator-statement.md)
- [<span data-ttu-id="0d978-143">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="0d978-143">Property Statement</span></span>](../property-statement.md)
- [<span data-ttu-id="0d978-144">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0d978-144">Sub Statement</span></span>](../sub-statement.md)
  
## <a name="see-also"></a><span data-ttu-id="0d978-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d978-145">See also</span></span>

- [<span data-ttu-id="0d978-146">Shadows</span><span class="sxs-lookup"><span data-stu-id="0d978-146">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="0d978-147">Ruchom</span><span class="sxs-lookup"><span data-stu-id="0d978-147">Static</span></span>](static.md)
- [<span data-ttu-id="0d978-148">Okres istnienia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d978-148">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="0d978-149">Procedury</span><span class="sxs-lookup"><span data-stu-id="0d978-149">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="0d978-150">Struktury</span><span class="sxs-lookup"><span data-stu-id="0d978-150">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0d978-151">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="0d978-151">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
