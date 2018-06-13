---
title: Jak rysować obraz z użyciem ImageDrawing
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: 2c7771f841fb3b600d4790eb4d484b0a09c45dd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559882"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a><span data-ttu-id="1ea2c-102">Jak rysować obraz z użyciem ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="1ea2c-102">How to: Draw an Image Using ImageDrawing</span></span>
<span data-ttu-id="1ea2c-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.ImageDrawing> do rysowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="1ea2c-103">This example shows how to use an <xref:System.Windows.Media.ImageDrawing> to draw an image.</span></span> <span data-ttu-id="1ea2c-104"><xref:System.Windows.Media.ImageDrawing> Umożliwia wyświetlania <xref:System.Windows.Media.ImageSource> z <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, lub <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="1ea2c-104">An <xref:System.Windows.Media.ImageDrawing> enables you display an <xref:System.Windows.Media.ImageSource> with a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="1ea2c-105">Aby narysować obrazu, należy utworzyć <xref:System.Windows.Media.ImageDrawing> i ustawić jej <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1ea2c-105">To draw an image, you create an <xref:System.Windows.Media.ImageDrawing> and set its <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> and <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="1ea2c-106"><xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Właściwość określa obraz do rysowania i <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> właściwość określa położenie i rozmiar każdego obrazu.</span><span class="sxs-lookup"><span data-stu-id="1ea2c-106">The <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> property specifies the image to draw, and the <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> property specifies the position and size of each image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ea2c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ea2c-107">Example</span></span>  
 <span data-ttu-id="1ea2c-108">Poniższy przykład tworzy rysunek złożonego za pomocą czterech <xref:System.Windows.Media.ImageDrawing> obiektów.</span><span class="sxs-lookup"><span data-stu-id="1ea2c-108">The following example creates a composite drawing using four <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="1ea2c-109">W tym przykładzie powoduje poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="1ea2c-109">This example produces the following image:</span></span>  
  
 <span data-ttu-id="1ea2c-110">![Niektóre obiekty DrawingImage](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span><span class="sxs-lookup"><span data-stu-id="1ea2c-110">![Several DrawingImage objects](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span></span>  
<span data-ttu-id="1ea2c-111">Cztery obiektów Obiekt ImageDrawing o rozmiarze</span><span class="sxs-lookup"><span data-stu-id="1ea2c-111">Four ImageDrawing objects</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <span data-ttu-id="1ea2c-112">Na przykład przedstawiający prosty sposób wyświetlania obrazu bez użycia <xref:System.Windows.Media.ImageDrawing>, zobacz [, korzystając z obrazu elementu](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span><span class="sxs-lookup"><span data-stu-id="1ea2c-112">For an example showing a simple way to display an image without using <xref:System.Windows.Media.ImageDrawing>, see [Use the Image Element](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea2c-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ea2c-113">See Also</span></span>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 <xref:System.Windows.Controls.Image>  
 [<span data-ttu-id="1ea2c-114">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="1ea2c-114">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="1ea2c-115">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="1ea2c-115">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="1ea2c-116">PresentationOptions:Freeze, atrybut</span><span class="sxs-lookup"><span data-stu-id="1ea2c-116">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
