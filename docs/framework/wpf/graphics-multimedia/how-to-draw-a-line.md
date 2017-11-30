---
title: "Jak narysować linię"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4911aea91416fb84e9a18d54c145b494737ef9dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line"></a>Jak narysować linię
W tym przykładzie przedstawiono sposób Rysowanie linii za pomocą <xref:System.Windows.Shapes.Line> elementu.  
  
 Rysowanie linii, należy utworzyć <xref:System.Windows.Shapes.Line> elementu. Użyj jego <xref:System.Windows.Shapes.Line.X1%2A> i <xref:System.Windows.Shapes.Line.Y1%2A> właściwości, aby ustawić jej punkt początkowy; i używać jej <xref:System.Windows.Shapes.Line.X2%2A> i <xref:System.Windows.Shapes.Line.Y2%2A> właściwości można ustawić punktu końcowego. Wreszcie, ustaw jej <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> ponieważ wiersza bez obrysu jest niewidoczny.  
  
 Ustawienie <xref:System.Windows.Shapes.Shape.Fill%2A> element wiersza nie ma wpływu, ponieważ ma nie wewnętrznych.  
  
 Poniższy przykład pobiera trzy wiersze wewnątrz <xref:System.Windows.Controls.Canvas> elementu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Shapes.Line>  
 [Przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037)
