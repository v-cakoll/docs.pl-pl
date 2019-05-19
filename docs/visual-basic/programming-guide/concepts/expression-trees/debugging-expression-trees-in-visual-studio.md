---
title: Debugowanie drzew w programie Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 7fc97d898c5956b5a569036e6e0fe1174714576d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879828"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Debugowanie drzew w programie Visual Studio (Visual Basic)
Można analizować struktury i zawartości drzew wyrażeń podczas debugowania aplikacji. Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwość, która reprezentuje drzew wyrażeń, przy użyciu specjalnej składni opisane [poniżej](#debugview-syntax). (Należy pamiętać, że `DebugView` jest dostępna tylko w trybie debugowania.)  

![DebugView drzewa wyrażeń w debugerze programu Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

Ponieważ `DebugView` jest ciągiem, możesz użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) do wyświetlenia w wielu wierszach, wybierając **Wizualizator tekstu** z na ikonę szkła powiększającego obok `DebugView` Etykieta.

 ![Wizualizator tekstu zastosowane do wyników "DebugView"](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

Alternatywnie, można zainstalować i używać [niestandardowego wizualizatora](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń:

* [Wyrażenia można odczytać](https://github.com/agileobjects/ReadableExpressions) ([licencją MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), która jest dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), powoduje wyświetlenie drzewa wyrażeń jako C# kodu:

  ![Czytelny Wizualizator wyrażeń](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [Wizualizatora drzewa wyrażenie](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencją MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), zawiera graficzne przedstawienie drzewa wyrażeń, jej właściwości i powiązane obiekty; i umożliwia renderowanie drzewa wyrażeń przy użyciu kodu języka Visual Basic:

  ![Wizualizator ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Aby otworzyć wizualizatora drzewa wyrażeń  
  
1. Kliknij ikonę lupy, która pojawia się obok drzewa wyrażeń w **DataTips**, **Obejrzyj** oknie **automatyczne** oknie lub **zmiennychlokalnych** okna.  
  
     Zostanie wyświetlona lista dostępnych wizualizatorów.: 

      ![Wizualizatory otwierania w programie Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. Kliknij pozycję Wizualizator, którego chcesz użyć.  

## <a name="debugview-syntax"></a>`DebugView` Składnia 

Każdy typ wyrażenia jest wyświetlany w wizualizatorze, zgodnie z opisem w poniższych sekcjach.

## <a name="parameterexpressions"></a>ParameterExpressions

<xref:System.Linq.Expressions.ParameterExpression> nazwy zmiennych są wyświetlane z symbolem "$" na początku.

Jeśli parametr nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `$var1` lub `$var2`.

### <a name="examples"></a>Przykłady

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer), "num")
    ```

    `DebugView` Właściwość

    `$num`

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer))
    ```

    `DebugView` Właściwość

    `$var1`

## <a name="constantexpressions"></a>ConstantExpressions
 Dla <xref:System.Linq.Expressions.ConstantExpression> obiekty reprezentujące wartości całkowitych, ciągów i `null`, jest wyświetlana wartość stałą.

### <a name="examples"></a>Przykłady

- `Expression`

    ```vb
    Dim num as Integer= 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    `DebugView` Właściwość

    10

- `Expression`

    ```vb
    Dim num As Double = 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    `DebugView` Właściwość

    10D

## <a name="blockexpression"></a>BlockExpression

Jeśli typ <xref:System.Linq.Expressions.BlockExpression> obiekt różni się od typu ostatniego wyrażenia w bloku, typ jest wyświetlany w `DebugInfo` właściwość w nawiasy ostre (\< i >). W przeciwnym razie typ <xref:System.Linq.Expressions.BlockExpression> obiektu nie jest wyświetlana.

### <a name="examples"></a>Przykłady

- `Expression`

    ```vb
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
    ```

    `DebugView` Właściwość

    `.Block() {`

    `"test"`

    `}`

- `Expression`

    ```vb
    Dim block As BlockExpression =
    Expression.Block(GetType(Object), Expression.Constant("test"))
    ```

    `DebugView` Właściwość

    `.Block<System.Object>() {`

    `"test"`

    `}`

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression> obiekty są wyświetlane wraz z ich typy delegowane.

Jeśli wyrażenie lambda ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Lambda1` lub `#Lambda2`.

### <a name="examples"></a>Przykłady

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))
    ```

    `DebugView` Właściwość

    `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`

    `1`

    `}`

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLambda", Nothing)
    ```

    `DebugView` Właściwość

    `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`

    `1`

    `}`

## <a name="labelexpression"></a>LabelExpression

Jeśli określisz wartość domyślną dla <xref:System.Linq.Expressions.LabelExpression> obiektu, ta wartość jest poprzedzana <xref:System.Linq.Expressions.LabelTarget> obiektu.

`.Label` Token wskazuje początek etykiety. `.LabelTarget` Token wskazuje docelowy obiektu docelowego, aby przejść do.

Jeśli etykieta nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Label1` lub `#Label2`.

### <a name="examples"></a>Przykłady

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
    Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1)))
    ```

    `DebugView` Właściwość

    `.Block() {`

    `.Goto SampleLabel { 0 };`

    `.Label`

    `-1`

    `.LabelTarget SampleLabel:`

    `}`

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label()
    Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), Expression.Label(target))
    ```

    `DebugView` Właściwość

    `.Block() {`

    `.Goto #Label1 { };`

    `.Label`

    `.LabelTarget #Label1:`

    `}`

## <a name="checked-operators"></a>Operatory zaznaczone

Operatory sprawdzane są wyświetlane z symbolu "#" w miejscu dostępnym dla operatora. Na przykład operator dodawania zaznaczone jest wyświetlany jako `#+`.

### <a name="examples"></a>Przykłady

- `Expression`

    ```vb
    Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1), Expression.Constant(2))
    ```

    `DebugView` Właściwość

    `1 #+ 2`

- `Expression`

    ```vb
    Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0), GetType(Integer))
    ```

    `DebugView` Właściwość

    `#(System.Int32)10D`

## <a name="see-also"></a>Zobacz także

- [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Tworzenie niestandardowych wizualizatorów](/visualstudio/debugger/create-custom-visualizers-of-data)
