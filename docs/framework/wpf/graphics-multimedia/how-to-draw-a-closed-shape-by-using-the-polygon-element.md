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
ms.openlocfilehash: b38efefa503ec3786b6e40f7b93bac59596b419f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Jak narysować kształt zamknięty przy użyciu elementu wielobocznego
W tym przykładzie pokazano, jak narysować kształt zamknięty przy użyciu <xref:System.Windows.Shapes.Polygon> elementu. Aby narysować kształt zamknięty, Utwórz <xref:System.Windows.Shapes.Polygon> elementu i użyj jej <xref:System.Windows.Shapes.Polygon.Points%2A> właściwości w celu określenia wierzchołków kształtu. Wiersz jest automatycznie rysowane łączącego punktów imię i nazwisko. Określ koniec <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>, lub obie.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], rozdzielonych spacjami listę par rozdzielanej przecinkami i y współrzędną x jest nieprawidłowa składnia dla punktów.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Mimo że w przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają wielokąty, można użyć elementów wielokąta (i inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> obsługujący nietekstowych zawartość.  
  
 Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037).
