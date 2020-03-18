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
# <a name="debugview-syntax"></a>`DebugView`Składni

Właściwość `DebugView` (dostępna tylko podczas debugowania) zapewnia renderowanie ciągdrzew wyrażeń. Większość składni jest dość prosta do zrozumienia; przypadki szczególne opisano w poniższych sekcjach.

Po każdym przykładzie następuje komentarz `DebugView`bloku, zawierający plik .

## <a name="parameterexpression"></a>Parameterexpression

<xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType>nazwy zmiennych są `$` wyświetlane z symbolem na początku.

Jeśli parametr nie ma nazwy, jest przypisywany automatycznie wygenerowanej nazwy, takich jak `$var1` lub `$var2`.

### <a name="examples"></a>Przykłady

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

## <a name="constantexpression"></a>Ekspresja stała

Dla <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> obiektów reprezentujących wartości całkowite, ciągi i `null`wartość stałej jest wyświetlany.

W przypadku typów liczbowych, które mają standardowe sufiksy jako literały C#, sufiks jest dodawany do wartości. W poniższej tabeli przedstawiono sufiksy skojarzone z różnymi typami liczbowymi.

| Typ | Słowo kluczowe | Sufiks |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [Uint](../../../language-reference/builtin-types/integral-numeric-types.md) | U |
| <xref:System.Int64?displayProperty=nameWithType> | [long](../../../language-reference/builtin-types/integral-numeric-types.md) | L |
| <xref:System.UInt64?displayProperty=nameWithType> | [ulong](../../../language-reference/builtin-types/integral-numeric-types.md) | UL |
| <xref:System.Double?displayProperty=nameWithType> | [double](../../../language-reference/builtin-types/floating-point-numeric-types.md) | D |
| <xref:System.Single?displayProperty=nameWithType> | [float](../../../language-reference/builtin-types/floating-point-numeric-types.md) | F |
| <xref:System.Decimal?displayProperty=nameWithType> | [decimal](../../../language-reference/builtin-types/floating-point-numeric-types.md) | M |

### <a name="examples"></a>Przykłady

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

## <a name="blockexpression"></a>BlokWyrażenie

Jeśli typ <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> obiektu różni się od typu ostatniego wyrażenia w bloku, typ jest wyświetlany`<` w `>`nawiasach kątowych ( i ). W przeciwnym razie <xref:System.Linq.Expressions.BlockExpression> typ obiektu nie jest wyświetlany.

### <a name="examples"></a>Przykłady

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

## <a name="lambdaexpression"></a>Lambdaexpression

<xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType>obiekty są wyświetlane razem z ich typami delegatów.

Jeśli wyrażenie lambda nie ma nazwy, jest przypisywana automatycznie wygenerowana `#Lambda1` nazwa, na przykład lub `#Lambda2`.

### <a name="examples"></a>Przykłady

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

## <a name="labelexpression"></a>Wyrażenie etykiet

Jeśli określisz wartość <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> domyślną dla obiektu, <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> ta wartość zostanie wyświetlona przed obiektem.

Token `.Label` wskazuje początek etykiety. Token `.LabelTarget` wskazuje miejsce docelowe obiektu docelowego, do który ma przejść.

Jeśli etykieta nie ma nazwy, jest przypisana automatycznie wygenerowana nazwa, na przykład `#Label1` lub `#Label2`.

### <a name="examples"></a>Przykłady

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

## <a name="checked-operators"></a>Sprawdzone operatory

Sprawdzone operatory są wyświetlane `#` z symbolem przed operatorem. Na przykład operator zaznaczonego dodawania `#+`jest wyświetlany jako .

### <a name="examples"></a>Przykłady

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
