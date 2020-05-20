---
title: Debugowanie drzew w programie Visual Studio
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 287f3096a1af8b9fa42d252c5240d7caefa6bac8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616904"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="035fc-102">Debugowanie drzew wyrażeń w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="035fc-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="035fc-103">Można analizować strukturę i zawartość drzew wyrażeń podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="035fc-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="035fc-104">Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwości, która reprezentuje drzewa wyrażeń [przy użyciu specjalnej składni](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="035fc-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="035fc-105">(Uwaga, która `DebugView` jest dostępna tylko w trybie debugowania).</span><span class="sxs-lookup"><span data-stu-id="035fc-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Zrzut ekranu przedstawiający DebugView drzewa wyrażenia.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

<span data-ttu-id="035fc-107">Ponieważ `DebugView` jest ciągiem, można użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , aby wyświetlić go w wielu wierszach, wybierając **wizualizator tekstu** z ikony lupy obok `DebugView` etykiety.</span><span class="sxs-lookup"><span data-stu-id="035fc-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Zrzut ekranu wizualizatora tekstu stosowany do wyników DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

<span data-ttu-id="035fc-109">Alternatywnie można zainstalować i używać [wizualizatora niestandardowego](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń, takich jak:</span><span class="sxs-lookup"><span data-stu-id="035fc-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="035fc-110">[Wyrażenia](https://github.com/agileobjects/ReadableExpressions) możliwe do odczytu ([licencja mit](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renderuje drzewo wyrażenia jako kod języka C# z możliwością programowania z różnymi opcjami renderowania:</span><span class="sxs-lookup"><span data-stu-id="035fc-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Zrzut ekranu przedstawiający wizualizator wyrażeń możliwych do odczytu.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="035fc-112">[Wizualizator drzewa wyrażeń](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([licencja mit](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) zawiera widok drzewa drzewa wyrażenia i jego poszczególne węzły; i można renderować drzewo wyrażeń przy użyciu składni Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="035fc-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes; and can render the expression tree using Visual Basic syntax:</span></span>

  ![Zrzut ekranu przedstawiający wizualizator drzewa wyrażeń.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="035fc-114">Aby otworzyć wizualizator dla drzewa wyrażenia</span><span class="sxs-lookup"><span data-stu-id="035fc-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="035fc-115">Kliknij ikonę lupy, która pojawia się obok drzewa wyrażenia w **etykietkach**danych, oknie **czujki** , oknie **autostarts** lub w oknie **zmiennych lokalnych** .</span><span class="sxs-lookup"><span data-stu-id="035fc-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
    <span data-ttu-id="035fc-116">Zostanie wyświetlona lista dostępnych wizualizatorów.:</span><span class="sxs-lookup"><span data-stu-id="035fc-116">A list of available visualizers is displayed.:</span></span>

    ![Zrzut ekranu przedstawiający Wizualizatory otwierające użytkownika z programu Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. <span data-ttu-id="035fc-118">Kliknij wizualizator, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="035fc-118">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="035fc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="035fc-119">See also</span></span>

- [<span data-ttu-id="035fc-120">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="035fc-120">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="035fc-121">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="035fc-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="035fc-122">Tworzenie niestandardowych wizualizatorów</span><span class="sxs-lookup"><span data-stu-id="035fc-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="035fc-123">`DebugView`obowiązuje</span><span class="sxs-lookup"><span data-stu-id="035fc-123">`DebugView` syntax</span></span>](debugview-syntax.md)
