---
title: "Jak ustawić rozmiar sąsiadujących kafelków dla TileBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 484419c05c3d607212ea6d565777cf49cbfdbc19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="33f9e-102">Jak ustawić rozmiar sąsiadujących kafelków dla TileBrush</span><span class="sxs-lookup"><span data-stu-id="33f9e-102">How to: Set the Tile Size for a TileBrush</span></span>
<span data-ttu-id="33f9e-103">W tym przykładzie pokazano, jak ustawić rozmiar kafelka <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="33f9e-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="33f9e-104">Domyślnie <xref:System.Windows.Media.TileBrush> tworzy pojedynczy fragment, który całkowicie wypełnienia malowanego obszaru.</span><span class="sxs-lookup"><span data-stu-id="33f9e-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="33f9e-105">To zachowanie można przesłonić, ustawiając <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="33f9e-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>  
  
 <span data-ttu-id="33f9e-106"><xref:System.Windows.Media.TileBrush.Viewport%2A> Właściwość określa rozmiar kafelka <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="33f9e-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="33f9e-107">Domyślnie wartość <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwość jest określana względem rozmiar obszaru są rysowane.</span><span class="sxs-lookup"><span data-stu-id="33f9e-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="33f9e-108">Aby <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwości określ rozmiar kafelka bezwzględne, ustaw <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="33f9e-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33f9e-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="33f9e-109">Example</span></span>  
 <span data-ttu-id="33f9e-110">W poniższym przykładzie użyto <xref:System.Windows.Media.ImageBrush>, typ <xref:System.Windows.Media.TileBrush>, namalować prostokąt z kafelków.</span><span class="sxs-lookup"><span data-stu-id="33f9e-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="33f9e-111">W przykładzie każdego kafelka na 50 procent 50 procent obszaru wyjściowego (prostokąt).</span><span class="sxs-lookup"><span data-stu-id="33f9e-111">The example sets each tile to  50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="33f9e-112">W związku z tym prostokąt jest malowany cztery projekcje obrazu.</span><span class="sxs-lookup"><span data-stu-id="33f9e-112">As a result, the rectangle is painted with four projections of the image.</span></span>  
  
 <span data-ttu-id="33f9e-113">Na poniższej ilustracji przedstawiono przykład tworzy dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="33f9e-113">The following illustration shows the output that the example produces.</span></span>
  
 <span data-ttu-id="33f9e-114">![Przykład kafelków za pomocą pędzla obrazu](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span><span class="sxs-lookup"><span data-stu-id="33f9e-114">![Example of tiling with an image brush](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 <span data-ttu-id="33f9e-115">W następnym przykładzie jest tworzony <xref:System.Windows.Media.ImageBrush>, ustawia jego <xref:System.Windows.Media.TileBrush.Viewport%2A> do `0,0,25,25` i jego <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> do <xref:System.Windows.Media.BrushMappingMode.Absolute>i używa go do malowania innego prostokąta.</span><span class="sxs-lookup"><span data-stu-id="33f9e-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="33f9e-116">W związku z tym pędzla tworzy Kafelki, które mają 25 pikseli szerokości i wysokości 25 pikseli.</span><span class="sxs-lookup"><span data-stu-id="33f9e-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>  
  
 <span data-ttu-id="33f9e-117">Na poniższej ilustracji przedstawiono przykład tworzy dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="33f9e-117">The following illustration shows the output that the example produces.</span></span>  
  
 <span data-ttu-id="33f9e-118">![A sąsiadująco obiekt TileBrush z 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span><span class="sxs-lookup"><span data-stu-id="33f9e-118">![A tiled TileBrush with a Viewport of 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 <span data-ttu-id="33f9e-119">Powyższych przykładach są częścią większego przykładu.</span><span class="sxs-lookup"><span data-stu-id="33f9e-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="33f9e-120">Pełny przykład, zobacz [próbki ImageBrush](http://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="33f9e-120">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
 <span data-ttu-id="33f9e-121">Mimo że w tym przykładzie użyto <xref:System.Windows.Media.ImageBrush> klasy <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości zachowują się tak samo dla pozostałych <xref:System.Windows.Media.TileBrush> obiekty, oznacza to, że dla <xref:System.Windows.Media.DrawingBrush> i <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="33f9e-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="33f9e-122">Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> i innych <xref:System.Windows.Media.TileBrush> obiekty, zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="33f9e-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f9e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33f9e-123">See Also</span></span>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="33f9e-124">Malowanie obrazów, rysunki i elementy wizualne</span><span class="sxs-lookup"><span data-stu-id="33f9e-124">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="33f9e-125">Utwórz kafelka różnych wzorców z element TileBrush</span><span class="sxs-lookup"><span data-stu-id="33f9e-125">Create Different Tile Patterns with a TileBrush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
