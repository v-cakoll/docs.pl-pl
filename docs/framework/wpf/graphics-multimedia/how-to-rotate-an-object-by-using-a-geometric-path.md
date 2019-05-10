---
title: 'Instrukcje: Obracanie obiektu przy użyciu ścieżki geometrycznej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: 6a0f566bab47d26aeb5e651b35845f577dfd7c48
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645387"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Instrukcje: Obracanie obiektu przy użyciu ścieżki geometrycznej
W tym przykładzie pokazano, jak obrócić (Tabela przestawna) obiekt na ścieżce geometryczne, który jest definiowany przez <xref:System.Windows.Media.PathGeometry> obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto trzy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> obiektów można przesuwać wzdłuż ścieżki geometrycznej.  
  
- Pierwszy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.RotateTransform> mający zastosowanie do prostokąta. Animacja generuje wartości kąta. To sprawia, że prostokąt Obróć (Tabela przestawna) wzdłuż konturów ścieżki.  
  
- Animowanie dwa obiekty <xref:System.Windows.Media.TranslateTransform.X%2A> i <xref:System.Windows.Media.TranslateTransform.Y%2A> wartości <xref:System.Windows.Media.TranslateTransform> mający zastosowanie do prostokąta. Dokonają prostokąt, Przenieś poziomo i pionowo wzdłuż ścieżki.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Obracanie obiektu przy użyciu ścieżki geometrycznej innym sposobem jest użycie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu i ustaw jego <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość `true`. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [Obracanie obiektu przy użyciu ścieżki geometrycznej (animacja Matrix)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
- [Przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
