---
title: "Jak narysować wielokąt przy użyciu elementu wielokątnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5fa8cafdaf7856e95129f648da1d4b4ccb2f54eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Jak narysować wielokąt przy użyciu elementu wielokątnego
W tym przykładzie przedstawiono sposób rysowania linii łamanej, który jest szereg połączone linie przy użyciu <xref:System.Windows.Shapes.Polyline> elementu.  
  
 Aby narysować łamaną, Utwórz <xref:System.Windows.Shapes.Polyline> elementu i użyj jej <xref:System.Windows.Shapes.Polyline.Points%2A> właściwości w celu określenia wierzchołków kształtu. Na koniec użyj <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> właściwości do opisywania linii łamanej konspektu, ponieważ wiersz bez pociągnięcia jest niewidoczny.  
  
> [!NOTE]
>  Ponieważ <xref:System.Windows.Shapes.Polyline> element nie jest zamknięty kształt <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość nie ma wpływu, nawet jeśli zamkniesz celowo kontur figury. Aby utworzyć zamknięty kształt z <xref:System.Windows.Shapes.Shape.Fill%2A>, użyj <xref:System.Windows.Shapes.Polygon> elementu.  
  
 Poniższy przykład rysuje dwa <xref:System.Windows.Shapes.Polyline> elementy wewnątrz <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], rozdzielonych spacjami listę par rozdzielanej przecinkami i y współrzędną x jest nieprawidłowa składnia dla punktów.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają linię, można użyć elementów łamanej (i inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> obsługujący nietekstowych zawartość.  
  
 Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Shapes.Polygon>  
 <xref:System.Windows.Shapes.Shape>  
 [Przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [Kształty i podstawowe rysunek w omówieniu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
