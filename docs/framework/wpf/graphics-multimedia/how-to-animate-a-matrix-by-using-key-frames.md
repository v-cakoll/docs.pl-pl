---
title: 'Instrukcje: Animowanie elementu Matrix przy użyciu klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 6aa3e27cdfda7597c9b6acbf2980a2774f2b667b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963022"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Instrukcje: Animowanie elementu Matrix przy użyciu klatek kluczowych
Ten przykład pokazuje, jak animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> Właściwość <xref:System.Windows.Media.MatrixTransform> z przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> klasy do <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animowania właściwości <xref:System.Windows.Media.MatrixTransform>. W przykładzie zastosowano <xref:System.Windows.Media.MatrixTransform> obiekt do przekształcenia wyglądu i położenia. <xref:System.Windows.Controls.Button>  
  
 Ta animacja używa <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> klasy do tworzenia dwóch kluczowych klatek i wykonuje następujące czynności:  
  
1. Animuj pierwszy <xref:System.Windows.Media.Matrix> w ciągu pierwszych 0,2 sekund. Przykład zmienia <xref:System.Windows.Media.Matrix.M11%2A> właściwości <xref:System.Windows.Media.Matrix.M12%2A>i. <xref:System.Windows.Media.Matrix> Ta zmiana powoduje, że przycisk rozciąga się i stanie się skośny. Przykład zmienia <xref:System.Windows.Media.Matrix.OffsetX%2A> również właściwości i <xref:System.Windows.Media.Matrix.OffsetY%2A> tak, aby przycisk zmienia pozycję.  
  
2. Animuj sekundę <xref:System.Windows.Media.Matrix> o 1,0 sekund. Przycisk jest przesuwany do innego położenia, gdy przycisk nie jest już skośny lub rozciągany.  
  
3. Powtarza animację na czas nieokreślony.  
  
> [!NOTE]
> Klatki kluczowe, które pochodzą od <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> obiektu, tworzą nagłe uskoki między wartościami, czyli przenoszenie animacji jest Jerky.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji klatki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
