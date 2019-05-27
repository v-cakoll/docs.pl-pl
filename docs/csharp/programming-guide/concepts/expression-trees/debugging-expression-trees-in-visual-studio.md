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
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="cd45b-102">Debugowanie drzew w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="cd45b-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="cd45b-103">Można analizować struktury i zawartości drzew wyrażeń podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd45b-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="cd45b-104">Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwość, która reprezentuje drzew wyrażeń [przy użyciu specjalnej składni](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="cd45b-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="cd45b-105">(Należy pamiętać, że `DebugView` jest dostępna tylko w trybie debugowania.)</span><span class="sxs-lookup"><span data-stu-id="cd45b-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![DebugView drzewa wyrażeń w debugerze programu Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

<span data-ttu-id="cd45b-107">Ponieważ `DebugView` jest ciągiem, możesz użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) do wyświetlenia w wielu wierszach, wybierając **Wizualizator tekstu** z na ikonę szkła powiększającego obok `DebugView` Etykieta.</span><span class="sxs-lookup"><span data-stu-id="cd45b-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Wizualizator tekstu zastosowane do wyników "DebugView"](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

<span data-ttu-id="cd45b-109">Alternatywnie, można zainstalować i używać [niestandardowego wizualizatora](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) drzew wyrażeń, takie jak:</span><span class="sxs-lookup"><span data-stu-id="cd45b-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

* <span data-ttu-id="cd45b-110">[Wyrażenia można odczytać](https://github.com/agileobjects/ReadableExpressions) ([licencją MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), która jest dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), powoduje wyświetlenie drzewa wyrażeń jako C# kodu:</span><span class="sxs-lookup"><span data-stu-id="cd45b-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Czytelny Wizualizator wyrażeń](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="cd45b-112">[Wizualizatora drzewa wyrażenie](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencją MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), zawiera graficzne przedstawienie drzewa wyrażeń, a jej właściwości i obiektów związanych z:</span><span class="sxs-lookup"><span data-stu-id="cd45b-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![Wizualizator ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="cd45b-114">Aby otworzyć wizualizatora drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="cd45b-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="cd45b-115">Kliknij ikonę lupy, która pojawia się obok drzewa wyrażeń w **DataTips**, **Obejrzyj** oknie **automatyczne** oknie lub **zmiennychlokalnych** okna.</span><span class="sxs-lookup"><span data-stu-id="cd45b-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="cd45b-116">Zostanie wyświetlona lista dostępnych wizualizatorów.:</span><span class="sxs-lookup"><span data-stu-id="cd45b-116">A list of available visualizers is displayed.:</span></span> 

      ![Wizualizatory otwierania w programie Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. <span data-ttu-id="cd45b-118">Kliknij pozycję Wizualizator, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="cd45b-118">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd45b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd45b-119">See also</span></span>

- [<span data-ttu-id="cd45b-120">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="cd45b-120">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="cd45b-121">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cd45b-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="cd45b-122">Tworzenie niestandardowych wizualizatorów</span><span class="sxs-lookup"><span data-stu-id="cd45b-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="cd45b-123">`DebugView` Składnia</span><span class="sxs-lookup"><span data-stu-id="cd45b-123">`DebugView` syntax</span></span>](debugview-syntax.md)
