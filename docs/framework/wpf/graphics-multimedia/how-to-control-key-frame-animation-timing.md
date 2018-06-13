---
title: Jak kontrolować chronometraż animacji kluczowych klatek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 7aacb975557a25b8ea7a80e02c16a59b8a746e26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562300"
---
# <a name="how-to-control-key-frame-animation-timing"></a>Jak kontrolować chronometraż animacji kluczowych klatek
W tym przykładzie przedstawiono sposób kontrolować czas klatek kluczowych w animacji ramki klucza. Podobnie jak inne animacje mają klucz poklatkowych <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości. Oprócz określanie czasu trwania animacji, należy określić, jaka część ten czas trwania jest przydzielony do każdego z jego klatek kluczowych. Aby przyznać czas, należy określić <xref:System.Windows.Media.Animation.KeyTime> dla każdego klatek kluczowych animacji.  
  
 <xref:System.Windows.Media.Animation.KeyTime> Dla każdej klatki określa podczas zakończenia klatki (nie określa czas odgrywa klatek kluczowych). Można określić <xref:System.Windows.Media.Animation.KeyTime> jako <xref:System.TimeSpan> wartości, w procentach lub jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> lub <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> specjalna wartość.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> do animowania prostokąt na ekranie. Klatek kluczowych klucza czasy są konfigurowane przy użyciu <xref:System.TimeSpan> wartości.  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 Na poniższej ilustracji pokazano po osiągnięciu wartości każdego klatki.  
  
 ![Wartości klucza są osiągane w 3, 4 i 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")  
  
 W kolejnym przykładzie pokazano animacji, który jest taki sam, z wyjątkiem tego, że czasy klucza klatek kluczowych są konfigurowane przy użyciu wartości procentowe.  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 Na poniższej ilustracji pokazano po osiągnięciu wartości każdego klatki.  
  
 ![Wartości klucza są osiągane w 3, 4 i 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")  
  
 W następnym przykładzie użyto <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> wartości czasu klucza.  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 Na poniższej ilustracji pokazano po osiągnięciu wartości każdego klatki.  
  
 ![Wartości klucza są osiągane w 3.3,6.6 i 9,9 s](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")  
  
 W ostatnim przykładzie użyto <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> wartości czasu klucza.  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 Na poniższej ilustracji pokazano po osiągnięciu wartości każdego klatki.  
  
 ![Wartości klucza są osiągane na 0, 5 i 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")  
  
 Dla uproszczenia wersje kodu to przykład użycia lokalnej animacji, nie scenorys, ponieważ tylko jednego animacji jest stosowana do jednej właściwości, ale może być modyfikowany przykłady zamiast tego użyć scenorys. Na przykład pokazujący sposób zadeklarować scenorysu w kodzie, zobacz [animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012). Aby uzyskać więcej informacji na temat klatek kluczowych animacji, zobacz [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
