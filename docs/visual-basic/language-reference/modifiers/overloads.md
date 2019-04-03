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
ms.openlocfilehash: 0d68846938aba809a7a3a6f7d27f185bb90a39cb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819336"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="d2b11-102">Overloads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2b11-102">Overloads (Visual Basic)</span></span>
<span data-ttu-id="d2b11-103">Określa, że właściwość lub procedura redeclares istniejących właściwości lub procedur o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="d2b11-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2b11-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2b11-104">Remarks</span></span>  
 <span data-ttu-id="d2b11-105">*Przeciążanie* w praktyce podawania więcej niż jedną definicję dla danej nazwy właściwość lub procedura w tym samym zakresie.</span><span class="sxs-lookup"><span data-stu-id="d2b11-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="d2b11-106">Redeclaring właściwość lub procedura z innym podpisem jest czasami nazywane *ukrywanie poprzez podpis*.</span><span class="sxs-lookup"><span data-stu-id="d2b11-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d2b11-107">reguły</span><span class="sxs-lookup"><span data-stu-id="d2b11-107">Rules</span></span>  
  
-   <span data-ttu-id="d2b11-108">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="d2b11-108">**Declaration Context.**</span></span> <span data-ttu-id="d2b11-109">Możesz użyć `Overloads` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="d2b11-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="d2b11-110">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="d2b11-110">**Combined Modifiers.**</span></span> <span data-ttu-id="d2b11-111">Nie można określić `Overloads` wraz z [cieni](../../../visual-basic/language-reference/modifiers/shadows.md) w tej samej deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="d2b11-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>  
  
-   <span data-ttu-id="d2b11-112">**Wymagane różnice.**</span><span class="sxs-lookup"><span data-stu-id="d2b11-112">**Required Differences.**</span></span> <span data-ttu-id="d2b11-113">*Podpisu* w tej deklaracji musi się różnić od podpisu co właściwość lub procedura, która przeciąża.</span><span class="sxs-lookup"><span data-stu-id="d2b11-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="d2b11-114">Podpis składa się nazwa właściwość lub procedura wraz z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d2b11-114">The signature comprises the property or procedure name together with the following:</span></span>  
  
    -   <span data-ttu-id="d2b11-115">Liczba parametrów</span><span class="sxs-lookup"><span data-stu-id="d2b11-115">the number of parameters</span></span>  
  
    -   <span data-ttu-id="d2b11-116">kolejność parametrów</span><span class="sxs-lookup"><span data-stu-id="d2b11-116">the order of the parameters</span></span>  
  
    -   <span data-ttu-id="d2b11-117">typy danych parametrów</span><span class="sxs-lookup"><span data-stu-id="d2b11-117">the data types of the parameters</span></span>  
  
    -   <span data-ttu-id="d2b11-118">Liczba parametrów typu (w przypadku ogólnych procedura)</span><span class="sxs-lookup"><span data-stu-id="d2b11-118">the number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="d2b11-119">zwracany typ (tylko dla procedury operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="d2b11-119">the return type (only for a conversion operator procedure)</span></span>  
  
     <span data-ttu-id="d2b11-120">Wszystkie przeciążenia musi mieć taką samą nazwę, ale każdy musi różnić się od wszystkich innych w co najmniej jednej poprzedniej aspektach.</span><span class="sxs-lookup"><span data-stu-id="d2b11-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="d2b11-121">Dzięki temu kompilator, aby odróżnić wyborze wersji do użycia, gdy kod wywołuje właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="d2b11-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>  
  
-   <span data-ttu-id="d2b11-122">**Niedozwolone różnice.**</span><span class="sxs-lookup"><span data-stu-id="d2b11-122">**Disallowed Differences.**</span></span> <span data-ttu-id="d2b11-123">Zmiana co najmniej jeden z następujących jest nieprawidłowa dla przeciążania właściwość lub procedura, ponieważ nie są one częścią podpisu:</span><span class="sxs-lookup"><span data-stu-id="d2b11-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>  
  
    -   <span data-ttu-id="d2b11-124">Określa, czy zwraca wartość (w przypadku procedura)</span><span class="sxs-lookup"><span data-stu-id="d2b11-124">whether or not it returns a value (for a procedure)</span></span>  
  
    -   <span data-ttu-id="d2b11-125">Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="d2b11-125">the data type of the return value (except for a conversion operator)</span></span>  
  
    -   <span data-ttu-id="d2b11-126">nazwy parametrów lub parametrów typu</span><span class="sxs-lookup"><span data-stu-id="d2b11-126">the names of the parameters or type parameters</span></span>  
  
    -   <span data-ttu-id="d2b11-127">ograniczenia dotyczące parametrów typu (w przypadku ogólnych procedura)</span><span class="sxs-lookup"><span data-stu-id="d2b11-127">the constraints on the type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="d2b11-128">słowa kluczowe modyfikator parametrów (takie jak `ByRef` lub `Optional`)</span><span class="sxs-lookup"><span data-stu-id="d2b11-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>  
  
    -   <span data-ttu-id="d2b11-129">Właściwość lub procedura modyfikator słowa kluczowe (takie jak `Public` lub `Shared`)</span><span class="sxs-lookup"><span data-stu-id="d2b11-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>  
  
-   <span data-ttu-id="d2b11-130">**Opcjonalny modyfikator właściwy.**</span><span class="sxs-lookup"><span data-stu-id="d2b11-130">**Optional Modifier.**</span></span> <span data-ttu-id="d2b11-131">Nie trzeba używać `Overloads` modyfikator podczas definiowania wielu przeciążone właściwości i procedury z tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="d2b11-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="d2b11-132">Jednak jeśli używasz `Overloads` w jednej deklaracji, musisz ją wykorzystać we wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="d2b11-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>  
  
-   <span data-ttu-id="d2b11-133">**Przesłanianie i przeciążeniu.**</span><span class="sxs-lookup"><span data-stu-id="d2b11-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="d2b11-134">`Overloads` można również w tle istniejącego elementu członkowskiego lub zestawu przeciążone elementy członkowskie w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="d2b11-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="d2b11-135">Kiedy używasz `Overloads` w ten sposób możesz deklarować właściwość lub metoda o tej samej nazwie i tę samą listę parametrów jako składowej klasy bazowej i nie trzeba dostarczać `Shadows` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d2b11-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>  
  
 <span data-ttu-id="d2b11-136">Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` tak, aby pracować z interfejsów API biblioteki C# łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="d2b11-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="d2b11-137">`Overloads` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="d2b11-137">The `Overloads` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d2b11-138">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d2b11-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="d2b11-139">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d2b11-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="d2b11-140">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="d2b11-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="d2b11-141">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d2b11-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d2b11-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2b11-142">See also</span></span>

- [<span data-ttu-id="d2b11-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="d2b11-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="d2b11-144">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="d2b11-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="d2b11-145">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2b11-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="d2b11-146">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="d2b11-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="d2b11-147">Instrukcje: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="d2b11-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
