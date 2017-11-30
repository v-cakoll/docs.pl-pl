---
title: "Przegląd Techniki animacji właściwości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a8c196ea15617b13abe8311f8501ab32fd320c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="property-animation-techniques-overview"></a>Przegląd Techniki animacji właściwości
W tym temacie opisano różne podejścia do animowania właściwości: scenorys, lokalne animacje zegary i na ramki animacji.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z animacji podstawowe funkcje opisane w [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="summary"></a>   
## <a name="different-ways-to-animate"></a>Różne sposoby animować  
 Ponieważ istnieje wiele różnych scenariuszy do animowania właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia kilka metod do animowania właściwości.  
  
 Dla każdego z podejść Poniższa tabela wskazuje, czy można używać poszczególnych wystąpień, style, szablonów kontrolki lub szablonów danych; Czy można używać w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; i czy podejście pozwala interaktywnie sterować animacji.  "Dla wystąpienia" odwołuje się do technika zastosowania animacji lub scenorysu bezpośrednio do wystąpienia obiektu, a nie w stylu, szablon formantu lub w szablonie danych.  
  
|Technika animacji|Scenariusze|Obsługuje XAML|Interaktywnie sterowane|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Animacja scenorysu|Na wystąpienie <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>,<xref:System.Windows.DataTemplate>|Tak|Tak|  
|Animacja lokalnego|Na wystąpienia|Nie|Nie|  
|Animacja zegara|Na wystąpienia|Nie|Tak|  
|Animacja ramki|Na wystąpienia|Nie|Brak|  
  
<a name="storyboard_animations"></a>   
## <a name="storyboard-animations"></a>Animacje scenorysu  
 Użyj <xref:System.Windows.Media.Animation.Storyboard> umożliwia definiowanie i zastosowania animacji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], interakcyjnego kontrolować animację po start, tworzenie złożonych drzewa animacji lub animować w <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> lub <xref:System.Windows.DataTemplate>. Dla obiekt to animowanie przez <xref:System.Windows.Media.Animation.Storyboard>, musi być <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, lub należy ustawić <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Aby uzyskać więcej informacji, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 A <xref:System.Windows.Media.Animation.Storyboard> jest specjalnym rodzajem kontenera <xref:System.Windows.Media.Animation.Timeline> zawierające informacje określania wartości docelowej dla animacji zawiera. Aby animować z <xref:System.Windows.Media.Animation.Storyboard>, wykonaj następujące kroki trzy.  
  
1.  Deklarowanie <xref:System.Windows.Media.Animation.Storyboard> i co najmniej jeden animacji.  
  
2.  Użyj <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> dołączonych właściwości, aby określić obiekt docelowy i właściwości każdej animacji.  
  
3.  (Tylko kod) Zdefiniuj <xref:System.Windows.NameScope> dla <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Zarejestruj nazwy obiektów do animowania z tym <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>.  
  
4.  Rozpocznij <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Począwszy od <xref:System.Windows.Media.Animation.Storyboard> dotyczy one animowania właściwości animacji i można je uruchomić. Istnieją dwa sposoby rozpoczęcia <xref:System.Windows.Media.Animation.Storyboard>: można użyć <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody dostarczone przez <xref:System.Windows.Media.Animation.Storyboard> klasy lub użyć <xref:System.Windows.Media.Animation.BeginStoryboard> akcji. Jedynym sposobem, aby animować w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest użycie <xref:System.Windows.Media.Animation.BeginStoryboard> akcji. A <xref:System.Windows.Media.Animation.BeginStoryboard> akcji mogą być używane w <xref:System.Windows.EventTrigger>, właściwość <xref:System.Windows.Trigger>, lub <xref:System.Windows.DataTrigger>.  
  
 W poniższej tabeli przedstawiono różnych miejscach gdzie każdy <xref:System.Windows.Media.Animation.Storyboard> rozpocząć technika jest obsługiwany: poszczególnych wystąpień, style, szablon formantu i szablon danych.  
  
|Scenorysu rozpoczyna się przy użyciu...|Na wystąpienia|Styl|Szablon formantu|Szablon danych|Przykład|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>i<xref:System.Windows.EventTrigger>|Tak|Tak|Tak|Tak|[Animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>i właściwości<xref:System.Windows.Trigger>|Nie|Tak|Tak|Tak|[Wyzwalanie animacji, gdy wartość właściwości](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>a<xref:System.Windows.DataTrigger>|Nie|Tak|Tak|Tak|[Porady: wyzwalanie animacji po zmianie danych](http://msdn.microsoft.com/en-us/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>— Metoda|Tak|Nie|Nie|Nie|[Animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Animation.Storyboard> obiekty, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
## <a name="local-animations"></a>Animacje lokalnego  
 Lokalne animacje oferują wygodny do animowania właściwości zależności dowolnego <xref:System.Windows.Media.Animation.Animatable> obiektu. Użyj lokalnej animacji, gdy chcesz zastosować do właściwości pojedynczego animacji i nie trzeba interaktywnie sterować animacji po jego uruchomieniu. W odróżnieniu od <xref:System.Windows.Media.Animation.Storyboard> animacji, lokalne animacji można animować obiekt, który nie jest skojarzony z <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Nie masz również do definiowania <xref:System.Windows.NameScope> dla tego typu animacji.  
  
 Animacje lokalnego może być używana tylko w kodzie i nie może być zdefiniowana w style, szablonów kontrolki lub szablony danych. Lokalne animacji nie interaktywnie sterować po jej uruchomieniu.  
  
 Aby animować przy użyciu lokalnego animacji, wykonaj następujące kroki.  
  
1.  Utwórz <xref:System.Windows.Media.Animation.AnimationTimeline> obiektu.  
  
2.  Użyj <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody obiektu, który chcesz animować dotyczyć <xref:System.Windows.Media.Animation.AnimationTimeline> do właściwości, który określisz.  
  
 Poniższy przykład przedstawia sposób animować kolor tła i szerokość <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Animacje zegara  
 Użyj <xref:System.Windows.Media.MediaPlayer.Clock%2A> obiekty można animować bez użycia <xref:System.Windows.Media.Animation.Storyboard> i chcesz utworzyć drzewa chronometrażu złożonych lub interaktywnie kontroluje animacji po rozpoczęciu. Obiekty Clock można użyć do animowania właściwości zależności dowolnego <xref:System.Windows.Media.Animation.Animatable> obiektu.  
  
 Nie można użyć <xref:System.Windows.Media.Animation.Clock> obiekty bezpośrednio do animowania w stylach, kontroli szablony lub szablony danych. (System synchronizację faktycznie używać <xref:System.Windows.Media.Animation.Clock> obiektów do animowania w style, szablony kontroli oraz szablony danych, ale należy utworzyć te <xref:System.Windows.Media.Animation.Clock> obiektów z <xref:System.Windows.Media.Animation.Storyboard>. Aby uzyskać więcej informacji na temat relacji między <xref:System.Windows.Media.Animation.Storyboard> obiektów i <xref:System.Windows.Media.Animation.Clock> obiekty, zobacz [animacji i Przegląd systemu chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).)  
  
 Aby zastosować jedną <xref:System.Windows.Media.Animation.Clock> do właściwości, wykonaj następujące kroki.  
  
1.  Utwórz <xref:System.Windows.Media.Animation.AnimationTimeline> obiektu.  
  
2.  Użyj <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> metody <xref:System.Windows.Media.Animation.AnimationTimeline> do utworzenia <xref:System.Windows.Media.Animation.AnimationClock>.  
  
3.  Użyj <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> metody obiektu, który chcesz animować do zastosowania <xref:System.Windows.Media.Animation.AnimationClock> do określenia właściwości.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do dwóch podobnych właściwości.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Aby utworzyć drzewo chronometrażu i korzystać z niego animowanie właściwości, zostaną wykonane następujące kroki.  
  
1.  Użyj <xref:System.Windows.Media.Animation.ParallelTimeline> i <xref:System.Windows.Media.Animation.AnimationTimeline> obiektów, aby utworzyć drzewo chronometrażu.  
  
2.  Użyj <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> głównego <xref:System.Windows.Media.Animation.ParallelTimeline> do utworzenia <xref:System.Windows.Media.Animation.ClockGroup>.  
  
3.  Iterowanie za pomocą <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> z <xref:System.Windows.Media.Animation.ClockGroup> i zastosować podrzędnej <xref:System.Windows.Media.Animation.Clock> obiektów. Dla każdego <xref:System.Windows.Media.Animation.AnimationClock> elementy podrzędne, użyj <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> metody obiektu, który chcesz animować do zastosowania <xref:System.Windows.Media.Animation.AnimationClock> możesz określić właściwości  
  
 Aby uzyskać więcej informacji o obiektach zegara, zobacz [animacji i Przegląd systemu chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Na ramki animacji: Pomijanie animacji i chronometrażu systemu  
 Tej metody należy użyć, gdy należy całkowicie pominąć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu animacji. Jeden scenariusz takie podejście jest animacje fizycznych, gdzie każdy krok animacji wymaga obiektów można przeliczane w zależności od ostatniego zestawu interakcje obiektu.  
  
 Nie można zdefiniować na poklatkowych wewnątrz style, szablonów kontrolki lub szablony danych.  
  
 Aby animować przez klatka, zarejestrujesz <xref:System.Windows.Media.CompositionTarget.Rendering> zdarzeń obiektu, który zawiera obiekty mają być animowane. Ta metoda obsługi zdarzeń jest wywoływana raz na klatkę. Każdej aktualizacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals danych utrwalonych renderowania w drzewie wizualnym w drzewie kompozycji sieci metoda obsługi zdarzeń jest wywoływana.  
  
 W program obsługi zdarzeń wykonaj niezależnie od obliczenia są niezbędne dla Twojego animacji i ustaw właściwości obiektów, które mają być animowane z tymi wartościami.  
  
 Można uzyskać czasu prezentacji dla bieżącej ramki <xref:System.EventArgs> skojarzony z tym zdarzeń mogą być rzutowane jako <xref:System.Windows.Media.RenderingEventArgs>, które zapewniają <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> właściwości, które można użyć w celu uzyskania bieżącej ramki do renderowania czasu.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.CompositionTarget.Rendering> strony.  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Scenorys — omówienie](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Animacja i chronometrażu Przegląd systemu](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
