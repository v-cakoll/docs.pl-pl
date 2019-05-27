---
title: Debugowanie drzew w programie Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 93b1b660181cd81c31055f5d30d43e535171bb55
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195983"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Debugowanie drzew w programie Visual Studio (C#)
Można analizować struktury i zawartości drzew wyrażeń podczas debugowania aplikacji. Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwość, która reprezentuje drzew wyrażeń [przy użyciu specjalnej składni](debugview-syntax.md). (Należy pamiętać, że `DebugView` jest dostępna tylko w trybie debugowania.)  

![DebugView drzewa wyrażeń w debugerze programu Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

Ponieważ `DebugView` jest ciągiem, możesz użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) do wyświetlenia w wielu wierszach, wybierając **Wizualizator tekstu** z na ikonę szkła powiększającego obok `DebugView` Etykieta.

 ![Wizualizator tekstu zastosowane do wyników "DebugView"](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

Alternatywnie, można zainstalować i używać [niestandardowego wizualizatora](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) drzew wyrażeń, takie jak:

* [Wyrażenia można odczytać](https://github.com/agileobjects/ReadableExpressions) ([licencją MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), która jest dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), powoduje wyświetlenie drzewa wyrażeń jako C# kodu:

  ![Czytelny Wizualizator wyrażeń](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [Wizualizatora drzewa wyrażenie](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencją MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), zawiera graficzne przedstawienie drzewa wyrażeń, a jej właściwości i obiektów związanych z:

  ![Wizualizator ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Aby otworzyć wizualizatora drzewa wyrażeń  
  
1. Kliknij ikonę lupy, która pojawia się obok drzewa wyrażeń w **DataTips**, **Obejrzyj** oknie **automatyczne** oknie lub **zmiennychlokalnych** okna.  
  
     Zostanie wyświetlona lista dostępnych wizualizatorów.: 

      ![Wizualizatory otwierania w programie Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. Kliknij pozycję Wizualizator, którego chcesz użyć.  
  
## <a name="see-also"></a>Zobacz także

- [Drzewa wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Tworzenie niestandardowych wizualizatorów](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView` Składnia](debugview-syntax.md)
