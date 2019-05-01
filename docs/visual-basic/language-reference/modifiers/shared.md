---
title: Shared (Visual Basic)
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
ms.openlocfilehash: 12c81a9a0651088a348afeaff3b71935d289da53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778745"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="6c162-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c162-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="6c162-103">Określa, że co najmniej jeden zadeklarowany element programistyczny skojarzonych z klasy lub struktury w dużych, a nie przy użyciu określonego wystąpienia klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="6c162-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c162-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c162-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="6c162-105">Kiedy należy używać udostępnionych</span><span class="sxs-lookup"><span data-stu-id="6c162-105">When to Use Shared</span></span>  
 <span data-ttu-id="6c162-106">Udostępnianie składowej klasy lub struktury sprawia, że dostępne dla każdego wystąpienia zamiast *nieudostępnionych*, gdzie każde wystąpienie zachowuje własną kopię.</span><span class="sxs-lookup"><span data-stu-id="6c162-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="6c162-107">Jest to przydatne, na przykład, jeśli wartość zmiennej ma zastosowanie do całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6c162-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="6c162-108">Przy deklarowaniu zmiennej jako `Shared`, następnie wszystkie wystąpienia dostęp do tej samej lokalizacji magazynu, a jeśli jedno wystąpienie zmienia wartość zmiennej, wszystkie wystąpienia dostęp zaktualizowane wartości.</span><span class="sxs-lookup"><span data-stu-id="6c162-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="6c162-109">Udostępnianie nie zmienia poziom dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="6c162-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="6c162-110">Na przykład, członek klasy mogą być udostępniane i prywatne (dostępny tylko w obrębie klasy), lub nieudostępnionych, jak i publicznych.</span><span class="sxs-lookup"><span data-stu-id="6c162-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="6c162-111">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6c162-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6c162-112">reguły</span><span class="sxs-lookup"><span data-stu-id="6c162-112">Rules</span></span>  
  
- <span data-ttu-id="6c162-113">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="6c162-113">**Declaration Context.**</span></span> <span data-ttu-id="6c162-114">Możesz użyć `Shared` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="6c162-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="6c162-115">Oznacza to, że kontekst deklaracji `Shared` element musi być klasą lub strukturą i nie może być plikiem źródłowym, przestrzeń nazw lub procedury.</span><span class="sxs-lookup"><span data-stu-id="6c162-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
- <span data-ttu-id="6c162-116">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="6c162-116">**Combined Modifiers.**</span></span> <span data-ttu-id="6c162-117">Nie można określić `Shared` wraz z [zastępuje](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), lub [ Statyczne](../../../visual-basic/language-reference/modifiers/static.md) w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="6c162-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
- <span data-ttu-id="6c162-118">**Uzyskiwanie dostępu do.**</span><span class="sxs-lookup"><span data-stu-id="6c162-118">**Accessing.**</span></span> <span data-ttu-id="6c162-119">Możesz uzyskać dostęp udostępnionego elementu kwalifikując jego nazwą klasy lub struktury, a nie nazwę zmiennej konkretnego wystąpienia swojej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="6c162-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="6c162-120">Nawet nie trzeba utworzyć wystąpienia klasy lub struktury dostęp do jego udostępnionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6c162-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="6c162-121">Poniższy przykład wywołuje procedury udostępnianej <xref:System.Double.IsNaN%2A> udostępnianych przez <xref:System.Double> struktury.</span><span class="sxs-lookup"><span data-stu-id="6c162-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- <span data-ttu-id="6c162-122">**Niejawne udostępniania.**</span><span class="sxs-lookup"><span data-stu-id="6c162-122">**Implicit Sharing.**</span></span> <span data-ttu-id="6c162-123">Nie można użyć `Shared` modyfikator w [instrukcja Const](../../../visual-basic/language-reference/statements/const-statement.md), ale stałe są niejawnie.</span><span class="sxs-lookup"><span data-stu-id="6c162-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="6c162-124">Podobnie nie można zadeklarować członek modułem lub interfejsem `Shared`, ale niejawnie są one udostępniane.</span><span class="sxs-lookup"><span data-stu-id="6c162-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6c162-125">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="6c162-125">Behavior</span></span>  
  
- <span data-ttu-id="6c162-126">**Storage.**</span><span class="sxs-lookup"><span data-stu-id="6c162-126">**Storage.**</span></span> <span data-ttu-id="6c162-127">Udostępniona zmienna lub zdarzenia są przechowywane w pamięci tylko raz, niezależnie od tego, ile lub kilka wystąpień tworzenia swojej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="6c162-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="6c162-128">Podobnie procedury udostępnianej lub właściwość zawiera tylko jeden zestaw zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="6c162-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
- <span data-ttu-id="6c162-129">**Dostęp za pośrednictwem zmiennej wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="6c162-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="6c162-130">Użytkownik może uzyskać dostęp do udostępnionego elementu kwalifikując nazwę zmiennej, która zawiera określone wystąpienie jego klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="6c162-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="6c162-131">Mimo że to zazwyczaj działa zgodnie z oczekiwaniami, kompilator generuje komunikat ostrzegawczy i sprawia, że dostęp za pośrednictwem nazwy klasy lub struktury, zamiast zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6c162-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
- <span data-ttu-id="6c162-132">**Uzyskiwanie dostępu do przy użyciu wyrażenia wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="6c162-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="6c162-133">Jeśli uzyskujesz dostęp do udostępnionego elementu za pomocą wyrażenia, która zwraca wystąpienie jego klasy lub struktury, kompilator sprawia, że dostęp za pośrednictwem nazwy klasy lub struktury, zamiast obliczając wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6c162-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="6c162-134">Daje nieoczekiwane wyniki, jeśli Twoim zamiarem wyrażenie które ma wykonywać inne czynności, a także zwracanie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6c162-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="6c162-135">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="6c162-135">The following example illustrates this.</span></span>  
  
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
  
     <span data-ttu-id="6c162-136">W poprzednim przykładzie, kompilator generuje ostrzeżenie razem kod uzyskuje dostęp do współdzielonej zmiennej `total` za pośrednictwem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6c162-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="6c162-137">W każdym przypadku to sprawia, że dostęp bezpośrednio za pomocą klasy `shareTotal` i nie powoduje użycie dowolnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6c162-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="6c162-138">W przypadku zamierzonej wywołaniu do procedury `returnClass`, oznacza to, że nie generuje nawet po wywołaniu `returnClass`, więc dodatkowe działania wyświetlania "returnClass() funkcji o nazwie" nie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="6c162-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="6c162-139">`Shared` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="6c162-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6c162-140">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6c162-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="6c162-141">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6c162-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="6c162-142">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6c162-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="6c162-143">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6c162-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="6c162-144">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="6c162-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="6c162-145">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6c162-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6c162-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c162-146">See also</span></span>

- [<span data-ttu-id="6c162-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="6c162-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="6c162-148">Static</span><span class="sxs-lookup"><span data-stu-id="6c162-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="6c162-149">Okres istnienia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c162-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="6c162-150">Procedury</span><span class="sxs-lookup"><span data-stu-id="6c162-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="6c162-151">Struktury</span><span class="sxs-lookup"><span data-stu-id="6c162-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6c162-152">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="6c162-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
