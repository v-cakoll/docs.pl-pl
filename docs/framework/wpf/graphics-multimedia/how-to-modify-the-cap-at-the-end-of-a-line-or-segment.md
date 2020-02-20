---
title: Jak modyfikować zakończenie na końcu linii lub segmentu
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 5f755d7b4d1682755ea461121f91c0666d450ad1
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452782"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="b2b61-102">Jak modyfikować zakończenie na końcu linii lub segmentu</span><span class="sxs-lookup"><span data-stu-id="b2b61-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="b2b61-103">Ten przykład pokazuje, jak zmodyfikować kształt na początku lub na końcu otwartego elementu <xref:System.Windows.Shapes.Shape>.</span><span class="sxs-lookup"><span data-stu-id="b2b61-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="b2b61-104">Aby zmienić zakończenie na początku otwartego <xref:System.Windows.Shapes.Shape>, użyj jego właściwości <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2b61-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="b2b61-105">Aby zmienić zakończenie na końcu otwartego <xref:System.Windows.Shapes.Shape>, użyj właściwości <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2b61-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="b2b61-106">Aby wyświetlić dostępne wersaliki, zobacz Wyliczenie <xref:System.Windows.Media.PenLineCap>.</span><span class="sxs-lookup"><span data-stu-id="b2b61-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2b61-107">Ta właściwość ma wpływ tylko na otwarty kształt, taki jak <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Polyline>lub otwarty element <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="b2b61-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="b2b61-108">Poniższy przykład rysuje cztery <xref:System.Windows.Shapes.Polyline> elementy i używa różnych zestawów kształtów na końcach każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="b2b61-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2b61-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2b61-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="b2b61-110">Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="b2b61-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b61-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2b61-111">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
