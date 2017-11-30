---
title: "Jak użyć rysowania jako źródła obrazu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e100bc29afb17a37bc0c66621261347bea6d210
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a>Jak użyć rysowania jako źródła obrazu
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Drawing> jako <xref:System.Windows.Controls.Image.Source%2A> dla <xref:System.Windows.Controls.Image> formantu. Aby wyświetlić <xref:System.Windows.Media.Drawing> z <xref:System.Windows.Controls.Image> kontrolować, użyj <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> formantu <xref:System.Windows.Controls.Image.Source%2A> i ustaw <xref:System.Windows.Media.DrawingImage> obiektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> właściwości do rysunku mają być wyświetlane.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingImage> i <xref:System.Windows.Controls.Image> formantu, aby wyświetlić <xref:System.Windows.Media.GeometryDrawing>. Ten przykład generuje następujące wyniki:  
  
 ![GeometryDrawing zawierający dwie elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [Rysuj obrazu przy użyciu Obiekt ImageDrawing o rozmiarze](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)  
 [Rysowanie obiekty — omówienie](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Obiekty obiektu freezable — omówienie](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Atrybut PresentationOptions:Freeze](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
