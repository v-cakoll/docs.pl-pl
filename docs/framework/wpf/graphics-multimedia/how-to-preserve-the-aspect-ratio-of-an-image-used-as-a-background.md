---
title: "Jak zachować format obrazu użytego jako tło"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a34377403a55ba42d9d3f2946ef26ea48982f5d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a><span data-ttu-id="9cbbe-102">Jak zachować format obrazu użytego jako tło</span><span class="sxs-lookup"><span data-stu-id="9cbbe-102">How to: Preserve the Aspect Ratio of an Image Used as a Background</span></span>
<span data-ttu-id="9cbbe-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość <xref:System.Windows.Media.ImageBrush> w celu zachowania proporcji obrazu.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of an <xref:System.Windows.Media.ImageBrush> in order to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="9cbbe-104">Domyślnie, gdy używasz <xref:System.Windows.Media.ImageBrush> namalować obszar jego zawartość zostanie rozciągnięty w celu wypełnia całkowicie obszaru wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-104">By default, when you use an <xref:System.Windows.Media.ImageBrush> to paint an area, its content stretches to completely fill the output area.</span></span> <span data-ttu-id="9cbbe-105">Jeśli do obszaru wyjściowego i obrazu różnych współczynników proporcji, obraz jest zniekształcony przez ten rozciąganie.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-105">When the output area and the image have different aspect ratios, the image is distorted by this stretching.</span></span>  
  
 <span data-ttu-id="9cbbe-106">Aby <xref:System.Windows.Media.ImageBrush> współczynnik proporcji jego obrazu, ustaw <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości <xref:System.Windows.Media.Stretch.Uniform> lub <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-106">To make an <xref:System.Windows.Media.ImageBrush> preserve the aspect ratio of its image, set the <xref:System.Windows.Media.TileBrush.Stretch%2A> property to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cbbe-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cbbe-107">Example</span></span>  
 <span data-ttu-id="9cbbe-108">W poniższym przykładzie użyto dwóch <xref:System.Windows.Media.ImageBrush> obiektów namalować dwóch prostokątów.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-108">The following example uses two <xref:System.Windows.Media.ImageBrush> objects to paint two rectangles.</span></span> <span data-ttu-id="9cbbe-109">Każdy prostokąt jest 300 pikseli 150 i każdy z nich zawiera obraz pikseli 300 przez 300.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-109">Each rectangle is 300 by 150 pixels and each contains a 300 by 300 pixel image.</span></span> <span data-ttu-id="9cbbe-110"><xref:System.Windows.Media.TileBrush.Stretch%2A> Ma ustawioną właściwość pędzla pierwszy <xref:System.Windows.Media.Stretch.Uniform>i <xref:System.Windows.Media.TileBrush.Stretch%2A> ma ustawioną właściwość pędzla drugi <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-110">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the first brush is set to <xref:System.Windows.Media.Stretch.Uniform>, and the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the second brush is set to <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 <span data-ttu-id="9cbbe-111">Na poniższej ilustracji przedstawiono dane wyjściowe pierwszy pędzla, który ma <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienie <xref:System.Windows.Media.Stretch.Uniform>.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-111">The following illustration shows the output of the first brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.Uniform>.</span></span>  
  
 <span data-ttu-id="9cbbe-112">![ImageBrush z Uniform rozciąganie](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span><span class="sxs-lookup"><span data-stu-id="9cbbe-112">![ImageBrush with Uniform stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span></span>  
  
 <span data-ttu-id="9cbbe-113">Na następnej ilustracji przedstawiono dane wyjściowe drugi pędzla, który ma <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienie <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-113">The next illustration shows the output of the second brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 <span data-ttu-id="9cbbe-114">![Obiekt ImageBrush z rozciągania typu UniformToFill](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span><span class="sxs-lookup"><span data-stu-id="9cbbe-114">![ImageBrush with UniformToFill stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span></span>  
  
 <span data-ttu-id="9cbbe-115">Należy pamiętać, że <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości zachowuje się tak samo dla siebie <xref:System.Windows.Media.TileBrush> obiekty, oznacza to, aby uzyskać <xref:System.Windows.Media.DrawingBrush> i <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-115">Note that the <xref:System.Windows.Media.TileBrush.Stretch%2A> property behaves identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="9cbbe-116">Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> i innych <xref:System.Windows.Media.TileBrush> obiekty, zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="9cbbe-116">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="9cbbe-117">Należy zauważyć, że, mimo że <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości pojawia się, aby określić sposób <xref:System.Windows.Media.TileBrush> zawartość zostanie rozciągnięty w celu dopasowania jej obszaru danych wyjściowych, faktycznie określa sposób <xref:System.Windows.Media.TileBrush> zawartości odcinkach do wypełnienia jej podstawowy Kafelek.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-117">Note also that, although the <xref:System.Windows.Media.TileBrush.Stretch%2A> property appears to specify how the <xref:System.Windows.Media.TileBrush> content stretches to fit its output area, it actually specifies how the <xref:System.Windows.Media.TileBrush> content stretches to fill its base tile.</span></span> <span data-ttu-id="9cbbe-118">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-118">For more information, see <xref:System.Windows.Media.TileBrush>.</span></span>  
  
 <span data-ttu-id="9cbbe-119">Ten przykładowy kod jest częścią większego przykładu udostępnionego dla <xref:System.Windows.Media.ImageBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="9cbbe-119">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="9cbbe-120">Pełny przykład, zobacz [próbki ImageBrush](http://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="9cbbe-120">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cbbe-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cbbe-121">See Also</span></span>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="9cbbe-122">Malowanie obrazów, rysunki i elementy wizualne</span><span class="sxs-lookup"><span data-stu-id="9cbbe-122">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
