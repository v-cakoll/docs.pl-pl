---
title: 'Instrukcje: Animuj obiekt na ścieżce (animacja matrycy akumulacją przesunięcia)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: e5e619de8b90737136559db134a131fdc1833fb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640098"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Instrukcje: Animuj obiekt na ścieżce (animacja matrycy akumulacją przesunięcia)
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> klasy animowanie obiektu na ścieżce i animacji są gromadzone przesunięcie wartości jak powtarza się.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform> stosowane do przycisku. W rezultacie przycisku przenosi wzdłuż ścieżki.  
  
 Ponadto w przykładzie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> właściwości `true`, co powoduje, że przesunięcie animowany macierzy kumulowania jako animacji powtarza się. Ponieważ w wyniku Przesunięcie przycisku porusza się dalej na ekran, gdy jest powtarzany animacji, zamiast zresetowanie do ustawień pozycja początkowa.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Należy zauważyć, że, mimo że <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> właściwości powoduje przesunięcia wartości są gromadzone przez powtórzeń, nie powoduje obrotu wartości do. Aby obrotu wartości są gromadzone, ustaw animacji <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> i <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> właściwości `true`.  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028). Aby uzyskać przykład pokazujący sposób animować <xref:System.Windows.Media.Matrix> wartość na ścieżce bez akumulacją przesunięcia, zobacz [animowanie obiektu na ścieżce (animacja Matrix)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Zobacz także
- [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Animacja ścieżki — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
