---
title: Jak narysować prostokąt
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 95191e9d90bc2ac32902399125d9a51192e897bf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452938"
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="cdaa3-102">Jak narysować prostokąt</span><span class="sxs-lookup"><span data-stu-id="cdaa3-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="cdaa3-103">Ten przykład pokazuje, jak narysować prostokąt przy użyciu elementu <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="cdaa3-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="cdaa3-104">Aby narysować prostokąt, Utwórz element <xref:System.Windows.Shapes.Rectangle> i określ jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdaa3-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="cdaa3-105">Aby malować wewnątrz prostokąta, ustaw jego <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdaa3-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="cdaa3-106">Aby nadać prostokątowi konspekt, użyj jego właściwości <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdaa3-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="cdaa3-107">Aby nadać prostokątom Zaokrąglone rogi, określ opcjonalne <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cdaa3-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="cdaa3-108">Właściwości <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> ustawiają promienie osi x i y wielokropka, która jest używana do zaokrąglania rogów prostokąta.</span><span class="sxs-lookup"><span data-stu-id="cdaa3-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="cdaa3-109">W poniższym przykładzie dwa elementy <xref:System.Windows.Shapes.Rectangle> są rysowane w <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="cdaa3-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="cdaa3-110">Pierwszy prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="cdaa3-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="cdaa3-111">Drugi prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> wnętrze, <xref:System.Windows.Media.Brushes.Black%2A> Konspekt i zaokrąglone rogi.</span><span class="sxs-lookup"><span data-stu-id="cdaa3-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdaa3-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="cdaa3-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="cdaa3-113">Mimo że w tym przykładzie użyto <xref:System.Windows.Controls.Canvas>, aby zawierać prostokąty, można użyć elementów prostokąta (i wszystkich innych elementów kształtu) z dowolnym <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control>, które obsługują zawartość inną niż tekst.</span><span class="sxs-lookup"><span data-stu-id="cdaa3-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="cdaa3-114">W rzeczywistości prostokąty są szczególnie przydatne do udostępniania tła dla części paneli <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="cdaa3-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="cdaa3-115">Aby zapoznać się z przykładem, zobacz sekcję [Omówienie tabeli](../advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cdaa3-115">For an example, see the [Table Overview](../advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="cdaa3-116">Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="cdaa3-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdaa3-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cdaa3-117">See also</span></span>

- <xref:System.Windows.Shapes.Rectangle>
- [<span data-ttu-id="cdaa3-118">Przykładowe elementy kształtu</span><span class="sxs-lookup"><span data-stu-id="cdaa3-118">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="cdaa3-119">Kształty i podstawowe rysowanie w programie WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="cdaa3-119">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="cdaa3-120">Omówienie tabel</span><span class="sxs-lookup"><span data-stu-id="cdaa3-120">Table Overview</span></span>](../advanced/table-overview.md)
