---
title: Debugowanie drzew w programie Visual Studio
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: c6c44d079ab0854b2325b82d3569280752da32fb
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266836"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="48a87-102">Drzewa wyrażeń debugowania w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48a87-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="48a87-103">Podczas debugowania aplikacji można analizować strukturę i zawartość drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="48a87-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="48a87-104">Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwości, która reprezentuje drzewa wyrażeń przy użyciu [specjalnej składni](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="48a87-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="48a87-105">(Należy `DebugView` zauważyć, że jest dostępny tylko w trybie debugowania.)</span><span class="sxs-lookup"><span data-stu-id="48a87-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Zrzut ekranu przedstawiający debugview drzewa wyrażeń.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

<span data-ttu-id="48a87-107">Ponieważ `DebugView` jest ciągiem, można użyć [wbudowanego wizualizatora tekstu,](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) aby wyświetlić go w wielu wierszach, `DebugView` wybierając **wizualizator tekstu** z ikony lupy obok etykiety.</span><span class="sxs-lookup"><span data-stu-id="48a87-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Zrzut ekranu przedstawiający wizualizator tekstu zastosowany do wyników debugview.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

<span data-ttu-id="48a87-109">Alternatywnie można zainstalować i używać [niestandardowego wizualizatora](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń, takich jak:</span><span class="sxs-lookup"><span data-stu-id="48a87-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="48a87-110">[Czytelne wyrażenia](https://github.com/agileobjects/ReadableExpressions) [(licencja MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostępna w [programie Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renderuje drzewo wyrażeń jako kod C#:</span><span class="sxs-lookup"><span data-stu-id="48a87-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Zrzut ekranu przedstawiający wizualizator wyrażeń czytelnych.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="48a87-112">[Wizualizator drzewa wyrażeń](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) [(licencja MIT),](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)zapewnia graficzny widok drzewa wyrażeń, jego właściwości i powiązanych obiektów; i może renderować drzewo wyrażeń przy użyciu kodu języka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="48a87-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects; and can render the expression tree using Visual Basic code:</span></span>

  ![Zrzut ekranu przedstawiający wizualizator ExpressionToString.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="48a87-114">Aby otworzyć wizualizator dla drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="48a87-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="48a87-115">Kliknij ikonę lupy wyświetlaną obok drzewa wyrażeń w **etykietkach danych**, oknie **Czujka,** **Autos** lub w oknie **Zmiennicy.**</span><span class="sxs-lookup"><span data-stu-id="48a87-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
    <span data-ttu-id="48a87-116">Zostanie wyświetlona lista dostępnych wizualizatorów.:</span><span class="sxs-lookup"><span data-stu-id="48a87-116">A list of available visualizers is displayed.:</span></span>

    ![Zrzut ekranu przedstawiający użytkownika otwierającego wizualizatory z programu Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. <span data-ttu-id="48a87-118">Kliknij wizualizator, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="48a87-118">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="48a87-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48a87-119">See also</span></span>

- [<span data-ttu-id="48a87-120">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48a87-120">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="48a87-121">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="48a87-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="48a87-122">Tworzenie niestandardowych wizualizatorów</span><span class="sxs-lookup"><span data-stu-id="48a87-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="48a87-123">`DebugView`Składni</span><span class="sxs-lookup"><span data-stu-id="48a87-123">`DebugView` syntax</span></span>](debugview-syntax.md)
