---
title: "Jak narysować prostokąt"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c163897af27c9b34c8cd87a3b197047f86d21ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-rectangle"></a>Jak narysować prostokąt
W tym przykładzie pokazano, jak narysować prostokąt przy użyciu <xref:System.Windows.Shapes.Rectangle> elementu.  
  
 Aby narysować prostokąt, Utwórz <xref:System.Windows.Shapes.Rectangle> element i określ jej <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>. Namalować wnętrze prostokąta, ustaw jej <xref:System.Windows.Shapes.Shape.Fill%2A>. Aby dać prostokąt konspektu, użyj jej <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> właściwości.  
  
 Aby dać prostokąt zaokrąglone narożniki, określ opcjonalny <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości. <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości ustawione promień osi x i y elipsy używanej do zaokrąglania narożników prostokąta.  
  
 W poniższym przykładzie dwa <xref:System.Windows.Shapes.Rectangle> elementy są rysowane <xref:System.Windows.Controls.Canvas>. Pierwszy prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> wewnętrznych. Drugi prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> wewnętrzne, <xref:System.Windows.Media.Brushes.Black%2A> konspektu i zaokrąglone narożniki.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają prostokątów, można użyć elementów prostokąt (i inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> obsługujący nietekstowych zawartość. W rzeczywistości prostokąty są szczególnie użyteczne w przypadku zapewnienia tła części <xref:System.Windows.Controls.Grid> paneli. Na przykład zobacz [omówienie tabeli](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
 Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Shapes.Rectangle>  
 [Przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [Kształty i podstawowe rysunek w omówieniu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Przegląd tabeli](../../../../docs/framework/wpf/advanced/table-overview.md)
