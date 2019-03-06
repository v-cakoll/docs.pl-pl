---
title: 'Instrukcje: Animuj obiekt na ścieżce (animacja Matrix)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: c0c4f1fad5ab6b8d30e6809aa866b4629d08af23
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363738"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Instrukcje: Animuj obiekt na ścieżce (animacja Matrix)
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> klasy animowanie obiektu na ścieżce, który jest definiowany przez <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład animuje obiekt na ścieżce, wykonując następujące czynności:  
  
-   Stosuje <xref:System.Windows.Media.MatrixTransform> do obiektu, aby go przenieść.  
  
-   Określa ścieżkę przy użyciu <xref:System.Windows.Media.PathGeometry>.  
  
-   Tworzy <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> i używa go, animować <xref:System.Windows.Media.Matrix> właściwość <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Przyjmuje <xref:System.Windows.Media.PathGeometry> i używa ich do generowania <xref:System.Windows.Media.Matrix> wartości.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028). Aby uzyskać więcej informacji na temat ścieżek geometrycznych zobacz [Przegląd Geometria](geometry-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- [Animacja — przegląd](animation-overview.md)
- [Przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
