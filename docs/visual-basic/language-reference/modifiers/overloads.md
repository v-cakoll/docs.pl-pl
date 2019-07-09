---
title: Overloads (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: 838207fe3ac5b8f57d030617546b9b7fa25dc939
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663540"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="3b184-102">Overloads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b184-102">Overloads (Visual Basic)</span></span>

<span data-ttu-id="3b184-103">Określa, że właściwość lub procedura redeclares istniejących właściwości lub procedur o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3b184-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>

## <a name="remarks"></a><span data-ttu-id="3b184-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b184-104">Remarks</span></span>

<span data-ttu-id="3b184-105">*Przeciążanie* w praktyce podawania więcej niż jedną definicję dla danej nazwy właściwość lub procedura w tym samym zakresie.</span><span class="sxs-lookup"><span data-stu-id="3b184-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="3b184-106">Redeclaring właściwość lub procedura z innym podpisem jest czasami nazywane *ukrywanie poprzez podpis*.</span><span class="sxs-lookup"><span data-stu-id="3b184-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>

## <a name="rules"></a><span data-ttu-id="3b184-107">reguły</span><span class="sxs-lookup"><span data-stu-id="3b184-107">Rules</span></span>

- <span data-ttu-id="3b184-108">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="3b184-108">**Declaration Context.**</span></span> <span data-ttu-id="3b184-109">Możesz użyć `Overloads` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="3b184-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="3b184-110">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="3b184-110">**Combined Modifiers.**</span></span> <span data-ttu-id="3b184-111">Nie można określić `Overloads` wraz z [cieni](../../../visual-basic/language-reference/modifiers/shadows.md) w tej samej deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="3b184-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>

- <span data-ttu-id="3b184-112">**Wymagane różnice.**</span><span class="sxs-lookup"><span data-stu-id="3b184-112">**Required Differences.**</span></span> <span data-ttu-id="3b184-113">*Podpisu* w tej deklaracji musi się różnić od podpisu co właściwość lub procedura, która przeciąża.</span><span class="sxs-lookup"><span data-stu-id="3b184-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="3b184-114">Podpis składa się nazwa właściwość lub procedura wraz z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="3b184-114">The signature comprises the property or procedure name together with the following:</span></span>

  - <span data-ttu-id="3b184-115">Liczba parametrów</span><span class="sxs-lookup"><span data-stu-id="3b184-115">the number of parameters</span></span>

  - <span data-ttu-id="3b184-116">kolejność parametrów</span><span class="sxs-lookup"><span data-stu-id="3b184-116">the order of the parameters</span></span>

  - <span data-ttu-id="3b184-117">typy danych parametrów</span><span class="sxs-lookup"><span data-stu-id="3b184-117">the data types of the parameters</span></span>

  - <span data-ttu-id="3b184-118">Liczba parametrów typu (w przypadku ogólnych procedura)</span><span class="sxs-lookup"><span data-stu-id="3b184-118">the number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="3b184-119">zwracany typ (tylko dla procedury operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="3b184-119">the return type (only for a conversion operator procedure)</span></span>

  <span data-ttu-id="3b184-120">Wszystkie przeciążenia musi mieć taką samą nazwę, ale każdy musi różnić się od wszystkich innych w co najmniej jednej poprzedniej aspektach.</span><span class="sxs-lookup"><span data-stu-id="3b184-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="3b184-121">Dzięki temu kompilator, aby odróżnić wyborze wersji do użycia, gdy kod wywołuje właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="3b184-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>

- <span data-ttu-id="3b184-122">**Niedozwolone różnice.**</span><span class="sxs-lookup"><span data-stu-id="3b184-122">**Disallowed Differences.**</span></span> <span data-ttu-id="3b184-123">Zmiana co najmniej jeden z następujących jest nieprawidłowa dla przeciążania właściwość lub procedura, ponieważ nie są one częścią podpisu:</span><span class="sxs-lookup"><span data-stu-id="3b184-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>

  - <span data-ttu-id="3b184-124">Określa, czy zwraca wartość (w przypadku procedura)</span><span class="sxs-lookup"><span data-stu-id="3b184-124">whether or not it returns a value (for a procedure)</span></span>

  - <span data-ttu-id="3b184-125">Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="3b184-125">the data type of the return value (except for a conversion operator)</span></span>

  - <span data-ttu-id="3b184-126">nazwy parametrów lub parametrów typu</span><span class="sxs-lookup"><span data-stu-id="3b184-126">the names of the parameters or type parameters</span></span>

  - <span data-ttu-id="3b184-127">ograniczenia dotyczące parametrów typu (w przypadku ogólnych procedura)</span><span class="sxs-lookup"><span data-stu-id="3b184-127">the constraints on the type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="3b184-128">słowa kluczowe modyfikator parametrów (takie jak `ByRef` lub `Optional`)</span><span class="sxs-lookup"><span data-stu-id="3b184-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>

  - <span data-ttu-id="3b184-129">Właściwość lub procedura modyfikator słowa kluczowe (takie jak `Public` lub `Shared`)</span><span class="sxs-lookup"><span data-stu-id="3b184-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>

- <span data-ttu-id="3b184-130">**Opcjonalny modyfikator właściwy.**</span><span class="sxs-lookup"><span data-stu-id="3b184-130">**Optional Modifier.**</span></span> <span data-ttu-id="3b184-131">Nie trzeba używać `Overloads` modyfikator podczas definiowania wielu przeciążone właściwości i procedury z tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="3b184-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="3b184-132">Jednak jeśli używasz `Overloads` w jednej deklaracji, musisz ją wykorzystać we wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="3b184-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>

- <span data-ttu-id="3b184-133">**Przesłanianie i przeciążeniu.**</span><span class="sxs-lookup"><span data-stu-id="3b184-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="3b184-134">`Overloads` można również w tle istniejącego elementu członkowskiego lub zestawu przeciążone elementy członkowskie w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="3b184-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="3b184-135">Kiedy używasz `Overloads` w ten sposób możesz deklarować właściwość lub metoda o tej samej nazwie i tę samą listę parametrów jako składowej klasy bazowej i nie trzeba dostarczać `Shadows` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3b184-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>

<span data-ttu-id="3b184-136">Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` tak, aby pracować z interfejsów API biblioteki C# łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="3b184-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="3b184-137">`Overloads` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="3b184-137">The `Overloads` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="3b184-138">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3b184-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="3b184-139">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3b184-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)

- [<span data-ttu-id="3b184-140">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="3b184-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="3b184-141">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3b184-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="3b184-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b184-142">See also</span></span>

- [<span data-ttu-id="3b184-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="3b184-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="3b184-144">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="3b184-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="3b184-145">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b184-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="3b184-146">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="3b184-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="3b184-147">Instrukcje: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="3b184-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
