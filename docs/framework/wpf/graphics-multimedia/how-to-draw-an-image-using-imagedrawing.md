---
title: 'Instrukcje: Rysuj obraz z użyciem ImageDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: 5c1617d1a60fde8e9f1c215a5b644f6fd330817a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629075"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a><span data-ttu-id="1418e-102">Instrukcje: Rysuj obraz z użyciem ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="1418e-102">How to: Draw an Image Using ImageDrawing</span></span>
<span data-ttu-id="1418e-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.ImageDrawing> do rysowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="1418e-103">This example shows how to use an <xref:System.Windows.Media.ImageDrawing> to draw an image.</span></span> <span data-ttu-id="1418e-104"><xref:System.Windows.Media.ImageDrawing> Umożliwia możesz wyświetlić <xref:System.Windows.Media.ImageSource> z <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, lub <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="1418e-104">An <xref:System.Windows.Media.ImageDrawing> enables you display an <xref:System.Windows.Media.ImageSource> with a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="1418e-105">Aby narysować obrazu, należy utworzyć <xref:System.Windows.Media.ImageDrawing> i ustaw jego <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1418e-105">To draw an image, you create an <xref:System.Windows.Media.ImageDrawing> and set its <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> and <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="1418e-106"><xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Właściwości Określa obraz do rysowania i <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> właściwość określa położenie i rozmiar każdego obrazu.</span><span class="sxs-lookup"><span data-stu-id="1418e-106">The <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> property specifies the image to draw, and the <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> property specifies the position and size of each image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1418e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1418e-107">Example</span></span>  
 <span data-ttu-id="1418e-108">Poniższy przykład obejmuje tworzenie złożonego rysunku przy użyciu czterech <xref:System.Windows.Media.ImageDrawing> obiektów.</span><span class="sxs-lookup"><span data-stu-id="1418e-108">The following example creates a composite drawing using four <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="1418e-109">Ten przykład generuje poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="1418e-109">This example produces the following image:</span></span>  
  
 <span data-ttu-id="1418e-110">![Niektóre obiekty DrawingImage](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span><span class="sxs-lookup"><span data-stu-id="1418e-110">![Several DrawingImage objects](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span></span>  
<span data-ttu-id="1418e-111">Cztery ImageDrawing — obiekty</span><span class="sxs-lookup"><span data-stu-id="1418e-111">Four ImageDrawing objects</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <span data-ttu-id="1418e-112">Na przykład przedstawiający prosty sposób wyświetlania obrazu bez użycia <xref:System.Windows.Media.ImageDrawing>, zobacz [Użyj elementu obrazu](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span><span class="sxs-lookup"><span data-stu-id="1418e-112">For an example showing a simple way to display an image without using <xref:System.Windows.Media.ImageDrawing>, see [Use the Image Element](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1418e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1418e-113">See also</span></span>
- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [<span data-ttu-id="1418e-114">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="1418e-114">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="1418e-115">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="1418e-115">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [<span data-ttu-id="1418e-116">PresentationOptions:Freeze, atrybut</span><span class="sxs-lookup"><span data-stu-id="1418e-116">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
