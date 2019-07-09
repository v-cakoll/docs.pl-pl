---
title: Składnia używana przez właściwość DebugView (C#)
description: W tym artykule opisano specjalnej składni używana przez właściwość programu DebugView do produkcji reprezentację ciągu drzew wyrażeń
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: ba695fc808108c49a4eee3c70a305b24c91769d8
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661715"
---
# <a name="debugview-syntax"></a><span data-ttu-id="828fb-103">`DebugView` Składnia</span><span class="sxs-lookup"><span data-stu-id="828fb-103">`DebugView` syntax</span></span>

<span data-ttu-id="828fb-104">`DebugView` (Dostępne tylko wtedy, gdy debugowanie) dostarcza renderowania ciągu, drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="828fb-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="828fb-105">Najczęściej składnia jest dość prosta zrozumieć; szczególne przypadki są opisane w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="828fb-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="828fb-106">Każdy przykład następuje komentarz bloku, zawierającego `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="828fb-106">Each example is followed by a block comment, containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="828fb-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="828fb-107">ParameterExpression</span></span>

<span data-ttu-id="828fb-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> nazwy zmiennych są wyświetlane z `$` symboli na początku.</span><span class="sxs-lookup"><span data-stu-id="828fb-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="828fb-109">Jeśli parametr nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `$var1` lub `$var2`.</span><span class="sxs-lookup"><span data-stu-id="828fb-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="828fb-110">Przykłady</span><span class="sxs-lookup"><span data-stu-id="828fb-110">Examples</span></span>

```csharp
ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");
/*
    $num
*/

ParameterExpression numParam =  Expression.Parameter(typeof(int));
/*
    $var1
*/
```

## <a name="constantexpression"></a><span data-ttu-id="828fb-111">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="828fb-111">ConstantExpression</span></span>

<span data-ttu-id="828fb-112">Dla <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> obiekty reprezentujące wartości całkowitych, ciągów i `null`, jest wyświetlana wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="828fb-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="828fb-113">Dla typów numerycznych, które mają standardowa sufiksy jako literały języka C# sufiks jest dodawany do wartości.</span><span class="sxs-lookup"><span data-stu-id="828fb-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="828fb-114">W poniższej tabeli przedstawiono sufiksy skojarzone z różnych typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="828fb-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="828fb-115">Typ</span><span class="sxs-lookup"><span data-stu-id="828fb-115">Type</span></span> | <span data-ttu-id="828fb-116">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="828fb-116">Keyword</span></span> | <span data-ttu-id="828fb-117">Suffix</span><span class="sxs-lookup"><span data-stu-id="828fb-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="828fb-118">uint</span><span class="sxs-lookup"><span data-stu-id="828fb-118">uint</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="828fb-119">U</span><span class="sxs-lookup"><span data-stu-id="828fb-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="828fb-120">long</span><span class="sxs-lookup"><span data-stu-id="828fb-120">long</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="828fb-121">L</span><span class="sxs-lookup"><span data-stu-id="828fb-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="828fb-122">ulong</span><span class="sxs-lookup"><span data-stu-id="828fb-122">ulong</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="828fb-123">UL</span><span class="sxs-lookup"><span data-stu-id="828fb-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="828fb-124">double</span><span class="sxs-lookup"><span data-stu-id="828fb-124">double</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="828fb-125">D</span><span class="sxs-lookup"><span data-stu-id="828fb-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="828fb-126">float</span><span class="sxs-lookup"><span data-stu-id="828fb-126">float</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="828fb-127">F</span><span class="sxs-lookup"><span data-stu-id="828fb-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="828fb-128">decimal</span><span class="sxs-lookup"><span data-stu-id="828fb-128">decimal</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="828fb-129">M</span><span class="sxs-lookup"><span data-stu-id="828fb-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="828fb-130">Przykłady</span><span class="sxs-lookup"><span data-stu-id="828fb-130">Examples</span></span>

```csharp
int num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10
*/

double num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10D
*/
```

## <a name="blockexpression"></a><span data-ttu-id="828fb-131">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="828fb-131">BlockExpression</span></span>

<span data-ttu-id="828fb-132">Jeśli typ <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> obiekt różni się od typu ostatniego wyrażenia w bloku, typ jest wyświetlany w nawiasach kątowych (`<` i `>`).</span><span class="sxs-lookup"><span data-stu-id="828fb-132">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="828fb-133">W przeciwnym razie typ <xref:System.Linq.Expressions.BlockExpression> obiektu nie jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="828fb-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="828fb-134">Przykłady</span><span class="sxs-lookup"><span data-stu-id="828fb-134">Examples</span></span>

```csharp
BlockExpression block = Expression.Block(Expression.Constant("test"));
/*
    .Block() {
        "test"
    }
*/

BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));
/*
    .Block<System.Object>() {
        "test"
    }
*/
```

## <a name="lambdaexpression"></a><span data-ttu-id="828fb-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="828fb-135">LambdaExpression</span></span>

<span data-ttu-id="828fb-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> obiekty są wyświetlane wraz z ich typy delegowane.</span><span class="sxs-lookup"><span data-stu-id="828fb-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="828fb-137">Jeśli wyrażenie lambda ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Lambda1` lub `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="828fb-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="828fb-138">Przykłady</span><span class="sxs-lookup"><span data-stu-id="828fb-138">Examples</span></span>

```csharp
LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));
/*
    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
        1
    }
*/

LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);
/*
    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
        1
    }
*/
```

## <a name="labelexpression"></a><span data-ttu-id="828fb-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="828fb-139">LabelExpression</span></span>

<span data-ttu-id="828fb-140">Jeśli określisz wartość domyślną dla <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> obiektu, ta wartość jest poprzedzana <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="828fb-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="828fb-141">`.Label` Token wskazuje początek etykiety.</span><span class="sxs-lookup"><span data-stu-id="828fb-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="828fb-142">`.LabelTarget` Token wskazuje docelowy obiektu docelowego, aby przejść do.</span><span class="sxs-lookup"><span data-stu-id="828fb-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="828fb-143">Jeśli etykieta nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Label1` lub `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="828fb-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="828fb-144">Przykłady</span><span class="sxs-lookup"><span data-stu-id="828fb-144">Examples</span></span>

```csharp
LabelTarget target = Expression.Label(typeof(int), "SampleLabel");
BlockExpression block = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
);
/*
    .Block() {
        .Goto SampleLabel { 0 };
        .Label
            -1
        .LabelTarget SampleLabel:
    }
*/

LabelTarget target = Expression.Label();
BlockExpression block = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
);
/*
    .Block() {
        .Goto #Label1 { };
        .Label
        .LabelTarget #Label1:
    }
*/
```

## <a name="checked-operators"></a><span data-ttu-id="828fb-145">Operatory zaznaczone</span><span class="sxs-lookup"><span data-stu-id="828fb-145">Checked Operators</span></span>

<span data-ttu-id="828fb-146">Operatory sprawdzane są wyświetlane z `#` symbol przed operatora.</span><span class="sxs-lookup"><span data-stu-id="828fb-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="828fb-147">Na przykład operator dodawania zaznaczone jest wyświetlany jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="828fb-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="828fb-148">Przykłady</span><span class="sxs-lookup"><span data-stu-id="828fb-148">Examples</span></span>

```csharp
Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));
/*
    1 #+ 2
*/

Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));
/*
    #(System.Int32)10D
*/
```
