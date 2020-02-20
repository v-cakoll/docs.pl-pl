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
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452912"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Jak animować obiekt na ścieżce (animacja Matrix)
Ten przykład pokazuje, jak używać klasy <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> do animowania obiektu w ścieżce zdefiniowanej przez <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia animowanie obiektu na ścieżce, wykonując następujące czynności:  
  
- Stosuje <xref:System.Windows.Media.MatrixTransform> do obiektu, aby go przenieść.  
  
- Definiuje ścieżkę przy użyciu <xref:System.Windows.Media.PathGeometry>.  
  
- Tworzy <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> i używa go do animowania właściwości <xref:System.Windows.Media.Matrix> <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pobiera <xref:System.Windows.Media.PathGeometry> i używa jej do generowania wartości <xref:System.Windows.Media.Matrix>.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations). Aby uzyskać więcej informacji na temat ścieżek geometrycznych, zobacz [Omówienie geometrii](geometry-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- [Animacja — przegląd](animation-overview.md)
- [Przykład animacji ścieżki](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
