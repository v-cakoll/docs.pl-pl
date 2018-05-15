---
title: Operator — Instrukcja
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
ms.openlocfilehash: cb7fe7929e4b6e61ca3b39be5615e09182f2fe0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="operator-statement"></a><span data-ttu-id="70481-102">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="70481-102">Operator Statement</span></span>
<span data-ttu-id="70481-103">Deklaruje symbol operatora, argumenty operacji i kod, który definiuje procedurę operatora w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="70481-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70481-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70481-104">Syntax</span></span>  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a><span data-ttu-id="70481-105">Części</span><span class="sxs-lookup"><span data-stu-id="70481-105">Parts</span></span>  
 `attrlist`  
 <span data-ttu-id="70481-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="70481-106">Optional.</span></span> <span data-ttu-id="70481-107">Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="70481-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `Public`  
 <span data-ttu-id="70481-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="70481-108">Required.</span></span> <span data-ttu-id="70481-109">Wskazuje, że ta procedura operator ma [publicznego](../../../visual-basic/language-reference/modifiers/public.md) dostępu.</span><span class="sxs-lookup"><span data-stu-id="70481-109">Indicates that this operator procedure has [Public](../../../visual-basic/language-reference/modifiers/public.md) access.</span></span>  
  
 `Overloads`  
 <span data-ttu-id="70481-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="70481-110">Optional.</span></span> <span data-ttu-id="70481-111">Zobacz [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="70481-111">See [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span></span>  
  
 `Shared`  
 <span data-ttu-id="70481-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="70481-112">Required.</span></span> <span data-ttu-id="70481-113">Oznacza, że ta procedura operator [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedury.</span><span class="sxs-lookup"><span data-stu-id="70481-113">Indicates that this operator procedure is a [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedure.</span></span>  
  
 `Shadows`  
 <span data-ttu-id="70481-114">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="70481-114">Optional.</span></span> <span data-ttu-id="70481-115">Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="70481-115">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
 `Widening`  
 <span data-ttu-id="70481-116">Wymagany dla operatora konwersji, chyba że zostanie `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="70481-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="70481-117">Wskazuje, że ta procedura operator definiuje [Widening](../../../visual-basic/language-reference/modifiers/widening.md) konwersji.</span><span class="sxs-lookup"><span data-stu-id="70481-117">Indicates that this operator procedure defines a [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion.</span></span> <span data-ttu-id="70481-118">Na tej stronie pomocy, zobacz "Rozszerzanie i zwężanie konwersji".</span><span class="sxs-lookup"><span data-stu-id="70481-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `Narrowing`  
 <span data-ttu-id="70481-119">Wymagany dla operatora konwersji, chyba że zostanie `Widening`.</span><span class="sxs-lookup"><span data-stu-id="70481-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="70481-120">Wskazuje, że ta procedura operator definiuje [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) konwersji.</span><span class="sxs-lookup"><span data-stu-id="70481-120">Indicates that this operator procedure defines a [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="70481-121">Na tej stronie pomocy, zobacz "Rozszerzanie i zwężanie konwersji".</span><span class="sxs-lookup"><span data-stu-id="70481-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `operatorsymbol`  
 <span data-ttu-id="70481-122">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="70481-122">Required.</span></span> <span data-ttu-id="70481-123">Symbol lub identyfikator operator, który definiuje tę procedurę operatora.</span><span class="sxs-lookup"><span data-stu-id="70481-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>  
  
 `operand1`  
 <span data-ttu-id="70481-124">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="70481-124">Required.</span></span> <span data-ttu-id="70481-125">Nazwa i typ pojedynczy argument operacji operatora jednoargumentowego (w tym operatora konwersji) lub lewy argument operacji operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="70481-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>  
  
 `operand2`  
 <span data-ttu-id="70481-126">Wymagany w przypadku operatorów binarnych.</span><span class="sxs-lookup"><span data-stu-id="70481-126">Required for binary operators.</span></span> <span data-ttu-id="70481-127">Nazwa i typ prawy argument operacji operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="70481-127">The name and type of the right operand of a binary operator.</span></span>  
  
 <span data-ttu-id="70481-128">`operand1` i `operand2` mają następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="70481-128">`operand1` and `operand2` have the following syntax and parts:</span></span>  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|<span data-ttu-id="70481-129">Część</span><span class="sxs-lookup"><span data-stu-id="70481-129">Part</span></span>|<span data-ttu-id="70481-130">Opis</span><span class="sxs-lookup"><span data-stu-id="70481-130">Description</span></span>|  
|----------|-----------------|  
|`ByVal`|<span data-ttu-id="70481-131">Opcjonalne, ale mechanizm przekazywania musi być [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="70481-131">Optional, but the passing mechanism must be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>|  
|`operandname`|<span data-ttu-id="70481-132">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="70481-132">Required.</span></span> <span data-ttu-id="70481-133">Nazwa zmiennej reprezentujący ten argument operacji.</span><span class="sxs-lookup"><span data-stu-id="70481-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="70481-134">Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="70481-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`operandtype`|<span data-ttu-id="70481-135">Opcjonalne chyba że `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="70481-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="70481-136">Typ danych tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="70481-136">Data type of this operand.</span></span>|  
  
 `type`  
 <span data-ttu-id="70481-137">Opcjonalne chyba że `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="70481-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="70481-138">Zwraca typ danych wartości procedury operatora.</span><span class="sxs-lookup"><span data-stu-id="70481-138">Data type of the value the operator procedure returns.</span></span>  
  
 `statements`  
 <span data-ttu-id="70481-139">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="70481-139">Optional.</span></span> <span data-ttu-id="70481-140">Blok instrukcji, które są wykonywane procedury operatora.</span><span class="sxs-lookup"><span data-stu-id="70481-140">Block of statements that the operator procedure runs.</span></span>  
  
 `returnvalue`  
 <span data-ttu-id="70481-141">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="70481-141">Required.</span></span> <span data-ttu-id="70481-142">Wartość, która zwraca procedury operatora do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="70481-142">The value that the operator procedure returns to the calling code.</span></span>  
  
 <span data-ttu-id="70481-143">`End``Operator`</span><span class="sxs-lookup"><span data-stu-id="70481-143">`End` `Operator`</span></span>  
 <span data-ttu-id="70481-144">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="70481-144">Required.</span></span> <span data-ttu-id="70481-145">Kończy definicję tej procedury operatora.</span><span class="sxs-lookup"><span data-stu-id="70481-145">Terminates the definition of this operator procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70481-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70481-146">Remarks</span></span>  
 <span data-ttu-id="70481-147">Można użyć `Operator` tylko w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="70481-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="70481-148">Oznacza to, że *kontekście deklaracji* operator nie może być plik źródłowy, przestrzeni nazw, modułu, interfejsu, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="70481-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="70481-149">Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).</span><span class="sxs-lookup"><span data-stu-id="70481-149">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="70481-150">Wszystkie operatory musi być `Public Shared`.</span><span class="sxs-lookup"><span data-stu-id="70481-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="70481-151">Nie można określić `ByRef`, `Optional`, lub `ParamArray` dla którykolwiek argument operacji.</span><span class="sxs-lookup"><span data-stu-id="70481-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>  
  
 <span data-ttu-id="70481-152">Symbol operatora lub identyfikatora nie można używać do przechowywania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="70481-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="70481-153">Należy użyć `Return` instrukcji, a musi określać wartość.</span><span class="sxs-lookup"><span data-stu-id="70481-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="70481-154">Dowolną liczbę `Return` instrukcje mogą występować w dowolnym miejscu w procedurze.</span><span class="sxs-lookup"><span data-stu-id="70481-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>  
  
 <span data-ttu-id="70481-155">Definiowanie operatora w ten sposób jest nazywany *przeładowania operatora*, czy używasz `Overloads` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="70481-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="70481-156">W poniższej tabeli wymieniono operatory, których można zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="70481-156">The following table lists the operators you can define.</span></span>  
  
|<span data-ttu-id="70481-157">Typ</span><span class="sxs-lookup"><span data-stu-id="70481-157">Type</span></span>|<span data-ttu-id="70481-158">Operatory</span><span class="sxs-lookup"><span data-stu-id="70481-158">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="70481-159">Jednoargumentowe</span><span class="sxs-lookup"><span data-stu-id="70481-159">Unary</span></span>|<span data-ttu-id="70481-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="70481-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="70481-161">plików binarnych</span><span class="sxs-lookup"><span data-stu-id="70481-161">Binary</span></span>|<span data-ttu-id="70481-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="70481-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="70481-163">Konwersja (jednoargumentowy)</span><span class="sxs-lookup"><span data-stu-id="70481-163">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="70481-164">Należy pamiętać, że `=` operator porównania nie operator przypisania jest operator binarny listy.</span><span class="sxs-lookup"><span data-stu-id="70481-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="70481-165">Podczas definiowania `CType`, należy określić `Widening` lub `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="70481-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>  
  
## <a name="matched-pairs"></a><span data-ttu-id="70481-166">Dopasowane pary</span><span class="sxs-lookup"><span data-stu-id="70481-166">Matched Pairs</span></span>  
 <span data-ttu-id="70481-167">Należy zdefiniować operatorów jako dopasowane pary.</span><span class="sxs-lookup"><span data-stu-id="70481-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="70481-168">W przypadku definiowania albo operator takich parze, należy zdefiniować innych również.</span><span class="sxs-lookup"><span data-stu-id="70481-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="70481-169">Dopasowane pary są następujące:</span><span class="sxs-lookup"><span data-stu-id="70481-169">The matched pairs are the following:</span></span>  
  
-   <span data-ttu-id="70481-170">`=` I `<>`</span><span class="sxs-lookup"><span data-stu-id="70481-170">`=` and `<>`</span></span>  
  
-   <span data-ttu-id="70481-171">`>` I `<`</span><span class="sxs-lookup"><span data-stu-id="70481-171">`>` and `<`</span></span>  
  
-   <span data-ttu-id="70481-172">`>=` I `<=`</span><span class="sxs-lookup"><span data-stu-id="70481-172">`>=` and `<=`</span></span>  
  
-   <span data-ttu-id="70481-173">`IsTrue` I `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="70481-173">`IsTrue` and `IsFalse`</span></span>  
  
## <a name="data-type-restrictions"></a><span data-ttu-id="70481-174">Ograniczenia dotyczące typu danych</span><span class="sxs-lookup"><span data-stu-id="70481-174">Data Type Restrictions</span></span>  
 <span data-ttu-id="70481-175">Co należy zdefiniować operator musi obejmować klasy lub struktury, w którym można zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="70481-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="70481-176">Oznacza to, że klasy lub struktury musi występować jako typ danych z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="70481-176">This means that the class or structure must appear as the data type of the following:</span></span>  
  
-   <span data-ttu-id="70481-177">Argument operacji operatora jednoargumentowego.</span><span class="sxs-lookup"><span data-stu-id="70481-177">The operand of a unary operator.</span></span>  
  
-   <span data-ttu-id="70481-178">Co najmniej jeden z argumentów operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="70481-178">At least one of the operands of a binary operator.</span></span>  
  
-   <span data-ttu-id="70481-179">Argument operacji lub typ zwracany operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="70481-179">Either the operand or the return type of a conversion operator.</span></span>  
  
 <span data-ttu-id="70481-180">Operatorów mają dodatkowe dane typu ograniczenia, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="70481-180">Certain operators have additional data type restrictions, as follows:</span></span>  
  
-   <span data-ttu-id="70481-181">W przypadku definiowania `IsTrue` i `IsFalse` operatorów, muszą one zarówno zwracać `Boolean` typu.</span><span class="sxs-lookup"><span data-stu-id="70481-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>  
  
-   <span data-ttu-id="70481-182">W przypadku definiowania `<<` i `>>` operatorów, ich trzeba określić `Integer` wpisz `operandtype` z `operand2`.</span><span class="sxs-lookup"><span data-stu-id="70481-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>  
  
 <span data-ttu-id="70481-183">Zwracany typ nie musi odpowiadać typowi którykolwiek argument operacji.</span><span class="sxs-lookup"><span data-stu-id="70481-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="70481-184">Na przykład operator porównania takich jak `=` lub `<>` może zwrócić `Boolean` nawet, jeśli żaden argument operacji jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="70481-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>  
  
## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="70481-185">Operatory logiczne i bitowe</span><span class="sxs-lookup"><span data-stu-id="70481-185">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="70481-186">`And`, `Or`, `Not`, I `Xor` operatorzy mogą wykonywać operacje logicznych lub bitowe w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="70481-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="70481-187">Jednak jeśli jeden z tych operatorów zdefiniowanej dla klasy lub struktury, można zdefiniować tylko jego operacji.</span><span class="sxs-lookup"><span data-stu-id="70481-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>  
  
 <span data-ttu-id="70481-188">Nie można zdefiniować `AndAlso` operator bezpośrednio z `Operator` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="70481-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="70481-189">Można jednak użyć `AndAlso` czy zostały spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="70481-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>  
  
-   <span data-ttu-id="70481-190">Zdefiniowano `And` na ten sam typ argumentu ma być używany dla `AndAlso`.</span><span class="sxs-lookup"><span data-stu-id="70481-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>  
  
-   <span data-ttu-id="70481-191">Definicja `And` zwraca ten sam typ co klasy lub struktury, w którym zdefiniowano go.</span><span class="sxs-lookup"><span data-stu-id="70481-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>  
  
-   <span data-ttu-id="70481-192">Zdefiniowano `IsFalse` operatora dla klasy lub struktury, w którym zdefiniowano `And`.</span><span class="sxs-lookup"><span data-stu-id="70481-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>  
  
 <span data-ttu-id="70481-193">Analogicznie, można użyć `OrElse` Jeśli zdefiniowano `Or` na tej samej operandy ze zwracanym typem klasy lub struktury, a zdefiniowane `IsTrue` dla klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="70481-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>  
  
## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="70481-194">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="70481-194">Widening and Narrowing Conversions</span></span>  
 <span data-ttu-id="70481-195">A *rozszerzanie konwersji* zawsze zakończy się pomyślnie w czasie wykonywania, gdy *konwersja zawężająca* może zakończyć się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="70481-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="70481-196">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="70481-196">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
 <span data-ttu-id="70481-197">W przypadku procedury konwersji za `Widening`, kod procedury należy wygenerować nie zakończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="70481-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="70481-198">Oznacza to następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="70481-198">This means the following:</span></span>  
  
-   <span data-ttu-id="70481-199">Musi ona zawsze zwrócić wartość prawidłowego typu `type`.</span><span class="sxs-lookup"><span data-stu-id="70481-199">It must always return a valid value of type `type`.</span></span>  
  
-   <span data-ttu-id="70481-200">Go musi obsługiwać wszystkich możliwych wyjątków i innych błędów.</span><span class="sxs-lookup"><span data-stu-id="70481-200">It must handle all possible exceptions and other error conditions.</span></span>  
  
-   <span data-ttu-id="70481-201">Go musi obsługiwać żadnych zwraca błąd z procedury wywoływanych przez nią.</span><span class="sxs-lookup"><span data-stu-id="70481-201">It must handle any error returns from any procedures it calls.</span></span>  
  
 <span data-ttu-id="70481-202">Jeśli brak możliwości, które procedury Konwersja może się nie powieść lub że może spowodować, że wystąpił nieobsługiwany wyjątek, muszą deklarować się `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="70481-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70481-203">Przykład</span><span class="sxs-lookup"><span data-stu-id="70481-203">Example</span></span>  
 <span data-ttu-id="70481-204">Poniższy przykład kodu wykorzystuje `Operator` instrukcji do zdefiniowania konturu struktura, która zawiera operator procedury dotyczące `And`, `Or`, `IsFalse`, i `IsTrue` operatorów.</span><span class="sxs-lookup"><span data-stu-id="70481-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="70481-205">`And` i `Or` każdego dwóch operandach typu `abc` i typ zwracany `abc`.</span><span class="sxs-lookup"><span data-stu-id="70481-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="70481-206">`IsFalse` i `IsTrue` każdego wykonać jeden operand typu `abc` i zwracać `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="70481-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="70481-207">Zezwalaj na te definicje kod wywołujący, aby użyć `And`, `AndAlso`, `Or`, i `OrElse` z argumentów operacji typu `abc`.</span><span class="sxs-lookup"><span data-stu-id="70481-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="70481-208">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70481-208">See Also</span></span>  
 [<span data-ttu-id="70481-209">IsFalse, operator</span><span class="sxs-lookup"><span data-stu-id="70481-209">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="70481-210">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="70481-210">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="70481-211">Widening</span><span class="sxs-lookup"><span data-stu-id="70481-211">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="70481-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="70481-212">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="70481-213">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="70481-213">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="70481-214">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="70481-214">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="70481-215">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="70481-215">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="70481-216">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="70481-216">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="70481-217">Instrukcje: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="70481-217">How to: Call an Operator Procedure</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="70481-218">Instrukcje: używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="70481-218">How to: Use a Class that Defines Operators</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
