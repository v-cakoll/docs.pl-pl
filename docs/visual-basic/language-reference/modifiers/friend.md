---
title: Friend (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 32f993e4b9bcd126ebb6d70310fc0781e8b137b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="friend-visual-basic"></a><span data-ttu-id="6012e-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6012e-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="6012e-103">Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie zestawu, który zawiera jego deklarację.</span><span class="sxs-lookup"><span data-stu-id="6012e-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6012e-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6012e-104">Remarks</span></span>  
 <span data-ttu-id="6012e-105">W wielu przypadkach ma elementów, takich jak klasy i struktury, który będzie używany przez cały zestaw nie tylko przez składnik, który je deklaruje programowania.</span><span class="sxs-lookup"><span data-stu-id="6012e-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="6012e-106">Jednak nie można ich jako dostępny przez kod poza zestaw (na przykład jeśli aplikacja jest zastrzeżone).</span><span class="sxs-lookup"><span data-stu-id="6012e-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="6012e-107">Jeśli chcesz ograniczyć dostęp do elementu w ten sposób można Zadeklaruj ją przy użyciu `Friend` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="6012e-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="6012e-108">Kod w innych klas, struktur i modułów, które są kompilowane do tego samego zestawu można uzyskać dostęp do wszystkich `Friend` elementów w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="6012e-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="6012e-109">`Friend`dostęp jest często poziomu preferowany elementom programowania aplikacji i `Friend` jest dostęp domyślny poziom interfejsu, modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="6012e-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="6012e-110">Można użyć `Friend` tylko na poziomie modułu, interfejsem lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6012e-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="6012e-111">W związku z tym kontekście deklaracji dla `Friend` elementu musi być plikiem źródłowym, przestrzeni nazw, interfejs, modułu, klasy lub struktury; nie może być procedury.</span><span class="sxs-lookup"><span data-stu-id="6012e-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  
  
 <span data-ttu-id="6012e-112">Można użyć `Friend` modyfikator w połączeniu z [chronione](../../../visual-basic/language-reference/modifiers/protected.md) modyfikator w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="6012e-112">You can use the `Friend` modifier in conjunction with the [Protected](../../../visual-basic/language-reference/modifiers/protected.md) modifier in the same declaration.</span></span> <span data-ttu-id="6012e-113">Ta kombinacja przyznaje zarówno `Friend` dostępu i chronionego dostępu na zadeklarowane elementy, dzięki czemu są one dostępne z dowolnej lokalizacji w tym samym zestawie, swojej klasy oraz klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="6012e-113">This combination confers both `Friend` access and protected access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="6012e-114">Można określić `Protected Friend` tylko w elementach członkowskich klas.</span><span class="sxs-lookup"><span data-stu-id="6012e-114">You can specify `Protected Friend` only on members of classes.</span></span>  
  
 <span data-ttu-id="6012e-115">Porównanie `Friend` i innych modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6012e-115">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6012e-116">Można określić, że inny zestaw jest przyjaznego zestawu, co umożliwia dostęp do wszystkich typów i elementów członkowskich, które są oznaczone jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="6012e-116">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="6012e-117">Aby uzyskać więcej informacji, zobacz [przyjazne zestawy](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span><span class="sxs-lookup"><span data-stu-id="6012e-117">For more information, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6012e-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="6012e-118">Example</span></span>  
 <span data-ttu-id="6012e-119">Następujące klasy używa `Friend` modyfikator zezwalająca na inne elementy programowania, w tym samym zestawie, aby dostęp do niektórych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6012e-119">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="6012e-120">Użycie</span><span class="sxs-lookup"><span data-stu-id="6012e-120">Usage</span></span>  
 <span data-ttu-id="6012e-121">Można użyć `Friend` modyfikator w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="6012e-121">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="6012e-122">Class — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="6012e-123">Const — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="6012e-124">DECLARE — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="6012e-125">Delegate — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="6012e-126">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="6012e-127">Enum — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="6012e-128">Event — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="6012e-129">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="6012e-130">Interface — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="6012e-131">Module — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="6012e-132">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-132">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="6012e-133">Structure — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-133">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="6012e-134">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6012e-134">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6012e-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6012e-135">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="6012e-136">Publiczna</span><span class="sxs-lookup"><span data-stu-id="6012e-136">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="6012e-137">Chronione</span><span class="sxs-lookup"><span data-stu-id="6012e-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="6012e-138">Prywatne</span><span class="sxs-lookup"><span data-stu-id="6012e-138">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="6012e-139">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6012e-139">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="6012e-140">Procedury</span><span class="sxs-lookup"><span data-stu-id="6012e-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="6012e-141">Struktury</span><span class="sxs-lookup"><span data-stu-id="6012e-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="6012e-142">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="6012e-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
