---
title: Operator — Instrukcja (Visual Basic)
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
ms.openlocfilehash: c4fae40992fa665121aff637ae427ef0cafbf547
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582381"
---
# <a name="operator-statement"></a><span data-ttu-id="22efa-102">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="22efa-102">Operator Statement</span></span>

<span data-ttu-id="22efa-103">Deklaruje symbol operatora, argumenty operacji i kod, który definiuje procedurę operatora w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="22efa-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="22efa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22efa-104">Syntax</span></span>

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a><span data-ttu-id="22efa-105">Części</span><span class="sxs-lookup"><span data-stu-id="22efa-105">Parts</span></span>

`attrlist`  
<span data-ttu-id="22efa-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="22efa-106">Optional.</span></span> <span data-ttu-id="22efa-107">Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="22efa-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

`Public`  
<span data-ttu-id="22efa-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="22efa-108">Required.</span></span> <span data-ttu-id="22efa-109">Wskazuje, że ta procedura operatora ma dostęp [publiczny](../../../visual-basic/language-reference/modifiers/public.md) .</span><span class="sxs-lookup"><span data-stu-id="22efa-109">Indicates that this operator procedure has [Public](../../../visual-basic/language-reference/modifiers/public.md) access.</span></span>

`Overloads`  
<span data-ttu-id="22efa-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="22efa-110">Optional.</span></span> <span data-ttu-id="22efa-111">Zobacz [przeciążenia](../../../visual-basic/language-reference/modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="22efa-111">See [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span></span>

`Shared`  
<span data-ttu-id="22efa-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="22efa-112">Required.</span></span> <span data-ttu-id="22efa-113">Wskazuje, że procedura operatora jest [wspólną](../../../visual-basic/language-reference/modifiers/shared.md) procedurą.</span><span class="sxs-lookup"><span data-stu-id="22efa-113">Indicates that this operator procedure is a [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedure.</span></span>

`Shadows`  
<span data-ttu-id="22efa-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="22efa-114">Optional.</span></span> <span data-ttu-id="22efa-115">Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="22efa-115">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

`Widening`  
<span data-ttu-id="22efa-116">Wymagane dla operatora konwersji, chyba że zostanie określona `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="22efa-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="22efa-117">Wskazuje, że ta procedura operatora definiuje konwersję [rozszerzającą](../../../visual-basic/language-reference/modifiers/widening.md) .</span><span class="sxs-lookup"><span data-stu-id="22efa-117">Indicates that this operator procedure defines a [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion.</span></span> <span data-ttu-id="22efa-118">Zobacz "rozszerzanie i zwężanie konwersji" na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="22efa-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`Narrowing`  
<span data-ttu-id="22efa-119">Wymagane dla operatora konwersji, chyba że zostanie określona `Widening`.</span><span class="sxs-lookup"><span data-stu-id="22efa-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="22efa-120">Wskazuje, że ta procedura operatora definiuje [Zawężanie](../../../visual-basic/language-reference/modifiers/narrowing.md) konwersji.</span><span class="sxs-lookup"><span data-stu-id="22efa-120">Indicates that this operator procedure defines a [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="22efa-121">Zobacz "rozszerzanie i zwężanie konwersji" na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="22efa-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`operatorsymbol`  
<span data-ttu-id="22efa-122">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="22efa-122">Required.</span></span> <span data-ttu-id="22efa-123">Symbol lub identyfikator operatora, który definiuje procedura operatora.</span><span class="sxs-lookup"><span data-stu-id="22efa-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>

`operand1`  
<span data-ttu-id="22efa-124">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="22efa-124">Required.</span></span> <span data-ttu-id="22efa-125">Nazwa i typ pojedynczego operandu operatora jednoargumentowego (w tym operatora konwersji) lub lewego operandu operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="22efa-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>

`operand2`  
<span data-ttu-id="22efa-126">Wymagane dla operatorów binarnych.</span><span class="sxs-lookup"><span data-stu-id="22efa-126">Required for binary operators.</span></span> <span data-ttu-id="22efa-127">Nazwa i typ prawnego operandu operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="22efa-127">The name and type of the right operand of a binary operator.</span></span>

<span data-ttu-id="22efa-128">`operand1` i `operand2` mają następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="22efa-128">`operand1` and `operand2` have the following syntax and parts:</span></span>

`[ ByVal ] operandname [ As operandtype ]`

|<span data-ttu-id="22efa-129">Części</span><span class="sxs-lookup"><span data-stu-id="22efa-129">Part</span></span>|<span data-ttu-id="22efa-130">Opis</span><span class="sxs-lookup"><span data-stu-id="22efa-130">Description</span></span>|
|----------|-----------------|
|`ByVal`|<span data-ttu-id="22efa-131">Opcjonalne, ale mechanizm przekazywania musi być [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="22efa-131">Optional, but the passing mechanism must be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>|
|`operandname`|<span data-ttu-id="22efa-132">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="22efa-132">Required.</span></span> <span data-ttu-id="22efa-133">Nazwa zmiennej reprezentującej ten operand.</span><span class="sxs-lookup"><span data-stu-id="22efa-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="22efa-134">Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="22efa-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`operandtype`|<span data-ttu-id="22efa-135">Opcjonalne, chyba że `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="22efa-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="22efa-136">Typ danych tego operandu.</span><span class="sxs-lookup"><span data-stu-id="22efa-136">Data type of this operand.</span></span>|

`type`  
<span data-ttu-id="22efa-137">Opcjonalne, chyba że `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="22efa-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="22efa-138">Typ danych wartości zwracanej przez procedurę operatora.</span><span class="sxs-lookup"><span data-stu-id="22efa-138">Data type of the value the operator procedure returns.</span></span>

`statements`  
<span data-ttu-id="22efa-139">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="22efa-139">Optional.</span></span> <span data-ttu-id="22efa-140">Blok instrukcji wykonywanych przez procedurę operatora.</span><span class="sxs-lookup"><span data-stu-id="22efa-140">Block of statements that the operator procedure runs.</span></span>

`returnvalue`  
<span data-ttu-id="22efa-141">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="22efa-141">Required.</span></span> <span data-ttu-id="22efa-142">Wartość, którą procedura operatora zwraca do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="22efa-142">The value that the operator procedure returns to the calling code.</span></span>

<span data-ttu-id="22efa-143">`End``Operator`</span><span class="sxs-lookup"><span data-stu-id="22efa-143">`End` `Operator`</span></span>  
<span data-ttu-id="22efa-144">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="22efa-144">Required.</span></span> <span data-ttu-id="22efa-145">Kończy definicję tej procedury operatora.</span><span class="sxs-lookup"><span data-stu-id="22efa-145">Terminates the definition of this operator procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="22efa-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22efa-146">Remarks</span></span>

<span data-ttu-id="22efa-147">@No__t_0 można używać tylko w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="22efa-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="22efa-148">Oznacza to, że *kontekst deklaracji* dla operatora nie może być plikiem źródłowym, przestrzenią nazw, modułem, interfejsem, procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="22efa-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="22efa-149">Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="22efa-149">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="22efa-150">Wszystkie operatory muszą być `Public Shared`.</span><span class="sxs-lookup"><span data-stu-id="22efa-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="22efa-151">Dla każdego operandu nie można określić `ByRef`, `Optional` lub `ParamArray`.</span><span class="sxs-lookup"><span data-stu-id="22efa-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>

<span data-ttu-id="22efa-152">Nie można użyć symbolu operatora lub identyfikatora do przechowywania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="22efa-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="22efa-153">Należy użyć instrukcji `Return` i określić wartość.</span><span class="sxs-lookup"><span data-stu-id="22efa-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="22efa-154">Dowolna liczba instrukcji `Return` może występować w dowolnym miejscu procedury.</span><span class="sxs-lookup"><span data-stu-id="22efa-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>

<span data-ttu-id="22efa-155">Definiowanie operatora w ten sposób jest nazywane *przeciążeniem operatora*, niezależnie od tego, czy jest używane słowo kluczowe `Overloads`.</span><span class="sxs-lookup"><span data-stu-id="22efa-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="22efa-156">W poniższej tabeli wymieniono operatory, które można zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="22efa-156">The following table lists the operators you can define.</span></span>

|<span data-ttu-id="22efa-157">Typ</span><span class="sxs-lookup"><span data-stu-id="22efa-157">Type</span></span>|<span data-ttu-id="22efa-158">Operatory</span><span class="sxs-lookup"><span data-stu-id="22efa-158">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="22efa-159">Jednostk</span><span class="sxs-lookup"><span data-stu-id="22efa-159">Unary</span></span>|<span data-ttu-id="22efa-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="22efa-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="22efa-161">plików binarnych</span><span class="sxs-lookup"><span data-stu-id="22efa-161">Binary</span></span>|<span data-ttu-id="22efa-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, 0, 1, 2, 3, 4, 5 , 6, 7, 8 9</span><span class="sxs-lookup"><span data-stu-id="22efa-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="22efa-163">Konwersja (Jednoargumentowa)</span><span class="sxs-lookup"><span data-stu-id="22efa-163">Conversion (unary)</span></span>|`CType`|

<span data-ttu-id="22efa-164">Należy zauważyć, że operator `=` na liście elementów binarnych jest operatorem porównania, a nie operatorem przypisania.</span><span class="sxs-lookup"><span data-stu-id="22efa-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

<span data-ttu-id="22efa-165">Podczas definiowania `CType` należy określić `Widening` lub `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="22efa-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>

## <a name="matched-pairs"></a><span data-ttu-id="22efa-166">Dopasowane pary</span><span class="sxs-lookup"><span data-stu-id="22efa-166">Matched Pairs</span></span>

<span data-ttu-id="22efa-167">Należy zdefiniować określone operatory jako dopasowane pary.</span><span class="sxs-lookup"><span data-stu-id="22efa-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="22efa-168">W przypadku zdefiniowania dowolnego operatora takiej pary należy zdefiniować również pozostałe.</span><span class="sxs-lookup"><span data-stu-id="22efa-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="22efa-169">Dopasowane pary są następujące:</span><span class="sxs-lookup"><span data-stu-id="22efa-169">The matched pairs are the following:</span></span>

- <span data-ttu-id="22efa-170">`=` i `<>`</span><span class="sxs-lookup"><span data-stu-id="22efa-170">`=` and `<>`</span></span>

- <span data-ttu-id="22efa-171">`>` i `<`</span><span class="sxs-lookup"><span data-stu-id="22efa-171">`>` and `<`</span></span>

- <span data-ttu-id="22efa-172">`>=` i `<=`</span><span class="sxs-lookup"><span data-stu-id="22efa-172">`>=` and `<=`</span></span>

- <span data-ttu-id="22efa-173">`IsTrue` i `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="22efa-173">`IsTrue` and `IsFalse`</span></span>

## <a name="data-type-restrictions"></a><span data-ttu-id="22efa-174">Ograniczenia dotyczące typów danych</span><span class="sxs-lookup"><span data-stu-id="22efa-174">Data Type Restrictions</span></span>

<span data-ttu-id="22efa-175">Każdy zdefiniowany operator musi zawierać klasę lub strukturę, w których ją zdefiniujesz.</span><span class="sxs-lookup"><span data-stu-id="22efa-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="22efa-176">Oznacza to, że Klasa lub struktura muszą występować jako typ danych następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="22efa-176">This means that the class or structure must appear as the data type of the following:</span></span>

- <span data-ttu-id="22efa-177">Operand operatora jednoargumentowego.</span><span class="sxs-lookup"><span data-stu-id="22efa-177">The operand of a unary operator.</span></span>

- <span data-ttu-id="22efa-178">Co najmniej jeden operand operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="22efa-178">At least one of the operands of a binary operator.</span></span>

- <span data-ttu-id="22efa-179">Operand lub zwracany typ operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="22efa-179">Either the operand or the return type of a conversion operator.</span></span>

 <span data-ttu-id="22efa-180">Niektóre operatory mają dodatkowe ograniczenia dotyczące typów danych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="22efa-180">Certain operators have additional data type restrictions, as follows:</span></span>

- <span data-ttu-id="22efa-181">Jeśli zdefiniujesz operatory `IsTrue` i `IsFalse`, muszą one zwracać typ `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="22efa-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>

- <span data-ttu-id="22efa-182">Jeśli zdefiniujesz operatory `<<` i `>>`, muszą one określić typ `Integer` dla `operandtype` `operand2`.</span><span class="sxs-lookup"><span data-stu-id="22efa-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>

<span data-ttu-id="22efa-183">Zwracany typ nie musi odpowiadać typowi żadnego operandu.</span><span class="sxs-lookup"><span data-stu-id="22efa-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="22efa-184">Na przykład operator porównania, taki jak `=` lub `<>`, może zwrócić `Boolean` nawet wtedy, gdy żaden operand nie jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="22efa-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>

## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="22efa-185">Operatory logiczne i bitowe</span><span class="sxs-lookup"><span data-stu-id="22efa-185">Logical and Bitwise Operators</span></span>

<span data-ttu-id="22efa-186">Operatory `And`, `Or`, `Not` i `Xor` mogą wykonywać operacje logiczne lub bitowe w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="22efa-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="22efa-187">Jeśli jednak zdefiniujesz jeden z tych operatorów w klasie lub strukturze, możesz zdefiniować tylko jej operację bitową.</span><span class="sxs-lookup"><span data-stu-id="22efa-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>

<span data-ttu-id="22efa-188">Nie można zdefiniować operatora `AndAlso` bezpośrednio przy użyciu instrukcji `Operator`.</span><span class="sxs-lookup"><span data-stu-id="22efa-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="22efa-189">Można jednak użyć `AndAlso`, jeśli spełniono następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="22efa-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>

- <span data-ttu-id="22efa-190">Zdefiniowano `And` w tych samych typach operandów, które mają być używane dla `AndAlso`.</span><span class="sxs-lookup"><span data-stu-id="22efa-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>

- <span data-ttu-id="22efa-191">Definicja `And` zwraca ten sam typ co Klasa lub struktura, w której została zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="22efa-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>

- <span data-ttu-id="22efa-192">Zdefiniowano operator `IsFalse` na klasie lub strukturze, na których zdefiniowano `And`.</span><span class="sxs-lookup"><span data-stu-id="22efa-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>

<span data-ttu-id="22efa-193">Podobnie, można użyć `OrElse`, jeśli zdefiniowano `Or` dla tych samych operandów, z typem zwracanym klasy lub struktury, a zdefiniowano `IsTrue` na klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="22efa-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>

## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="22efa-194">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="22efa-194">Widening and Narrowing Conversions</span></span>

<span data-ttu-id="22efa-195">*Konwersja rozszerzająca* zawsze powiedzie się w czasie wykonywania, podczas gdy *Konwersja wąskiego* może zakończyć się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="22efa-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="22efa-196">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="22efa-196">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="22efa-197">Jeśli deklarujesz procedurę konwersji do `Widening`, kod procedury nie może generować żadnych błędów.</span><span class="sxs-lookup"><span data-stu-id="22efa-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="22efa-198">Oznacza to następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="22efa-198">This means the following:</span></span>

- <span data-ttu-id="22efa-199">Musi zawsze zwracać prawidłową wartość typu `type`.</span><span class="sxs-lookup"><span data-stu-id="22efa-199">It must always return a valid value of type `type`.</span></span>

- <span data-ttu-id="22efa-200">Musi obsługiwać wszystkie możliwe wyjątki i inne warunki błędu.</span><span class="sxs-lookup"><span data-stu-id="22efa-200">It must handle all possible exceptions and other error conditions.</span></span>

- <span data-ttu-id="22efa-201">Musi obsłużyć wszelkie błędy zwracane przez wszystkie procedury, które wywołuje.</span><span class="sxs-lookup"><span data-stu-id="22efa-201">It must handle any error returns from any procedures it calls.</span></span>

<span data-ttu-id="22efa-202">Jeśli istnieje jakakolwiek możliwość, że procedura konwersji może się nie powieść lub że może to spowodować nieobsługiwany wyjątek, należy zadeklarować ją jako `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="22efa-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>

## <a name="example"></a><span data-ttu-id="22efa-203">Przykład</span><span class="sxs-lookup"><span data-stu-id="22efa-203">Example</span></span>

<span data-ttu-id="22efa-204">Poniższy przykład kodu używa instrukcji `Operator` do definiowania konspektu struktury, która zawiera procedury operatorów dla operatorów `And`, `Or`, `IsFalse` i `IsTrue`.</span><span class="sxs-lookup"><span data-stu-id="22efa-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="22efa-205">`And` i `Or` każda z nich przyjmuje dwa operandy typu `abc` i zwracany typ `abc`.</span><span class="sxs-lookup"><span data-stu-id="22efa-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="22efa-206">`IsFalse` i `IsTrue` każda z nich przyjmuje jeden operand typu `abc` i zwraca `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="22efa-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="22efa-207">Te definicje umożliwiają wywołującemu kod używanie `And`, `AndAlso`, `Or` i `OrElse` z operandami typu `abc`.</span><span class="sxs-lookup"><span data-stu-id="22efa-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a><span data-ttu-id="22efa-208">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22efa-208">See also</span></span>

- [<span data-ttu-id="22efa-209">IsFalse, operator</span><span class="sxs-lookup"><span data-stu-id="22efa-209">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="22efa-210">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="22efa-210">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="22efa-211">Widening</span><span class="sxs-lookup"><span data-stu-id="22efa-211">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="22efa-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="22efa-212">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="22efa-213">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="22efa-213">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="22efa-214">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="22efa-214">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="22efa-215">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="22efa-215">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="22efa-216">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="22efa-216">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="22efa-217">Instrukcje: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="22efa-217">How to: Call an Operator Procedure</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="22efa-218">Instrukcje: używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="22efa-218">How to: Use a Class that Defines Operators</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
