---
title: Jak dodawać wartość danych wyjściowych animacji do wartości początkowej animacji
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: bae7bf57507e3345c92cbbaf24491d86772425a4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407054"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>Jak dodawać wartość danych wyjściowych animacji do wartości początkowej animacji
W tym przykładzie pokazano, jak dodawać wartość danych wyjściowych animacji do wartości początkowej animacji.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Właściwość określa, czy ma zostać zwrócona wartość danych wyjściowych animacji dodane do początkowej wartości (wartości bazowej) właściwością animowany. Możesz użyć <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> właściwość najbardziej podstawowym animacje i większości klatek kluczowych animacji. Aby uzyskać więcej informacji, zobacz [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) i [Przegląd Animacja kluczowych klatek](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 Poniższy przykład przedstawia efekt użycia <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> właściwość o <xref:System.Windows.Media.Animation.DoubleAnimation> i przy użyciu <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> właściwość o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Gromadzenie wartości animacji podczas cykli powtórzeń](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animacja i chronometraż](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
