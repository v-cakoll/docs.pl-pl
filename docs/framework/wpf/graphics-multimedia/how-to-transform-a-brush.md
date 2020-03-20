---
title: Jak przekształcić pędzel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187334"
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="6d1ff-102">Jak przekształcić pędzel</span><span class="sxs-lookup"><span data-stu-id="6d1ff-102">How to: Transform a Brush</span></span>
<span data-ttu-id="6d1ff-103">W tym przykładzie <xref:System.Windows.Media.Brush> pokazano, jak przekształcić obiekty <xref:System.Windows.Media.Brush.RelativeTransform%2A> <xref:System.Windows.Media.Brush.Transform%2A>przy użyciu ich dwóch właściwości transformacji: i .</span><span class="sxs-lookup"><span data-stu-id="6d1ff-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="6d1ff-104">Poniższe przykłady <xref:System.Windows.Media.RotateTransform> używają a, aby <xref:System.Windows.Media.ImageBrush> obrócić zawartość o 45 stopni.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="6d1ff-105">Na <xref:System.Windows.Media.ImageBrush> poniższej ilustracji <xref:System.Windows.Media.RotateTransform>przedstawiono <xref:System.Windows.Media.RotateTransform> bez , <xref:System.Windows.Media.Brush.RelativeTransform%2A> z zastosowane <xref:System.Windows.Media.RotateTransform> do właściwości <xref:System.Windows.Media.Brush.Transform%2A> i z zastosowane do właściwości.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="6d1ff-106">![Ustawienia Brush RelativeTransform i Transform](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="6d1ff-106">![Brush RelativeTransform and Transform settings](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d1ff-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d1ff-107">Example</span></span>  
 <span data-ttu-id="6d1ff-108">Pierwszy przykład stosuje <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Brush.RelativeTransform%2A> do właściwości <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="6d1ff-109">Właściwości <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> obiektu <xref:System.Windows.Media.RotateTransform> są ustawione na 0,5, co jest względną współrzędną punktu środkowego tej zawartości.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="6d1ff-110">W rezultacie <xref:System.Windows.Media.ImageBrush> zawartość obraca się wokół jego środka.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="6d1ff-111">Drugi przykład dotyczy również <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.ImageBrush>do ; jednak w tym przykładzie używa <xref:System.Windows.Media.Brush.Transform%2A> właściwości <xref:System.Windows.Media.Brush.RelativeTransform%2A> zamiast właściwości.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="6d1ff-112">Aby obrócić pędzel wokół jego środka, w przykładzie ustawia <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości <xref:System.Windows.Media.RotateTransform> obiektu do współrzędnych bezwzględnych.</span><span class="sxs-lookup"><span data-stu-id="6d1ff-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="6d1ff-113">Ponieważ pędzel maluje prostokąt o rozmiarze 175 na 90 pikseli, punktem środkowym prostokąta jest (87,5, 45).</span><span class="sxs-lookup"><span data-stu-id="6d1ff-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="6d1ff-114">Aby uzyskać opis <xref:System.Windows.Media.Brush.RelativeTransform%2A> działania <xref:System.Windows.Media.Brush.Transform%2A> i właściwości, zobacz [Omówienie transformacji pędzla](brush-transformation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6d1ff-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="6d1ff-115">Aby uzyskać pełną próbkę, zobacz [Próbka pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="6d1ff-115">For the complete sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="6d1ff-116">Aby uzyskać więcej informacji na temat pędzli, zobacz [Malowanie za pomocą jednolitych kolorów i gradientów Omówienie](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6d1ff-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1ff-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d1ff-117">See also</span></span>

- [<span data-ttu-id="6d1ff-118">Przekształcanie pędzla — przegląd</span><span class="sxs-lookup"><span data-stu-id="6d1ff-118">Brush Transformation Overview</span></span>](brush-transformation-overview.md)
- [<span data-ttu-id="6d1ff-119">Przegląd Malowanie jednolitymi kolorami i gradientami</span><span class="sxs-lookup"><span data-stu-id="6d1ff-119">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="6d1ff-120">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="6d1ff-120">Transforms Overview</span></span>](transforms-overview.md)
