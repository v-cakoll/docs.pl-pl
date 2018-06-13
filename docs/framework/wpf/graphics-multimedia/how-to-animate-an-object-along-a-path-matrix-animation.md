---
title: Jak animować obiekt na ścieżce (animacja Matrix)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 03e1e40f8ee6840558ad7b712d96e63d9e2bf15f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559006"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Jak animować obiekt na ścieżce (animacja Matrix)
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> klasy do animowania obiektu wzdłuż ścieżki, która jest definiowana za pomocą <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład animuje obiektu wzdłuż ścieżki, wykonując następujące czynności:  
  
-   Stosuje <xref:System.Windows.Media.MatrixTransform> do obiektu, aby go przenieść.  
  
-   Określa ścieżkę przy użyciu <xref:System.Windows.Media.PathGeometry>.  
  
-   Tworzy <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> i używa go do animowania <xref:System.Windows.Media.Matrix> właściwość <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Przyjmuje <xref:System.Windows.Media.PathGeometry> i używa go do wygenerowania <xref:System.Windows.Media.Matrix> wartości.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Pełny przykład, zobacz [próbki animacji ścieżki](http://go.microsoft.com/fwlink/?LinkID=160028). Aby uzyskać więcej informacji o ścieżkach geometryczne, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Ścieżka animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Animacja ścieżki — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
