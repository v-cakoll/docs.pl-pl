---
title: Jak rysować tekst do Visual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: 654bfadb42f053b6dcf353d4423bddf281d69478
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094556"
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="9d57c-102">Jak rysować tekst do Visual</span><span class="sxs-lookup"><span data-stu-id="9d57c-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="9d57c-103">Poniższy przykład przedstawia sposób rysowania tekstu do <xref:System.Windows.Media.DrawingVisual> przy użyciu obiektu <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="9d57c-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="9d57c-104">Kontekst rysowania jest zwracany przez wywołanie metody <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> obiektu <xref:System.Windows.Media.DrawingVisual>.</span><span class="sxs-lookup"><span data-stu-id="9d57c-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="9d57c-105">Możesz narysować grafikę i tekst w kontekście rysowania.</span><span class="sxs-lookup"><span data-stu-id="9d57c-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="9d57c-106">Aby narysować tekst w kontekście rysowania, użyj metody <xref:System.Windows.Media.DrawingContext.DrawText%2A> obiektu <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="9d57c-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="9d57c-107">Po zakończeniu rysowania zawartości w kontekście rysowania Wywołaj metodę <xref:System.Windows.Media.DrawingContext.Close%2A>, aby zamknąć kontekst rysowania i zachować zawartość.</span><span class="sxs-lookup"><span data-stu-id="9d57c-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d57c-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d57c-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="9d57c-109">Aby uzyskać kompletny przykład kodu, z którego został wyodrębniony poprzedni przykład kodu, zobacz [test trafień za pomocą przykładu DrawingVisuals](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).</span><span class="sxs-lookup"><span data-stu-id="9d57c-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).</span></span>
