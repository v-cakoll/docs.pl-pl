---
title: 'Instrukcje: Animowanie obiektu na ścieżce (animacja punktu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: 4ef28118975d02500916676ca50e0f9622c7a3e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129593"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Instrukcje: Animowanie obiektu na ścieżce (animacja punktu)
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.PointAnimationUsingPath> obiektu animować <xref:System.Windows.Point> wzdłuż ścieżki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.EllipseGeometry> wzdłuż ścieżki definicją <xref:System.Windows.Media.PathGeometry>. Geometria elipsy <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwość, która przyjmuje <xref:System.Windows.Point> wartość, określa jej położenie; geometrii elipsy, animowanie możesz przenieść jego <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwości. W przykładzie użyto <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animować <xref:System.Windows.Media.EllipseGeometry> obiektu <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwości.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Wersja kodu powyższego przykładu używane <xref:System.Windows.Media.Animation.Storyboard> animować <xref:System.Windows.Media.EllipseGeometry>, mimo że zastosowano tylko jednej animacji. A <xref:System.Windows.Media.Animation.Storyboard> często jest najprostszym sposobem na stosowanie wielu animacji, ponieważ te animacje mogą być kontrolowane przez ten sam <xref:System.Windows.Media.Animation.Storyboard>. Jednak ułatwiających stosowanie jednej animacji z właściwością przy użyciu kodu jest użycie <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody. Aby uzyskać przykład, zobacz [animować właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028)
- [Animacja — przegląd](animation-overview.md)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
