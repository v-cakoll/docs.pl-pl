---
title: "Jak narysować kształt zamknięty przy użyciu elementu wielobocznego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0cf842c22238105510b13407d55c8c9773f84a70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Jak narysować kształt zamknięty przy użyciu elementu wielobocznego
W tym przykładzie pokazano, jak narysować kształt zamknięty przy użyciu <xref:System.Windows.Shapes.Polygon> elementu. Aby narysować kształt zamknięty, Utwórz <xref:System.Windows.Shapes.Polygon> elementu i użyj jej <xref:System.Windows.Shapes.Polygon.Points%2A> właściwości w celu określenia wierzchołków kształtu. Wiersz jest automatycznie rysowane łączącego punktów imię i nazwisko. Określ koniec <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>, lub obie.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], rozdzielonych spacjami listę par rozdzielanej przecinkami i y współrzędną x jest nieprawidłowa składnia dla punktów.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Mimo że w przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają wielokąty, można użyć elementów wielokąta (i inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> obsługujący nietekstowych zawartość.  
  
 Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037).
