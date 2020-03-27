---
title: Jak kontrolować chronometraż animacji kluczowych klatek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-frame animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 8cfd2be0bbc526ed92a5fb1b558a5a41dc9c3113
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344734"
---
# <a name="how-to-control-key-frame-animation-timing"></a>Jak kontrolować chronometraż animacji kluczowych klatek

W tym przykładzie pokazano, jak kontrolować czas klatek kluczowych w animacji klatki kluczowej. Podobnie jak inne animacje, animacje <xref:System.Windows.Media.Animation.Timeline.Duration%2A> klatek kluczowych mają właściwość. Oprócz określenia czasu trwania animacji, należy określić, jaka część tego czasu trwania jest przydzielana do każdej z jej klatek kluczowych. Aby przymielić czas, należy określić <xref:System.Windows.Media.Animation.KeyTime> dla każdej klatki kluczowej w animacji.

Dla <xref:System.Windows.Media.Animation.KeyTime> każdej klatki kluczowej określa się, kiedy kończy się klatka kluczowa (nie określa czasu odtwarzania klatki kluczowej). Można określić <xref:System.Windows.Media.Animation.KeyTime> jako <xref:System.TimeSpan> wartość, jako wartość procentową lub jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> wartość specjalną lub specjalną. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>

## <a name="example"></a>Przykład

W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> do animowania prostokąta na ekranie. Czasy kluczowe ramki są <xref:System.TimeSpan> ustawiane z wartościami.

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

Na poniższej ilustracji pokazano, kiedy zostanie osiągnięta wartość każdej klatki kluczowej.

![Wartości kluczy są osiągane po 3, 4 i 10 sekundach](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")

W następnym przykładzie pokazano animację, która jest identyczna, z tą różnicą, że czasy klucza klatek kluczowych są ustawiane z wartościami procentowymi.

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

Na poniższej ilustracji pokazano, kiedy zostanie osiągnięta wartość każdej klatki kluczowej.

![Wartości kluczy są osiągane po 3, 4 i 10 sekundach](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")

W następnym przykładzie użyto <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> kluczowych wartości czasu.

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

Na poniższej ilustracji pokazano, kiedy zostanie osiągnięta wartość każdej klatki kluczowej.

![Wartości kluczy są osiągane na poziomie 3,3,6,6 i 9,9 sekundy](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")

W przykładzie <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> końcowym użyto kluczowych wartości czasu.

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

Na poniższej ilustracji pokazano, kiedy zostanie osiągnięta wartość każdej klatki kluczowej.

![Wartości kluczy są osiągane w 0, 5 i 10 sekund](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")

Dla uproszczenia wersje kodu w tym przykładzie używają animacji lokalnych, a nie scenoprzyokiłów, ponieważ tylko pojedyncza animacja jest stosowana do jednej właściwości, ale przykłady mogą być modyfikowane w celu użycia scenodzielek zamiast tego. Aby zapoznać się z przykładem przedstawiającym sposób deklarowania serii ujęć w kodzie, zobacz [Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md).

Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation). Aby uzyskać więcej informacji na temat animacji klatek kluczowych, zobacz [Omówienie animacji klatek kluczowych](key-frame-animations-overview.md).

## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Przegląd Animacja](animation-overview.md)
- [— Tematy porad](animation-and-timing-how-to-topics.md)
