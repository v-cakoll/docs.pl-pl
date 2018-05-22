---
title: Friend (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: d906fc8ada19f22059da44acbd76dd07dacd4801
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="friend-visual-basic"></a><span data-ttu-id="1ce24-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ce24-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="1ce24-103">Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie zestawu, który zawiera jego deklarację.</span><span class="sxs-lookup"><span data-stu-id="1ce24-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ce24-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ce24-104">Remarks</span></span>  
 <span data-ttu-id="1ce24-105">W wielu przypadkach ma elementów, takich jak klasy i struktury, który będzie używany przez cały zestaw nie tylko przez składnik, który je deklaruje programowania.</span><span class="sxs-lookup"><span data-stu-id="1ce24-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="1ce24-106">Jednak nie można ich jako dostępny przez kod poza zestaw (na przykład jeśli aplikacja jest zastrzeżone).</span><span class="sxs-lookup"><span data-stu-id="1ce24-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="1ce24-107">Jeśli chcesz ograniczyć dostęp do elementu w ten sposób można Zadeklaruj ją przy użyciu `Friend` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="1ce24-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="1ce24-108">Kod w innych klas, struktur i modułów, które są kompilowane do tego samego zestawu można uzyskać dostęp do wszystkich `Friend` elementów w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="1ce24-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="1ce24-109">`Friend` dostęp jest często poziomu preferowany elementom programowania aplikacji i `Friend` jest dostęp domyślny poziom interfejsu, modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="1ce24-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="1ce24-110">Można użyć `Friend` tylko na poziomie modułu, interfejsem lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1ce24-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="1ce24-111">W związku z tym kontekście deklaracji dla `Friend` elementu musi być plikiem źródłowym, przestrzeni nazw, interfejs, modułu, klasy lub struktury; nie może być procedury.</span><span class="sxs-lookup"><span data-stu-id="1ce24-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="1ce24-112">Można również użyć [Protected Friend](protected-friend.md) modyfikator dostępu, co sprawia, że element członkowski klasy jest dostępny w obrębie klasy, z klasy pochodnej i z tego samego zestawu, w którym klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="1ce24-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="1ce24-113">Aby ograniczyć dostęp do elementu członkowskiego z w swojej klasie i klasach pochodnych w tym samym zestawie, należy użyć [prywatne chronione](private-protected.md) modyfikator dostępu.</span><span class="sxs-lookup"><span data-stu-id="1ce24-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="1ce24-114">Porównanie `Friend` i innych modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1ce24-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ce24-115">Można określić, że inny zestaw jest przyjaznego zestawu, co umożliwia dostęp do wszystkich typów i elementów członkowskich, które są oznaczone jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="1ce24-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="1ce24-116">Aby uzyskać więcej informacji, zobacz [przyjazne zestawy](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="1ce24-116">For more information, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ce24-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ce24-117">Example</span></span>  
 <span data-ttu-id="1ce24-118">Następujące klasy używa `Friend` modyfikator zezwalająca na inne elementy programowania, w tym samym zestawie, aby dostęp do niektórych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="1ce24-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="1ce24-119">Użycie</span><span class="sxs-lookup"><span data-stu-id="1ce24-119">Usage</span></span>  
 <span data-ttu-id="1ce24-120">Można użyć `Friend` modyfikator w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="1ce24-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="1ce24-121">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="1ce24-122">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="1ce24-123">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="1ce24-124">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="1ce24-125">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="1ce24-126">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="1ce24-127">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="1ce24-128">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="1ce24-129">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="1ce24-130">Module, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="1ce24-131">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="1ce24-132">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="1ce24-133">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ce24-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1ce24-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ce24-134">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="1ce24-135">Public</span><span class="sxs-lookup"><span data-stu-id="1ce24-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="1ce24-136">Protected</span><span class="sxs-lookup"><span data-stu-id="1ce24-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="1ce24-137">Private</span><span class="sxs-lookup"><span data-stu-id="1ce24-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="1ce24-138">[Prywatne chronione](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="1ce24-138">[Private Protected](./private-protected.md) </span></span>  
 <span data-ttu-id="1ce24-139">[Friend chronionych](./protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="1ce24-139">[Protected Friend](./protected-friend.md) </span></span>  
 [<span data-ttu-id="1ce24-140">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ce24-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="1ce24-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ce24-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="1ce24-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="1ce24-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="1ce24-143">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="1ce24-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
