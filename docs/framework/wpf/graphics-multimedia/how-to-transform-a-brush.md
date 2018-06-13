---
title: Jak przekształcić pędzel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: 5caa00a378101ff4dff7745a18c3ec8905cc168b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561609"
---
# <a name="how-to-transform-a-brush"></a>Jak przekształcić pędzel
W tym przykładzie przedstawiono sposób przekształcania <xref:System.Windows.Media.Brush> obiektów przy użyciu ich właściwości dwóch przekształcenia: <xref:System.Windows.Media.Brush.RelativeTransform%2A> i <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 W poniższych przykładach użyto <xref:System.Windows.Media.RotateTransform> obracania zawartość <xref:System.Windows.Media.ImageBrush> o 45 stopni.  
  
 Na poniższej ilustracji pokazano <xref:System.Windows.Media.ImageBrush> bez <xref:System.Windows.Media.RotateTransform>, z <xref:System.Windows.Media.RotateTransform> stosowane do <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości oraz z <xref:System.Windows.Media.RotateTransform> dotyczą <xref:System.Windows.Media.Brush.Transform%2A> właściwości.  
  
 ![Pędzel RelativeTransform i przekształcanie ustawienia](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>Przykład  
 Pierwszy przykład dotyczy <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwość <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości <xref:System.Windows.Media.RotateTransform> obiektu są ustawione na 0,5, który jest względny współrzędnych punktu centralnego tej zawartości. W związku z tym <xref:System.Windows.Media.ImageBrush> zawartości obraca się o jego center.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Drugi przykład dotyczy także <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.ImageBrush>, jednak w tym przykładzie użyto <xref:System.Windows.Media.Brush.Transform%2A> właściwości zamiast <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości.  
  
 Obracanie pędzla o jego Centrum, w przykładzie <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości <xref:System.Windows.Media.RotateTransform> obiektu współrzędne bezwzględne. Ponieważ pędzla farby prostokąt jest 175 90 pikseli, jest punktu centralnego prostokąta (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Opis sposobu <xref:System.Windows.Media.Brush.RelativeTransform%2A> i <xref:System.Windows.Media.Brush.Transform%2A> właściwości pracy, zobacz [omówienie przekształcania pędzla](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).  
  
 Pełny przykład, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973). Aby uzyskać więcej informacji na temat pędzle, zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przekształcanie pędzla — przegląd](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
