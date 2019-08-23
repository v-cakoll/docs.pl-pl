---
title: 'Instrukcje: Rysowanie tekstu w wizualizacji'
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
ms.openlocfilehash: bd760a06150098d0fff17dbdce95b55a0e5fe713
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963847"
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="973c1-102">Instrukcje: Rysowanie tekstu w wizualizacji</span><span class="sxs-lookup"><span data-stu-id="973c1-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="973c1-103">Poniższy przykład pokazuje, jak narysować tekst w <xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.Media.DrawingContext> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="973c1-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="973c1-104">Kontekst rysowania jest zwracany przez wywołanie <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metody <xref:System.Windows.Media.DrawingVisual> obiektu.</span><span class="sxs-lookup"><span data-stu-id="973c1-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="973c1-105">Możesz narysować grafikę i tekst w kontekście rysowania.</span><span class="sxs-lookup"><span data-stu-id="973c1-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="973c1-106">Aby narysować tekst w kontekście rysowania, użyj <xref:System.Windows.Media.DrawingContext.DrawText%2A> metody <xref:System.Windows.Media.DrawingContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="973c1-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="973c1-107">Po zakończeniu rysowania zawartości w kontekście rysowania Wywołaj <xref:System.Windows.Media.DrawingContext.Close%2A> metodę, aby zamknąć kontekst rysowania i zachować zawartość.</span><span class="sxs-lookup"><span data-stu-id="973c1-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="973c1-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="973c1-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="973c1-109">Aby uzyskać kompletny przykład kodu, z którego został wyodrębniony poprzedni przykład kodu, zobacz [test trafień za pomocą przykładu DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).</span><span class="sxs-lookup"><span data-stu-id="973c1-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).</span></span>
