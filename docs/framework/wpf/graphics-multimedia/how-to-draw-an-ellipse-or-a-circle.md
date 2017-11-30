---
title: "Jak narysować elipsę na okręgu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4da623c34b4c3b84dee0f02d631d032eb1c061d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Jak narysować elipsę na okręgu
W tym przykładzie pokazano, jak Rysowanie elips i okręgi przy użyciu <xref:System.Windows.Shapes.Ellipse> elementu. Aby narysować elipsę, Utwórz <xref:System.Windows.Shapes.Ellipse> element i określ jej <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>. Użyj jego <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości w celu określenia <xref:System.Windows.Media.Brush> używany do wnętrza elipsy. Użyj jego <xref:System.Windows.Shapes.Shape.Stroke%2A> właściwości w celu określenia <xref:System.Windows.Media.Brush> używany namalować kontur elipsy. <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> Właściwość określa szerokość konturu elipsy.  
  
 Aby narysować okrąg, <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Shapes.Ellipse> element taki sam do siebie.  
  
 Poniższy przykład rysuje cztery <xref:System.Windows.Shapes.Ellipse> elementów w obrębie <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają wielokropek, można użyć elementów elipsy (i inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> obsługujący nietekstowych zawartość.  
  
 Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [Przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037)
