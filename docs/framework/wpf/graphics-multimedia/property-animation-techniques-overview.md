---
title: Przegląd Techniki animacji właściwości
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
ms.openlocfilehash: 09e778f89f58556a53f19b4c89e3d82ed94cd64b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614165"
---
# <a name="property-animation-techniques-overview"></a>Przegląd Techniki animacji właściwości
W tym temacie opisano różne metody animowania właściwości: scenorysów, lokalnego animacji, zegary i animacje w poszczególnych klatkach.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z funkcjami podstawowa Animacja opisanego w [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="summary"></a>   
## <a name="different-ways-to-animate"></a>Różne sposoby, aby animować  
 Ponieważ istnieje wiele różnych scenariuszy animowania właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia kilka metod animowania właściwości.  
  
 W przypadku każde podejście Poniższa tabela wskazuje, czy może być używany dla wystąpienia, style, szablonach formantów lub szablonów danych; czy może być używana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; i czy podejście pozwala interaktywnie kontrolować animację.  "Na wystąpienie" odnosi się do technika stosowania animacji lub scenorysu bezpośrednio do wystąpienia obiektu, a nie w stylu, szablon kontrolki lub szablon danych.  
  
|Techniki animacji|Scenariusze|Obsługa w XAML|Interaktywnie kontrolowania|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Animacja scenorysu|Na wystąpienie <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.DataTemplate>|Tak|Tak|  
|Lokalna Animacja|Na wystąpienie|Nie|Nie|  
|Animacja zegara|Na wystąpienie|Nie|Tak|  
|Animacja ramki|Na wystąpienie|Nie|Brak|  
  
<a name="storyboard_animations"></a>   
## <a name="storyboard-animations"></a>Animacjami scenorysu  
 Użyj <xref:System.Windows.Media.Animation.Storyboard> umożliwia definiowanie i stosowanie animacji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], interaktywnie kontrolować animacji, po uruchamianie, tworzenie złożonych drzewa animacji i animować w <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> lub <xref:System.Windows.DataTemplate>. Aby obiekt można być animowane przez <xref:System.Windows.Media.Animation.Storyboard>, musi to być <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, lub musi być używany do ustawiania <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Aby uzyskać więcej informacji, zobacz [Przegląd Scenorysy](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 A <xref:System.Windows.Media.Animation.Storyboard> to specjalny typ kontenera <xref:System.Windows.Media.Animation.Timeline> zawierające informacje określania wartości docelowej dla animacji zawiera. Aby animować z <xref:System.Windows.Media.Animation.Storyboard>, wykonaj następujące trzy kroki.  
  
1.  Zadeklaruj <xref:System.Windows.Media.Animation.Storyboard> i co najmniej jeden animacji.  
  
2.  Użyj <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> dołączonych właściwości, aby określić obiekt docelowy i właściwości każdej animacji.  
  
3.  (Tylko kod) Zdefiniuj <xref:System.Windows.NameScope> dla <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Zarejestruj nazwy obiektów, aby animować z tym <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>.  
  
4.  Rozpocznij <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Począwszy od <xref:System.Windows.Media.Animation.Storyboard> dotyczy animacji właściwości one animować i można je uruchomić. Istnieją dwa sposoby, aby rozpocząć <xref:System.Windows.Media.Animation.Storyboard>: możesz użyć <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody dostarczone przez <xref:System.Windows.Media.Animation.Storyboard> klas, lub użyć <xref:System.Windows.Media.Animation.BeginStoryboard> akcji. Jedynym sposobem, aby animować w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest użycie <xref:System.Windows.Media.Animation.BeginStoryboard> akcji. A <xref:System.Windows.Media.Animation.BeginStoryboard> akcji mogą być używane w <xref:System.Windows.EventTrigger>, właściwość <xref:System.Windows.Trigger>, lub <xref:System.Windows.DataTrigger>.  
  
 W poniższej tabeli przedstawiono różnych miejscach gdzie każdy <xref:System.Windows.Media.Animation.Storyboard> rozpocząć techniką jest obsługiwany: poszczególnych wystąpień, style, szablon kontrolki i szablon danych.  
  
|Rozpoczyna się scenorysu, za pomocą...|Na wystąpienie|Styl|Szablon kontrolki|Szablon danych|Przykład|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> i <xref:System.Windows.EventTrigger>|Tak|Yes|Yes|Tak|[Animowanie właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> i właściwości <xref:System.Windows.Trigger>|Nie|Yes|Yes|Tak|[Wyzwalanie animacji w przypadku zmiany wartości właściwości](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.DataTrigger>|Nie|Yes|Yes|Tak|[Instrukcje: Wyzwalanie animacji w przypadku zmiany danych](https://msdn.microsoft.com/library/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> — Metoda|Tak|Nie|Nie|Nie|[Animowanie właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Animation.Storyboard> obiekty, zobacz [Przegląd Scenorysy](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
## <a name="local-animations"></a>Lokalne animacji  
 Animacje lokalne zapewniają wygodny sposób, aby animować właściwości zależności dowolnego <xref:System.Windows.Media.Animation.Animatable> obiektu. Użyj lokalnej animacji, gdy chcesz zastosować jednej animacji z właściwością i nie ma potrzeby interaktywnie kontrolować animację po uruchomieniu. W odróżnieniu od <xref:System.Windows.Media.Animation.Storyboard> animacji, lokalna Animacja można animować obiekt, który nie jest skojarzony z <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Ponadto nie trzeba zdefiniować <xref:System.Windows.NameScope> dla tego typu animacji.  
  
 Animacje lokalne mogą być używane tylko w kodzie, a nie może być zdefiniowana w style, szablonach formantów lub szablonów danych. Lokalna animacja nie mogą być interaktywnie kontrolowane po jej ponownym uruchomieniu.  
  
 Aby animować przy użyciu lokalnego animacji, wykonaj następujące czynności.  
  
1.  Utwórz <xref:System.Windows.Media.Animation.AnimationTimeline> obiektu.  
  
2.  Użyj <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda obiektu, który chcesz animować do zastosowania <xref:System.Windows.Media.Animation.AnimationTimeline> do właściwości, które określisz.  
  
 Poniższy przykład pokazuje, jak animować kolor tła i szerokość <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Animacje zegara  
 Użyj <xref:System.Windows.Media.MediaPlayer.Clock%2A> obiekty, gdy chcesz animować bez użycia <xref:System.Windows.Media.Animation.Storyboard> i chcesz utworzyć złożone chronometrażu drzewa lub interaktywnie kontrolować animacji, po uruchomieniu. Obiekty Clock można użyć, aby animować właściwości zależności dowolnego <xref:System.Windows.Media.Animation.Animatable> obiektu.  
  
 Nie można użyć <xref:System.Windows.Media.Animation.Clock> obiektów bezpośrednio animować w stylach, kontrolują szablonów lub szablonów danych. (Animacja i chronometraż rzeczywiście używane w systemie <xref:System.Windows.Media.Animation.Clock> obiektów, aby animować w style, szablonów kontrolek, a szablony danych, ale należy utworzyć te <xref:System.Windows.Media.Animation.Clock> obiektów z <xref:System.Windows.Media.Animation.Storyboard>. Aby uzyskać więcej informacji na temat relacji między <xref:System.Windows.Media.Animation.Storyboard> obiektów i <xref:System.Windows.Media.Animation.Clock> obiekty, zobacz [Animacja i System chronometrażu w — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).)  
  
 Aby zastosować jeden <xref:System.Windows.Media.Animation.Clock> do właściwości, wykonaj następujące kroki.  
  
1.  Utwórz <xref:System.Windows.Media.Animation.AnimationTimeline> obiektu.  
  
2.  Użyj <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> metody <xref:System.Windows.Media.Animation.AnimationTimeline> utworzyć <xref:System.Windows.Media.Animation.AnimationClock>.  
  
3.  Użyj <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> metoda obiektu, który chcesz animować do zastosowania <xref:System.Windows.Media.Animation.AnimationClock> należy określić wartość właściwości.  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do dwóch podobnych właściwości.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Aby utworzyć drzewo czasu i używać go animowanie właściwości, zostaną wykonane następujące kroki.  
  
1.  Użyj <xref:System.Windows.Media.Animation.ParallelTimeline> i <xref:System.Windows.Media.Animation.AnimationTimeline> obiektów, aby utworzyć drzewo chronometrażu.  
  
2.  Użyj <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> głównego <xref:System.Windows.Media.Animation.ParallelTimeline> utworzyć <xref:System.Windows.Media.Animation.ClockGroup>.  
  
3.  Iteracyjne przeglądanie <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> z <xref:System.Windows.Media.Animation.ClockGroup> i stosuje się jego podrzędny <xref:System.Windows.Media.Animation.Clock> obiektów. Dla każdego <xref:System.Windows.Media.Animation.AnimationClock> podrzędnych, użyj <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> metoda obiektu, który chcesz animować do zastosowania <xref:System.Windows.Media.Animation.AnimationClock> należy określić wartość właściwości  
  
 Aby uzyskać więcej informacji o obiektach zegara, zobacz [Animacja i System chronometrażu w — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Dla ramek animacji: Pomijanie Animacja i System chronometrażu  
 Korzystając z tego podejścia, gdy trzeba całkowicie pominąć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system animacji. Jeden scenariusz, w tym podejściu jest fizyki animacje, gdzie każdy krok w animacji wymaga obiektów przeliczane w oparciu o ostatni zestaw interakcje obiektu.  
  
 Dla ramek animacji nie może być zdefiniowana wewnątrz style, szablony kontrolek i szablonów danych.  
  
 Aby animować klatka po klatce, zarejestrujesz <xref:System.Windows.Media.CompositionTarget.Rendering> zdarzenia obiektu, który zawiera obiekty mają być animowane. Ta metoda obsługi zdarzeń jest wywoływana raz na klatkę. Każdym razem, gdy program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals danych utrwalonych renderowania, w drzewie wizualnym w drzewie kompozycji, Twoja metoda programu obsługi zdarzeń jest wywoływana.  
  
 W obsługi zdarzenia należy wykonać niezależnie od obliczeń są niezbędne dla Twojego animacji i ustaw właściwości obiektów, których chcesz animować z tymi wartościami.  
  
 Uzyskać czasu prezentacji dla bieżącej ramki <xref:System.EventArgs> skojarzony z tym zdarzeń może być rzutowany jako <xref:System.Windows.Media.RenderingEventArgs>, które zapewniają <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> właściwość, która służy do uzyskania bieżącej ramki przez renderowanie czasu.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.CompositionTarget.Rendering> strony.  
  
## <a name="see-also"></a>Zobacz także
- [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Scenorysy — przegląd](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
- [Animacja i system chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)
- [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
