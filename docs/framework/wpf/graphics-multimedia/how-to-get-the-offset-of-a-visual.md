---
title: Jak pobrać przesunięcie Visual
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
ms.openlocfilehash: 97f4de9e2e40840962e4233b1de25843a4b885b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561852"
---
# <a name="how-to-get-the-offset-of-a-visual"></a><span data-ttu-id="ed772-102">Jak pobrać przesunięcie Visual</span><span class="sxs-lookup"><span data-stu-id="ed772-102">How to: Get the Offset of a Visual</span></span>
<span data-ttu-id="ed772-103">Poniższe przykłady pokazują, jak można pobrać wartości przesunięcia względem jego elementu nadrzędnego lub żadnych nadrzędnym lub podrzędnym obiektu visual.</span><span class="sxs-lookup"><span data-stu-id="ed772-103">These examples show how to retrieve the offset value of a visual object that is relative to its parent, or any ancestor or descendant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed772-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed772-104">Example</span></span>  
 <span data-ttu-id="ed772-105">W poniższym przykładzie pokazano kod znaczników <xref:System.Windows.Controls.TextBlock> zdefiniowanego z <xref:System.Windows.FrameworkElement.Margin%2A> o wartości 4.</span><span class="sxs-lookup"><span data-stu-id="ed772-105">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is defined with <xref:System.Windows.FrameworkElement.Margin%2A> value of 4.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 <span data-ttu-id="ed772-106">Poniższy przykładowy kod przedstawia sposób użycia <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> metoda pobierania przesunięcie <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="ed772-106">The following code example shows how to use the <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="ed772-107">Wartości przesunięcia są zawarte w zwróconym <xref:System.Windows.Vector> wartość.</span><span class="sxs-lookup"><span data-stu-id="ed772-107">The offset values are contained within the returned <xref:System.Windows.Vector> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 <span data-ttu-id="ed772-108">Przesunięcie bierze pod uwagę <xref:System.Windows.FrameworkElement.Margin%2A> wartość.</span><span class="sxs-lookup"><span data-stu-id="ed772-108">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> value.</span></span> <span data-ttu-id="ed772-109">W takim przypadku <xref:System.Windows.Vector.X%2A> 4, i <xref:System.Windows.Vector.Y%2A> to 4.</span><span class="sxs-lookup"><span data-stu-id="ed772-109">In this case, <xref:System.Windows.Vector.X%2A> is 4, and <xref:System.Windows.Vector.Y%2A> is 4.</span></span>  
  
 <span data-ttu-id="ed772-110">Zwrócona wartość przesunięcia jest określana względem elementu nadrzędnego <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="ed772-110">The returned offset value is relative to the parent of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="ed772-111">Jeśli chcesz zwrócić wartość przesunięcia, które nie jest określana względem elementu nadrzędnego <xref:System.Windows.Media.Visual>, użyj <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ed772-111">If you want to return an offset value that is not relative to the parent of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a><span data-ttu-id="ed772-112">Pierwsze przesunięcie względem elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="ed772-112">Getting the Offset Relative to an Ancestor</span></span>  
 <span data-ttu-id="ed772-113">W poniższym przykładzie pokazano kod znaczników <xref:System.Windows.Controls.TextBlock> zagnieżdżony w dwóch <xref:System.Windows.Controls.StackPanel> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ed772-113">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is nested within two <xref:System.Windows.Controls.StackPanel> objects.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 <span data-ttu-id="ed772-114">Na poniższej ilustracji przedstawiono wyniki znaczników.</span><span class="sxs-lookup"><span data-stu-id="ed772-114">The following illustration shows the results of the markup.</span></span>  
  
 <span data-ttu-id="ed772-115">![Wartości przesunięcia obiektów](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")</span><span class="sxs-lookup"><span data-stu-id="ed772-115">![Offset values of objects](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")</span></span>  
<span data-ttu-id="ed772-116">W dwóch StackPanels zagnieżdżony blok tekstu</span><span class="sxs-lookup"><span data-stu-id="ed772-116">TextBlock nested within two StackPanels</span></span>  
  
 <span data-ttu-id="ed772-117">Poniższy przykładowy kod przedstawia sposób użycia <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metoda pobierania przesunięcie <xref:System.Windows.Controls.TextBlock> względem zawierający <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="ed772-117">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock> relative to the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="ed772-118">Wartości przesunięcia są zawarte w zwróconym <xref:System.Windows.Media.GeneralTransform> wartość.</span><span class="sxs-lookup"><span data-stu-id="ed772-118">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 <span data-ttu-id="ed772-119">Przesunięcie bierze pod uwagę <xref:System.Windows.FrameworkElement.Margin%2A> wartości dla wszystkich obiektów w ramach zawierający <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="ed772-119">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects within the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="ed772-120">W takim przypadku <xref:System.Windows.Vector.X%2A> jest 28 (16 + 8 + 4), a <xref:System.Windows.Vector.Y%2A> to 28.</span><span class="sxs-lookup"><span data-stu-id="ed772-120">In this case, <xref:System.Windows.Vector.X%2A> is 28 (16 + 8 + 4), and <xref:System.Windows.Vector.Y%2A> is 28.</span></span>  
  
 <span data-ttu-id="ed772-121">Zwrócona wartość przesunięcia jest określana względem element nadrzędny elementu <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="ed772-121">The returned offset value is relative to the ancestor of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="ed772-122">Jeśli chcesz zwrócić wartość przesunięcia względem obiektu podrzędnego z <xref:System.Windows.Media.Visual>, użyj <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ed772-122">If you want to return an offset value that is relative to the descendant of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a><span data-ttu-id="ed772-123">Pierwsze przesunięcie względem element podrzędny</span><span class="sxs-lookup"><span data-stu-id="ed772-123">Getting the Offset Relative to a Descendant</span></span>  
 <span data-ttu-id="ed772-124">W poniższym przykładzie pokazano kod znaczników <xref:System.Windows.Controls.TextBlock> zawarty w <xref:System.Windows.Controls.StackPanel> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ed772-124">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is contained within a <xref:System.Windows.Controls.StackPanel> object.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 <span data-ttu-id="ed772-125">Poniższy przykładowy kod przedstawia sposób użycia <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metoda pobierania przesunięcie <xref:System.Windows.Controls.StackPanel> względem jego podrzędny <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="ed772-125">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method to retrieve the offset of the <xref:System.Windows.Controls.StackPanel> relative to its child <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="ed772-126">Wartości przesunięcia są zawarte w zwróconym <xref:System.Windows.Media.GeneralTransform> wartość.</span><span class="sxs-lookup"><span data-stu-id="ed772-126">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 <span data-ttu-id="ed772-127">Przesunięcie bierze pod uwagę <xref:System.Windows.FrameworkElement.Margin%2A> wartości dla wszystkich obiektów.</span><span class="sxs-lookup"><span data-stu-id="ed772-127">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects.</span></span> <span data-ttu-id="ed772-128">W takim przypadku <xref:System.Windows.Vector.X%2A> jest -4, i <xref:System.Windows.Vector.Y%2A> jest -4.</span><span class="sxs-lookup"><span data-stu-id="ed772-128">In this case, <xref:System.Windows.Vector.X%2A> is -4, and <xref:System.Windows.Vector.Y%2A> is -4.</span></span> <span data-ttu-id="ed772-129">Wartości przesunięcia są wartości ujemnych, ponieważ obiekt nadrzędny negatywnie jest przesuwane względem jego obiektu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ed772-129">The offset values are negative values, since the parent object is negatively offset relative to its child object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed772-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed772-130">See Also</span></span>  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [<span data-ttu-id="ed772-131">Renderowanie grafiki WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="ed772-131">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
