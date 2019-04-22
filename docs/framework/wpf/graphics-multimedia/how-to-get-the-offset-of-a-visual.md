---
title: 'Instrukcje: Pobieranie przesunięcia wizualizacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: 4787b771c7e59a8b033b9267079c068a5845a1e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093413"
---
# <a name="how-to-get-the-offset-of-a-visual"></a><span data-ttu-id="b2c8c-102">Instrukcje: Pobieranie przesunięcia wizualizacji</span><span class="sxs-lookup"><span data-stu-id="b2c8c-102">How to: Get the Offset of a Visual</span></span>
<span data-ttu-id="b2c8c-103">Te przykłady pokazują, jak można pobrać wartości przesunięcia visual obiektu, który jest określana względem jego elementu nadrzędnego lub dowolnego nadrzędnym lub obiekt podrzędny.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-103">These examples show how to retrieve the offset value of a visual object that is relative to its parent, or any ancestor or descendant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2c8c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2c8c-104">Example</span></span>  
 <span data-ttu-id="b2c8c-105">W poniższym przykładzie przedstawiono znaczników <xref:System.Windows.Controls.TextBlock> zdefiniowanego za pomocą <xref:System.Windows.FrameworkElement.Margin%2A> wartość 4.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-105">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is defined with <xref:System.Windows.FrameworkElement.Margin%2A> value of 4.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 <span data-ttu-id="b2c8c-106">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> metodę, aby pobrać przesunięcie <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-106">The following code example shows how to use the <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="b2c8c-107">Wartości przesunięcia znajdują się w ciągu zwracanym <xref:System.Windows.Vector> wartość.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-107">The offset values are contained within the returned <xref:System.Windows.Vector> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 <span data-ttu-id="b2c8c-108">Przesunięcie uwzględnia <xref:System.Windows.FrameworkElement.Margin%2A> wartość.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-108">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> value.</span></span> <span data-ttu-id="b2c8c-109">W tym przypadku <xref:System.Windows.Vector.X%2A> to 4, i <xref:System.Windows.Vector.Y%2A> wynosi 4.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-109">In this case, <xref:System.Windows.Vector.X%2A> is 4, and <xref:System.Windows.Vector.Y%2A> is 4.</span></span>  
  
 <span data-ttu-id="b2c8c-110">Zwrócona wartość przesunięcia jest określana względem elementu nadrzędnego <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-110">The returned offset value is relative to the parent of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="b2c8c-111">Jeśli chcesz zwrócić wartości przesunięcia, która nie jest określana względem elementu nadrzędnego <xref:System.Windows.Media.Visual>, użyj <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-111">If you want to return an offset value that is not relative to the parent of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a><span data-ttu-id="b2c8c-112">Pobieranie przesunięcia względem elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="b2c8c-112">Getting the Offset Relative to an Ancestor</span></span>  
 <span data-ttu-id="b2c8c-113">W poniższym przykładzie przedstawiono znaczników <xref:System.Windows.Controls.TextBlock> zagnieżdżony w ramach dwóch <xref:System.Windows.Controls.StackPanel> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-113">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is nested within two <xref:System.Windows.Controls.StackPanel> objects.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 <span data-ttu-id="b2c8c-114">Poniższa ilustracja przedstawia wyniki znaczników.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-114">The following illustration shows the results of the markup.</span></span>  
  
 <span data-ttu-id="b2c8c-115">![Wartości przesunięcia obiektów](./media/visualoffset-01.png "VisualOffset_01")</span><span class="sxs-lookup"><span data-stu-id="b2c8c-115">![Offset values of objects](./media/visualoffset-01.png "VisualOffset_01")</span></span>  
<span data-ttu-id="b2c8c-116">Zagnieżdżone w obrębie dwóch StackPanels TextBlock</span><span class="sxs-lookup"><span data-stu-id="b2c8c-116">TextBlock nested within two StackPanels</span></span>  
  
 <span data-ttu-id="b2c8c-117">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metodę, aby pobrać przesunięcie <xref:System.Windows.Controls.TextBlock> względem zawierający <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-117">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock> relative to the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="b2c8c-118">Wartości przesunięcia znajdują się w ciągu zwracanym <xref:System.Windows.Media.GeneralTransform> wartość.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-118">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 <span data-ttu-id="b2c8c-119">Przesunięcie uwzględnia <xref:System.Windows.FrameworkElement.Margin%2A> wartości dla wszystkich obiektów w ramach zawierający <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-119">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects within the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="b2c8c-120">W tym przypadku <xref:System.Windows.Vector.X%2A> to 28 (16 + 8 + 4), a <xref:System.Windows.Vector.Y%2A> to 28.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-120">In this case, <xref:System.Windows.Vector.X%2A> is 28 (16 + 8 + 4), and <xref:System.Windows.Vector.Y%2A> is 28.</span></span>  
  
 <span data-ttu-id="b2c8c-121">Zwrócona wartość przesunięcia jest określana względem element nadrzędny elementu <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-121">The returned offset value is relative to the ancestor of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="b2c8c-122">Jeśli chcesz przywrócić wartość przesunięcia względem obiektu podrzędnego z <xref:System.Windows.Media.Visual>, użyj <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-122">If you want to return an offset value that is relative to the descendant of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a><span data-ttu-id="b2c8c-123">Pobieranie przesunięcia względem element podrzędny</span><span class="sxs-lookup"><span data-stu-id="b2c8c-123">Getting the Offset Relative to a Descendant</span></span>  
 <span data-ttu-id="b2c8c-124">W poniższym przykładzie przedstawiono znaczników <xref:System.Windows.Controls.TextBlock> zawarty w <xref:System.Windows.Controls.StackPanel> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-124">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is contained within a <xref:System.Windows.Controls.StackPanel> object.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 <span data-ttu-id="b2c8c-125">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metodę, aby pobrać przesunięcie <xref:System.Windows.Controls.StackPanel> względem jego podrzędny <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-125">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method to retrieve the offset of the <xref:System.Windows.Controls.StackPanel> relative to its child <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="b2c8c-126">Wartości przesunięcia znajdują się w ciągu zwracanym <xref:System.Windows.Media.GeneralTransform> wartość.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-126">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 <span data-ttu-id="b2c8c-127">Przesunięcie uwzględnia <xref:System.Windows.FrameworkElement.Margin%2A> wartości dla wszystkich obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-127">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects.</span></span> <span data-ttu-id="b2c8c-128">W tym przypadku <xref:System.Windows.Vector.X%2A> jest -4, i <xref:System.Windows.Vector.Y%2A> jest -4.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-128">In this case, <xref:System.Windows.Vector.X%2A> is -4, and <xref:System.Windows.Vector.Y%2A> is -4.</span></span> <span data-ttu-id="b2c8c-129">Wartości przesunięcia są wartości ujemnych, ponieważ obiekt nadrzędny negatywny jest przesuwane względem jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b2c8c-129">The offset values are negative values, since the parent object is negatively offset relative to its child object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c8c-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2c8c-130">See also</span></span>

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="b2c8c-131">Renderowanie grafiki WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="b2c8c-131">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
