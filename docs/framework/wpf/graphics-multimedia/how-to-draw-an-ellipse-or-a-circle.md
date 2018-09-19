---
title: Jak narysować elipsę na okręgu
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: ddeada8619d1b6c8970f1efb7cca1bc98773d0c5
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003948"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Jak narysować elipsę na okręgu
W tym przykładzie pokazano, jak Rysowanie elips i okręgów przy użyciu <xref:System.Windows.Shapes.Ellipse> elementu. Aby narysować elipsę, należy utworzyć <xref:System.Windows.Shapes.Ellipse> elementu i określ jej <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>. Użyj jego <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości w celu określenia <xref:System.Windows.Media.Brush> umożliwiający namalować wnętrze elipsy. Użyj jego <xref:System.Windows.Shapes.Shape.Stroke%2A> właściwości w celu określenia <xref:System.Windows.Media.Brush> używany namalować kontur elipsy. <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> Właściwość określa grubość konturu elipsy.  
  
 Aby narysować okrąg, <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Shapes.Ellipse> element równy ze sobą.  
  
 Poniższy przykład pobiera cztery <xref:System.Windows.Shapes.Ellipse> elementów w obrębie <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają wielokropek, można użyć elementów wielokropka (i wszystkie inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> , która obsługuje zawartość nietekstową.  
  
 W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [Przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037)
