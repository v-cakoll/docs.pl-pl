---
title: Promocja typu (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ddb0d61f0f1c94e8e28493d0c62afe1e09503804
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="4287f-102">Promocja typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4287f-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="4287f-103">Deklaracja elementu programistycznego w module języka Visual Basic zamienia jego zakresu przestrzeni nazw zawierającej modułu.</span><span class="sxs-lookup"><span data-stu-id="4287f-103">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="4287f-104">Jest to nazywane *wpisz podwyższania poziomu*.</span><span class="sxs-lookup"><span data-stu-id="4287f-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="4287f-105">W poniższym przykładzie przedstawiono definicję szkielet modułu i dwa elementy członkowskie tego modułu.</span><span class="sxs-lookup"><span data-stu-id="4287f-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 <span data-ttu-id="4287f-106">W ramach `projModule`, programowania elementy zadeklarowane na poziomie modułu awansowane na `projNamespace`.</span><span class="sxs-lookup"><span data-stu-id="4287f-106">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="4287f-107">W powyższym przykładzie `basicEnum` i `innerClass` awansowane, ale `numberSub` jest, ponieważ nie jest zadeklarowany na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="4287f-107">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="4287f-108">Efekt promocja typu</span><span class="sxs-lookup"><span data-stu-id="4287f-108">Effect of Type Promotion</span></span>  
 <span data-ttu-id="4287f-109">Promocja typu powoduje ciąg kwalifikacji nie musi zawierać nazwę modułu.</span><span class="sxs-lookup"><span data-stu-id="4287f-109">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="4287f-110">Poniższy przykład powoduje, że dwa wywołania do procedury w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4287f-110">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 <span data-ttu-id="4287f-111">W powyższym przykładzie pierwsze wywołanie używa ciągów pełnej kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="4287f-111">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="4287f-112">Jednak nie jest to konieczne ze względu na typ podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="4287f-112">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="4287f-113">Drugi wywołać również uzyskuje dostęp do elementów członkowskich modułu bez uwzględniania `projModule` w ciągach kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="4287f-113">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="4287f-114">Sprawność promocja typu</span><span class="sxs-lookup"><span data-stu-id="4287f-114">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="4287f-115">Jeśli przestrzeń nazw ma już element członkowski o takiej samej nazwie jako członek modułu, typu promocji jest bezcelowe dla tego elementu członkowskiego modułu.</span><span class="sxs-lookup"><span data-stu-id="4287f-115">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="4287f-116">Poniższy przykład przedstawia definicję szkielet wyliczenie i modułu w ramach tego samego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="4287f-116">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 <span data-ttu-id="4287f-117">W powyższym przykładzie Visual Basic nie można podwyższyć poziomu klasy `abc` do `thisNameSpace` , ponieważ istnieje już wyliczenie o tej samej nazwie na poziomie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4287f-117">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="4287f-118">Aby uzyskać dostęp do `abcSub`, należy użyć ciągu pełnej kwalifikacji `thisNamespace.thisModule.abc.abcSub`.</span><span class="sxs-lookup"><span data-stu-id="4287f-118">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="4287f-119">Jednak klasy `xyz` nadal jest podwyższany, uzyskasz dostęp do `xyzSub` z krótszego ciągu kwalifikacji `thisNamespace.xyz.xyzSub`.</span><span class="sxs-lookup"><span data-stu-id="4287f-119">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="4287f-120">Sprawność promocja typu dla typów częściowych</span><span class="sxs-lookup"><span data-stu-id="4287f-120">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="4287f-121">Jeśli korzysta z klasy lub struktury wewnątrz modułu [częściowe](../../../../visual-basic/language-reference/modifiers/partial.md) — słowo kluczowe, promocja typu jest automatycznie bezcelowe dla tej klasy lub struktury, czy przestrzeń nazw ma element członkowski o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4287f-121">If a class or structure inside a module uses the [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="4287f-122">Inne elementy w module nadal kwalifikują się do typu podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="4287f-122">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="4287f-123">**Skutki.**</span><span class="sxs-lookup"><span data-stu-id="4287f-123">**Consequences.**</span></span> <span data-ttu-id="4287f-124">Sprawność promocja typu z częściowa definicja może spowodować nieoczekiwane wyniki, a nawet błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="4287f-124">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="4287f-125">W poniższym przykładzie przedstawiono szkielet definicji częściowej klasy, z których jeden jest wewnątrz modułu.</span><span class="sxs-lookup"><span data-stu-id="4287f-125">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 <span data-ttu-id="4287f-126">W poprzednim przykładzie, deweloper może spodziewać się kompilatora można scalić dwóch definicji częściowej `sampleClass`.</span><span class="sxs-lookup"><span data-stu-id="4287f-126">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="4287f-127">Jednak kompilator nie należy wziąć pod uwagę podwyższania poziomu dla definicji częściowej wewnątrz `sampleModule`.</span><span class="sxs-lookup"><span data-stu-id="4287f-127">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="4287f-128">W związku z tym próbuje skompilować dwóch oddzielnych klas, o nazwie `sampleClass` , ale z inną kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4287f-128">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="4287f-129">Kompilator scala definicji częściowej tylko wtedy, gdy ich w pełni kwalifikowanej ścieżki są identyczne.</span><span class="sxs-lookup"><span data-stu-id="4287f-129">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="4287f-130">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="4287f-130">Recommendations</span></span>  
 <span data-ttu-id="4287f-131">Poniższe zalecenia reprezentują dobrym rozwiązaniem programowania.</span><span class="sxs-lookup"><span data-stu-id="4287f-131">The following recommendations represent good programming practice.</span></span>  
  
-   <span data-ttu-id="4287f-132">**Unikatowe nazwy.**</span><span class="sxs-lookup"><span data-stu-id="4287f-132">**Unique Names.**</span></span> <span data-ttu-id="4287f-133">Jeśli masz pełną kontrolę nad nazw elementów programowania zawsze jest warto użyć wszędzie unikatowe nazwy.</span><span class="sxs-lookup"><span data-stu-id="4287f-133">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="4287f-134">Identycznych nazw wymagają dodatkowe wymagania i wprowadzić kod trudniejsze do odczytu.</span><span class="sxs-lookup"><span data-stu-id="4287f-134">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="4287f-135">Również może prowadzić do powstawania błędów i nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="4287f-135">They can also lead to subtle errors and unexpected results.</span></span>  
  
-   <span data-ttu-id="4287f-136">**Pełnej kwalifikacji.**</span><span class="sxs-lookup"><span data-stu-id="4287f-136">**Full Qualification.**</span></span> <span data-ttu-id="4287f-137">Podczas pracy z modułów i inne elementy w tej samej przestrzeni nazw najbezpieczniejszym rozwiązaniem jest zawsze użycie pełnej kwalifikacji dla wszystkich elementów programowania.</span><span class="sxs-lookup"><span data-stu-id="4287f-137">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="4287f-138">Promocja typu jest bezcelowe dla elementu członkowskiego moduł, możesz nie pełni kwalifikuje się ten element członkowski może przypadkowo uzyskać dostępu do innego elementu programowania.</span><span class="sxs-lookup"><span data-stu-id="4287f-138">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4287f-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4287f-139">See Also</span></span>  
 [<span data-ttu-id="4287f-140">Module, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4287f-140">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="4287f-141">Namespace, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4287f-141">Namespace Statement</span></span>](../../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="4287f-142">Partial</span><span class="sxs-lookup"><span data-stu-id="4287f-142">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="4287f-143">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4287f-143">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="4287f-144">Instrukcje: kontrolowanie zakresu zmiennej</span><span class="sxs-lookup"><span data-stu-id="4287f-144">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [<span data-ttu-id="4287f-145">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="4287f-145">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
