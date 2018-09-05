---
title: Jak narysować elipsę na okręgu
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: ddeada8619d1b6c8970f1efb7cca1bc98773d0c5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43660384"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="6e036-102">Jak narysować elipsę na okręgu</span><span class="sxs-lookup"><span data-stu-id="6e036-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="6e036-103">W tym przykładzie pokazano, jak Rysowanie elips i okręgów przy użyciu <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="6e036-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="6e036-104">Aby narysować elipsę, należy utworzyć <xref:System.Windows.Shapes.Ellipse> elementu i określ jej <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e036-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="6e036-105">Użyj jego <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości w celu określenia <xref:System.Windows.Media.Brush> umożliwiający namalować wnętrze elipsy.</span><span class="sxs-lookup"><span data-stu-id="6e036-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="6e036-106">Użyj jego <xref:System.Windows.Shapes.Shape.Stroke%2A> właściwości w celu określenia <xref:System.Windows.Media.Brush> używany namalować kontur elipsy.</span><span class="sxs-lookup"><span data-stu-id="6e036-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="6e036-107"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A> Właściwość określa grubość konturu elipsy.</span><span class="sxs-lookup"><span data-stu-id="6e036-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="6e036-108">Aby narysować okrąg, <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Shapes.Ellipse> element równy ze sobą.</span><span class="sxs-lookup"><span data-stu-id="6e036-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="6e036-109">Poniższy przykład pobiera cztery <xref:System.Windows.Shapes.Ellipse> elementów w obrębie <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="6e036-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e036-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e036-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="6e036-111">Mimo że w tym przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają wielokropek, można użyć elementów wielokropka (i wszystkie inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> , która obsługuje zawartość nietekstową.</span><span class="sxs-lookup"><span data-stu-id="6e036-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="6e036-112">W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="6e036-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e036-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e036-113">See Also</span></span>  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [<span data-ttu-id="6e036-114">Przykładowe elementy kształtu</span><span class="sxs-lookup"><span data-stu-id="6e036-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
