---
title: 'Instrukcje: Modyfikowanie zakończenia na końcu linii lub segmentu'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 53487417636dae8d855fe70b7b9255351a2dfb1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916132"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="40545-102">Instrukcje: Modyfikowanie zakończenia na końcu linii lub segmentu</span><span class="sxs-lookup"><span data-stu-id="40545-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="40545-103">Ten przykład pokazuje, jak zmodyfikować kształt na początku lub na końcu otwartego <xref:System.Windows.Shapes.Shape> elementu.</span><span class="sxs-lookup"><span data-stu-id="40545-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="40545-104">Aby zmienić zakończenie na początku otwartego <xref:System.Windows.Shapes.Shape>, użyj jego <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="40545-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="40545-105">Aby zmienić zakończenie na końcu otwartego <xref:System.Windows.Shapes.Shape>, użyj jego <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="40545-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="40545-106">Aby wyświetlić dostępne wersaliki, zobacz <xref:System.Windows.Media.PenLineCap> Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="40545-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40545-107">Ta właściwość ma wpływ tylko na otwarty kształt, taki jak <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>lub otwarty <xref:System.Windows.Shapes.Path> element.</span><span class="sxs-lookup"><span data-stu-id="40545-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="40545-108">Poniższy przykład rysuje cztery <xref:System.Windows.Shapes.Polyline> elementy i używa różnego zestawu kształtów na końcach każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="40545-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40545-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="40545-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="40545-110">Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="40545-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40545-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40545-111">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
