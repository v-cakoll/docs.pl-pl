---
title: 'Instrukcje: Animowanie nieprzezroczystości elementu lub pędzla'
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: 2f18861eb18f81b631245d1d933b7acb1b3e0e42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950513"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Instrukcje: Animowanie nieprzezroczystości elementu lub pędzla
Aby element Framework przechodził do i z widoku, można animować jego <xref:System.Windows.UIElement.Opacity%2A> właściwość lub <xref:System.Windows.Media.Brush.Opacity%2A> animować Właściwość <xref:System.Windows.Media.Brush> (lub pędzle) służącą do malowania. Animowanie nieprzezroczystości elementu sprawia, że jego elementy podrzędne zmniejszają się i znikają z widoku, ale animowanie pędzla użytego do malowania elementu umożliwia bardziej wybiórcze przeciemnienie części elementu. Można na przykład animować nieprzezroczystość pędzla używanego do malowania tła przycisku. Mogłoby to spowodować zanikanie i wyjście tła przycisku, pozostawiając jego tekst w pełni nieprzezroczysty.  
  
> [!NOTE]
> Animowanie a <xref:System.Windows.Media.Brush> zapewnia <xref:System.Windows.UIElement.Opacity%2A> korzyści z wydajności nad animacją właściwości elementu. <xref:System.Windows.Media.Brush.Opacity%2A>  
  
 W poniższym przykładzie dwa przyciski są animowane w taki sposób, aby były stopniowo rozjaśniane i niewidoczne. Nieprzezroczystość pierwszego <xref:System.Windows.Controls.Button> jest animowana od `1.0` do `0.0` <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 5 sekund. Drugi przycisk jest również animowany, ale nieprzezroczystość SolidColorBrush użyta do malowania <xref:System.Windows.Controls.Control.Background%2A> jest animowana, a nie przezroczystość całego przycisku. Po uruchomieniu tego przykładu, pierwszy przycisk jest całkowicie rozjaśniany i wychodzący z widoku, podczas gdy tylko tło drugiego przycisku zanika do i z widoku. Jego tekst i obramowanie pozostają w pełni nieprzezroczyste.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#10](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 Kod został pominięty w tym przykładzie. Pełny przykład pokazuje również, jak animować nieprzezroczystość <xref:System.Windows.Media.Color> <xref:System.Windows.Media.LinearGradientBrush>w obrębie.  Aby uzyskać pełny przykład, zobacz animowanie nieprzezroczystości [przykładu elementu](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/OpacityAnimation).
