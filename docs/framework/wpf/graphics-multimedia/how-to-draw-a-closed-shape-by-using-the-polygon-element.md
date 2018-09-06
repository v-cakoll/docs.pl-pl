---
title: Jak narysować kształt zamknięty przy użyciu elementu wielobocznego
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 89c78877e196e803f6b4139ffcfa2b4def1a07d7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732056"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Jak narysować kształt zamknięty przy użyciu elementu wielobocznego
W tym przykładzie pokazano, jak narysować kształt zamknięty przy użyciu <xref:System.Windows.Shapes.Polygon> elementu. Aby narysować kształt zamknięty, należy utworzyć <xref:System.Windows.Shapes.Polygon> element i użyj jej <xref:System.Windows.Shapes.Polygon.Points%2A> właściwości w celu określenia wierzchołków kształtu. Wiersz jest automatycznie pobierane łączącej punkty imię i nazwisko. Ponadto określ <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>, lub obu.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], prawidłowej składni dla punktów znajduje się lista rozdzielonych przecinkami x - i współrzędne y pary rozdzielonych spacjami.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Chociaż w przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają wielokąty, można użyć elementów wielokąta (i wszystkie inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> , która obsługuje zawartość nietekstową.  
  
 W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037).
