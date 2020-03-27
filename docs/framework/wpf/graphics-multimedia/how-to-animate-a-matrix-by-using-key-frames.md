---
title: Jak animować Matrix z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344918"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Jak animować Matrix z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość a <xref:System.Windows.Media.MatrixTransform> za pomocą klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> użyto <xref:System.Windows.Media.MatrixTransform.Matrix%2A> klasy do <xref:System.Windows.Media.MatrixTransform>animowania właściwości . . W przykładzie <xref:System.Windows.Media.MatrixTransform> użyto obiektu do przekształcenia wyglądu i położenia pliku <xref:System.Windows.Controls.Button>.  
  
 Ta animacja <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> używa klasy do utworzenia dwóch klatek kluczowych i wykonuje następujące czynności z nimi:  
  
1. Animowanie pierwszego <xref:System.Windows.Media.Matrix> w ciągu pierwszych 0,2 sekundy. W przykładzie <xref:System.Windows.Media.Matrix.M11%2A> <xref:System.Windows.Media.Matrix.M12%2A> zmienia się <xref:System.Windows.Media.Matrix>właściwości . Ta zmiana powoduje, że przycisk się rozciąga i staje się pochylony. W przykładzie <xref:System.Windows.Media.Matrix.OffsetX%2A> również <xref:System.Windows.Media.Matrix.OffsetY%2A> zmienia właściwości i tak, aby przycisk zmienia położenie.  
  
2. Animowanie drugiego <xref:System.Windows.Media.Matrix> w 1,0 sekundy. Przycisk przesuwa się w inne miejsce, gdy przycisk nie jest już skośny lub rozciągnięty.  
  
3. Powtarza animację przez czas nieokreślony.  
  
> [!NOTE]
> Klatki kluczowe, które <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> wynikają z obiektu, tworzą nagłe skoki między wartościami, czyli ruch animacji jest szarpany.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
