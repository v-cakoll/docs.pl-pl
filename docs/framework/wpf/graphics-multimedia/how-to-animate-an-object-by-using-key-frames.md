---
title: 'Instrukcje: Animowanie obiektu przy użyciu klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933907"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Instrukcje: Animowanie obiektu przy użyciu klatek kluczowych
Ten przykład pokazuje, jak animować obiekt, który w tym przykładzie jest <xref:System.Windows.Controls.Page.Background%2A> właściwością <xref:System.Windows.Controls.Page> kontrolki, przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasy do animowania zmian <xref:System.Windows.Controls.Page.Background%2A> koloru właściwości <xref:System.Windows.Controls.Page> formantu. Przykład animacji zmienia się w inny Pędzel tła w regularnych odstępach czasu. Ta animacja używa klasy <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> , aby utworzyć trzy różne kluczowe klatki. Animacja używa kluczowych klatek w następujący sposób:  
  
1. Na końcu pierwszej sekundy program Animuj wystąpienie <xref:System.Windows.Media.LinearGradientBrush> klasy. W tej sekcji przykładu stosuje się gradient liniowy do koloru tła, dzięki czemu kolory z żółtej do pomarańczy są zmieniane na czerwony.  
  
2. Na końcu kolejnej sekundy program Animuj wystąpienie <xref:System.Windows.Media.RadialGradientBrush> klasy. W tej sekcji przykładu stosuje się gradient promieniowy do koloru tła, dzięki czemu kolory z czerni do czerni mają być czarne.  
  
3. Na końcu trzeciej sekundy program Animuj wystąpienie <xref:System.Windows.Media.DrawingBrush> klasy. W tej sekcji przykładu stosuje się wzór szachownicy do tła.  
  
4. Animacja rozpocznie się ponownie i powtarza się w nieskończoność.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>jest jedynym typem ramki klucza, której można użyć z <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasą. Kluczowe klatki, <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> takie jak tworzenie nagłych zmian w wartości, oznacza to, że kolor zmiany w tym przykładzie wystąpił nagle.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji klatki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
