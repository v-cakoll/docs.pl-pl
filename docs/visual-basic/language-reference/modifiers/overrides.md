---
title: Przesłonięcia
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
ms.openlocfilehash: 657f838b2959a5b6a7cef5ff18295a4ada709e9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392031"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="ccc5e-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccc5e-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="ccc5e-103">Określa, że właściwość lub procedura przesłania właściwość lub procedurę, która jest dziedziczona z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="ccc5e-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="ccc5e-104">Reguły</span><span class="sxs-lookup"><span data-stu-id="ccc5e-104">Rules</span></span>

- <span data-ttu-id="ccc5e-105">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="ccc5e-105">**Declaration Context.**</span></span> <span data-ttu-id="ccc5e-106">Można użyć `Overrides` tylko w instrukcji deklaracji właściwości lub procedury.</span><span class="sxs-lookup"><span data-stu-id="ccc5e-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="ccc5e-107">**Połączone modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="ccc5e-107">**Combined Modifiers.**</span></span> <span data-ttu-id="ccc5e-108">Nie można określić `Overrides` razem z `Shadows` lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ccc5e-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="ccc5e-109">Ponieważ przesłaniający element jest niejawnie możliwy do zastąpienia, nie można połączyć `Overridable` się z `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="ccc5e-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="ccc5e-110">**Pasujące podpisy.**</span><span class="sxs-lookup"><span data-stu-id="ccc5e-110">**Matching Signatures.**</span></span> <span data-ttu-id="ccc5e-111">Podpis tej deklaracji musi być dokładnie zgodny z *podpisem* właściwości lub procedury, która zastąpi.</span><span class="sxs-lookup"><span data-stu-id="ccc5e-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="ccc5e-112">Oznacza to, że listy parametrów muszą mieć taką samą liczbę parametrów, w tej samej kolejności, przy użyciu tych samych typów danych.</span><span class="sxs-lookup"><span data-stu-id="ccc5e-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="ccc5e-113">Oprócz podpisu, deklaracja zastępująca musi być dokładnie zgodna z następującymi:</span><span class="sxs-lookup"><span data-stu-id="ccc5e-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="ccc5e-114">Poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="ccc5e-114">The access level</span></span>

  - <span data-ttu-id="ccc5e-115">Zwracany typ, jeśli istnieje</span><span class="sxs-lookup"><span data-stu-id="ccc5e-115">The return type, if any</span></span>

- <span data-ttu-id="ccc5e-116">**Podpisy ogólne.**</span><span class="sxs-lookup"><span data-stu-id="ccc5e-116">**Generic Signatures.**</span></span> <span data-ttu-id="ccc5e-117">W przypadku procedury ogólnej podpis obejmuje liczbę parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="ccc5e-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="ccc5e-118">W związku z tym, deklaracja zastępująca musi być zgodna z wersją klasy bazowej w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ccc5e-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="ccc5e-119">**Dodatkowe dopasowanie.**</span><span class="sxs-lookup"><span data-stu-id="ccc5e-119">**Additional Matching.**</span></span> <span data-ttu-id="ccc5e-120">Oprócz dopasowania sygnatury wersji klasy bazowej, ta deklaracja musi również być zgodna z następującymi kwestiami:</span><span class="sxs-lookup"><span data-stu-id="ccc5e-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="ccc5e-121">Modyfikator poziomu dostępu (na przykład [publiczny](public.md))</span><span class="sxs-lookup"><span data-stu-id="ccc5e-121">Access-level modifier (such as [Public](public.md))</span></span>

  - <span data-ttu-id="ccc5e-122">Mechanizm przekazywania każdego parametru ([ByVal](byval.md) lub [ByRef](byref.md))</span><span class="sxs-lookup"><span data-stu-id="ccc5e-122">Passing mechanism of each parameter ([ByVal](byval.md) or [ByRef](byref.md))</span></span>

  - <span data-ttu-id="ccc5e-123">Listy ograniczeń dla każdego parametru typu procedury ogólnej</span><span class="sxs-lookup"><span data-stu-id="ccc5e-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="ccc5e-124">**Przesłanianie i zastępowanie.**</span><span class="sxs-lookup"><span data-stu-id="ccc5e-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="ccc5e-125">Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami.</span><span class="sxs-lookup"><span data-stu-id="ccc5e-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="ccc5e-126">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="ccc5e-126">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="ccc5e-127">W przypadku korzystania `Overrides` z programu kompilator niejawnie dodaje w `Overloads` taki sposób, aby interfejsy API biblioteki działały w łatwiejszy sposób.</span><span class="sxs-lookup"><span data-stu-id="ccc5e-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="ccc5e-128">`Overrides`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="ccc5e-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="ccc5e-129">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ccc5e-129">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="ccc5e-130">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="ccc5e-130">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="ccc5e-131">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ccc5e-131">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="ccc5e-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccc5e-132">See also</span></span>

- [<span data-ttu-id="ccc5e-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="ccc5e-133">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="ccc5e-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="ccc5e-134">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="ccc5e-135">Overridable</span><span class="sxs-lookup"><span data-stu-id="ccc5e-135">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="ccc5e-136">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ccc5e-136">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="ccc5e-137">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ccc5e-137">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="ccc5e-138">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ccc5e-138">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="ccc5e-139">Lista typów</span><span class="sxs-lookup"><span data-stu-id="ccc5e-139">Type List</span></span>](../statements/type-list.md)
