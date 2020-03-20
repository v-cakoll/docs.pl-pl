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
ms.openlocfilehash: 0b4bf6d4963f32ad83f762fce73c805197ff9c9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181842"
---
# <a name="property-animation-techniques-overview"></a>Przegląd Techniki animacji właściwości
W tym temacie opisano różne podejścia do animowania właściwości: scenorysy, animacje lokalne, zegary i animacje na klatkę.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zapoznać się z podstawowymi funkcjami animacji opisanymi w [przeglądzie animacji](animation-overview.md).  
  
<a name="summary"></a>
## <a name="different-ways-to-animate"></a>Różne sposoby animowania  
 Ponieważ istnieje wiele różnych scenariuszy animacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości, zawiera kilka podejść do animowania właściwości.  
  
 Dla każdego podejścia w poniższej tabeli wskazuje, czy może być używany dla każdego wystąpienia, w stylach, w szablonach kontroli lub w szablonach danych; czy może być [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]stosowany w ; oraz czy podejście umożliwia interaktywne sterowanie animacją.  "Na wystąpienie" odnosi się do techniki stosowania animacji lub scenorysu bezpośrednio do wystąpień obiektu, a nie w stylu, szablonu formantu lub szablonu danych.  
  
|Technika animacji|Scenariusze|Obsługuje kod XAML|Interaktywnie sterowane|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Animacja scenorysu|Na <xref:System.Windows.Style>wystąpienie, <xref:System.Windows.Controls.ControlTemplate>,<xref:System.Windows.DataTemplate>|Tak|Tak|  
|Animacja lokalna|Na wystąpienie|Nie|Nie|  
|Animacja zegara|Na wystąpienie|Nie|Tak|  
|Animacja na klatkę|Na wystąpienie|Nie|Nie dotyczy|  
  
<a name="storyboard_animations"></a>
## <a name="storyboard-animations"></a>Animacje scenorysu  
 <xref:System.Windows.Media.Animation.Storyboard> Użyj, gdy chcesz zdefiniować i zastosować [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]animacje w programie , interaktywnie steruj animacjami po ich <xref:System.Windows.Style>uruchomieniu, utwórz złożone drzewo animacji lub animuj w programie , <xref:System.Windows.Controls.ControlTemplate> lub <xref:System.Windows.DataTemplate>. Aby obiekt był animowany <xref:System.Windows.Media.Animation.Storyboard>przez , <xref:System.Windows.FrameworkElement> musi <xref:System.Windows.FrameworkContentElement>być lub , lub <xref:System.Windows.FrameworkElement> musi <xref:System.Windows.FrameworkContentElement>być używany do ustawiania lub . Aby uzyskać więcej informacji, zobacz [Omówienie scenoki .](storyboards-overview.md)  
  
 A <xref:System.Windows.Media.Animation.Storyboard> jest specjalnym typem kontenera, <xref:System.Windows.Media.Animation.Timeline> który zawiera informacje o określaniunienie celu dla animacji, które zawiera. Aby animować <xref:System.Windows.Media.Animation.Storyboard>za pomocą programu , należy wykonać następujące trzy kroki.  
  
1. Deklaruj <xref:System.Windows.Media.Animation.Storyboard> jedną lub więcej animacji.  
  
2. Właściwości <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> dołączone służy do określania obiektu docelowego i właściwości każdej animacji.  
  
3. (Tylko kod) Zdefiniuj <xref:System.Windows.NameScope> fora <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Zarejestruj nazwy obiektów, aby animować z tym <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>.  
  
4. Rozpocznij plik <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Początek <xref:System.Windows.Media.Animation.Storyboard> stosuje animacje do właściwości, które animują i uruchamia je. Istnieją dwa sposoby <xref:System.Windows.Media.Animation.Storyboard>rozpoczęcia a : <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> można użyć <xref:System.Windows.Media.Animation.Storyboard> metody dostarczonej przez <xref:System.Windows.Media.Animation.BeginStoryboard> klasę lub można użyć akcji. Jedynym sposobem animowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w jest <xref:System.Windows.Media.Animation.BeginStoryboard> użycie akcji. Akcja <xref:System.Windows.Media.Animation.BeginStoryboard> może być używana <xref:System.Windows.EventTrigger>w <xref:System.Windows.Trigger>, <xref:System.Windows.DataTrigger>właściwości lub .  
  
 W poniższej tabeli przedstawiono różne miejsca, w których obsługiwana jest każda <xref:System.Windows.Media.Animation.Storyboard> technika rozpoczęcia: dla wystąpienia, stylu, szablonu formantu i szablonu danych.  
  
|Scenorysu jest rozpoczęty przy użyciu ...|Na wystąpienie|Styl|Szablon formantu|Szablon danych|Przykład|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>oraz<xref:System.Windows.EventTrigger>|Tak|Tak|Tak|Tak|[Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>i nieruchomości<xref:System.Windows.Trigger>|Nie|Tak|Tak|Tak|[Wyzwalanie animacji w przypadku zmiany wartości właściwości](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>oraz<xref:System.Windows.DataTrigger>|Nie|Tak|Tak|Tak|[Jak: Wyzwalanie animacji po zmianie danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|Metoda <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Tak|Nie|Nie|Nie|[Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Aby uzyskać <xref:System.Windows.Media.Animation.Storyboard> więcej informacji o obiektach, zobacz [Omówienie scenoki](storyboards-overview.md).  
  
## <a name="local-animations"></a>Animacje lokalne  
 Animacje lokalne zapewniają wygodny sposób animowania właściwości <xref:System.Windows.Media.Animation.Animatable> zależności dowolnego obiektu. Użyj animacji lokalnych, jeśli chcesz zastosować pojedynczą animację do właściwości i nie trzeba interaktywnie kontrolować animacji po jej uruchomieniu. W <xref:System.Windows.Media.Animation.Storyboard> przeciwieństwie do animacji animacja lokalna może animować <xref:System.Windows.FrameworkElement> obiekt, który nie jest skojarzony z a lub . <xref:System.Windows.FrameworkContentElement> Nie trzeba również definiować <xref:System.Windows.NameScope> dla tego typu animacji.  
  
 Animacje lokalne mogą być używane tylko w kodzie i nie mogą być definiowane w stylach, szablonach formantów ani szablonach danych. Po uruchomieniu animacji lokalnej nie można kontrolować interaktywnie.  
  
 Aby animować przy użyciu animacji lokalnej, wykonaj następujące kroki.  
  
1. Utwórz <xref:System.Windows.Media.Animation.AnimationTimeline> obiekt.  
  
2. Użyj <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody obiektu, który chcesz animować, <xref:System.Windows.Media.Animation.AnimationTimeline> aby zastosować go do określonej właściwości.  
  
 W poniższym przykładzie pokazano, jak animować szerokość i kolor tła <xref:System.Windows.Controls.Button>pliku .  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Animacje zegara  
 Obiekty <xref:System.Windows.Media.MediaPlayer.Clock%2A> należy używać, gdy chcesz <xref:System.Windows.Media.Animation.Storyboard> animować bez użycia a i chcesz utworzyć złożone drzewa chronometrażu lub interaktywnie kontrolować animacje po ich uruchomieniu. Za pomocą Clock obiektów do animowania właściwości <xref:System.Windows.Media.Animation.Animatable> zależności dowolnego obiektu.  
  
 Obiekty nie <xref:System.Windows.Media.Animation.Clock> mogą używać bezpośrednio do animowania stylów, szablonów formantów ani szablonów danych. (System animacji i chronometrażu faktycznie używa <xref:System.Windows.Media.Animation.Clock> obiektów do animowania w stylach, <xref:System.Windows.Media.Animation.Clock> szablonach formantów i szablonach danych, ale musi tworzyć te obiekty z pliku <xref:System.Windows.Media.Animation.Storyboard>. Aby uzyskać więcej informacji <xref:System.Windows.Media.Animation.Storyboard> na <xref:System.Windows.Media.Animation.Clock> temat relacji między obiektami i obiektami, zobacz [Omówienie systemu animacji i chronometrażu).](animation-and-timing-system-overview.md)  
  
 Aby zastosować <xref:System.Windows.Media.Animation.Clock> pojedynczy do właściwości, należy wykonać następujące kroki.  
  
1. Utwórz <xref:System.Windows.Media.Animation.AnimationTimeline> obiekt.  
  
2. Użyj <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> metody, <xref:System.Windows.Media.Animation.AnimationTimeline> aby utworzyć <xref:System.Windows.Media.Animation.AnimationClock>plik .  
  
3. Użyj <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> metody obiektu, który chcesz animować, <xref:System.Windows.Media.Animation.AnimationClock> aby zastosować go do określonej właściwości.  
  
 W poniższym <xref:System.Windows.Media.Animation.AnimationClock> przykładzie pokazano, jak utworzyć i zastosować go do dwóch podobnych właściwości.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Aby utworzyć drzewo chronometrażu i użyć go animować właściwości, należy wykonać następujące kroki.  
  
1. Użyj <xref:System.Windows.Media.Animation.ParallelTimeline> <xref:System.Windows.Media.Animation.AnimationTimeline> i obiektów, aby utworzyć drzewo chronometrażu.  
  
2. <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> Użyj katalogu głównego, <xref:System.Windows.Media.Animation.ParallelTimeline> aby utworzyć plik <xref:System.Windows.Media.Animation.ClockGroup>.  
  
3. Iterować przez <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> <xref:System.Windows.Media.Animation.ClockGroup> i zastosować jego <xref:System.Windows.Media.Animation.Clock> obiekty podrzędne. Dla <xref:System.Windows.Media.Animation.AnimationClock> każdego dziecka <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> użyj metody obiektu, który chcesz animować, aby zastosować <xref:System.Windows.Media.Animation.AnimationClock> do właściwości, którą określisz  
  
 Aby uzyskać więcej informacji na temat obiektów Clock, zobacz [Omówienie systemu animacji i chronometrażu](animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Animacja na klatkę: omiń system animacji i chronometrażu  
 Użyj tego podejścia, gdy trzeba [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] całkowicie pominąć system animacji. Jednym ze scenariuszy dla tego podejścia jest animacje fizyki, gdzie każdy krok w animacji wymaga obiektów do ponownego przeliczenia na podstawie ostatniego zestawu interakcji obiektu.  
  
 Animacji na klatkę nie można definiować wewnątrz stylów, szablonów formantów ani szablonów danych.  
  
 Aby animować klatka po klatce, <xref:System.Windows.Media.CompositionTarget.Rendering> należy zarejestrować zdarzenie obiektu zawierającego obiekty, które chcesz animować. Ta metoda obsługi zdarzeń zostanie wywołana raz na klatkę. Za każdym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] razem, gdy marshals utrwalone dane renderowania w drzewie wizualnym w poprzek drzewa kompozycji, metoda obsługi zdarzeń jest wywoływana.  
  
 W programie obsługi zdarzeń wykonaj wszelkie obliczenia są niezbędne dla efektu animacji i ustaw właściwości obiektów, które chcesz animować z tymi wartościami.  
  
 Aby uzyskać czas prezentacji dla bieżącej ramki, <xref:System.EventArgs> skojarzone <xref:System.Windows.Media.RenderingEventArgs>z tym <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> zdarzeniem można rzutować jako , które zapewniają właściwość, której można użyć do uzyskania bieżącego czasu renderowania ramki.  
  
 Aby uzyskać więcej <xref:System.Windows.Media.CompositionTarget.Rendering> informacji, zobacz stronę.  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja](animation-overview.md)
- [Przegląd Scenorysy](storyboards-overview.md)
- [Przegląd Animacja i system chronometrażu](animation-and-timing-system-overview.md)
- [Przegląd Właściwości zależności](../advanced/dependency-properties-overview.md)
