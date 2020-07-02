---
title: Jak narysować elipsę na okręgu
description: Dowiedz się, jak narysować elipsę lub okrąg z opcjami dla grubości i koloru kolorowego w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: afa0e7d2af42aaee39dca164f23b1a1cacf430ca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853570"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="00cc7-103">Jak narysować elipsę na okręgu</span><span class="sxs-lookup"><span data-stu-id="00cc7-103">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="00cc7-104">Ten przykład pokazuje, jak rysować wielokropek i okręgi przy użyciu <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="00cc7-104">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="00cc7-105">Aby narysować wielokropek, Utwórz <xref:System.Windows.Shapes.Ellipse> element i określ jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> .</span><span class="sxs-lookup"><span data-stu-id="00cc7-105">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="00cc7-106">Użyj swojej <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości, aby określić <xref:System.Windows.Media.Brush> , który jest używany do malowania wnętrza wielokropka.</span><span class="sxs-lookup"><span data-stu-id="00cc7-106">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="00cc7-107">Użyj swojej <xref:System.Windows.Shapes.Shape.Stroke%2A> właściwości, aby określić <xref:System.Windows.Media.Brush> , że jest używany do malowania konturu elipsy.</span><span class="sxs-lookup"><span data-stu-id="00cc7-107">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="00cc7-108"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>Właściwość określa grubość konturu elipsy.</span><span class="sxs-lookup"><span data-stu-id="00cc7-108">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="00cc7-109">Aby narysować okrąg, upewnij się, że <xref:System.Windows.FrameworkElement.Width%2A> elementy i są <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Shapes.Ellipse> równe siebie.</span><span class="sxs-lookup"><span data-stu-id="00cc7-109">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="00cc7-110">Poniższy przykład rysuje cztery <xref:System.Windows.Shapes.Ellipse> elementy w <xref:System.Windows.Controls.Canvas> .</span><span class="sxs-lookup"><span data-stu-id="00cc7-110">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00cc7-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="00cc7-111">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="00cc7-112">Mimo że w tym przykładzie użyto, <xref:System.Windows.Controls.Canvas> aby zawierać wielokropek, można użyć elementów wielokropka (i wszystkich innych elementów kształtu) z dowolnym lub obsługującym <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Control> zawartość nietekstową.</span><span class="sxs-lookup"><span data-stu-id="00cc7-112">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="00cc7-113">Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="00cc7-113">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00cc7-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00cc7-114">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="00cc7-115">Przykładowe elementy kształtu</span><span class="sxs-lookup"><span data-stu-id="00cc7-115">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
