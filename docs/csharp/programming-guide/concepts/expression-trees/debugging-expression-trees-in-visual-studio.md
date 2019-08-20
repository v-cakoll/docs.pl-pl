---
title: Debugowanie drzew wyrażeń w programie Visual StudioC#()
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 19d00aaa99c7ef08e291337f38bf74a3beac12b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595224"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="3a8e7-102">Debugowanie drzew wyrażeń w programie Visual StudioC#()</span><span class="sxs-lookup"><span data-stu-id="3a8e7-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="3a8e7-103">Można analizować strukturę i zawartość drzew wyrażeń podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a8e7-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="3a8e7-104">Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwości, która reprezentuje drzewa wyrażeń [przy użyciu specjalnej składni](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="3a8e7-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="3a8e7-105">(Uwaga, `DebugView` która jest dostępna tylko w trybie debugowania).</span><span class="sxs-lookup"><span data-stu-id="3a8e7-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![DebugView drzewa wyrażenia w debugerze programu Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

<span data-ttu-id="3a8e7-107">Ponieważ `DebugView` jest ciągiem, można użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , aby wyświetlić go w wielu wierszach, wybierając **wizualizator tekstu** z ikony lupy obok `DebugView` etykiety.</span><span class="sxs-lookup"><span data-stu-id="3a8e7-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Wizualizator tekstu zastosowany do wyników elementu "DebugView"](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

<span data-ttu-id="3a8e7-109">Alternatywnie można zainstalować i używać wizualizatora [niestandardowego](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń, takich jak:</span><span class="sxs-lookup"><span data-stu-id="3a8e7-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

* <span data-ttu-id="3a8e7-110">Możliwe do [odczytu wyrażenia](https://github.com/agileobjects/ReadableExpressions) ([Licencja mit](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renderuje drzewo wyrażenia jako C# kod:</span><span class="sxs-lookup"><span data-stu-id="3a8e7-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Wizualizator wyrażeń do odczytu](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="3a8e7-112">[Wizualizator drzewa wyrażeń](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([Licencja mit](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), udostępnia widok graficzny drzewa wyrażenia, jego właściwości i powiązane obiekty:</span><span class="sxs-lookup"><span data-stu-id="3a8e7-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![Wizualizator ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="3a8e7-114">Aby otworzyć wizualizator dla drzewa wyrażenia</span><span class="sxs-lookup"><span data-stu-id="3a8e7-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="3a8e7-115">Kliknij ikonę lupy, która pojawia się obok drzewa wyrażenia w **etykietkach**danych, oknie czujki, oknie autostarts lub w oknie **zmiennych lokalnych** .</span><span class="sxs-lookup"><span data-stu-id="3a8e7-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="3a8e7-116">Zostanie wyświetlona lista dostępnych wizualizatorów.:</span><span class="sxs-lookup"><span data-stu-id="3a8e7-116">A list of available visualizers is displayed.:</span></span> 

      ![Otwieranie wizualizatorów z programu Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. <span data-ttu-id="3a8e7-118">Kliknij wizualizator, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="3a8e7-118">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a8e7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a8e7-119">See also</span></span>

- [<span data-ttu-id="3a8e7-120">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="3a8e7-120">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="3a8e7-121">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3a8e7-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="3a8e7-122">Tworzenie niestandardowych wizualizatorów</span><span class="sxs-lookup"><span data-stu-id="3a8e7-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="3a8e7-123">`DebugView`obowiązuje</span><span class="sxs-lookup"><span data-stu-id="3a8e7-123">`DebugView` syntax</span></span>](debugview-syntax.md)
