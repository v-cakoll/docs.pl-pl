---
title: 'Instrukcje: Animowanie obiektu na ścieżce (animacja Matrix)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: ab15126680b7d8c6936246a7dae2f67c7541233b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651444"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Instrukcje: Animowanie obiektu na ścieżce (animacja Matrix)
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> klasy animowanie obiektu na ścieżce, który jest definiowany przez <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład animuje obiekt na ścieżce, wykonując następujące czynności:  
  
- Stosuje <xref:System.Windows.Media.MatrixTransform> do obiektu, aby go przenieść.  
  
- Określa ścieżkę przy użyciu <xref:System.Windows.Media.PathGeometry>.  
  
- Tworzy <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> i używa go, animować <xref:System.Windows.Media.Matrix> właściwość <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Przyjmuje <xref:System.Windows.Media.PathGeometry> i używa ich do generowania <xref:System.Windows.Media.Matrix> wartości.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028). Aby uzyskać więcej informacji na temat ścieżek geometrycznych zobacz [Przegląd Geometria](geometry-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
- [Przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
