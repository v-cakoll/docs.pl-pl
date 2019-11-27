---
title: Overrides
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
ms.openlocfilehash: 04f1cb27d6a8366c2dd13f8fdc1d975d382f1cfd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351386"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="5972e-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5972e-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="5972e-103">Określa, że właściwość lub procedura przesłania właściwość lub procedurę, która jest dziedziczona z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="5972e-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="5972e-104">Reguły</span><span class="sxs-lookup"><span data-stu-id="5972e-104">Rules</span></span>

- <span data-ttu-id="5972e-105">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="5972e-105">**Declaration Context.**</span></span> <span data-ttu-id="5972e-106">`Overrides` można użyć tylko w instrukcji deklaracji właściwości lub procedury.</span><span class="sxs-lookup"><span data-stu-id="5972e-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="5972e-107">**Połączone modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="5972e-107">**Combined Modifiers.**</span></span> <span data-ttu-id="5972e-108">Nie można określić `Overrides` razem z `Shadows` lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="5972e-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="5972e-109">Ponieważ przesłaniający element jest niejawnie możliwy do zastąpienia, nie można połączyć `Overridable` z `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="5972e-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="5972e-110">**Pasujące podpisy.**</span><span class="sxs-lookup"><span data-stu-id="5972e-110">**Matching Signatures.**</span></span> <span data-ttu-id="5972e-111">Podpis tej deklaracji musi być dokładnie zgodny z *podpisem* właściwości lub procedury, która zastąpi.</span><span class="sxs-lookup"><span data-stu-id="5972e-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="5972e-112">Oznacza to, że listy parametrów muszą mieć taką samą liczbę parametrów, w tej samej kolejności, przy użyciu tych samych typów danych.</span><span class="sxs-lookup"><span data-stu-id="5972e-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="5972e-113">Oprócz podpisu, deklaracja zastępująca musi być dokładnie zgodna z następującymi:</span><span class="sxs-lookup"><span data-stu-id="5972e-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="5972e-114">Poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="5972e-114">The access level</span></span>

  - <span data-ttu-id="5972e-115">Zwracany typ, jeśli istnieje</span><span class="sxs-lookup"><span data-stu-id="5972e-115">The return type, if any</span></span>

- <span data-ttu-id="5972e-116">**Podpisy ogólne.**</span><span class="sxs-lookup"><span data-stu-id="5972e-116">**Generic Signatures.**</span></span> <span data-ttu-id="5972e-117">W przypadku procedury ogólnej podpis obejmuje liczbę parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="5972e-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="5972e-118">W związku z tym, deklaracja zastępująca musi być zgodna z wersją klasy bazowej w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="5972e-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="5972e-119">**Dodatkowe dopasowanie.**</span><span class="sxs-lookup"><span data-stu-id="5972e-119">**Additional Matching.**</span></span> <span data-ttu-id="5972e-120">Oprócz dopasowania sygnatury wersji klasy bazowej, ta deklaracja musi również być zgodna z następującymi kwestiami:</span><span class="sxs-lookup"><span data-stu-id="5972e-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="5972e-121">Modyfikator poziomu dostępu (na przykład [publiczny](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="5972e-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>

  - <span data-ttu-id="5972e-122">Mechanizm przekazywania każdego parametru ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="5972e-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>

  - <span data-ttu-id="5972e-123">Listy ograniczeń dla każdego parametru typu procedury ogólnej</span><span class="sxs-lookup"><span data-stu-id="5972e-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="5972e-124">**Przesłanianie i zastępowanie.**</span><span class="sxs-lookup"><span data-stu-id="5972e-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="5972e-125">Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami.</span><span class="sxs-lookup"><span data-stu-id="5972e-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="5972e-126">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="5972e-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="5972e-127">Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` tak, aby interfejsy API biblioteki działały C# łatwiej.</span><span class="sxs-lookup"><span data-stu-id="5972e-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="5972e-128">Modyfikator `Overrides` może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="5972e-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="5972e-129">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5972e-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="5972e-130">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5972e-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="5972e-131">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5972e-131">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="5972e-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5972e-132">See also</span></span>

- [<span data-ttu-id="5972e-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="5972e-133">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="5972e-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="5972e-134">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="5972e-135">Overridable</span><span class="sxs-lookup"><span data-stu-id="5972e-135">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="5972e-136">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="5972e-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="5972e-137">Obserwowanie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5972e-137">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="5972e-138">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5972e-138">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="5972e-139">Lista typów</span><span class="sxs-lookup"><span data-stu-id="5972e-139">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
