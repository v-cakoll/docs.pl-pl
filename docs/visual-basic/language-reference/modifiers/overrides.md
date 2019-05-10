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
ms.openlocfilehash: 7fff91d993743574d13030aa3d5cc1e462e76838
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751029"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="fe81b-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe81b-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="fe81b-103">Określa, że właściwość lub procedura przesłania właściwość o identycznej nazwie lub dziedziczone z klasy bazowej procedury.</span><span class="sxs-lookup"><span data-stu-id="fe81b-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="fe81b-104">reguły</span><span class="sxs-lookup"><span data-stu-id="fe81b-104">Rules</span></span>

- <span data-ttu-id="fe81b-105">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="fe81b-105">**Declaration Context.**</span></span> <span data-ttu-id="fe81b-106">Możesz użyć `Overrides` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="fe81b-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="fe81b-107">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="fe81b-107">**Combined Modifiers.**</span></span> <span data-ttu-id="fe81b-108">Nie można określić `Overrides` wraz z `Shadows` lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="fe81b-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="fe81b-109">Ponieważ element nadrzędnych jest niejawnie możliwym do zastąpienia, nie można połączyć `Overridable` z `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="fe81b-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="fe81b-110">**Podpisów dopasowania.**</span><span class="sxs-lookup"><span data-stu-id="fe81b-110">**Matching Signatures.**</span></span> <span data-ttu-id="fe81b-111">Podpis tej deklaracji musi dokładnie odpowiadać *podpisu* właściwość lub procedurę, która zastępuje ona.</span><span class="sxs-lookup"><span data-stu-id="fe81b-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="fe81b-112">Oznacza to, list parametrów muszą mieć taką samą liczbę parametrów, w tej samej kolejności, z tymi samymi typami danych.</span><span class="sxs-lookup"><span data-stu-id="fe81b-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="fe81b-113">Oprócz podpisu nadrzędnych deklaracji musi również dokładnie odpowiadać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fe81b-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="fe81b-114">Poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="fe81b-114">The access level</span></span>

  - <span data-ttu-id="fe81b-115">Typ zwracany, jeśli istnieje</span><span class="sxs-lookup"><span data-stu-id="fe81b-115">The return type, if any</span></span>

- <span data-ttu-id="fe81b-116">**Sygnatur ogólnych.**</span><span class="sxs-lookup"><span data-stu-id="fe81b-116">**Generic Signatures.**</span></span> <span data-ttu-id="fe81b-117">Procedury ogólne podpis zawiera liczbę parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="fe81b-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="fe81b-118">W związku z tym nadrzędnych deklaracja musi odpowiadać wersją klasy bazowej, w tym zakresie, a także.</span><span class="sxs-lookup"><span data-stu-id="fe81b-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="fe81b-119">**Dodatkowe dopasowywania.**</span><span class="sxs-lookup"><span data-stu-id="fe81b-119">**Additional Matching.**</span></span> <span data-ttu-id="fe81b-120">Oprócz dopasowania podpis wersją klasy bazowej, ta deklaracja musi być również zgodna go pod następującymi względami:</span><span class="sxs-lookup"><span data-stu-id="fe81b-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="fe81b-121">Modyfikator poziom dostępu (takich jak [publicznych](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="fe81b-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>

  - <span data-ttu-id="fe81b-122">Przekazywanie mechanizm każdego parametru ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="fe81b-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>

  - <span data-ttu-id="fe81b-123">Ograniczenie listy dla każdego parametru typu ogólnego procedury</span><span class="sxs-lookup"><span data-stu-id="fe81b-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="fe81b-124">**Przesłanianiem i zastępowaniem.**</span><span class="sxs-lookup"><span data-stu-id="fe81b-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="fe81b-125">Zarówno przesłanianiem i zastępowaniem przedefiniować dziedziczonego elementu, ale istnieją znaczne różnice między dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="fe81b-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="fe81b-126">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="fe81b-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="fe81b-127">Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` tak, aby pracować z interfejsów API biblioteki C# łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="fe81b-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="fe81b-128">`Overrides` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="fe81b-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="fe81b-129">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="fe81b-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="fe81b-130">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="fe81b-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="fe81b-131">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="fe81b-131">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="fe81b-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe81b-132">See also</span></span>

- [<span data-ttu-id="fe81b-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="fe81b-133">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="fe81b-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="fe81b-134">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="fe81b-135">Overridable</span><span class="sxs-lookup"><span data-stu-id="fe81b-135">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="fe81b-136">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="fe81b-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="fe81b-137">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe81b-137">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="fe81b-138">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe81b-138">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="fe81b-139">Lista typów</span><span class="sxs-lookup"><span data-stu-id="fe81b-139">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
