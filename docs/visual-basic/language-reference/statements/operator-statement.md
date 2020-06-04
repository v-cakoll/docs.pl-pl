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
ms.openlocfilehash: f9e6ffe5a49715592399321ab471d73826e05d8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404398"
---
# <a name="operator-statement"></a><span data-ttu-id="8ca46-102">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="8ca46-102">Operator Statement</span></span>

<span data-ttu-id="8ca46-103">Deklaruje symbol operatora, argumenty operacji i kod, który definiuje procedurę operatora w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="8ca46-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="8ca46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ca46-104">Syntax</span></span>

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a><span data-ttu-id="8ca46-105">Części</span><span class="sxs-lookup"><span data-stu-id="8ca46-105">Parts</span></span>

`attrlist`  
<span data-ttu-id="8ca46-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8ca46-106">Optional.</span></span> <span data-ttu-id="8ca46-107">Zobacz [listę atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="8ca46-107">See [Attribute List](attribute-list.md).</span></span>

`Public`  
<span data-ttu-id="8ca46-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8ca46-108">Required.</span></span> <span data-ttu-id="8ca46-109">Wskazuje, że ta procedura operatora ma dostęp [publiczny](../modifiers/public.md) .</span><span class="sxs-lookup"><span data-stu-id="8ca46-109">Indicates that this operator procedure has [Public](../modifiers/public.md) access.</span></span>

`Overloads`  
<span data-ttu-id="8ca46-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8ca46-110">Optional.</span></span> <span data-ttu-id="8ca46-111">Zobacz [przeciążenia](../modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="8ca46-111">See [Overloads](../modifiers/overloads.md).</span></span>

`Shared`  
<span data-ttu-id="8ca46-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8ca46-112">Required.</span></span> <span data-ttu-id="8ca46-113">Wskazuje, że procedura operatora jest [wspólną](../modifiers/shared.md) procedurą.</span><span class="sxs-lookup"><span data-stu-id="8ca46-113">Indicates that this operator procedure is a [Shared](../modifiers/shared.md) procedure.</span></span>

`Shadows`  
<span data-ttu-id="8ca46-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8ca46-114">Optional.</span></span> <span data-ttu-id="8ca46-115">Zobacz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="8ca46-115">See [Shadows](../modifiers/shadows.md).</span></span>

`Widening`  
<span data-ttu-id="8ca46-116">Wymagane dla operatora konwersji, chyba że zostanie określony `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="8ca46-117">Wskazuje, że ta procedura operatora definiuje konwersję [rozszerzającą](../modifiers/widening.md) .</span><span class="sxs-lookup"><span data-stu-id="8ca46-117">Indicates that this operator procedure defines a [Widening](../modifiers/widening.md) conversion.</span></span> <span data-ttu-id="8ca46-118">Zobacz "rozszerzanie i zwężanie konwersji" na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="8ca46-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`Narrowing`  
<span data-ttu-id="8ca46-119">Wymagane dla operatora konwersji, chyba że zostanie określony `Widening` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="8ca46-120">Wskazuje, że ta procedura operatora definiuje [Zawężanie](../modifiers/narrowing.md) konwersji.</span><span class="sxs-lookup"><span data-stu-id="8ca46-120">Indicates that this operator procedure defines a [Narrowing](../modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="8ca46-121">Zobacz "rozszerzanie i zwężanie konwersji" na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="8ca46-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`operatorsymbol`  
<span data-ttu-id="8ca46-122">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8ca46-122">Required.</span></span> <span data-ttu-id="8ca46-123">Symbol lub identyfikator operatora, który definiuje procedura operatora.</span><span class="sxs-lookup"><span data-stu-id="8ca46-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>

`operand1`  
<span data-ttu-id="8ca46-124">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8ca46-124">Required.</span></span> <span data-ttu-id="8ca46-125">Nazwa i typ pojedynczego operandu operatora jednoargumentowego (w tym operatora konwersji) lub lewego operandu operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="8ca46-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>

`operand2`  
<span data-ttu-id="8ca46-126">Wymagane dla operatorów binarnych.</span><span class="sxs-lookup"><span data-stu-id="8ca46-126">Required for binary operators.</span></span> <span data-ttu-id="8ca46-127">Nazwa i typ prawnego operandu operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="8ca46-127">The name and type of the right operand of a binary operator.</span></span>

<span data-ttu-id="8ca46-128">`operand1`i `operand2` mają następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="8ca46-128">`operand1` and `operand2` have the following syntax and parts:</span></span>

`[ ByVal ] operandname [ As operandtype ]`

|<span data-ttu-id="8ca46-129">Część</span><span class="sxs-lookup"><span data-stu-id="8ca46-129">Part</span></span>|<span data-ttu-id="8ca46-130">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca46-130">Description</span></span>|
|----------|-----------------|
|`ByVal`|<span data-ttu-id="8ca46-131">Opcjonalne, ale mechanizm przekazywania musi być [ByVal](../modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="8ca46-131">Optional, but the passing mechanism must be [ByVal](../modifiers/byval.md).</span></span>|
|`operandname`|<span data-ttu-id="8ca46-132">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8ca46-132">Required.</span></span> <span data-ttu-id="8ca46-133">Nazwa zmiennej reprezentującej ten operand.</span><span class="sxs-lookup"><span data-stu-id="8ca46-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="8ca46-134">Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="8ca46-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`operandtype`|<span data-ttu-id="8ca46-135">Opcjonalne, chyba że `Option Strict` jest `On` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="8ca46-136">Typ danych tego operandu.</span><span class="sxs-lookup"><span data-stu-id="8ca46-136">Data type of this operand.</span></span>|

`type`  
<span data-ttu-id="8ca46-137">Opcjonalne, chyba że `Option Strict` jest `On` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="8ca46-138">Typ danych wartości zwracanej przez procedurę operatora.</span><span class="sxs-lookup"><span data-stu-id="8ca46-138">Data type of the value the operator procedure returns.</span></span>

`statements`  
<span data-ttu-id="8ca46-139">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8ca46-139">Optional.</span></span> <span data-ttu-id="8ca46-140">Blok instrukcji wykonywanych przez procedurę operatora.</span><span class="sxs-lookup"><span data-stu-id="8ca46-140">Block of statements that the operator procedure runs.</span></span>

`returnvalue`  
<span data-ttu-id="8ca46-141">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8ca46-141">Required.</span></span> <span data-ttu-id="8ca46-142">Wartość, którą procedura operatora zwraca do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8ca46-142">The value that the operator procedure returns to the calling code.</span></span>

<span data-ttu-id="8ca46-143">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="8ca46-143">`End` `Operator`</span></span>  
<span data-ttu-id="8ca46-144">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8ca46-144">Required.</span></span> <span data-ttu-id="8ca46-145">Kończy definicję tej procedury operatora.</span><span class="sxs-lookup"><span data-stu-id="8ca46-145">Terminates the definition of this operator procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ca46-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ca46-146">Remarks</span></span>

<span data-ttu-id="8ca46-147">Można używać `Operator` tylko w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="8ca46-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="8ca46-148">Oznacza to, że *kontekst deklaracji* dla operatora nie może być plikiem źródłowym, przestrzenią nazw, modułem, interfejsem, procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="8ca46-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="8ca46-149">Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8ca46-149">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="8ca46-150">Wszystkie operatory muszą być `Public Shared` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="8ca46-151">Nie można określić `ByRef` , `Optional` , lub `ParamArray` dla obu operandów.</span><span class="sxs-lookup"><span data-stu-id="8ca46-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>

<span data-ttu-id="8ca46-152">Nie można użyć symbolu operatora lub identyfikatora do przechowywania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="8ca46-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="8ca46-153">Musisz użyć `Return` instrukcji i określić wartość.</span><span class="sxs-lookup"><span data-stu-id="8ca46-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="8ca46-154">Dowolna liczba `Return` instrukcji może pojawić się w dowolnym miejscu w procedurze.</span><span class="sxs-lookup"><span data-stu-id="8ca46-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>

<span data-ttu-id="8ca46-155">Definiowanie operatora w ten sposób jest nazywane *przeciążeniem operatora*, niezależnie od tego, czy jest używane `Overloads` słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8ca46-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="8ca46-156">W poniższej tabeli wymieniono operatory, które można zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="8ca46-156">The following table lists the operators you can define.</span></span>

|<span data-ttu-id="8ca46-157">Typ</span><span class="sxs-lookup"><span data-stu-id="8ca46-157">Type</span></span>|<span data-ttu-id="8ca46-158">Operatory</span><span class="sxs-lookup"><span data-stu-id="8ca46-158">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="8ca46-159">Jednoargumentowy</span><span class="sxs-lookup"><span data-stu-id="8ca46-159">Unary</span></span>|<span data-ttu-id="8ca46-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="8ca46-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="8ca46-161">Binarne</span><span class="sxs-lookup"><span data-stu-id="8ca46-161">Binary</span></span>|<span data-ttu-id="8ca46-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="8ca46-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="8ca46-163">Konwersja (Jednoargumentowa)</span><span class="sxs-lookup"><span data-stu-id="8ca46-163">Conversion (unary)</span></span>|`CType`|

<span data-ttu-id="8ca46-164">Należy zauważyć, że `=` operator na liście Binary jest operatorem porównania, a nie operatorem przypisania.</span><span class="sxs-lookup"><span data-stu-id="8ca46-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

<span data-ttu-id="8ca46-165">Podczas definiowania należy `CType` określić albo `Widening` lub `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>

## <a name="matched-pairs"></a><span data-ttu-id="8ca46-166">Dopasowane pary</span><span class="sxs-lookup"><span data-stu-id="8ca46-166">Matched Pairs</span></span>

<span data-ttu-id="8ca46-167">Należy zdefiniować określone operatory jako dopasowane pary.</span><span class="sxs-lookup"><span data-stu-id="8ca46-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="8ca46-168">W przypadku zdefiniowania dowolnego operatora takiej pary należy zdefiniować również pozostałe.</span><span class="sxs-lookup"><span data-stu-id="8ca46-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="8ca46-169">Dopasowane pary są następujące:</span><span class="sxs-lookup"><span data-stu-id="8ca46-169">The matched pairs are the following:</span></span>

- <span data-ttu-id="8ca46-170">`=` i `<>`</span><span class="sxs-lookup"><span data-stu-id="8ca46-170">`=` and `<>`</span></span>

- <span data-ttu-id="8ca46-171">`>` i `<`</span><span class="sxs-lookup"><span data-stu-id="8ca46-171">`>` and `<`</span></span>

- <span data-ttu-id="8ca46-172">`>=` i `<=`</span><span class="sxs-lookup"><span data-stu-id="8ca46-172">`>=` and `<=`</span></span>

- <span data-ttu-id="8ca46-173">`IsTrue` i `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="8ca46-173">`IsTrue` and `IsFalse`</span></span>

## <a name="data-type-restrictions"></a><span data-ttu-id="8ca46-174">Ograniczenia dotyczące typów danych</span><span class="sxs-lookup"><span data-stu-id="8ca46-174">Data Type Restrictions</span></span>

<span data-ttu-id="8ca46-175">Każdy zdefiniowany operator musi zawierać klasę lub strukturę, w których ją zdefiniujesz.</span><span class="sxs-lookup"><span data-stu-id="8ca46-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="8ca46-176">Oznacza to, że Klasa lub struktura muszą występować jako typ danych następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="8ca46-176">This means that the class or structure must appear as the data type of the following:</span></span>

- <span data-ttu-id="8ca46-177">Operand operatora jednoargumentowego.</span><span class="sxs-lookup"><span data-stu-id="8ca46-177">The operand of a unary operator.</span></span>

- <span data-ttu-id="8ca46-178">Co najmniej jeden operand operatora binarnego.</span><span class="sxs-lookup"><span data-stu-id="8ca46-178">At least one of the operands of a binary operator.</span></span>

- <span data-ttu-id="8ca46-179">Operand lub zwracany typ operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="8ca46-179">Either the operand or the return type of a conversion operator.</span></span>

 <span data-ttu-id="8ca46-180">Niektóre operatory mają dodatkowe ograniczenia dotyczące typów danych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8ca46-180">Certain operators have additional data type restrictions, as follows:</span></span>

- <span data-ttu-id="8ca46-181">Jeśli zdefiniujesz `IsTrue` Operatory i `IsFalse` , muszą one zwracać `Boolean` Typ.</span><span class="sxs-lookup"><span data-stu-id="8ca46-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>

- <span data-ttu-id="8ca46-182">Jeśli zdefiniujesz `<<` Operatory i `>>` , muszą one określić `Integer` Typ dla `operandtype` elementu `operand2` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>

<span data-ttu-id="8ca46-183">Zwracany typ nie musi odpowiadać typowi żadnego operandu.</span><span class="sxs-lookup"><span data-stu-id="8ca46-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="8ca46-184">Na przykład operator porównania, taki jak `=` lub, `<>` może zwrócić `Boolean` nawet wtedy, gdy żaden operand nie jest `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>

## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="8ca46-185">Operatory logiczne i bitowe</span><span class="sxs-lookup"><span data-stu-id="8ca46-185">Logical and Bitwise Operators</span></span>

<span data-ttu-id="8ca46-186">`And`Operatory, `Or` , `Not` i `Xor` mogą wykonywać operacje logiczne lub bitowe w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8ca46-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="8ca46-187">Jeśli jednak zdefiniujesz jeden z tych operatorów w klasie lub strukturze, możesz zdefiniować tylko jej operację bitową.</span><span class="sxs-lookup"><span data-stu-id="8ca46-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>

<span data-ttu-id="8ca46-188">Nie można zdefiniować `AndAlso` operatora bezpośrednio przy użyciu `Operator` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8ca46-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="8ca46-189">Można jednak użyć, `AndAlso` jeśli spełniono następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="8ca46-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>

- <span data-ttu-id="8ca46-190">Zdefiniowano `And` te same typy operandów, których chcesz użyć dla `AndAlso` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>

- <span data-ttu-id="8ca46-191">Twoja definicja `And` zwraca ten sam typ co Klasa lub struktura, w której została zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="8ca46-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>

- <span data-ttu-id="8ca46-192">Zdefiniowano `IsFalse` operator na klasie lub strukturze, na których zdefiniowano `And` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>

<span data-ttu-id="8ca46-193">Analogicznie, można użyć, `OrElse` Jeśli zdefiniowano `Or` dla tych samych operandów, z typem zwracanym klasy lub struktury i zdefiniowanej `IsTrue` na klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="8ca46-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>

## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="8ca46-194">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="8ca46-194">Widening and Narrowing Conversions</span></span>

<span data-ttu-id="8ca46-195">*Konwersja rozszerzająca* zawsze powiedzie się w czasie wykonywania, podczas gdy *Konwersja wąskiego* może zakończyć się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8ca46-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="8ca46-196">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="8ca46-196">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="8ca46-197">Jeśli deklarujesz procedurę konwersji `Widening` , kod procedury nie może generować żadnych błędów.</span><span class="sxs-lookup"><span data-stu-id="8ca46-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="8ca46-198">Oznacza to, że:</span><span class="sxs-lookup"><span data-stu-id="8ca46-198">This means the following:</span></span>

- <span data-ttu-id="8ca46-199">Musi zawsze zwracać prawidłową wartość typu `type` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-199">It must always return a valid value of type `type`.</span></span>

- <span data-ttu-id="8ca46-200">Musi obsługiwać wszystkie możliwe wyjątki i inne warunki błędu.</span><span class="sxs-lookup"><span data-stu-id="8ca46-200">It must handle all possible exceptions and other error conditions.</span></span>

- <span data-ttu-id="8ca46-201">Musi obsłużyć wszelkie błędy zwracane przez wszystkie procedury, które wywołuje.</span><span class="sxs-lookup"><span data-stu-id="8ca46-201">It must handle any error returns from any procedures it calls.</span></span>

<span data-ttu-id="8ca46-202">Jeśli istnieje jakakolwiek możliwość, że procedura konwersji może zakończyć się niepowodzeniem lub może spowodować nieobsługiwany wyjątek, należy zadeklarować ją jako `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>

## <a name="example"></a><span data-ttu-id="8ca46-203">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ca46-203">Example</span></span>

<span data-ttu-id="8ca46-204">Poniższy przykład kodu używa `Operator` instrukcji do definiowania konspektu struktury, która zawiera procedury operatorów dla `And` `Or` operatorów,, `IsFalse` i `IsTrue` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="8ca46-205">`And`i `Or` każdy z nich przyjmuje dwa operandy typu `abc` i zwracanego typu `abc` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="8ca46-206">`IsFalse`i `IsTrue` każdy z nich przyjmuje jeden operand typu `abc` i Return `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="8ca46-207">Te definicje umożliwiają wywołującemu kod użycie `And` , `AndAlso` , `Or` i `OrElse` z operandami typu `abc` .</span><span class="sxs-lookup"><span data-stu-id="8ca46-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a><span data-ttu-id="8ca46-208">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ca46-208">See also</span></span>

- [<span data-ttu-id="8ca46-209">IsFalse, operator</span><span class="sxs-lookup"><span data-stu-id="8ca46-209">IsFalse Operator</span></span>](../operators/isfalse-operator.md)
- [<span data-ttu-id="8ca46-210">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="8ca46-210">IsTrue Operator</span></span>](../operators/istrue-operator.md)
- [<span data-ttu-id="8ca46-211">Widening</span><span class="sxs-lookup"><span data-stu-id="8ca46-211">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="8ca46-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="8ca46-212">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="8ca46-213">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="8ca46-213">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="8ca46-214">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="8ca46-214">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="8ca46-215">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="8ca46-215">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="8ca46-216">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="8ca46-216">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="8ca46-217">Instrukcje: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="8ca46-217">How to: Call an Operator Procedure</span></span>](../../programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="8ca46-218">Instrukcje: używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="8ca46-218">How to: Use a Class that Defines Operators</span></span>](../../programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
