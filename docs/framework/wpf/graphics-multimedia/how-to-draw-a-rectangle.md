---
title: 'Instrukcje: Rysowanie prostokąta'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 261026b994b432565928b38ff1657115ff7cbe4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217357"
---
# <a name="how-to-draw-a-rectangle"></a>Instrukcje: Rysowanie prostokąta
W tym przykładzie pokazano, jak narysować prostokąt przy użyciu <xref:System.Windows.Shapes.Rectangle> elementu.  
  
 Aby narysować prostokąt, należy utworzyć <xref:System.Windows.Shapes.Rectangle> elementu i określ jej <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>. Namalować wnętrze prostokąt, ustaw jego <xref:System.Windows.Shapes.Shape.Fill%2A>. Aby dać prostokąta konspektu, użyj jej <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> właściwości.  
  
 Aby dać prostokąta zaokrąglone rogi, należy określić opcjonalny <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości. <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości ustawione promienie osi x i y elipsy używanej do zaokrąglania narożników prostokąta.  
  
 W poniższym przykładzie dwa <xref:System.Windows.Shapes.Rectangle> elementy są rysowane <xref:System.Windows.Controls.Canvas>. Pierwszy prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> posługiwanie się nimi. Drugi prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> posługiwanie się nimi, <xref:System.Windows.Media.Brushes.Black%2A> konspekt i zaokrąglone rogi.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają prostokątów, można użyć elementów prostokąt (i wszystkie inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> , która obsługuje zawartość nietekstową. W rzeczywistości są szczególnie przydatne do prezentowania tła dla części prostokąty <xref:System.Windows.Controls.Grid> paneli. Aby uzyskać przykład, zobacz [Omówienie tabel](../advanced/table-overview.md).  
  
 W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Shapes.Rectangle>
- [Przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037)
- [Przegląd Kształty i podstawowe rysowanie w WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Przegląd Tabela](../advanced/table-overview.md)
