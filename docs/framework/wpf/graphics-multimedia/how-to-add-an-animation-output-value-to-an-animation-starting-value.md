---
title: 'Instrukcje: Dodawanie wartości danych wyjściowych animacji do wartości początkowej animacji'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 945675d03a280e2394fdb0eab27c0978dc7cc320
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102612"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>Instrukcje: Dodawanie wartości danych wyjściowych animacji do wartości początkowej animacji
W tym przykładzie pokazano, jak dodawać wartość danych wyjściowych animacji do wartości początkowej animacji.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Właściwość określa, czy ma zostać zwrócona wartość danych wyjściowych animacji dodane do początkowej wartości (wartości bazowej) właściwością animowany. Możesz użyć <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> właściwość najbardziej podstawowym animacje i większości klatek kluczowych animacji. Aby uzyskać więcej informacji, zobacz [Przegląd animacja](animation-overview.md) i [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md).  
  
 Poniższy przykład przedstawia efekt użycia <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> właściwość o <xref:System.Windows.Media.Animation.DoubleAnimation> i przy użyciu <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> właściwość o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Gromadzenie wartości animacji podczas cykli powtórzeń](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [Animacja — przegląd](animation-overview.md)
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Animacja i chronometraż tematy porad](animation-and-timing-how-to-topics.md)
