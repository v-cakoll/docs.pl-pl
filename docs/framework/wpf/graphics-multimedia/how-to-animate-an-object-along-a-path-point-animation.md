---
title: Jak animować obiekt na ścieżce (animacja punktu)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452899"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Jak animować obiekt na ścieżce (animacja punktu)
W tym przykładzie pokazano, jak za pomocą obiektu <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animować <xref:System.Windows.Point> wzdłuż ścieżki zakrzywionej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przenosi <xref:System.Windows.Media.EllipseGeometry> wzdłuż ścieżki zdefiniowanej przez <xref:System.Windows.Media.PathGeometry>. Właściwość <xref:System.Windows.Media.EllipseGeometry.Center%2A> geometrii wielokropka, która przyjmuje wartość <xref:System.Windows.Point>, określa jej pozycję. Aby przenieść geometrię elipsy, należy animować jej Właściwość <xref:System.Windows.Media.EllipseGeometry.Center%2A>. W przykładzie używa się <xref:System.Windows.Media.Animation.PointAnimationUsingPath> do animowania właściwości <xref:System.Windows.Media.EllipseGeometry.Center%2A> obiektu <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Wersja kodu powyższego przykładu użyła <xref:System.Windows.Media.Animation.Storyboard>, aby animować <xref:System.Windows.Media.EllipseGeometry>, nawet jeśli zastosowano tylko jedną animację. <xref:System.Windows.Media.Animation.Storyboard> jest często najprostszym sposobem zastosowania wielu animacji, ponieważ te animacje mogą być kontrolowane przez ten sam <xref:System.Windows.Media.Animation.Storyboard>. Jednak łatwiejszym sposobem zastosowania pojedynczej animacji do właściwości przy użyciu kodu jest użycie metody <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>. Aby zapoznać się z przykładem, zobacz [Animuj a Property bez używania scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przykład animacji ścieżki](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Animacja — przegląd](animation-overview.md)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
