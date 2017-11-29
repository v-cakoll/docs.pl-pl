---
title: "Jak narysować prostokąt"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c163897af27c9b34c8cd87a3b197047f86d21ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="f1c1b-102">Jak narysować prostokąt</span><span class="sxs-lookup"><span data-stu-id="f1c1b-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="f1c1b-103">W tym przykładzie pokazano, jak narysować prostokąt przy użyciu <xref:System.Windows.Shapes.Rectangle> elementu.</span><span class="sxs-lookup"><span data-stu-id="f1c1b-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="f1c1b-104">Aby narysować prostokąt, Utwórz <xref:System.Windows.Shapes.Rectangle> element i określ jej <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1c1b-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="f1c1b-105">Namalować wnętrze prostokąta, ustaw jej <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1c1b-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="f1c1b-106">Aby dać prostokąt konspektu, użyj jej <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1c1b-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="f1c1b-107">Aby dać prostokąt zaokrąglone narożniki, określ opcjonalny <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1c1b-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="f1c1b-108"><xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości ustawione promień osi x i y elipsy używanej do zaokrąglania narożników prostokąta.</span><span class="sxs-lookup"><span data-stu-id="f1c1b-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="f1c1b-109">W poniższym przykładzie dwa <xref:System.Windows.Shapes.Rectangle> elementy są rysowane <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="f1c1b-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="f1c1b-110">Pierwszy prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="f1c1b-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="f1c1b-111">Drugi prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> wewnętrzne, <xref:System.Windows.Media.Brushes.Black%2A> konspektu i zaokrąglone narożniki.</span><span class="sxs-lookup"><span data-stu-id="f1c1b-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1c1b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1c1b-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="f1c1b-113">Mimo że w tym przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają prostokątów, można użyć elementów prostokąt (i inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> obsługujący nietekstowych zawartość.</span><span class="sxs-lookup"><span data-stu-id="f1c1b-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="f1c1b-114">W rzeczywistości prostokąty są szczególnie użyteczne w przypadku zapewnienia tła części <xref:System.Windows.Controls.Grid> paneli.</span><span class="sxs-lookup"><span data-stu-id="f1c1b-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="f1c1b-115">Na przykład zobacz [omówienie tabeli](../../../../docs/framework/wpf/advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f1c1b-115">For an example, see the [Table Overview](../../../../docs/framework/wpf/advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="f1c1b-116">Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="f1c1b-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c1b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1c1b-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Rectangle>  
 [<span data-ttu-id="f1c1b-118">Przykładowe elementy kształtu</span><span class="sxs-lookup"><span data-stu-id="f1c1b-118">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [<span data-ttu-id="f1c1b-119">Kształty i podstawowe rysunek w omówieniu WPF</span><span class="sxs-lookup"><span data-stu-id="f1c1b-119">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="f1c1b-120">Przegląd tabeli</span><span class="sxs-lookup"><span data-stu-id="f1c1b-120">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
