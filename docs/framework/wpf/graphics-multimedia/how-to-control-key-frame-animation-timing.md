---
title: 'Instrukcje: Kontroluj chronometraż animacji kluczowych klatek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 02171c4e2bf444d0bd31bc53fab9d451f081a93c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353728"
---
# <a name="how-to-control-key-frame-animation-timing"></a>Instrukcje: Kontroluj chronometraż animacji kluczowych klatek
W tym przykładzie pokazano, jak kontrolować chronometraż klatek kluczowych w animacji kluczowych klatek. Podobnie jak inne animacji mają Animacja kluczowych klatek <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości. Oprócz określenia czasu trwania animacji, należy określić, jaka część za ten czas jest przydzielony do każdego z jego użyciem klatek kluczowych. Aby przydzielić czas, należy określić <xref:System.Windows.Media.Animation.KeyTime> dla każdej ramki kluczowe animacji.  
  
 <xref:System.Windows.Media.Animation.KeyTime> Dla każdej ramki kluczowe określa po zakończeniu klatek kluczowych (nie określa długość czasu odtwarzania klatek kluczowych). Można określić <xref:System.Windows.Media.Animation.KeyTime> jako <xref:System.TimeSpan> wartości, jako wartość procentowa lub jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> lub <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> specjalna wartość.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> animować prostokąt na ekranie. Czasy kluczowych klatek kluczowych są konfigurowane przy użyciu <xref:System.TimeSpan> wartości.  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 Poniższa ilustracja przedstawia po osiągnięciu wartości poszczególnych kluczowych klatek.  
  
 ![Wartości klucza są osiągane na 3, 4 i 10 sekund](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")  
  
 W kolejnym przykładzie pokazano animacji, który jest identyczny, z tą różnicą, że czasy kluczowych klatek kluczowych są konfigurowane przy użyciu wartości procentowe.  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 Poniższa ilustracja przedstawia po osiągnięciu wartości poszczególnych kluczowych klatek.  
  
 ![Wartości klucza są osiągane na 3, 4 i 10 sekund](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")  
  
 W następnym przykładzie użyto <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> wartości czasu klucza.  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 Poniższa ilustracja przedstawia po osiągnięciu wartości poszczególnych kluczowych klatek.  
  
 ![Wartości klucza są osiągane w 3.3,6.6 i 9,9 s](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")  
  
 W ostatnim przykładzie użyto <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> wartości czasu klucza.  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 Poniższa ilustracja przedstawia po osiągnięciu wartości poszczególnych kluczowych klatek.  
  
 ![Wartości klucza są osiągane na 0, 5 i 10 sekund](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")  
  
 Dla uproszczenia wersje kodu, ten przykład użycia lokalnej animacji, nie scenorysy, ponieważ tylko jednej animacji są stosowane do pojedynczej właściwości, ale przykłady może zmodyfikować tak, aby zamiast tego użyj scenorysów. Przykład przedstawiający sposób deklarowania scenorysu w kodzie, zobacz [animować właściwość przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012). Aby uzyskać więcej informacji na temat klatek kluczowych animacji zobacz [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Animacja — przegląd](animation-overview.md)
- [Tematy z instrukcjami](animation-and-timing-how-to-topics.md)
