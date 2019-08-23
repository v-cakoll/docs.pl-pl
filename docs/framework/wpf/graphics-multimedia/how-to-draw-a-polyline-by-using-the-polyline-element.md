---
title: 'Instrukcje: Rysowanie wielokąta przy użyciu elementu wielokątnego'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: fb5220082989a9d0a22c4998bb79c0a196067e7e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934964"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Instrukcje: Rysowanie wielokąta przy użyciu elementu wielokątnego
Ten przykład pokazuje, jak narysować linię łamaną, która jest serią połączonych linii przy użyciu <xref:System.Windows.Shapes.Polyline> elementu.  
  
 Aby narysować linię łamaną, Utwórz <xref:System.Windows.Shapes.Polyline> element i użyj jego <xref:System.Windows.Shapes.Polyline.Points%2A> właściwości, aby określić wierzchołki kształtu. Na koniec Użyj <xref:System.Windows.Shapes.Shape.Stroke%2A> właściwości i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> , aby opisać kontur linii łamanej, ponieważ linia bez pociągnięcia jest niewidoczna.  
  
> [!NOTE]
> Ponieważ element nie jest zamkniętym kształtem <xref:System.Windows.Shapes.Shape.Fill%2A> , właściwość nie ma żadnego efektu, nawet jeśli odcelowo zamknie konspekt kształtu. <xref:System.Windows.Shapes.Polyline> Aby utworzyć zamknięty kształt z <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Polygon> Użyj elementu.  
  
 Poniższy przykład rysuje dwa <xref:System.Windows.Shapes.Polyline> elementy <xref:System.Windows.Controls.Canvas>wewnątrz.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]programie prawidłowa składnia dla punktów to rozdzielana spacjami lista par współrzędnych x i y oddzielanych przecinkami.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Mimo że w tym przykładzie <xref:System.Windows.Controls.Canvas> używa się, aby zawierać linie łamane, można użyć elementów łamaną (i wszystkich innych elementów kształtu) z dowolnym <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> obsługującym zawartość nietekstową.  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037)
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](shapes-and-basic-drawing-in-wpf-overview.md)
