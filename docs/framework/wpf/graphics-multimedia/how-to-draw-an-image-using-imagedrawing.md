---
title: 'Instrukcje: Rysuj obraz z użyciem ImageDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: 5c1617d1a60fde8e9f1c215a5b644f6fd330817a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629075"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>Instrukcje: Rysuj obraz z użyciem ImageDrawing
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.ImageDrawing> do rysowania obrazu. <xref:System.Windows.Media.ImageDrawing> Umożliwia możesz wyświetlić <xref:System.Windows.Media.ImageSource> z <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, lub <xref:System.Windows.Media.Visual>. Aby narysować obrazu, należy utworzyć <xref:System.Windows.Media.ImageDrawing> i ustaw jego <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> właściwości. <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Właściwości Określa obraz do rysowania i <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> właściwość określa położenie i rozmiar każdego obrazu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład obejmuje tworzenie złożonego rysunku przy użyciu czterech <xref:System.Windows.Media.ImageDrawing> obiektów. Ten przykład generuje poniższej ilustracji:  
  
 ![Niektóre obiekty DrawingImage](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
Cztery ImageDrawing — obiekty  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 Na przykład przedstawiający prosty sposób wyświetlania obrazu bez użycia <xref:System.Windows.Media.ImageDrawing>, zobacz [Użyj elementu obrazu](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [PresentationOptions:Freeze, atrybut](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
