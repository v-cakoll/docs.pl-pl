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
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186874"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej
W tym przykładzie pokazano, jak obrócić (obrócić) obiekt <xref:System.Windows.Media.PathGeometry> wzdłuż ścieżki geometrycznej zdefiniowanej przez obiekt.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto trzech <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> obiektów do przesuń prostokąt wzdłuż ścieżki geometrycznej.  
  
- Pierwszy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.RotateTransform> a, który jest stosowany do prostokąta. Animacja generuje wartości kąta. To sprawia, że prostokąt obraca się (pivot) wzdłuż konturów ścieżki.  
  
- Pozostałe dwa obiekty animują <xref:System.Windows.Media.TranslateTransform.X%2A> wartości i <xref:System.Windows.Media.TranslateTransform.Y%2A> wartości <xref:System.Windows.Media.TranslateTransform> a, które są stosowane do prostokąta. Sprawiają, że prostokąt porusza się poziomo i pionowo wzdłuż ścieżki.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Innym sposobem obracania obiektu za pomocą ścieżki geometrycznej jest użycie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu i ustawienie jego <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwości na `true`. Aby uzyskać więcej informacji i przykład, zobacz [Obracanie obiektu przy użyciu ścieżki geometrycznej (animacja macierzy)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład animacji ścieżki](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja](animation-overview.md)
- [Przykład animacji ścieżki](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
