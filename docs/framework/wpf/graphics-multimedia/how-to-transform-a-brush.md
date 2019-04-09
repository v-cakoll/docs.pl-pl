---
title: 'Instrukcje: Przekształcanie pędzla'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: a83f3b1c046e94faa8816e8c310f438b4711048a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163010"
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="043e5-102">Instrukcje: Przekształcanie pędzla</span><span class="sxs-lookup"><span data-stu-id="043e5-102">How to: Transform a Brush</span></span>
<span data-ttu-id="043e5-103">W tym przykładzie pokazano, jak przekształcić <xref:System.Windows.Media.Brush> obiektów przy użyciu ich właściwości dwóch transformacji: <xref:System.Windows.Media.Brush.RelativeTransform%2A> i <xref:System.Windows.Media.Brush.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="043e5-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="043e5-104">W poniższych przykładach używane <xref:System.Windows.Media.RotateTransform> obracanie zawartości <xref:System.Windows.Media.ImageBrush> o 45 stopni.</span><span class="sxs-lookup"><span data-stu-id="043e5-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="043e5-105">Poniższa ilustracja przedstawia <xref:System.Windows.Media.ImageBrush> bez <xref:System.Windows.Media.RotateTransform>, za pomocą <xref:System.Windows.Media.RotateTransform> stosowane do <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości i <xref:System.Windows.Media.RotateTransform> stosowane do <xref:System.Windows.Media.Brush.Transform%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="043e5-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="043e5-106">![Pędzel RelativeTransform i przekształcać ustawienia](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="043e5-106">![Brush RelativeTransform and Transform settings](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="043e5-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="043e5-107">Example</span></span>  
 <span data-ttu-id="043e5-108">Pierwszy przykład dotyczy <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwość <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="043e5-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="043e5-109"><xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości <xref:System.Windows.Media.RotateTransform> obiektu są ustawione na 0,5, czyli współrzędne względne punktu centralnego tej zawartości.</span><span class="sxs-lookup"><span data-stu-id="043e5-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="043e5-110">W rezultacie <xref:System.Windows.Media.ImageBrush> zawartości obraca się o jej środka.</span><span class="sxs-lookup"><span data-stu-id="043e5-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="043e5-111">Drugi przykład dotyczy także <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.ImageBrush>; Jednakże, w tym przykładzie użyto <xref:System.Windows.Media.Brush.Transform%2A> właściwości zamiast <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="043e5-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="043e5-112">Aby obrócić pędzla o jej środka, w przykładzie <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości <xref:System.Windows.Media.RotateTransform> obiektu współrzędne bezwzględne.</span><span class="sxs-lookup"><span data-stu-id="043e5-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="043e5-113">Ponieważ pędzel farby prostokąt, który jest 175 pikseli 90, jest punktu centralnego prostokąt (87.5, 45).</span><span class="sxs-lookup"><span data-stu-id="043e5-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="043e5-114">Aby uzyskać opis sposób <xref:System.Windows.Media.Brush.RelativeTransform%2A> i <xref:System.Windows.Media.Brush.Transform%2A> właściwości pracy, zobacz [Przekształcanie pędzla — Przegląd](brush-transformation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="043e5-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="043e5-115">Aby uzyskać pełny przykład, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="043e5-115">For the complete sample, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="043e5-116">Aby uzyskać więcej informacji na temat pędzle, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="043e5-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="043e5-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="043e5-117">See also</span></span>

- [<span data-ttu-id="043e5-118">Przegląd Przekształcanie pędzla</span><span class="sxs-lookup"><span data-stu-id="043e5-118">Brush Transformation Overview</span></span>](brush-transformation-overview.md)
- [<span data-ttu-id="043e5-119">Przegląd Malowanie jednolitymi kolorami i gradientami</span><span class="sxs-lookup"><span data-stu-id="043e5-119">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="043e5-120">Przegląd Przekształcenia</span><span class="sxs-lookup"><span data-stu-id="043e5-120">Transforms Overview</span></span>](transforms-overview.md)
