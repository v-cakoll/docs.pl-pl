---
title: Jak animować obiekt z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 7dc49bc6b3f9156507cb821bfc32b269365b206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Jak animować obiekt z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować obiekt, który w tym przykładzie jest <xref:System.Windows.Controls.Page.Background%2A> właściwość <xref:System.Windows.Controls.Page> formantu przy użyciu klucza ramki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasy animacji kolorów zmiany dla <xref:System.Windows.Controls.Page.Background%2A> właściwość <xref:System.Windows.Controls.Page> formantu. Przykład zmiany animacji pędzel tła różnych w regularnych odstępach czasu. Używa tego animacji <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> klasy w celu utworzenia trzech różnych klatek kluczowych. Animacja używa klatek kluczowych w następujący sposób:  
  
1.  Na końcu pierwszego sekundę animuje wystąpienia <xref:System.Windows.Media.LinearGradientBrush> klasy. Ta sekcja przykładu dotyczy gradientu liniowego kolor tła, tak aby kolor przejścia z żółtym na pomarańczowy na czerwony.  
  
2.  Po zakończeniu następnej sekundy animuje wystąpienia <xref:System.Windows.Media.RadialGradientBrush> klasy. Ta sekcja przykładu dotyczy gradient promieniowy kolor tła, tak aby kolor przejścia od białego na niebieski na kolor czarny.  
  
3.  Na końcu drugiej danej wejściowej trzecie animuje wystąpienia <xref:System.Windows.Media.DrawingBrush> klasy. Ta sekcja przykładu dotyczy wzorzec szachownicy tła.  
  
4.  Animacja rozpoczyna się od nowa i nieskończoność powtarza się.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> jest to jedyny typ klucza ramki, w której można używać z <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasy. Klucz ramek, takich jak <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> utworzyć nagłym zmian w wartości, oznacza to, zmiany kolorów w tym przykładzie występują nagle.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
