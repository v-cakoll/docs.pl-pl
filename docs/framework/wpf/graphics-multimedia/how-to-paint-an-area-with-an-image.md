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
ms.openlocfilehash: 5899531291c22ada76213905d0f2ca6944fcbba7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857209"
---
# <a name="how-to-paint-an-area-with-an-image"></a><span data-ttu-id="3fee4-102">Jak malować obszar za pomocą obrazu</span><span class="sxs-lookup"><span data-stu-id="3fee4-102">How to: Paint an Area with an Image</span></span>
<span data-ttu-id="3fee4-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.ImageBrush> klasy Maluj obszar za pomocą obrazu.</span><span class="sxs-lookup"><span data-stu-id="3fee4-103">This example shows how to use the <xref:System.Windows.Media.ImageBrush> class to paint an area with an image.</span></span> <span data-ttu-id="3fee4-104"><xref:System.Windows.Media.ImageBrush> Wyświetla pojedynczy obraz, który jest określony przez jego <xref:System.Windows.Media.ImageBrush.ImageSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3fee4-104">An <xref:System.Windows.Media.ImageBrush> displays a single image, which is specified by its <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fee4-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fee4-105">Example</span></span>  
 <span data-ttu-id="3fee4-106">Poniższy przykład farby <xref:System.Windows.Controls.Control.Background%2A> przycisku przy użyciu <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="3fee4-106">The following example paints the <xref:System.Windows.Controls.Control.Background%2A> of a button by using an <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 <span data-ttu-id="3fee4-107">Domyślnie <xref:System.Windows.Media.ImageBrush> rozciąga obraz do całkowitego wypełnienia malowanego obszaru.</span><span class="sxs-lookup"><span data-stu-id="3fee4-107">By default, an <xref:System.Windows.Media.ImageBrush> stretches its image to completely fill the area that you are painting.</span></span> <span data-ttu-id="3fee4-108">W powyższym przykładzie obraz jest rozciągany tak, wypełnienie przycisku, prawdopodobnie zakłócanie obrazu.</span><span class="sxs-lookup"><span data-stu-id="3fee4-108">In the preceding example, the image is stretched to fill the button, possibly distorting the image.</span></span> <span data-ttu-id="3fee4-109">To zachowanie można kontrolować przez ustawienie <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość <xref:System.Windows.Media.TileBrush> do <xref:System.Windows.Media.Stretch.Uniform> lub <xref:System.Windows.Media.Stretch.UniformToFill>, co powoduje, że pędzla zachować współczynnik proporcji obrazu.</span><span class="sxs-lookup"><span data-stu-id="3fee4-109">You can control this behavior by setting the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of <xref:System.Windows.Media.TileBrush> to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>, which causes the brush to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="3fee4-110">Jeśli ustawisz <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwości <xref:System.Windows.Media.ImageBrush>, możesz utworzyć powtarzające się wzorca.</span><span class="sxs-lookup"><span data-stu-id="3fee4-110">If you set the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties of an <xref:System.Windows.Media.ImageBrush>, you can create a repeating pattern.</span></span> <span data-ttu-id="3fee4-111">Poniższy przykład umożliwia malowanie przycisk za pomocą wzorca, który jest tworzony z obrazu.</span><span class="sxs-lookup"><span data-stu-id="3fee4-111">The following example paints a button by using a pattern that is created from an image.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <span data-ttu-id="3fee4-112">Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> klasy, zobacz [malowanie obrazami, rysowaniem i Visual](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="3fee4-112">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="3fee4-113">Ten przykład kodu jest częścią większego przykładu, który jest udostępniany dla <xref:System.Windows.Media.ImageBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="3fee4-113">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="3fee4-114">Aby uzyskać pełny przykład, zobacz [przykładowe ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="3fee4-114">For the complete sample, see [ImageBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fee4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fee4-115">See Also</span></span>  
 [<span data-ttu-id="3fee4-116">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="3fee4-116">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
