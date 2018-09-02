---
title: Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: 6d6d21f3f7b609cb2933093a6990425deb39d4a6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398151"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej
W tym przykładzie pokazano, jak obrócić (Tabela przestawna) obiekt na ścieżce geometryczne, który jest definiowany przez <xref:System.Windows.Media.PathGeometry> obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto trzy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> obiektów można przesuwać wzdłuż ścieżki geometrycznej.  
  
-   Pierwszy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.RotateTransform> mający zastosowanie do prostokąta. Animacja generuje wartości kąta. To sprawia, że prostokąt Obróć (Tabela przestawna) wzdłuż konturów ścieżki.  
  
-   Animowanie dwa obiekty <xref:System.Windows.Media.TranslateTransform.X%2A> i <xref:System.Windows.Media.TranslateTransform.Y%2A> wartości <xref:System.Windows.Media.TranslateTransform> mający zastosowanie do prostokąta. Dokonają prostokąt, Przenieś poziomo i pionowo wzdłuż ścieżki.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Obracanie obiektu przy użyciu ścieżki geometrycznej innym sposobem jest użycie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu i ustaw jego <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość `true`. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [Obracanie obiektu przy użyciu ścieżki geometrycznej (animacja Matrix)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [Animacja ścieżki — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
