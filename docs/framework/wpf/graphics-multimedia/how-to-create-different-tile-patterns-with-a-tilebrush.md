---
title: "Jak utworzyć różne wzory sąsiadujących kafelek z użyciem TileBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 646ce5142875c95c0b1ca19643790f73f7eb83e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a>Jak utworzyć różne wzory sąsiadujących kafelek z użyciem TileBrush
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwość <xref:System.Windows.Media.TileBrush> utworzyć wzorca.  
  
 <xref:System.Windows.Media.TileBrush.TileMode%2A> Właściwości można określić sposób zawartości <xref:System.Windows.Media.TileBrush> jest powtarzany, oznacza to, sąsiadująco w celu wypełnienia obszaru wyjściowego. Aby utworzyć wzorzec, należy ustawić <xref:System.Windows.Media.TileBrush.TileMode%2A> do <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, lub <xref:System.Windows.Media.TileMode.FlipXY>. Należy także ustawić <xref:System.Windows.Media.TileBrush.Viewport%2A> z <xref:System.Windows.Media.TileBrush> , aby była mniejsza niż obszar malowanego; w przeciwnym razie pojedynczy fragment jest wyprodukowania, niezależnie od tego, co <xref:System.Windows.Media.TileBrush.TileMode%2A> ustawienie używasz.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy pięciu <xref:System.Windows.Media.DrawingBrush> obiektów, daje im każdej innej <xref:System.Windows.Media.TileBrush.TileMode%2A> ustawienie i używa ich do malowania prostokąty pięć. Mimo że w tym przykładzie użyto <xref:System.Windows.Media.DrawingBrush> klasy, aby zademonstrować <xref:System.Windows.Media.TileBrush.TileMode%2A> zachowanie, <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwości działa tak samo dla wszystkich <xref:System.Windows.Media.TileBrush> obiekty, oznacza to, że dla <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, i <xref:System.Windows.Media.DrawingBrush>.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe, który spowoduje utworzenie w tym przykładzie.  
  
 ![Ustawianie widoku kafelków przykładowe dane wyjściowe TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")  
Wzorce kafelka utworzyć z właściwością TileMode  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie rozmiaru kafelka dla elementu TileBrush](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
