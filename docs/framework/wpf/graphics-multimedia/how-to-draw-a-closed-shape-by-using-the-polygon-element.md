---
title: Jak narysować kształt zamknięty przy użyciu elementu wielobocznego
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 324a5623ee658789b8600a43a89ce26cab7cd6cd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452977"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Jak narysować kształt zamknięty przy użyciu elementu wielobocznego
Ten przykład pokazuje, jak narysować zamknięty kształt przy użyciu elementu <xref:System.Windows.Shapes.Polygon>. Aby narysować zamknięty kształt, Utwórz element <xref:System.Windows.Shapes.Polygon> i użyj jego właściwości <xref:System.Windows.Shapes.Polygon.Points%2A>, aby określić wierzchołki kształtu. Zostanie automatycznie narysowana linia łącząca pierwszy i ostatni punkt. Na koniec Określ <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>lub oba te elementy.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]prawidłowa składnia dla punktów to rozdzielana spacjami lista par współrzędnych x i y oddzielanych przecinkami.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Chociaż w przykładzie użyto <xref:System.Windows.Controls.Canvas>, aby zawierać wielokąty, można użyć elementów wielokąt (i wszystkich innych elementów kształtu) z dowolnym <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control>, który obsługuje zawartość nietekstową.  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).
