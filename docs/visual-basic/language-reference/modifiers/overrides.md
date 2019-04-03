---
title: Overrides (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 9eb19bf5e89b12a32cae28b2c087570acc10f3ad
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826590"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="6e784-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e784-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="6e784-103">Określa, że właściwość lub procedura przesłania właściwość o identycznej nazwie lub dziedziczone z klasy bazowej procedury.</span><span class="sxs-lookup"><span data-stu-id="6e784-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e784-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e784-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6e784-105">reguły</span><span class="sxs-lookup"><span data-stu-id="6e784-105">Rules</span></span>  
  
-   <span data-ttu-id="6e784-106">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="6e784-106">**Declaration Context.**</span></span> <span data-ttu-id="6e784-107">Możesz użyć `Overrides` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="6e784-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="6e784-108">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="6e784-108">**Combined Modifiers.**</span></span> <span data-ttu-id="6e784-109">Nie można określić `Overrides` wraz z `Shadows` lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="6e784-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="6e784-110">Ponieważ element nadrzędnych jest niejawnie możliwym do zastąpienia, nie można połączyć `Overridable` z `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="6e784-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="6e784-111">**Podpisów dopasowania.**</span><span class="sxs-lookup"><span data-stu-id="6e784-111">**Matching Signatures.**</span></span> <span data-ttu-id="6e784-112">Podpis tej deklaracji musi dokładnie odpowiadać *podpisu* właściwość lub procedurę, która zastępuje ona.</span><span class="sxs-lookup"><span data-stu-id="6e784-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="6e784-113">Oznacza to, list parametrów muszą mieć taką samą liczbę parametrów, w tej samej kolejności, z tymi samymi typami danych.</span><span class="sxs-lookup"><span data-stu-id="6e784-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="6e784-114">Oprócz podpisu nadrzędnych deklaracji musi również dokładnie odpowiadać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6e784-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="6e784-115">Poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="6e784-115">The access level</span></span>  
  
    -   <span data-ttu-id="6e784-116">Typ zwracany, jeśli istnieje</span><span class="sxs-lookup"><span data-stu-id="6e784-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="6e784-117">**Sygnatur ogólnych.**</span><span class="sxs-lookup"><span data-stu-id="6e784-117">**Generic Signatures.**</span></span> <span data-ttu-id="6e784-118">Procedury ogólne podpis zawiera liczbę parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="6e784-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="6e784-119">W związku z tym nadrzędnych deklaracja musi odpowiadać wersją klasy bazowej, w tym zakresie, a także.</span><span class="sxs-lookup"><span data-stu-id="6e784-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="6e784-120">**Dodatkowe dopasowywania.**</span><span class="sxs-lookup"><span data-stu-id="6e784-120">**Additional Matching.**</span></span> <span data-ttu-id="6e784-121">Oprócz dopasowania podpis wersją klasy bazowej, ta deklaracja musi być również zgodna go pod następującymi względami:</span><span class="sxs-lookup"><span data-stu-id="6e784-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="6e784-122">Modyfikator poziom dostępu (takich jak [publicznych](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="6e784-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="6e784-123">Przekazywanie mechanizm każdego parametru ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="6e784-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="6e784-124">Ograniczenie listy dla każdego parametru typu ogólnego procedury</span><span class="sxs-lookup"><span data-stu-id="6e784-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="6e784-125">**Przesłanianiem i zastępowaniem.**</span><span class="sxs-lookup"><span data-stu-id="6e784-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="6e784-126">Zarówno przesłanianiem i zastępowaniem przedefiniować dziedziczonego elementu, ale istnieją znaczne różnice między dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="6e784-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="6e784-127">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="6e784-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="6e784-128">Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` tak, aby pracować z interfejsów API biblioteki C# łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="6e784-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="6e784-129">`Overrides` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="6e784-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6e784-130">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6e784-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="6e784-131">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="6e784-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="6e784-132">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6e784-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6e784-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e784-133">See also</span></span>

- [<span data-ttu-id="6e784-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="6e784-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="6e784-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="6e784-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="6e784-136">Overridable</span><span class="sxs-lookup"><span data-stu-id="6e784-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="6e784-137">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="6e784-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="6e784-138">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e784-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="6e784-139">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e784-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="6e784-140">Lista typów</span><span class="sxs-lookup"><span data-stu-id="6e784-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
