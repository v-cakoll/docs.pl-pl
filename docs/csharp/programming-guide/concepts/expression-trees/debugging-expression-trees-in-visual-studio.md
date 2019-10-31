---
title: Debugowanie drzew wyrażeń w programie Visual StudioC#()
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 30f538712881e41b4fd0e62d06f74373d755ea40
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195686"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="1f2f0-102">Debugowanie drzew wyrażeń w programie Visual StudioC#()</span><span class="sxs-lookup"><span data-stu-id="1f2f0-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="1f2f0-103">Można analizować strukturę i zawartość drzew wyrażeń podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1f2f0-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="1f2f0-104">Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć właściwości `DebugView`, która reprezentuje drzewa wyrażeń [przy użyciu specjalnej składni](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="1f2f0-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="1f2f0-105">(Należy zauważyć, że `DebugView` jest dostępny tylko w trybie debugowania).</span><span class="sxs-lookup"><span data-stu-id="1f2f0-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Zrzut ekranu przedstawiający DebugView drzewa wyrażenia w debugerze programu VS.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="1f2f0-107">Ponieważ `DebugView` jest ciągiem, można użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , aby wyświetlić go w wielu wierszach, wybierając **wizualizator tekstu** z ikony lupy, obok etykiety `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="1f2f0-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Zrzut ekranu przedstawiający wizualizator tekstu stosowany do wyników DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="1f2f0-109">Alternatywnie można zainstalować i używać [wizualizatora niestandardowego](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń, takich jak:</span><span class="sxs-lookup"><span data-stu-id="1f2f0-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="1f2f0-110">[Wyrażenia](https://github.com/agileobjects/ReadableExpressions) możliwe do odczytu ([licencja mit](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renderowanie drzewa wyrażenia C# jako kodu:</span><span class="sxs-lookup"><span data-stu-id="1f2f0-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Zrzut ekranu przedstawiający wizualizator wyrażeń możliwych do odczytu.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="1f2f0-112">[Wizualizator drzewa wyrażeń](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencja mit](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) zawiera widok graficzny drzewa wyrażenia, jego właściwości i powiązane obiekty:</span><span class="sxs-lookup"><span data-stu-id="1f2f0-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![Zrzut ekranu przedstawiający wizualizator drzewa wyrażeń.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="1f2f0-114">Aby otworzyć wizualizator dla drzewa wyrażenia</span><span class="sxs-lookup"><span data-stu-id="1f2f0-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="1f2f0-115">Kliknij ikonę lupy, która pojawia się obok drzewa wyrażenia w **etykietkach**danych, oknie **czujki** , oknie **autostarts** lub w oknie **zmiennych lokalnych** .</span><span class="sxs-lookup"><span data-stu-id="1f2f0-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="1f2f0-116">Zostanie wyświetlona lista dostępnych wizualizatorów.:</span><span class="sxs-lookup"><span data-stu-id="1f2f0-116">A list of available visualizers is displayed.:</span></span> 

    ![Zrzut ekranu przedstawiający otwieranie wizualizatorów z programu Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="1f2f0-118">Kliknij wizualizator, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="1f2f0-118">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f2f0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f2f0-119">See also</span></span>

- [<span data-ttu-id="1f2f0-120">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="1f2f0-120">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="1f2f0-121">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1f2f0-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="1f2f0-122">Tworzenie niestandardowych wizualizatorów</span><span class="sxs-lookup"><span data-stu-id="1f2f0-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="1f2f0-123">Składnia `DebugView`</span><span class="sxs-lookup"><span data-stu-id="1f2f0-123">`DebugView` syntax</span></span>](debugview-syntax.md)
