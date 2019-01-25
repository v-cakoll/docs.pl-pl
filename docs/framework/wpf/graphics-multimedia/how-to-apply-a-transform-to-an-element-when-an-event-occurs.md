---
title: 'Instrukcje: Zastosuj przekształcenie do elementu kiedy wystąpi zdarzenie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: 3862ffcb8e0dcabd2de67c495204470ac9fa6c14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726393"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a><span data-ttu-id="4625a-102">Instrukcje: Zastosuj przekształcenie do elementu kiedy wystąpi zdarzenie</span><span class="sxs-lookup"><span data-stu-id="4625a-102">How to: Apply a Transform to an Element When an Event Occurs</span></span>
<span data-ttu-id="4625a-103">Ten przykład przedstawia sposób zastosowania <xref:System.Windows.Media.ScaleTransform> po wystąpieniu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4625a-103">This example shows how to apply a <xref:System.Windows.Media.ScaleTransform> when an event occurs.</span></span> <span data-ttu-id="4625a-104">Pojęcia, która jest wyświetlana w tym miejscu jest taka sama, używanej do stosowania innych rodzajów przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="4625a-104">The concept that is shown here is the same that you use for applying other types of transformations.</span></span> <span data-ttu-id="4625a-105">Aby uzyskać więcej informacji na temat dostępnych typów przekształcenia zobacz <xref:System.Windows.Media.Transform> klasy lub [przekształca Przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4625a-105">For more information about the available types of transformations, see the <xref:System.Windows.Media.Transform> class or [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>  
  
 <span data-ttu-id="4625a-106">Należy zastosować przekształcenie do elementu w jeden z następujących dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="4625a-106">You can apply a transform to an element in either of these two ways:</span></span>  
  
-   <span data-ttu-id="4625a-107">Jeśli to zrobisz *nie* ma przekształcenia wpływają na układ, należy użyć <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu.</span><span class="sxs-lookup"><span data-stu-id="4625a-107">If you do *not* want the transform to affect layout, use the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
-   <span data-ttu-id="4625a-108">Przekształcanie wpływ na układ, użyć <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości elementu.</span><span class="sxs-lookup"><span data-stu-id="4625a-108">If you do want the transform to affect layout, use the <xref:System.Windows.FrameworkElement.LayoutTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="4625a-109">Następujący przykład dotyczy <xref:System.Windows.Media.ScaleTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość przycisku.</span><span class="sxs-lookup"><span data-stu-id="4625a-109">The following example applies a <xref:System.Windows.Media.ScaleTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a button.</span></span> <span data-ttu-id="4625a-110">Gdy wskaźnik myszy porusza się na przycisku <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości <xref:System.Windows.Media.ScaleTransform> są ustawione na `2`, co powoduje, że przycisk aby stać się zbyt duży.</span><span class="sxs-lookup"><span data-stu-id="4625a-110">When the mouse moves over the button, the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties of the <xref:System.Windows.Media.ScaleTransform> are set to `2`, which causes the button to become larger.</span></span> <span data-ttu-id="4625a-111">Gdy wskaźnik myszy przesunięty, poza <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> są ustawione na `1`, co powoduje, że przycisk, aby powrócić do oryginalnego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="4625a-111">When the mouse moves off the button, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> are set to `1`, which causes the button to return to its original size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4625a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="4625a-112">Example</span></span>  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a><span data-ttu-id="4625a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4625a-113">See also</span></span>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="4625a-114">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="4625a-114">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [<span data-ttu-id="4625a-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="4625a-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
- [<span data-ttu-id="4625a-116">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="4625a-116">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
