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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920573"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="8c03a-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c03a-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="8c03a-103">Określa, że właściwość lub procedura przesłania właściwość o identycznej nazwie lub dziedziczone z klasy bazowej procedury.</span><span class="sxs-lookup"><span data-stu-id="8c03a-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c03a-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c03a-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="8c03a-105">reguły</span><span class="sxs-lookup"><span data-stu-id="8c03a-105">Rules</span></span>  
  
-   <span data-ttu-id="8c03a-106">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="8c03a-106">**Declaration Context.**</span></span> <span data-ttu-id="8c03a-107">Możesz użyć `Overrides` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="8c03a-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="8c03a-108">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="8c03a-108">**Combined Modifiers.**</span></span> <span data-ttu-id="8c03a-109">Nie można określić `Overrides` wraz z `Shadows` lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="8c03a-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="8c03a-110">Ponieważ element nadrzędnych jest niejawnie możliwym do zastąpienia, nie można połączyć `Overridable` z `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="8c03a-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="8c03a-111">**Podpisów dopasowania.**</span><span class="sxs-lookup"><span data-stu-id="8c03a-111">**Matching Signatures.**</span></span> <span data-ttu-id="8c03a-112">Podpis tej deklaracji musi dokładnie odpowiadać *podpisu* właściwość lub procedurę, która zastępuje ona.</span><span class="sxs-lookup"><span data-stu-id="8c03a-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="8c03a-113">Oznacza to, list parametrów muszą mieć taką samą liczbę parametrów, w tej samej kolejności, z tymi samymi typami danych.</span><span class="sxs-lookup"><span data-stu-id="8c03a-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="8c03a-114">Oprócz podpisu nadrzędnych deklaracji musi również dokładnie odpowiadać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8c03a-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="8c03a-115">Poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="8c03a-115">The access level</span></span>  
  
    -   <span data-ttu-id="8c03a-116">Typ zwracany, jeśli istnieje</span><span class="sxs-lookup"><span data-stu-id="8c03a-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="8c03a-117">**Sygnatur ogólnych.**</span><span class="sxs-lookup"><span data-stu-id="8c03a-117">**Generic Signatures.**</span></span> <span data-ttu-id="8c03a-118">Procedury ogólne podpis zawiera liczbę parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="8c03a-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="8c03a-119">W związku z tym nadrzędnych deklaracja musi odpowiadać wersją klasy bazowej, w tym zakresie, a także.</span><span class="sxs-lookup"><span data-stu-id="8c03a-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="8c03a-120">**Dodatkowe dopasowywania.**</span><span class="sxs-lookup"><span data-stu-id="8c03a-120">**Additional Matching.**</span></span> <span data-ttu-id="8c03a-121">Oprócz dopasowania podpis wersją klasy bazowej, ta deklaracja musi być również zgodna go pod następującymi względami:</span><span class="sxs-lookup"><span data-stu-id="8c03a-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="8c03a-122">Modyfikator poziom dostępu (takich jak [publicznych](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="8c03a-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="8c03a-123">Przekazywanie mechanizm każdego parametru ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="8c03a-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="8c03a-124">Ograniczenie listy dla każdego parametru typu ogólnego procedury</span><span class="sxs-lookup"><span data-stu-id="8c03a-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="8c03a-125">**Przesłanianiem i zastępowaniem.**</span><span class="sxs-lookup"><span data-stu-id="8c03a-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="8c03a-126">Zarówno przesłanianiem i zastępowaniem przedefiniować dziedziczonego elementu, ale istnieją znaczne różnice między dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="8c03a-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="8c03a-127">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="8c03a-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="8c03a-128">Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` tak, aby pracować z interfejsów API biblioteki C# łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="8c03a-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="8c03a-129">`Overrides` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="8c03a-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="8c03a-130">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c03a-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="8c03a-131">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="8c03a-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="8c03a-132">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c03a-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8c03a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c03a-133">See also</span></span>

- [<span data-ttu-id="8c03a-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="8c03a-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="8c03a-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="8c03a-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="8c03a-136">Overridable</span><span class="sxs-lookup"><span data-stu-id="8c03a-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="8c03a-137">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8c03a-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="8c03a-138">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c03a-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="8c03a-139">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c03a-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="8c03a-140">Lista typów</span><span class="sxs-lookup"><span data-stu-id="8c03a-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
