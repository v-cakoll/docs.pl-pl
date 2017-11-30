---
title: Overrides (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1bee6a6235b87a7e20f087a73bef76e0fc7bf124
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="f09a1-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f09a1-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="f09a1-103">Określa, że właściwość lub procedura przesłania o identycznej nazwie właściwość lub procedura dziedziczona z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="f09a1-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f09a1-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f09a1-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f09a1-105">Reguły</span><span class="sxs-lookup"><span data-stu-id="f09a1-105">Rules</span></span>  
  
-   <span data-ttu-id="f09a1-106">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="f09a1-106">**Declaration Context.**</span></span> <span data-ttu-id="f09a1-107">Można użyć `Overrides` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="f09a1-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="f09a1-108">**Łączna modyfikatorów.**</span><span class="sxs-lookup"><span data-stu-id="f09a1-108">**Combined Modifiers.**</span></span> <span data-ttu-id="f09a1-109">Nie można określić `Overrides` razem z `Shadows` lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="f09a1-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="f09a1-110">Zastępowanie elementu jest niejawnie możliwym do zastąpienia, nie można łączyć `Overridable` z `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="f09a1-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="f09a1-111">**Dopasowywanie podpisów.**</span><span class="sxs-lookup"><span data-stu-id="f09a1-111">**Matching Signatures.**</span></span> <span data-ttu-id="f09a1-112">Podpis tej deklaracji musi dokładnie odpowiadać *podpisu* właściwości lub procedury, która zastępuje on.</span><span class="sxs-lookup"><span data-stu-id="f09a1-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="f09a1-113">Oznacza to, listy parametrów muszą mieć taką samą liczbę parametrów, w takiej samej kolejności, z tymi samymi typami danych.</span><span class="sxs-lookup"><span data-stu-id="f09a1-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="f09a1-114">Oprócz podpisu Zastępowanie deklaracji musi również dokładnie odpowiadać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f09a1-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="f09a1-115">Poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="f09a1-115">The access level</span></span>  
  
    -   <span data-ttu-id="f09a1-116">Typ zwracany, jeśli istnieje</span><span class="sxs-lookup"><span data-stu-id="f09a1-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="f09a1-117">**Ogólny podpisów.**</span><span class="sxs-lookup"><span data-stu-id="f09a1-117">**Generic Signatures.**</span></span> <span data-ttu-id="f09a1-118">Procedury ogólne podpis zawiera liczbę parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="f09a1-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="f09a1-119">W związku z tym zastępowanie deklaracja musi odpowiadać wersji klasy podstawowej w tym zakresie, a także.</span><span class="sxs-lookup"><span data-stu-id="f09a1-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="f09a1-120">**Dodatkowe dopasowania.**</span><span class="sxs-lookup"><span data-stu-id="f09a1-120">**Additional Matching.**</span></span> <span data-ttu-id="f09a1-121">Oprócz dopasowania podpis wersji klasę podstawową, ta deklaracja musi być również zgodna go w następujących aspektach:</span><span class="sxs-lookup"><span data-stu-id="f09a1-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="f09a1-122">Modyfikator dostępu na poziomie (takich jak [publicznego](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="f09a1-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="f09a1-123">Przekazywanie mechanizmem poszczególnych parametrów ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="f09a1-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="f09a1-124">Ograniczenie listy dla każdego parametru typu ogólnego procedury</span><span class="sxs-lookup"><span data-stu-id="f09a1-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="f09a1-125">**Przesłanianiem i zastępowaniem.**</span><span class="sxs-lookup"><span data-stu-id="f09a1-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="f09a1-126">Zarówno przesłanianiem i zastępowaniem ponownego zdefiniowania odziedziczonego elementu, ale są istotne różnice między dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="f09a1-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="f09a1-127">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="f09a1-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="f09a1-128">Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` , aby pracować z C# łatwiej biblioteki interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="f09a1-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="f09a1-129">`Overrides` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="f09a1-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f09a1-130">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f09a1-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="f09a1-131">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f09a1-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="f09a1-132">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f09a1-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f09a1-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f09a1-133">See Also</span></span>  
 [<span data-ttu-id="f09a1-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="f09a1-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="f09a1-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="f09a1-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="f09a1-136">Możliwym do zastąpienia</span><span class="sxs-lookup"><span data-stu-id="f09a1-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="f09a1-137">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f09a1-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="f09a1-138">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f09a1-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="f09a1-139">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f09a1-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="f09a1-140">Lista typów</span><span class="sxs-lookup"><span data-stu-id="f09a1-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
