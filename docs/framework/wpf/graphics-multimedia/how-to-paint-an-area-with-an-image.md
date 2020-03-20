---
title: Jak malować obszar za pomocą obrazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 92969778c04c6ac634a2964c402d6c3439b96b49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186053"
---
# <a name="how-to-paint-an-area-with-an-image"></a><span data-ttu-id="4ee60-102">Jak malować obszar za pomocą obrazu</span><span class="sxs-lookup"><span data-stu-id="4ee60-102">How to: Paint an Area with an Image</span></span>
<span data-ttu-id="4ee60-103">W tym przykładzie <xref:System.Windows.Media.ImageBrush> pokazano, jak używać klasy do malowania obszaru obrazem.</span><span class="sxs-lookup"><span data-stu-id="4ee60-103">This example shows how to use the <xref:System.Windows.Media.ImageBrush> class to paint an area with an image.</span></span> <span data-ttu-id="4ee60-104">Wyświetla <xref:System.Windows.Media.ImageBrush> pojedynczy obraz, który jest <xref:System.Windows.Media.ImageBrush.ImageSource%2A> określony przez jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ee60-104">An <xref:System.Windows.Media.ImageBrush> displays a single image, which is specified by its <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ee60-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ee60-105">Example</span></span>  
 <span data-ttu-id="4ee60-106">Poniższy przykład maluje <xref:System.Windows.Controls.Control.Background%2A> przycisk za <xref:System.Windows.Media.ImageBrush>pomocą .</span><span class="sxs-lookup"><span data-stu-id="4ee60-106">The following example paints the <xref:System.Windows.Controls.Control.Background%2A> of a button by using an <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 <span data-ttu-id="4ee60-107">Domyślnie jego <xref:System.Windows.Media.ImageBrush> obraz jest rozciągany, aby całkowicie wypełnić malowane go miejsce.</span><span class="sxs-lookup"><span data-stu-id="4ee60-107">By default, an <xref:System.Windows.Media.ImageBrush> stretches its image to completely fill the area that you are painting.</span></span> <span data-ttu-id="4ee60-108">W poprzednim przykładzie obraz jest rozciągnięty, aby wypełnić przycisk, co może zniekształcić obraz.</span><span class="sxs-lookup"><span data-stu-id="4ee60-108">In the preceding example, the image is stretched to fill the button, possibly distorting the image.</span></span> <span data-ttu-id="4ee60-109">To zachowanie można kontrolować, <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawiając <xref:System.Windows.Media.Stretch.Uniform> <xref:System.Windows.Media.Stretch.UniformToFill>właściwość <xref:System.Windows.Media.TileBrush> do lub , co powoduje, że pędzel zachowuje proporcje obrazu.</span><span class="sxs-lookup"><span data-stu-id="4ee60-109">You can control this behavior by setting the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of <xref:System.Windows.Media.TileBrush> to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>, which causes the brush to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="4ee60-110">Jeśli <xref:System.Windows.Media.TileBrush.Viewport%2A> ustawisz <xref:System.Windows.Media.TileBrush.TileMode%2A> i właściwości <xref:System.Windows.Media.ImageBrush>elementu , można utworzyć wzorzec powtarzalny.</span><span class="sxs-lookup"><span data-stu-id="4ee60-110">If you set the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties of an <xref:System.Windows.Media.ImageBrush>, you can create a repeating pattern.</span></span> <span data-ttu-id="4ee60-111">Poniższy przykład maluje przycisk przy użyciu wzoru, który jest tworzony na podstawie obrazu.</span><span class="sxs-lookup"><span data-stu-id="4ee60-111">The following example paints a button by using a pattern that is created from an image.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <span data-ttu-id="4ee60-112">Aby uzyskać więcej <xref:System.Windows.Media.ImageBrush> informacji na temat klasy, zobacz [Malowanie obrazami, rysunkami i wizualizacjami](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="4ee60-112">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="4ee60-113">W tym przykładzie kodu jest częścią większego <xref:System.Windows.Media.ImageBrush> przykładu, który jest dostarczany dla klasy.</span><span class="sxs-lookup"><span data-stu-id="4ee60-113">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="4ee60-114">Aby uzyskać pełną próbkę, zobacz [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span><span class="sxs-lookup"><span data-stu-id="4ee60-114">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ee60-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ee60-115">See also</span></span>

- [<span data-ttu-id="4ee60-116">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="4ee60-116">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
