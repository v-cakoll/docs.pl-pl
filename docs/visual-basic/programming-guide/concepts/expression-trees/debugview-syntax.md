---
title: Składnia używana przez właściwość DebugView
description: Opisuje specjalną składnię używaną przez właściwość DebugView, aby utworzyć ciąg reprezentujący drzewa wyrażeń
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 98ceba37aa226fab68ae1c1028e2a1139b3b8e7e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346867"
---
# <a name="debugview-syntax"></a>Składnia `DebugView`

Właściwość `DebugView` (dostępna tylko w przypadku debugowania) zapewnia renderowanie ciągów drzew wyrażeń. Większość składni jest dość prosta do zrozumienia; specjalne przypadki opisano w poniższych sekcjach.

W każdym przykładzie następuje blok komentarza zawierający `DebugView`.

## <a name="parameterexpression"></a>ParameterExpression

nazwy zmiennych <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> są wyświetlane z symbolem "$" na początku.

Jeśli parametr nie ma nazwy, zostanie przypisana automatycznie wygenerowana nazwa, taka jak `$var1` lub `$var2`.

### <a name="examples"></a>Przykłady

```vb
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")
'
'    $num
'

Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer))
'
'    $var1
'
```

## <a name="constantexpressions"></a>ConstantExpressions

Dla <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> obiektów, które reprezentują wartości całkowite, ciągi i `null`, zostanie wyświetlona wartość stałej.

W przypadku niektórych typów liczbowych sufiks jest dodawany do wartości:

| Typ | Słowo kluczowe | Suffix |
|--|--|--|
| <xref:System.UInt32> | [UInteger —](../../../language-reference/data-types/uinteger-data-type.md) | U |
| <xref:System.Int64> | [Długo](../../../language-reference/data-types/long-data-type.md) | L |
| <xref:System.UInt64> | [ULong](../../../language-reference/data-types/ulong-data-type.md) | UL |
| <xref:System.Double> | [Double](../../../language-reference/data-types/double-data-type.md) | D |
| <xref:System.Single> | [Wiersz](../../../language-reference/data-types/single-data-type.md) | F |
| <xref:System.Decimal> | [Dokładności](../../../language-reference/data-types/decimal-data-type.md) | M |

### <a name="examples"></a>Przykłady

```vb
Dim num as Integer = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10
'

Dim num As Double = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10D
'
```

## <a name="blockexpression"></a>BlockExpression

Jeśli typ obiektu <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> różni się od typu ostatniego wyrażenia w bloku, typ jest wyświetlany w nawiasach kątowych (`<` i `>`). W przeciwnym razie typ obiektu <xref:System.Linq.Expressions.BlockExpression> nie jest wyświetlany.

### <a name="examples"></a>Przykłady

```vb
Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
'
'    .Block() {
'        "test"
'    }
'

Dim block As BlockExpression = Expression.Block(
    GetType(Object),
    Expression.Constant("test")
)
'
'    .Block<System.Object>() {
'        "test"
'    }
'
```

## <a name="lambdaexpression"></a>LambdaExpression

obiekty <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> są wyświetlane razem z ich typami delegatów.

Jeśli wyrażenie lambda nie ma nazwy, zostanie przypisana automatycznie wygenerowana nazwa, taka jak `#Lambda1` lub `#Lambda2`.

### <a name="examples"></a>Przykłady

```vb
Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1)
)
'
'    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
'        1
'    }
'

Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1),
    "SampleLambda",
    Nothing
)
'
'    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
'        1
'    }
'
```

## <a name="labelexpression"></a>LabelExpression

Jeśli określisz wartość domyślną dla obiektu <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, ta wartość będzie wyświetlana przed obiektem <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.

Token `.Label` wskazuje początek etykiety. Token `.LabelTarget` wskazuje miejsce docelowe miejsca docelowego, do którego chcesz przejść.

Jeśli etykieta nie ma nazwy, zostanie przypisana automatycznie wygenerowana nazwa, taka jak `#Label1` lub `#Label2`.

### <a name="examples"></a>Przykłady

```vb
Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
)
'
'    .Block() {
'        .Goto SampleLabel { 0 };
'        .Label
'            -1
'        .LabelTarget SampleLabel:
'    }
'

Dim target As LabelTarget = Expression.Label()
Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
)
'
'    .Block() {
'        .Goto #Label1 { };
'        .Label
'        .LabelTarget #Label1:
'    }
'
```

## <a name="checked-operators"></a>Sprawdzone operatory

Zaznaczone operatory są wyświetlane z symbolem `#` przed operatorem. Na przykład, zaznaczony operator dodawania jest wyświetlany jako `#+`.

### <a name="examples"></a>Przykłady

```vb
Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1),
    Expression.Constant(2)
)
'
'     1 #+ 2
'

Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0),
    GetType(Integer)
)
'
'    #(System.Int32)10D
'
```
