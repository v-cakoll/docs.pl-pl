---
title: "Jak rysować obraz z użyciem ImageDrawing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d975d33bb3c102e5294d78dc76d8136ab521953
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>Jak rysować obraz z użyciem ImageDrawing
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.ImageDrawing> do rysowania obrazu. <xref:System.Windows.Media.ImageDrawing> Umożliwia wyświetlania <xref:System.Windows.Media.ImageSource> z <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, lub <xref:System.Windows.Media.Visual>. Aby narysować obrazu, należy utworzyć <xref:System.Windows.Media.ImageDrawing> i ustawić jej <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> właściwości. <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Właściwość określa obraz do rysowania i <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> właściwość określa położenie i rozmiar każdego obrazu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy rysunek złożonego za pomocą czterech <xref:System.Windows.Media.ImageDrawing> obiektów. W tym przykładzie powoduje poniższej ilustracji:  
  
 ![Niektóre obiekty DrawingImage](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
Cztery obiektów Obiekt ImageDrawing o rozmiarze  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 Na przykład przedstawiający prosty sposób wyświetlania obrazu bez użycia <xref:System.Windows.Media.ImageDrawing>, zobacz [, korzystając z obrazu elementu](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Freezable.Freeze%2A>  
 <xref:System.Windows.Controls.Image>  
 [Rysowanie obiekty — omówienie](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Obiekty obiektu freezable — omówienie](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Atrybut PresentationOptions:Freeze](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
