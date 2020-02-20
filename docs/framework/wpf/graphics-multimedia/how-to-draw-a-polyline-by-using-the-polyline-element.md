---
title: Jak narysować wielokąt przy użyciu elementu wielokątnego
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 6698141bcaa3b0fd5f5b9cf66bcab1be1f4ea2f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452964"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Jak narysować wielokąt przy użyciu elementu wielokątnego
Ten przykład pokazuje, jak narysować linię łamaną, która jest serią połączonych linii przy użyciu elementu <xref:System.Windows.Shapes.Polyline>.  
  
 Aby narysować linię łamaną, Utwórz <xref:System.Windows.Shapes.Polyline> element i użyj jej właściwości <xref:System.Windows.Shapes.Polyline.Points%2A>, aby określić wierzchołki kształtu. Na koniec Użyj właściwości <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> do opisania konturu linii łamanej, ponieważ linia bez pociągnięcia jest niewidoczna.  
  
> [!NOTE]
> Ponieważ element <xref:System.Windows.Shapes.Polyline> nie jest zamkniętym kształtem, właściwość <xref:System.Windows.Shapes.Shape.Fill%2A> nie ma żadnego efektu, nawet jeśli odcelowo zamknie konspekt kształtu. Aby utworzyć zamknięty kształt z <xref:System.Windows.Shapes.Shape.Fill%2A>, użyj elementu <xref:System.Windows.Shapes.Polygon>.  
  
 Poniższy przykład rysuje dwa elementy <xref:System.Windows.Shapes.Polyline> wewnątrz <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]prawidłowa składnia dla punktów to rozdzielana spacjami lista par współrzędnych x i y oddzielanych przecinkami.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Chociaż w tym przykładzie użyto <xref:System.Windows.Controls.Canvas>, aby zawierała linie łamane, można użyć elementów łamaną (i wszystkich innych elementów kształtu) z dowolnym <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control>, które obsługują zawartość nietekstową.  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Przykładowe elementy kształtu](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](shapes-and-basic-drawing-in-wpf-overview.md)
