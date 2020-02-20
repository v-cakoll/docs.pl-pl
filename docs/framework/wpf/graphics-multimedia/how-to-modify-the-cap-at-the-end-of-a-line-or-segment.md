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
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Jak modyfikować zakończenie na końcu linii lub segmentu
Ten przykład pokazuje, jak zmodyfikować kształt na początku lub na końcu otwartego elementu <xref:System.Windows.Shapes.Shape>. Aby zmienić zakończenie na początku otwartego <xref:System.Windows.Shapes.Shape>, użyj jego właściwości <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>. Aby zmienić zakończenie na końcu otwartego <xref:System.Windows.Shapes.Shape>, użyj właściwości <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>. Aby wyświetlić dostępne wersaliki, zobacz Wyliczenie <xref:System.Windows.Media.PenLineCap>.  
  
> [!NOTE]
> Ta właściwość ma wpływ tylko na otwarty kształt, taki jak <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Polyline>lub otwarty element <xref:System.Windows.Shapes.Path>.  
  
 Poniższy przykład rysuje cztery <xref:System.Windows.Shapes.Polyline> elementy i używa różnych zestawów kształtów na końcach każdego z nich.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
