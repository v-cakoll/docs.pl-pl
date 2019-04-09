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
ms.openlocfilehash: 4f55ecc206be0ef4947923047e796c36131c70ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114849"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Instrukcje: Rysowanie wielokąta przy użyciu elementu wielokątnego
W tym przykładzie pokazano, jak narysować wielokąt, czyli serię połączone linie przy użyciu <xref:System.Windows.Shapes.Polyline> elementu.  
  
 Aby narysować wielokąt, należy utworzyć <xref:System.Windows.Shapes.Polyline> element i użyj jej <xref:System.Windows.Shapes.Polyline.Points%2A> właściwości w celu określenia wierzchołków kształtu. Na koniec użyj <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> właściwości opisujących linii łamanej konspektu, ponieważ wiersz bez pociągnięcia jest niewidoczne.  
  
> [!NOTE]
>  Ponieważ <xref:System.Windows.Shapes.Polyline> element nie jest kształt zamknięty <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości nie obowiązuje, nawet wtedy, gdy zamkniesz celowo kontur figury. Aby utworzyć kształt zamknięty przy użyciu <xref:System.Windows.Shapes.Shape.Fill%2A>, użyj <xref:System.Windows.Shapes.Polygon> elementu.  
  
 Poniższy przykład pobiera dwa <xref:System.Windows.Shapes.Polyline> elementy wewnątrz <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], prawidłowej składni dla punktów znajduje się lista rozdzielonych przecinkami x - i współrzędne y pary rozdzielonych spacjami.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają łamane, można użyć elementów linii łamanej (i wszystkie inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> , która obsługuje zawartość nietekstową.  
  
 W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037)
- [Przegląd Kształty i podstawowe rysowanie w WPF](shapes-and-basic-drawing-in-wpf-overview.md)
