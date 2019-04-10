---
title: 'Instrukcje: Rysowanie prostokąta'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 261026b994b432565928b38ff1657115ff7cbe4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217357"
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="b4adc-102">Instrukcje: Rysowanie prostokąta</span><span class="sxs-lookup"><span data-stu-id="b4adc-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="b4adc-103">W tym przykładzie pokazano, jak narysować prostokąt przy użyciu <xref:System.Windows.Shapes.Rectangle> elementu.</span><span class="sxs-lookup"><span data-stu-id="b4adc-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="b4adc-104">Aby narysować prostokąt, należy utworzyć <xref:System.Windows.Shapes.Rectangle> elementu i określ jej <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4adc-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="b4adc-105">Namalować wnętrze prostokąt, ustaw jego <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4adc-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="b4adc-106">Aby dać prostokąta konspektu, użyj jej <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b4adc-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="b4adc-107">Aby dać prostokąta zaokrąglone rogi, należy określić opcjonalny <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b4adc-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="b4adc-108"><xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości ustawione promienie osi x i y elipsy używanej do zaokrąglania narożników prostokąta.</span><span class="sxs-lookup"><span data-stu-id="b4adc-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="b4adc-109">W poniższym przykładzie dwa <xref:System.Windows.Shapes.Rectangle> elementy są rysowane <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="b4adc-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="b4adc-110">Pierwszy prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> posługiwanie się nimi.</span><span class="sxs-lookup"><span data-stu-id="b4adc-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="b4adc-111">Drugi prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> posługiwanie się nimi, <xref:System.Windows.Media.Brushes.Black%2A> konspekt i zaokrąglone rogi.</span><span class="sxs-lookup"><span data-stu-id="b4adc-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4adc-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4adc-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="b4adc-113">Mimo że w tym przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają prostokątów, można użyć elementów prostokąt (i wszystkie inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> , która obsługuje zawartość nietekstową.</span><span class="sxs-lookup"><span data-stu-id="b4adc-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="b4adc-114">W rzeczywistości są szczególnie przydatne do prezentowania tła dla części prostokąty <xref:System.Windows.Controls.Grid> paneli.</span><span class="sxs-lookup"><span data-stu-id="b4adc-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="b4adc-115">Aby uzyskać przykład, zobacz [Omówienie tabel](../advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b4adc-115">For an example, see the [Table Overview](../advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="b4adc-116">W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="b4adc-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4adc-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4adc-117">See also</span></span>

- <xref:System.Windows.Shapes.Rectangle>
- [<span data-ttu-id="b4adc-118">Przykładowe elementy kształtu</span><span class="sxs-lookup"><span data-stu-id="b4adc-118">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
- [<span data-ttu-id="b4adc-119">Przegląd Kształty i podstawowe rysowanie w WPF</span><span class="sxs-lookup"><span data-stu-id="b4adc-119">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="b4adc-120">Przegląd Tabela</span><span class="sxs-lookup"><span data-stu-id="b4adc-120">Table Overview</span></span>](../advanced/table-overview.md)
