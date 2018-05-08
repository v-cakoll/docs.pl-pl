---
title: Jak narysować kształt zamknięty przy użyciu elementu wielobocznego
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 4105139e159783cf0197f4e56c82001835077cbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Jak narysować kształt zamknięty przy użyciu elementu wielobocznego
W tym przykładzie pokazano, jak narysować kształt zamknięty przy użyciu <xref:System.Windows.Shapes.Polygon> elementu. Aby narysować kształt zamknięty, Utwórz <xref:System.Windows.Shapes.Polygon> elementu i użyj jej <xref:System.Windows.Shapes.Polygon.Points%2A> właściwości w celu określenia wierzchołków kształtu. Wiersz jest automatycznie rysowane łączącego punktów imię i nazwisko. Określ koniec <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>, lub obie.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], rozdzielonych spacjami listę par rozdzielanej przecinkami i y współrzędną x jest nieprawidłowa składnia dla punktów.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Mimo że w przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają wielokąty, można użyć elementów wielokąta (i inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> obsługujący nietekstowych zawartość.  
  
 Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037).
