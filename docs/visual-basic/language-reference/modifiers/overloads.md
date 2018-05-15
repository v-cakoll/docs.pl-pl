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
ms.openlocfilehash: b68c13d192845fc4bedf1b34a40165ccc1a5ff75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="41f2c-102">Overloads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41f2c-102">Overloads (Visual Basic)</span></span>
<span data-ttu-id="41f2c-103">Określa, że właściwość lub procedura programistyczny ponownie deklaruje co najmniej jednej właściwości istniejących lub procedury o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="41f2c-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41f2c-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41f2c-104">Remarks</span></span>  
 <span data-ttu-id="41f2c-105">*Przeciążanie* praktyką podawania więcej niż jedną definicję dla danej nazwy właściwość lub procedura w tym samym zakresie.</span><span class="sxs-lookup"><span data-stu-id="41f2c-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="41f2c-106">Ponownego deklarowania właściwość lub procedurę o innym podpisie jest czasami nazywany *ukrywanie poprzez podpis*.</span><span class="sxs-lookup"><span data-stu-id="41f2c-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="41f2c-107">Reguły</span><span class="sxs-lookup"><span data-stu-id="41f2c-107">Rules</span></span>  
  
-   <span data-ttu-id="41f2c-108">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="41f2c-108">**Declaration Context.**</span></span> <span data-ttu-id="41f2c-109">Można użyć `Overloads` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="41f2c-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="41f2c-110">**Łączna modyfikatorów.**</span><span class="sxs-lookup"><span data-stu-id="41f2c-110">**Combined Modifiers.**</span></span> <span data-ttu-id="41f2c-111">Nie można określić `Overloads` razem z [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) w tej samej deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="41f2c-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>  
  
-   <span data-ttu-id="41f2c-112">**Wymagane różnice.**</span><span class="sxs-lookup"><span data-stu-id="41f2c-112">**Required Differences.**</span></span> <span data-ttu-id="41f2c-113">*Podpisu* w tej deklaracji musi być inna niż podpisu co właściwość lub procedura, która przeciąża.</span><span class="sxs-lookup"><span data-stu-id="41f2c-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="41f2c-114">Sygnatura obejmuje nazwę właściwość lub procedura wraz z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="41f2c-114">The signature comprises the property or procedure name together with the following:</span></span>  
  
    -   <span data-ttu-id="41f2c-115">Liczba parametrów</span><span class="sxs-lookup"><span data-stu-id="41f2c-115">the number of parameters</span></span>  
  
    -   <span data-ttu-id="41f2c-116">kolejność parametrów</span><span class="sxs-lookup"><span data-stu-id="41f2c-116">the order of the parameters</span></span>  
  
    -   <span data-ttu-id="41f2c-117">typy danych parametrów</span><span class="sxs-lookup"><span data-stu-id="41f2c-117">the data types of the parameters</span></span>  
  
    -   <span data-ttu-id="41f2c-118">Liczba parametrów typu (dla procedury ogólny)</span><span class="sxs-lookup"><span data-stu-id="41f2c-118">the number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="41f2c-119">zwracany typ (tylko dla procedury operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="41f2c-119">the return type (only for a conversion operator procedure)</span></span>  
  
     <span data-ttu-id="41f2c-120">Wszystkie przeciążenia musi mieć taką samą nazwę, ale każdy musi różnić się od wszystkich innych w co najmniej jednego z poprzednich względem.</span><span class="sxs-lookup"><span data-stu-id="41f2c-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="41f2c-121">Umożliwia kompilatorowi rozróżnienie wersji do użycia, gdy kod wywołuje właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="41f2c-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>  
  
-   <span data-ttu-id="41f2c-122">**Niedozwolone różnice.**</span><span class="sxs-lookup"><span data-stu-id="41f2c-122">**Disallowed Differences.**</span></span> <span data-ttu-id="41f2c-123">Zmiana jednego lub więcej z następujących jest nieprawidłowa dla przeładowanie właściwość lub procedura, ponieważ nie są częścią podpisu:</span><span class="sxs-lookup"><span data-stu-id="41f2c-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>  
  
    -   <span data-ttu-id="41f2c-124">Określa, czy zwraca wartość (procedura)</span><span class="sxs-lookup"><span data-stu-id="41f2c-124">whether or not it returns a value (for a procedure)</span></span>  
  
    -   <span data-ttu-id="41f2c-125">Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="41f2c-125">the data type of the return value (except for a conversion operator)</span></span>  
  
    -   <span data-ttu-id="41f2c-126">nazwy parametrów lub parametry typu</span><span class="sxs-lookup"><span data-stu-id="41f2c-126">the names of the parameters or type parameters</span></span>  
  
    -   <span data-ttu-id="41f2c-127">ograniczenia dotyczące parametrów typu (dla procedury ogólny)</span><span class="sxs-lookup"><span data-stu-id="41f2c-127">the constraints on the type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="41f2c-128">słowa kluczowe modyfikator parametrów (takich jak `ByRef` lub `Optional`)</span><span class="sxs-lookup"><span data-stu-id="41f2c-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>  
  
    -   <span data-ttu-id="41f2c-129">Właściwość lub procedura modyfikator słowa kluczowe (takich jak `Public` lub `Shared`)</span><span class="sxs-lookup"><span data-stu-id="41f2c-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>  
  
-   <span data-ttu-id="41f2c-130">**Modyfikator opcjonalne.**</span><span class="sxs-lookup"><span data-stu-id="41f2c-130">**Optional Modifier.**</span></span> <span data-ttu-id="41f2c-131">Nie trzeba używać `Overloads` modyfikator podczas definiowania wielu przeciążone właściwości lub procedury opisane w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="41f2c-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="41f2c-132">Jednak jeśli używasz `Overloads` w jednej deklaracji, należy użyć go we wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="41f2c-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>  
  
-   <span data-ttu-id="41f2c-133">**Przesłanianie i przeciążeniu.**</span><span class="sxs-lookup"><span data-stu-id="41f2c-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="41f2c-134">`Overloads` można również tle istniejącego elementu członkowskiego lub zestawu przeciążone elementy członkowskie w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="41f2c-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="41f2c-135">Jeśli używasz `Overloads` w ten sposób można zadeklarować właściwości lub metody o tej samej nazwie i tej samej listy parametrów jako element członkowski klasy podstawowej i nie zostanie podana `Shadows` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="41f2c-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>  
  
 <span data-ttu-id="41f2c-136">Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` , aby pracować z C# łatwiej biblioteki interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="41f2c-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="41f2c-137">`Overloads` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="41f2c-137">The `Overloads` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="41f2c-138">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="41f2c-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="41f2c-139">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="41f2c-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="41f2c-140">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="41f2c-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="41f2c-141">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="41f2c-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="41f2c-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41f2c-142">See Also</span></span>  
 [<span data-ttu-id="41f2c-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="41f2c-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="41f2c-144">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="41f2c-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="41f2c-145">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41f2c-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="41f2c-146">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="41f2c-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="41f2c-147">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="41f2c-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
