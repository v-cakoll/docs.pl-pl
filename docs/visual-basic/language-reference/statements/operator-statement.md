---
title: Operator — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: 69dea99cf71bd1e091116e54e244abfca291ffdb
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46517911"
---
# <a name="operator-statement"></a><span data-ttu-id="cb256-102">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cb256-102">Operator Statement</span></span>
<span data-ttu-id="cb256-103">Deklaruje symbol operatora, argumenty operacji i kod, który definiuje procedurę operatora w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="cb256-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb256-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb256-104">Syntax</span></span>  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a><span data-ttu-id="cb256-105">Części</span><span class="sxs-lookup"><span data-stu-id="cb256-105">Parts</span></span>  
 `attrlist`  
 <span data-ttu-id="cb256-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cb256-106">Optional.</span></span> <span data-ttu-id="cb256-107">Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="cb256-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `Public`  
 <span data-ttu-id="cb256-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="cb256-108">Required.</span></span> <span data-ttu-id="cb256-109">Wskazuje, że ta procedura operator ma [publicznych](../../../visual-basic/language-reference/modifiers/public.md) dostępu.</span><span class="sxs-lookup"><span data-stu-id="cb256-109">Indicates that this operator procedure has [Public](../../../visual-basic/language-reference/modifiers/public.md) access.</span></span>  
  
 `Overloads`  
 <span data-ttu-id="cb256-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cb256-110">Optional.</span></span> <span data-ttu-id="cb256-111">Zobacz [przeciążenia](../../../visual-basic/language-reference/modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="cb256-111">See [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span></span>  
  
 `Shared`  
 <span data-ttu-id="cb256-112">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="cb256-112">Required.</span></span> <span data-ttu-id="cb256-113">Wskazuje, że ta procedura operator [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedury.</span><span class="sxs-lookup"><span data-stu-id="cb256-113">Indicates that this operator procedure is a [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedure.</span></span>  
  
 `Shadows`  
 <span data-ttu-id="cb256-114">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cb256-114">Optional.</span></span> <span data-ttu-id="cb256-115">Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="cb256-115">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
 `Widening`  
 <span data-ttu-id="cb256-116">Wymagane dla operatora konwersji, chyba że określisz `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="cb256-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="cb256-117">Wskazuje, że ta procedura operator definiuje [Widening](../../../visual-basic/language-reference/modifiers/widening.md) konwersji.</span><span class="sxs-lookup"><span data-stu-id="cb256-117">Indicates that this operator procedure defines a [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion.</span></span> <span data-ttu-id="cb256-118">Zobacz "Rozszerzające i zawężające konwersje" na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="cb256-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `Narrowing`  
 <span data-ttu-id="cb256-119">Wymagane dla operatora konwersji, chyba że określisz `Widening`.</span><span class="sxs-lookup"><span data-stu-id="cb256-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="cb256-120">Wskazuje, że ta procedura operator definiuje [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) konwersji.</span><span class="sxs-lookup"><span data-stu-id="cb256-120">Indicates that this operator procedure defines a [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="cb256-121">Zobacz "Rozszerzające i zawężające konwersje" na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="cb256-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `operatorsymbol`  
 <span data-ttu-id="cb256-122">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="cb256-122">Required.</span></span> <span data-ttu-id="cb256-123">Symbol lub identyfikator operator, który definiuje tę procedurę operatora.</span><span class="sxs-lookup"><span data-stu-id="cb256-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>  
  
 `operand1`  
 <span data-ttu-id="cb256-124">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="cb256-124">Required.</span></span> <span data-ttu-id="cb256-125">Nazwa i typ jeden argument operacji operatora jednoargumentowego (w tym operatora konwersji) lub lewy operand operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="cb256-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>  
  
 `operand2`  
 <span data-ttu-id="cb256-126">Wymagane dla operatorów binarnych.</span><span class="sxs-lookup"><span data-stu-id="cb256-126">Required for binary operators.</span></span> <span data-ttu-id="cb256-127">Nazwa i typ prawy operand operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="cb256-127">The name and type of the right operand of a binary operator.</span></span>  
  
 <span data-ttu-id="cb256-128">`operand1` i `operand2` poniższej składni i części:</span><span class="sxs-lookup"><span data-stu-id="cb256-128">`operand1` and `operand2` have the following syntax and parts:</span></span>  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|<span data-ttu-id="cb256-129">Część</span><span class="sxs-lookup"><span data-stu-id="cb256-129">Part</span></span>|<span data-ttu-id="cb256-130">Opis</span><span class="sxs-lookup"><span data-stu-id="cb256-130">Description</span></span>|  
|----------|-----------------|  
|`ByVal`|<span data-ttu-id="cb256-131">Opcjonalne, ale mechanizm przekazywania musi być [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="cb256-131">Optional, but the passing mechanism must be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>|  
|`operandname`|<span data-ttu-id="cb256-132">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="cb256-132">Required.</span></span> <span data-ttu-id="cb256-133">Nazwa zmiennej, reprezentujący ten argument operacji.</span><span class="sxs-lookup"><span data-stu-id="cb256-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="cb256-134">Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="cb256-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`operandtype`|<span data-ttu-id="cb256-135">Opcjonalne chyba że `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="cb256-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="cb256-136">Typ danych ten argument operacji.</span><span class="sxs-lookup"><span data-stu-id="cb256-136">Data type of this operand.</span></span>|  
  
 `type`  
 <span data-ttu-id="cb256-137">Opcjonalne chyba że `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="cb256-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="cb256-138">Zwraca typ danych wartości procedury operatora.</span><span class="sxs-lookup"><span data-stu-id="cb256-138">Data type of the value the operator procedure returns.</span></span>  
  
 `statements`  
 <span data-ttu-id="cb256-139">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cb256-139">Optional.</span></span> <span data-ttu-id="cb256-140">Blok instrukcji, które są wykonywane procedury operatora.</span><span class="sxs-lookup"><span data-stu-id="cb256-140">Block of statements that the operator procedure runs.</span></span>  
  
 `returnvalue`  
 <span data-ttu-id="cb256-141">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="cb256-141">Required.</span></span> <span data-ttu-id="cb256-142">Wartość, która procedura operator zwraca do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="cb256-142">The value that the operator procedure returns to the calling code.</span></span>  
  
 <span data-ttu-id="cb256-143">`End``Operator`</span><span class="sxs-lookup"><span data-stu-id="cb256-143">`End` `Operator`</span></span>  
 <span data-ttu-id="cb256-144">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="cb256-144">Required.</span></span> <span data-ttu-id="cb256-145">Kończy definicję tej procedury operatora.</span><span class="sxs-lookup"><span data-stu-id="cb256-145">Terminates the definition of this operator procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb256-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb256-146">Remarks</span></span>  
 <span data-ttu-id="cb256-147">Możesz użyć `Operator` tylko w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="cb256-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="cb256-148">Oznacza to, że *kontekst deklaracji* operator nie może być plik źródłowy, przestrzeni nazw, moduł, interfejsu, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="cb256-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="cb256-149">Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cb256-149">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="cb256-150">Wszystkie operatory muszą być `Public Shared`.</span><span class="sxs-lookup"><span data-stu-id="cb256-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="cb256-151">Nie można określić `ByRef`, `Optional`, lub `ParamArray` na jeden z operandów.</span><span class="sxs-lookup"><span data-stu-id="cb256-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>  
  
 <span data-ttu-id="cb256-152">Symbol operatora lub identyfikatora nie można użyć do przechowywania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="cb256-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="cb256-153">Należy użyć `Return` instrukcji i należy określić wartość.</span><span class="sxs-lookup"><span data-stu-id="cb256-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="cb256-154">Dowolną liczbę `Return` instrukcji może występować w dowolnym miejscu w procedurze.</span><span class="sxs-lookup"><span data-stu-id="cb256-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>  
  
 <span data-ttu-id="cb256-155">Definiowanie operatora w ten sposób jest nazywany *przeciążania operatorów*, czy używasz `Overloads` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="cb256-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="cb256-156">W poniższej tabeli wymieniono operatory, które można zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="cb256-156">The following table lists the operators you can define.</span></span>  
  
|<span data-ttu-id="cb256-157">Typ</span><span class="sxs-lookup"><span data-stu-id="cb256-157">Type</span></span>|<span data-ttu-id="cb256-158">Operatory</span><span class="sxs-lookup"><span data-stu-id="cb256-158">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="cb256-159">Jednoargumentowy</span><span class="sxs-lookup"><span data-stu-id="cb256-159">Unary</span></span>|<span data-ttu-id="cb256-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="cb256-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="cb256-161">plików binarnych</span><span class="sxs-lookup"><span data-stu-id="cb256-161">Binary</span></span>|<span data-ttu-id="cb256-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="cb256-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="cb256-163">Konwersja (jednoargumentowy)</span><span class="sxs-lookup"><span data-stu-id="cb256-163">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="cb256-164">Należy pamiętać, że `=` operator binarny listy jest operator porównania nie operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="cb256-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="cb256-165">Podczas definiowania `CType`, należy określić `Widening` lub `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="cb256-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>  
  
## <a name="matched-pairs"></a><span data-ttu-id="cb256-166">Dopasowane pary</span><span class="sxs-lookup"><span data-stu-id="cb256-166">Matched Pairs</span></span>  
 <span data-ttu-id="cb256-167">Należy zdefiniować jako dopasowane pary niektórych operatorów.</span><span class="sxs-lookup"><span data-stu-id="cb256-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="cb256-168">Jeśli zdefiniujesz albo operator takich pary, należy zdefiniować innych także.</span><span class="sxs-lookup"><span data-stu-id="cb256-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="cb256-169">Dopasowane pary są następujące:</span><span class="sxs-lookup"><span data-stu-id="cb256-169">The matched pairs are the following:</span></span>  
  
-   <span data-ttu-id="cb256-170">`=` i `<>`</span><span class="sxs-lookup"><span data-stu-id="cb256-170">`=` and `<>`</span></span>  
  
-   <span data-ttu-id="cb256-171">`>` i `<`</span><span class="sxs-lookup"><span data-stu-id="cb256-171">`>` and `<`</span></span>  
  
-   <span data-ttu-id="cb256-172">`>=` i `<=`</span><span class="sxs-lookup"><span data-stu-id="cb256-172">`>=` and `<=`</span></span>  
  
-   <span data-ttu-id="cb256-173">`IsTrue` i `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="cb256-173">`IsTrue` and `IsFalse`</span></span>  
  
## <a name="data-type-restrictions"></a><span data-ttu-id="cb256-174">Ograniczenia dotyczące typu danych</span><span class="sxs-lookup"><span data-stu-id="cb256-174">Data Type Restrictions</span></span>  
 <span data-ttu-id="cb256-175">Każdy operator, który zdefiniujesz muszą obejmować klasy lub struktury, w którym można zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="cb256-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="cb256-176">Oznacza to, że klasa lub struktura musi znajdować się w formie typu danych z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="cb256-176">This means that the class or structure must appear as the data type of the following:</span></span>  
  
-   <span data-ttu-id="cb256-177">Argument operacji operatora jednoargumentowego.</span><span class="sxs-lookup"><span data-stu-id="cb256-177">The operand of a unary operator.</span></span>  
  
-   <span data-ttu-id="cb256-178">Co najmniej jeden z operandów operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="cb256-178">At least one of the operands of a binary operator.</span></span>  
  
-   <span data-ttu-id="cb256-179">Argument lub zwracany typ operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="cb256-179">Either the operand or the return type of a conversion operator.</span></span>  
  
 <span data-ttu-id="cb256-180">Niektóre operatory mają dodatkowe dane, wpisz następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="cb256-180">Certain operators have additional data type restrictions, as follows:</span></span>  
  
-   <span data-ttu-id="cb256-181">Jeśli zdefiniujesz `IsTrue` i `IsFalse` operatorów, muszą one zarówno zwracać `Boolean` typu.</span><span class="sxs-lookup"><span data-stu-id="cb256-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>  
  
-   <span data-ttu-id="cb256-182">Jeśli zdefiniujesz `<<` i `>>` operatorów, muszą oni zarówno określić `Integer` wpisz `operandtype` z `operand2`.</span><span class="sxs-lookup"><span data-stu-id="cb256-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>  
  
 <span data-ttu-id="cb256-183">Zwracany typ nie musi odpowiadać typowi jeden z operandów.</span><span class="sxs-lookup"><span data-stu-id="cb256-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="cb256-184">Na przykład operator porównania takich jak `=` lub `<>` może zwrócić `Boolean` nawet jeśli żaden z operandów jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cb256-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>  
  
## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="cb256-185">Operatory logiczne i bitowe</span><span class="sxs-lookup"><span data-stu-id="cb256-185">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="cb256-186">`And`, `Or`, `Not`, I `Xor` operatorzy mogą wykonywać operacji logicznych lub bitowe w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cb256-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="cb256-187">Jednak jeśli zdefiniujesz jednego z tych operatorów dla klasy lub struktury, można zdefiniować tylko jego operacji na poziomie bitowym.</span><span class="sxs-lookup"><span data-stu-id="cb256-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>  
  
 <span data-ttu-id="cb256-188">Nie można zdefiniować `AndAlso` operator bezpośrednio z `Operator` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cb256-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="cb256-189">Można jednak użyć `AndAlso` jeśli zostały spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="cb256-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>  
  
-   <span data-ttu-id="cb256-190">Zdefiniowano `And` na te same typy operand, którego chcesz użyć dla `AndAlso`.</span><span class="sxs-lookup"><span data-stu-id="cb256-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>  
  
-   <span data-ttu-id="cb256-191">Definicja `And` zwraca ten sam typ co klasa lub struktura, w którym zdefiniowano go.</span><span class="sxs-lookup"><span data-stu-id="cb256-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>  
  
-   <span data-ttu-id="cb256-192">Zdefiniowano `IsFalse` operator dla klasy lub struktury, w którym zdefiniowano `And`.</span><span class="sxs-lookup"><span data-stu-id="cb256-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>  
  
 <span data-ttu-id="cb256-193">Podobnie, można użyć `OrElse` Jeżeli posiadasz zdefiniowane `Or` na tych samych argumentów o zwracanym typie krawędzi klasy lub struktury, a zdefiniowano `IsTrue` dla klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="cb256-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>  
  
## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="cb256-194">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="cb256-194">Widening and Narrowing Conversions</span></span>  
 <span data-ttu-id="cb256-195">A *poszerzenie konwersji* zawsze zakończy się pomyślnie w czasie wykonywania, podczas gdy *konwersja zawężająca* może zakończyć się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cb256-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="cb256-196">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="cb256-196">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
 <span data-ttu-id="cb256-197">Jeśli zadeklarujesz procedury konwersji za `Widening`, kod procedury nie należy wygenerować zakończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="cb256-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="cb256-198">Oznacza to, że:</span><span class="sxs-lookup"><span data-stu-id="cb256-198">This means the following:</span></span>  
  
-   <span data-ttu-id="cb256-199">Zawsze musi zwracać prawidłowe wartości typu `type`.</span><span class="sxs-lookup"><span data-stu-id="cb256-199">It must always return a valid value of type `type`.</span></span>  
  
-   <span data-ttu-id="cb256-200">Musi on obsługiwać wszystkich możliwych wyjątków i inne warunki błędu.</span><span class="sxs-lookup"><span data-stu-id="cb256-200">It must handle all possible exceptions and other error conditions.</span></span>  
  
-   <span data-ttu-id="cb256-201">Jego musi obsługiwać żadnych zwraca błąd z procedury wywoływanych przez nią.</span><span class="sxs-lookup"><span data-stu-id="cb256-201">It must handle any error returns from any procedures it calls.</span></span>  
  
 <span data-ttu-id="cb256-202">Jeśli ma żadnych możliwość, że procedura Konwersja może się nie powieść lub jej może spowodować, że nieobsługiwany wyjątek, należy zadeklarować ją jako `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="cb256-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb256-203">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb256-203">Example</span></span>  
 <span data-ttu-id="cb256-204">Poniższy przykład kodu wykorzystuje `Operator` instrukcję w celu zdefiniowania konturu to struktura, która zawiera procedury operatora `And`, `Or`, `IsFalse`, i `IsTrue` operatorów.</span><span class="sxs-lookup"><span data-stu-id="cb256-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="cb256-205">`And` i `Or` uwzględniać dwóch argumentów operacji typu `abc` i zwracany typ `abc`.</span><span class="sxs-lookup"><span data-stu-id="cb256-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="cb256-206">`IsFalse` i `IsTrue` uwzględniać jeden argument operacji typu `abc` i zwracają `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cb256-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="cb256-207">Te definicje Zezwalaj na kod wywołujący, aby użyć `And`, `AndAlso`, `Or`, i `OrElse` z argumentów operacji typu `abc`.</span><span class="sxs-lookup"><span data-stu-id="cb256-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cb256-208">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb256-208">See Also</span></span>  
 [<span data-ttu-id="cb256-209">IsFalse, operator</span><span class="sxs-lookup"><span data-stu-id="cb256-209">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="cb256-210">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="cb256-210">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="cb256-211">Widening</span><span class="sxs-lookup"><span data-stu-id="cb256-211">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="cb256-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="cb256-212">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="cb256-213">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="cb256-213">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="cb256-214">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="cb256-214">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="cb256-215">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="cb256-215">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="cb256-216">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="cb256-216">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="cb256-217">Instrukcje: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="cb256-217">How to: Call an Operator Procedure</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="cb256-218">Instrukcje: używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="cb256-218">How to: Use a Class that Defines Operators</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
