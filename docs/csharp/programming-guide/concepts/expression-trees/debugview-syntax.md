---
title: Składnia używana przez właściwość DebugView (C#)
description: Opisuje specjalną składnię używaną przez DebugView właściwość do tworzenia reprezentacji ciąg drzew wyrażeń
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: ba695fc808108c49a4eee3c70a305b24c91769d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "67661715"
---
# <a name="debugview-syntax"></a><span data-ttu-id="75820-103">`DebugView`Składni</span><span class="sxs-lookup"><span data-stu-id="75820-103">`DebugView` syntax</span></span>

<span data-ttu-id="75820-104">Właściwość `DebugView` (dostępna tylko podczas debugowania) zapewnia renderowanie ciągdrzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="75820-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="75820-105">Większość składni jest dość prosta do zrozumienia; przypadki szczególne opisano w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="75820-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="75820-106">Po każdym przykładzie następuje komentarz `DebugView`bloku, zawierający plik .</span><span class="sxs-lookup"><span data-stu-id="75820-106">Each example is followed by a block comment, containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="75820-107">Parameterexpression</span><span class="sxs-lookup"><span data-stu-id="75820-107">ParameterExpression</span></span>

<span data-ttu-id="75820-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType>nazwy zmiennych są `$` wyświetlane z symbolem na początku.</span><span class="sxs-lookup"><span data-stu-id="75820-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="75820-109">Jeśli parametr nie ma nazwy, jest przypisywany automatycznie wygenerowanej nazwy, takich jak `$var1` lub `$var2`.</span><span class="sxs-lookup"><span data-stu-id="75820-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="75820-110">Przykłady</span><span class="sxs-lookup"><span data-stu-id="75820-110">Examples</span></span>

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

## <a name="constantexpression"></a><span data-ttu-id="75820-111">Ekspresja stała</span><span class="sxs-lookup"><span data-stu-id="75820-111">ConstantExpression</span></span>

<span data-ttu-id="75820-112">Dla <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> obiektów reprezentujących wartości całkowite, ciągi i `null`wartość stałej jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="75820-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="75820-113">W przypadku typów liczbowych, które mają standardowe sufiksy jako literały C#, sufiks jest dodawany do wartości.</span><span class="sxs-lookup"><span data-stu-id="75820-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="75820-114">W poniższej tabeli przedstawiono sufiksy skojarzone z różnymi typami liczbowymi.</span><span class="sxs-lookup"><span data-stu-id="75820-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="75820-115">Typ</span><span class="sxs-lookup"><span data-stu-id="75820-115">Type</span></span> | <span data-ttu-id="75820-116">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="75820-116">Keyword</span></span> | <span data-ttu-id="75820-117">Sufiks</span><span class="sxs-lookup"><span data-stu-id="75820-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="75820-118">Uint</span><span class="sxs-lookup"><span data-stu-id="75820-118">uint</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="75820-119">U</span><span class="sxs-lookup"><span data-stu-id="75820-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="75820-120">long</span><span class="sxs-lookup"><span data-stu-id="75820-120">long</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="75820-121">L</span><span class="sxs-lookup"><span data-stu-id="75820-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="75820-122">ulong</span><span class="sxs-lookup"><span data-stu-id="75820-122">ulong</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="75820-123">UL</span><span class="sxs-lookup"><span data-stu-id="75820-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="75820-124">double</span><span class="sxs-lookup"><span data-stu-id="75820-124">double</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="75820-125">D</span><span class="sxs-lookup"><span data-stu-id="75820-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="75820-126">float</span><span class="sxs-lookup"><span data-stu-id="75820-126">float</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="75820-127">F</span><span class="sxs-lookup"><span data-stu-id="75820-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="75820-128">decimal</span><span class="sxs-lookup"><span data-stu-id="75820-128">decimal</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="75820-129">M</span><span class="sxs-lookup"><span data-stu-id="75820-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="75820-130">Przykłady</span><span class="sxs-lookup"><span data-stu-id="75820-130">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="75820-131">BlokWyrażenie</span><span class="sxs-lookup"><span data-stu-id="75820-131">BlockExpression</span></span>

<span data-ttu-id="75820-132">Jeśli typ <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> obiektu różni się od typu ostatniego wyrażenia w bloku, typ jest wyświetlany`<` w `>`nawiasach kątowych ( i ).</span><span class="sxs-lookup"><span data-stu-id="75820-132">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="75820-133">W przeciwnym razie <xref:System.Linq.Expressions.BlockExpression> typ obiektu nie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="75820-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="75820-134">Przykłady</span><span class="sxs-lookup"><span data-stu-id="75820-134">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="75820-135">Lambdaexpression</span><span class="sxs-lookup"><span data-stu-id="75820-135">LambdaExpression</span></span>

<span data-ttu-id="75820-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType>obiekty są wyświetlane razem z ich typami delegatów.</span><span class="sxs-lookup"><span data-stu-id="75820-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="75820-137">Jeśli wyrażenie lambda nie ma nazwy, jest przypisywana automatycznie wygenerowana `#Lambda1` nazwa, na przykład lub `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="75820-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="75820-138">Przykłady</span><span class="sxs-lookup"><span data-stu-id="75820-138">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="75820-139">Wyrażenie etykiet</span><span class="sxs-lookup"><span data-stu-id="75820-139">LabelExpression</span></span>

<span data-ttu-id="75820-140">Jeśli określisz wartość <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> domyślną dla obiektu, <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> ta wartość zostanie wyświetlona przed obiektem.</span><span class="sxs-lookup"><span data-stu-id="75820-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="75820-141">Token `.Label` wskazuje początek etykiety.</span><span class="sxs-lookup"><span data-stu-id="75820-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="75820-142">Token `.LabelTarget` wskazuje miejsce docelowe obiektu docelowego, do który ma przejść.</span><span class="sxs-lookup"><span data-stu-id="75820-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="75820-143">Jeśli etykieta nie ma nazwy, jest przypisana automatycznie wygenerowana nazwa, na przykład `#Label1` lub `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="75820-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="75820-144">Przykłady</span><span class="sxs-lookup"><span data-stu-id="75820-144">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="75820-145">Sprawdzone operatory</span><span class="sxs-lookup"><span data-stu-id="75820-145">Checked Operators</span></span>

<span data-ttu-id="75820-146">Sprawdzone operatory są wyświetlane `#` z symbolem przed operatorem.</span><span class="sxs-lookup"><span data-stu-id="75820-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="75820-147">Na przykład operator zaznaczonego dodawania `#+`jest wyświetlany jako .</span><span class="sxs-lookup"><span data-stu-id="75820-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="75820-148">Przykłady</span><span class="sxs-lookup"><span data-stu-id="75820-148">Examples</span></span>

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
