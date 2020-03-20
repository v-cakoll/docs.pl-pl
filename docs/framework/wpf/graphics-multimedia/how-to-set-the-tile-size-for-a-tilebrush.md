---
title: Jak ustawić rozmiar sąsiadujących kafelków dla TileBrush
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186834"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="c314b-102">Jak ustawić rozmiar sąsiadujących kafelków dla TileBrush</span><span class="sxs-lookup"><span data-stu-id="c314b-102">How to: Set the Tile Size for a TileBrush</span></span>

<span data-ttu-id="c314b-103">W tym przykładzie pokazano, jak <xref:System.Windows.Media.TileBrush>ustawić rozmiar kafelka dla pliku .</span><span class="sxs-lookup"><span data-stu-id="c314b-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="c314b-104">Domyślnie tworzy <xref:System.Windows.Media.TileBrush> pojedynczy kafelek, który całkowicie wypełnia obszar, który malujesz.</span><span class="sxs-lookup"><span data-stu-id="c314b-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="c314b-105">To zachowanie można zastąpić, <xref:System.Windows.Media.TileBrush.Viewport%2A> ustawiając <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości i.</span><span class="sxs-lookup"><span data-stu-id="c314b-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>

<span data-ttu-id="c314b-106">Właściwość <xref:System.Windows.Media.TileBrush.Viewport%2A> określa rozmiar kafelka <xref:System.Windows.Media.TileBrush>dla .</span><span class="sxs-lookup"><span data-stu-id="c314b-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="c314b-107">Domyślnie wartość <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwości jest względem rozmiaru obszaru malowanego.</span><span class="sxs-lookup"><span data-stu-id="c314b-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="c314b-108">Aby <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwość określała bezwzględny rozmiar <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> kafelka, ustaw właściwość na <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="c314b-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>

## <a name="example"></a><span data-ttu-id="c314b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c314b-109">Example</span></span>

<span data-ttu-id="c314b-110">W poniższym przykładzie <xref:System.Windows.Media.ImageBrush>użyto <xref:System.Windows.Media.TileBrush>, typu , do malowania prostokąta kafelkami.</span><span class="sxs-lookup"><span data-stu-id="c314b-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="c314b-111">W przykładzie ustawia każdy kafelek na 50 procent przez 50 procent obszaru wyjściowego (prostokąt).</span><span class="sxs-lookup"><span data-stu-id="c314b-111">The example sets each tile to 50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="c314b-112">W rezultacie prostokąt jest malowany czterema projekcjami obrazu.</span><span class="sxs-lookup"><span data-stu-id="c314b-112">As a result, the rectangle is painted with four projections of the image.</span></span>

<span data-ttu-id="c314b-113">Na poniższej ilustracji przedstawiono dane wyjściowe, które daje przykład:</span><span class="sxs-lookup"><span data-stu-id="c314b-113">The following illustration shows the output that the example produces:</span></span>

![Prostokąt z czterema wiśniami demonstrującymi układanie za pomocą pędzla obrazu.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

<span data-ttu-id="c314b-115">W <xref:System.Windows.Media.ImageBrush>następnym przykładzie tworzy <xref:System.Windows.Media.TileBrush.Viewport%2A> `0,0,25,25` , <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> ustawia <xref:System.Windows.Media.BrushMappingMode.Absolute>jego do i jego do , i używa go do malowania innego prostokąta.</span><span class="sxs-lookup"><span data-stu-id="c314b-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="c314b-116">W rezultacie pędzel tworzy płytki o szerokości 25 pikseli i wysokości 25 pikseli.</span><span class="sxs-lookup"><span data-stu-id="c314b-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>

<span data-ttu-id="c314b-117">Na poniższej ilustracji przedstawiono dane wyjściowe, które daje przykład:</span><span class="sxs-lookup"><span data-stu-id="c314b-117">The following illustration shows the output that the example produces:</span></span>

![Prostokąt z czterdziestu ośmiu wiśni demonstrujących płytki wyłożone kafelkamiBrush z Viewport.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

<span data-ttu-id="c314b-119">Powyższe przykłady są częścią większej próbki.</span><span class="sxs-lookup"><span data-stu-id="c314b-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="c314b-120">Aby uzyskać pełną próbkę, zobacz [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span><span class="sxs-lookup"><span data-stu-id="c314b-120">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>

<span data-ttu-id="c314b-121">Chociaż w tym <xref:System.Windows.Media.ImageBrush> przykładzie <xref:System.Windows.Media.TileBrush.Viewport%2A> używa <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> klasy, i właściwości <xref:System.Windows.Media.TileBrush> zachowują się identycznie <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>dla innych obiektów, czyli dla i .</span><span class="sxs-lookup"><span data-stu-id="c314b-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="c314b-122">Aby uzyskać <xref:System.Windows.Media.ImageBrush> więcej informacji <xref:System.Windows.Media.TileBrush> o i innych obiektach, zobacz [Malowanie obrazami, rysunkami i wizualizacjami](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="c314b-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c314b-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c314b-123">See also</span></span>

- <xref:System.Windows.Media.TileBrush>
- [<span data-ttu-id="c314b-124">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="c314b-124">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="c314b-125">Tworzenie różnych wzorów kafelkowych z użyciem elementu TileBrush</span><span class="sxs-lookup"><span data-stu-id="c314b-125">Create Different Tile Patterns with a TileBrush</span></span>](how-to-create-different-tile-patterns-with-a-tilebrush.md)
