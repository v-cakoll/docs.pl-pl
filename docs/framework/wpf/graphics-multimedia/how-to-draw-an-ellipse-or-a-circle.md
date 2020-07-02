---
title: Jak narysować elipsę na okręgu
description: Dowiedz się, jak narysować elipsę lub okrąg z opcjami dla grubości i koloru kolorowego w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: afa0e7d2af42aaee39dca164f23b1a1cacf430ca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853570"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Jak narysować elipsę na okręgu
Ten przykład pokazuje, jak rysować wielokropek i okręgi przy użyciu <xref:System.Windows.Shapes.Ellipse> elementu. Aby narysować wielokropek, Utwórz <xref:System.Windows.Shapes.Ellipse> element i określ jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> . Użyj swojej <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości, aby określić <xref:System.Windows.Media.Brush> , który jest używany do malowania wnętrza wielokropka. Użyj swojej <xref:System.Windows.Shapes.Shape.Stroke%2A> właściwości, aby określić <xref:System.Windows.Media.Brush> , że jest używany do malowania konturu elipsy. <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>Właściwość określa grubość konturu elipsy.  
  
 Aby narysować okrąg, upewnij się, że <xref:System.Windows.FrameworkElement.Width%2A> elementy i są <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Shapes.Ellipse> równe siebie.  
  
 Poniższy przykład rysuje cztery <xref:System.Windows.Shapes.Ellipse> elementy w <xref:System.Windows.Controls.Canvas> .  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Mimo że w tym przykładzie użyto, <xref:System.Windows.Controls.Canvas> aby zawierać wielokropek, można użyć elementów wielokropka (i wszystkich innych elementów kształtu) z dowolnym lub obsługującym <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Control> zawartość nietekstową.  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [Przykładowe elementy kształtu](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
