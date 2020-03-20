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
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187334"
---
# <a name="how-to-transform-a-brush"></a>Jak przekształcić pędzel
W tym przykładzie <xref:System.Windows.Media.Brush> pokazano, jak przekształcić obiekty <xref:System.Windows.Media.Brush.RelativeTransform%2A> <xref:System.Windows.Media.Brush.Transform%2A>przy użyciu ich dwóch właściwości transformacji: i .  
  
 Poniższe przykłady <xref:System.Windows.Media.RotateTransform> używają a, aby <xref:System.Windows.Media.ImageBrush> obrócić zawartość o 45 stopni.  
  
 Na <xref:System.Windows.Media.ImageBrush> poniższej ilustracji <xref:System.Windows.Media.RotateTransform>przedstawiono <xref:System.Windows.Media.RotateTransform> bez , <xref:System.Windows.Media.Brush.RelativeTransform%2A> z zastosowane <xref:System.Windows.Media.RotateTransform> do właściwości <xref:System.Windows.Media.Brush.Transform%2A> i z zastosowane do właściwości.  
  
 ![Ustawienia Brush RelativeTransform i Transform](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>Przykład  
 Pierwszy przykład stosuje <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Brush.RelativeTransform%2A> do właściwości <xref:System.Windows.Media.ImageBrush>. Właściwości <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> obiektu <xref:System.Windows.Media.RotateTransform> są ustawione na 0,5, co jest względną współrzędną punktu środkowego tej zawartości. W rezultacie <xref:System.Windows.Media.ImageBrush> zawartość obraca się wokół jego środka.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Drugi przykład dotyczy również <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.ImageBrush>do ; jednak w tym przykładzie używa <xref:System.Windows.Media.Brush.Transform%2A> właściwości <xref:System.Windows.Media.Brush.RelativeTransform%2A> zamiast właściwości.  
  
 Aby obrócić pędzel wokół jego środka, w przykładzie ustawia <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości <xref:System.Windows.Media.RotateTransform> obiektu do współrzędnych bezwzględnych. Ponieważ pędzel maluje prostokąt o rozmiarze 175 na 90 pikseli, punktem środkowym prostokąta jest (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Aby uzyskać opis <xref:System.Windows.Media.Brush.RelativeTransform%2A> działania <xref:System.Windows.Media.Brush.Transform%2A> i właściwości, zobacz [Omówienie transformacji pędzla](brush-transformation-overview.md).  
  
 Aby uzyskać pełną próbkę, zobacz [Próbka pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Aby uzyskać więcej informacji na temat pędzli, zobacz [Malowanie za pomocą jednolitych kolorów i gradientów Omówienie](painting-with-solid-colors-and-gradients-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przekształcanie pędzla — przegląd](brush-transformation-overview.md)
- [Przegląd Malowanie jednolitymi kolorami i gradientami](painting-with-solid-colors-and-gradients-overview.md)
- [Przekształcenia — przegląd](transforms-overview.md)
