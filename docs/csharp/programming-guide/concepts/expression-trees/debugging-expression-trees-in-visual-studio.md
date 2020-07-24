---
title: Debugowanie drzew wyrażeń w programie Visual Studio (C#)
description: Dowiedz się więcej o właściwości DebugView w programie Visual Studio. Zobacz, jak używać tej właściwości do analizowania struktury i zawartości drzew wyrażeń.
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 5d62a5e6fa5ce537a1ea8b316e7322eb976200c0
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105638"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="fb516-104">Debugowanie drzew wyrażeń w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="fb516-104">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="fb516-105">Można analizować strukturę i zawartość drzew wyrażeń podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb516-105">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="fb516-106">Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwości, która reprezentuje drzewa wyrażeń [przy użyciu specjalnej składni](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="fb516-106">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="fb516-107">(Uwaga, która `DebugView` jest dostępna tylko w trybie debugowania).</span><span class="sxs-lookup"><span data-stu-id="fb516-107">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Zrzut ekranu przedstawiający DebugView drzewa wyrażenia w debugerze programu VS.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="fb516-109">Ponieważ `DebugView` jest ciągiem, można użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , aby wyświetlić go w wielu wierszach, wybierając **wizualizator tekstu** z ikony lupy obok `DebugView` etykiety.</span><span class="sxs-lookup"><span data-stu-id="fb516-109">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Zrzut ekranu przedstawiający wizualizator tekstu stosowany do wyników DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="fb516-111">Alternatywnie można zainstalować i używać [wizualizatora niestandardowego](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń, takich jak:</span><span class="sxs-lookup"><span data-stu-id="fb516-111">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="fb516-112">[Wyrażenia](https://github.com/agileobjects/ReadableExpressions) możliwe do odczytu ([licencja mit](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renderuje drzewo wyrażenia jako kod języka C# z możliwością programowania z różnymi opcjami renderowania:</span><span class="sxs-lookup"><span data-stu-id="fb516-112">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Zrzut ekranu przedstawiający wizualizator wyrażeń możliwych do odczytu.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="fb516-114">[Wizualizator drzewa wyrażeń](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([licencja mit](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) zawiera widok drzewa drzewa wyrażenia i jego poszczególne węzły:</span><span class="sxs-lookup"><span data-stu-id="fb516-114">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes:</span></span>

  ![Zrzut ekranu przedstawiający wizualizator drzewa wyrażeń.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="fb516-116">Aby otworzyć wizualizator dla drzewa wyrażenia</span><span class="sxs-lookup"><span data-stu-id="fb516-116">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="fb516-117">Kliknij ikonę lupy, która pojawia się obok drzewa wyrażenia w **etykietkach**danych, oknie **czujki** , oknie **autostarts** lub w oknie **zmiennych lokalnych** .</span><span class="sxs-lookup"><span data-stu-id="fb516-117">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="fb516-118">Zostanie wyświetlona lista dostępnych wizualizatorów.:</span><span class="sxs-lookup"><span data-stu-id="fb516-118">A list of available visualizers is displayed.:</span></span>

    ![Zrzut ekranu przedstawiający otwieranie wizualizatorów z programu Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="fb516-120">Kliknij wizualizator, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="fb516-120">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb516-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb516-121">See also</span></span>

- [<span data-ttu-id="fb516-122">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="fb516-122">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="fb516-123">Debugowanie w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fb516-123">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="fb516-124">Tworzenie niestandardowych wizualizatorów</span><span class="sxs-lookup"><span data-stu-id="fb516-124">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="fb516-125">`DebugView`obowiązuje</span><span class="sxs-lookup"><span data-stu-id="fb516-125">`DebugView` syntax</span></span>](debugview-syntax.md)
