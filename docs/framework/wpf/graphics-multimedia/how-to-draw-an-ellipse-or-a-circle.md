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
ms.openlocfilehash: 5f17615da4907cba6e25b68f2f934602c2f8a390
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452925"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="1555b-102">Jak narysować elipsę na okręgu</span><span class="sxs-lookup"><span data-stu-id="1555b-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="1555b-103">Ten przykład pokazuje, jak rysować wielokropek i okręgi przy użyciu elementu <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="1555b-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="1555b-104">Aby narysować wielokropek, Utwórz element <xref:System.Windows.Shapes.Ellipse> i określ jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="1555b-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="1555b-105">Użyj właściwości <xref:System.Windows.Shapes.Shape.Fill%2A>, aby określić <xref:System.Windows.Media.Brush> używany do malowania wnętrza wielokropka.</span><span class="sxs-lookup"><span data-stu-id="1555b-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="1555b-106">Użyj właściwości <xref:System.Windows.Shapes.Shape.Stroke%2A>, aby określić <xref:System.Windows.Media.Brush> używany do malowania konturu elipsy.</span><span class="sxs-lookup"><span data-stu-id="1555b-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="1555b-107">Właściwość <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> określa grubość konturu elipsy.</span><span class="sxs-lookup"><span data-stu-id="1555b-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="1555b-108">Aby narysować okrąg, <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> elementu <xref:System.Windows.Shapes.Ellipse> być równe siebie.</span><span class="sxs-lookup"><span data-stu-id="1555b-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="1555b-109">Poniższy przykład rysuje cztery <xref:System.Windows.Shapes.Ellipse> elementy w <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="1555b-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1555b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1555b-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="1555b-111">Chociaż w tym przykładzie użyto <xref:System.Windows.Controls.Canvas>, aby zawierać wielokropek, można użyć elementów wielokropka (i wszystkich innych elementów kształtu) z dowolnym <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> obsługującym zawartość nietekstową.</span><span class="sxs-lookup"><span data-stu-id="1555b-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="1555b-112">Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="1555b-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1555b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1555b-113">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="1555b-114">Przykładowe elementy kształtu</span><span class="sxs-lookup"><span data-stu-id="1555b-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
