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
ms.openlocfilehash: de82a738430cdd37c4905a5ae7da5faeb46f00a4
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196521"
---
# <a name="debugview-syntax"></a>`DebugView` Składnia

`DebugView` (Dostępne tylko wtedy, gdy debugowanie) dostarcza renderowania ciągu, drzew wyrażeń. Najczęściej składnia jest dość prosta zrozumieć; szczególne przypadki są opisane w poniższych sekcjach.

Każdy przykład następuje komentarz bloku, zawierającego `DebugView`. 

## <a name="parameterexpression"></a>ParameterExpression 

<xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> nazwy zmiennych są wyświetlane z `$` symboli na początku.
  
Jeśli parametr nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `$var1` lub `$var2`.
  
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

## <a name="constantexpression"></a>ConstantExpression  

Dla <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> obiekty reprezentujące wartości całkowitych, ciągów i `null`, jest wyświetlana wartość stałą.  
  
Dla typów numerycznych, które mają standardowa sufiksy jako literały języka C# sufiks jest dodawany do wartości. W poniższej tabeli przedstawiono sufiksy skojarzone z różnych typów liczbowych.  

| Typ | Słowo kluczowe | Suffix |  
|--|--|--|  
| <xref:System.UInt32?displayProperty=nameWithType> | [uint](../../../language-reference/keywords/uint.md) | U |  
| <xref:System.Int64?displayProperty=nameWithType> | [long](../../../language-reference/keywords/long.md) | L |  
| <xref:System.UInt64?displayProperty=nameWithType> | [ulong](../../../language-reference/keywords/ulong.md) | UL |  
| <xref:System.Double?displayProperty=nameWithType> | [double](../../../language-reference/keywords/double.md) | D |  
| <xref:System.Single?displayProperty=nameWithType> | [float](../../../language-reference/keywords/float.md) | F |  
| <xref:System.Decimal?displayProperty=nameWithType> | [decimal](../../../language-reference/keywords/decimal.md) | M |  
  
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

## <a name="blockexpression"></a>BlockExpression
 
Jeśli typ <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> obiekt różni się od typu ostatniego wyrażenia w bloku, typ jest wyświetlany w nawiasach kątowych (`<` i `>`). W przeciwnym razie typ <xref:System.Linq.Expressions.BlockExpression> obiektu nie jest wyświetlana.  
  
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

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> obiekty są wyświetlane wraz z ich typy delegowane.
  
Jeśli wyrażenie lambda ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Lambda1` lub `#Lambda2`.
  
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
  
## <a name="labelexpression"></a>LabelExpression

Jeśli określisz wartość domyślną dla <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> obiektu, ta wartość jest poprzedzana <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> obiektu.
  
`.Label` Token wskazuje początek etykiety. `.LabelTarget` Token wskazuje docelowy obiektu docelowego, aby przejść do.
  
Jeśli etykieta nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Label1` lub `#Label2`.
  
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
  
## <a name="checked-operators"></a>Operatory zaznaczone  

Operatory sprawdzane są wyświetlane z `#` symbol przed operatora. Na przykład operator dodawania zaznaczone jest wyświetlany jako `#+`.  
  
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