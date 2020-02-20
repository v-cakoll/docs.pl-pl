---
title: Jak animować obiekt na ścieżce (animacja matrycy akumulacją przesunięcia)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453107"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Jak animować obiekt na ścieżce (animacja matrycy akumulacją przesunięcia)
Ten przykład pokazuje, jak używać klasy <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> do animowania obiektu na ścieżce i czy animacja będzie zbierać wartości przesunięcia w miarę ich powtarzania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa obiektu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>, aby animować Właściwość <xref:System.Windows.Media.MatrixTransform.Matrix%2A> <xref:System.Windows.Media.MatrixTransform> zastosowana do przycisku. W efekcie przycisk jest przesuwany wzdłuż ścieżki zakrzywionej.  
  
 Ponadto, przykład ustawia właściwość <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> na `true`, co powoduje, że przesunięcie animowanej macierzy będzie sumowane w miarę powtarzania animacji. Ze względu na to, że przesunięcie zostanie wykonane, przycisk przesuwa się dalej na ekranie, gdy animacja powtarza się, a nie resetuje do pozycji początkowej.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Należy zauważyć, że mimo że właściwość <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> powoduje, że wartości przesunięcia są sumowane za pośrednictwem powtórzeń, nie powoduje sumowania wartości obrotu. Aby narastać wartości rotacji, ustaw właściwości <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> i <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> animacji na `true`.  
  
 Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations). Aby zapoznać się z przykładem pokazującym, jak animować wartość <xref:System.Windows.Media.Matrix> wzdłuż ścieżki bez kumulacji przesunięcia, zobacz [animowanie obiektu na ścieżce (animacja macierzy)](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Zobacz też

- [Animacja — przegląd](animation-overview.md)
- [Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)
