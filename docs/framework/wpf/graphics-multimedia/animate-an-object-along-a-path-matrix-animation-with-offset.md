---
title: "Jak animować obiekt na ścieżce (animacja matrycy akumulacją przesunięcia)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a9fd282d3ca4603eadd0ed10436944f7e9ab593
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Jak animować obiekt na ścieżce (animacja matrycy akumulacją przesunięcia)
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> klasy do animowania obiektu wzdłuż ścieżki i animacji gromadzone jego przesunięcie wartości jak powtarza się.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu do animowania <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform> stosowane do przycisku. W związku z tym przycisku przenosi wzdłuż ścieżki.  
  
 Ponadto w przykładzie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> właściwości `true`, co powoduje, że przesunięcie animowany macierzy gromadzone jako powtarza animacji. Ponieważ w wyniku przesunięcie, przycisk przechodzi dalej wzdłuż ekranu, gdy animacji jest powtarzany, zamiast zresetowanie do pozycji początkowej.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Należy zauważyć, że chociaż <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> właściwości powoduje przesunięcia wartości gromadzone przez powtórzeń, nie powoduje wartości obrotu kumulują się. Aby wartości obrotu gromadzone, ustaw animację <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> i <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> właściwości `true`.  
  
 Pełny przykład, zobacz [próbki animacji ścieżki](http://go.microsoft.com/fwlink/?LinkID=160028). Na przykład przedstawiający sposób animować <xref:System.Windows.Media.Matrix> wartość wzdłuż ścieżki bez przesunięcia akumulacji, zobacz [Animowanie obiektów wzdłuż ścieżki (macierzy Animacja)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Ścieżka animacji — tematy porad](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
