---
title: Jak animować obiekt na ścieżce (animacja double)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: 084caac26fd68b6914ec3858652ec44557a0dbd7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452860"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a>Jak animować obiekt na ścieżce (animacja double)
Ten przykład pokazuje, jak używać klasy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> do przenoszenia obiektu w ścieżce zdefiniowanej przez <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa dwóch <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> obiektów do przenoszenia prostokąta wzdłuż ścieżki geometrycznej:  
  
- Pierwszy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> Animuj <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> zastosowany do prostokąta. Sprawia, że prostokąt przemieszcza się w poziomie wzdłuż ścieżki.  
  
- Druga <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> Animuj <xref:System.Windows.Media.TranslateTransform.Y%2A> <xref:System.Windows.Media.TranslateTransform> zastosowana do prostokąta. Sprawia, że prostokąt przemieszcza się w pionie wzdłuż ścieżki.  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Innym sposobem przenoszenia obiektu przy użyciu ścieżki geometrycznej jest użycie obiektu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>. Aby zapoznać się z przykładem, zobacz [animowanie obiektu na ścieżce (animacja matrycy)](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Zobacz też

- [Animacja — przegląd](animation-overview.md)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
