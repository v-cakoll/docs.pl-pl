---
title: "Przegląd Animacja"
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
helpviewer_keywords:
- Storyboards [WPF], animations
- animations [WPF], overview
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
caps.latest.revision: "73"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15eeb27d493cd1138b0d3d41b55a57228a226a11
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="animation-overview"></a>Przegląd Animacja
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia zaawansowany zestaw funkcji grafiki i układu, które umożliwiają tworzenie interfejsów użytkownika atrakcyjne i atrakcyjne dokumentów. Animacji można wprowadzać atrakcyjny interfejs jeszcze bardziej znaczny i można go użyć. Przez właśnie animacji kolor tła lub animowany <xref:System.Windows.Media.Transform>, można utworzyć przejścia znacznej ekranu lub podaj przydatne wizualnych.  
  
 Ten przegląd zawiera wprowadzenie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji i czasu systemu. Dotyczy on animacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów przy użyciu scenorys.  

<a name="introducinganimations"></a>   
## <a name="introducing-animations"></a>Wprowadzenie do animacji  
 Animacja jest iluzji jest tworzony przez szybkie przewijanie serie obrazów, każdy nieco inne niż ostatni. Inteligencji przewiduje grupy obrazów jako pojedynczy sceny zmiany. W filmu to wrażenie jest tworzona przy użyciu aparaty fotograficzne, służące do rejestrowania wielu fotografii lub ramki, każdej sekundy. Jeśli klatkach są odtwarzane przez projektora, odbiorców widzi ruchomy obraz.  
  
 Przypomina animacji na komputerze. Na przykład program, który powoduje Rysowanie zanikania prostokąt niewidocznymi może działać w następujący sposób.  
  
-   Program tworzy czasomierza.  
  
-   Program sprawdza czasomierza w ustalonych odstępach czasu, aby zobaczyć, jak dużo czasu.  
  
-   Zawsze program sprawdza czasomierz, oblicza bieżącą wartość nieprzezroczystości prostokąta, w oparciu o czas, jaki upłynął.  
  
-   Następnie program aktualizuje prostokąt z nową wartością i ponownie go rysuje.  
  
 Przed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] deweloperzy było tworzyć i zarządzać systemów chronometrażu lub Użyj specjalnych niestandardowych bibliotek. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obejmuje system chronometrażu wydajne, który jest uwidaczniany za pomocą kodu zarządzanego i [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i jest ściśle zintegrowana do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]animacji można łatwo Animuj formanty i innych obiektów graficznych.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje wszystkie wewnętrznych pracy zarządzania systemem chronometrażu i efektywnie ponownego narysowania ekranu. Zawiera klasy chronometrażu, które pozwalają skupić się na efekty, który chcesz utworzyć, zamiast mechanika osiągnięcie tych skutków. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ułatwia także do tworzenia własnych animacji w przypadku wystawianego animacji klas podstawowych, z których może dziedziczyć z klasy, aby wygenerować dostosowany animacji. Te niestandardowe animacje uzyskać wiele korzyści w zakresie wydajności klas standardowe animacji.  
  
<a name="thewpftimingsystem"></a>   
## <a name="wpf-property-animation-system"></a>System animacji właściwość WPF  
 Jeśli znasz kilka ważnych pojęć dotyczących systemu chronometrażu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji może być łatwiejsze do użycia. Najważniejsze jest fakt, że w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], animowanie obiektów stosując animacji do ich indywidualnych właściwości. Na przykład, aby element framework powiększania, animowania jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości. Aby obiekt stopniowe z widoku, animować jego <xref:System.Windows.UIElement.Opacity%2A> właściwości.  
  
 Dla właściwości mają możliwości animacji spełniają trzy następujące wymagania:  
  
-   Musi ona właściwości zależności.  
  
-   Musi należeć do klasy, która dziedziczy <xref:System.Windows.DependencyObject> i implementuje <xref:System.Windows.Media.Animation.IAnimatable> interfejsu.  
  
-   Musi istnieć typu zgodny animacji dostępne. (Jeśli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie ma jednego, Utwórz swój własny. Zobacz [omówienie animacji niestandardowej](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md).)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wiele obiektów, które mają <xref:System.Windows.Media.Animation.IAnimatable> właściwości. Formanty, takie jak <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.TabControl>, a także <xref:System.Windows.Controls.Panel> i <xref:System.Windows.Shapes.Shape> obiekty dziedziczyć <xref:System.Windows.DependencyObject>. Większość jego właściwości są właściwości zależności.  
  
 Możesz użyć animacji niemal dowolnego miejsca, w tym style i szablony formantu. Animacji musi być visual; obiekty, które nie są częścią interfejsu użytkownika, jeśli spełniają kryteria, które zostały opisane w tej sekcji można animować.  
  
<a name="storyboardwalkthrough"></a>   
## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Przykład: Wprowadź zanikania elementu i widoku  
 Ten przykład przedstawia sposób użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji do animowania wartość właściwości zależności. Używa <xref:System.Windows.Media.Animation.DoubleAnimation>, który jest typem animacji, które generuje <xref:System.Double> wartości, aby animować <xref:System.Windows.UIElement.Opacity%2A> właściwość <xref:System.Windows.Shapes.Rectangle>. W związku z tym <xref:System.Windows.Shapes.Rectangle> stopniowo i widoku.  
  
 Pierwsza część przykładzie tworzy <xref:System.Windows.Shapes.Rectangle> elementu. Wykonaj kroki pokazują, jak utworzyć animację i zastosować je na prostokąt <xref:System.Windows.UIElement.Opacity%2A> właściwości.
  
 Poniżej pokazano, jak utworzyć <xref:System.Windows.Shapes.Rectangle> element <xref:System.Windows.Controls.StackPanel> w języku XAML.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]  
  
 Poniżej pokazano, jak utworzyć <xref:System.Windows.Shapes.Rectangle> element <xref:System.Windows.Controls.StackPanel> w kodzie.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]  
  
<a name="opacity_animation_step1"></a>   
### <a name="part-1-create-a-doubleanimation"></a>Część 1: Tworzenie DoubleAnimation  
 Jednym ze sposobów do uczynienia elementu zanikania i widoku jest do animowania jego <xref:System.Windows.UIElement.Opacity%2A> właściwości. Ponieważ <xref:System.Windows.UIElement.Opacity%2A> właściwość jest typu <xref:System.Double>, potrzebujesz animacji tworzącego wartości double. A <xref:System.Windows.Media.Animation.DoubleAnimation> jest jeden taki animacji. A <xref:System.Windows.Media.Animation.DoubleAnimation> tworzy przejścia między dwiema wartościami dwa razy. Aby określić jego wartości początkowej, należy ustawić jej <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości. Aby określić wartość końcową, należy ustawić jej <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości.  
  
1.  Wartość `1.0` sprawia, że obiekt całkowicie nieprzezroczysta i wartość `0.0` ułatwia całkowicie niewidoczne. Aby animacji przejście ze `1.0` do `0.0` ustawisz jego <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości `1.0` i jego <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości `0.0`. Poniżej pokazano, jak utworzyć <xref:System.Windows.Media.Animation.DoubleAnimation> w języku XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]  
  
     Poniżej pokazano, jak utworzyć <xref:System.Windows.Media.Animation.DoubleAnimation> w kodzie.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]  
  
2.  Następnie należy określić <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Animacji Określa, jak długo trwa przechodzenie od swojej wartości początkowej do jego wartości docelowej. Poniżej pokazano, jak ustawić <xref:System.Windows.Media.Animation.Timeline.Duration%2A> do pięciu sekund w języku XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]  
  
     Poniżej pokazano, jak ustawić <xref:System.Windows.Media.Animation.Timeline.Duration%2A> do pięciu sekund w kodzie.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]  
  
3.  Poprzedni kod wykazały animację przejścia z `1.0` do `0.0`, co powoduje, że stopniowe z całkowicie nieprzezroczyste, aby całkowicie niewidoczne elementu docelowego. Aby element zanikania wrócić do widoku po nieodpowiedniej, ustaw <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwości animacji w `true`. Aby animacji powtarzania nieskończoność, ustaw jej <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Poniżej pokazano, jak ustawić <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> i <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości w języku XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]  
  
     Poniżej pokazano, jak ustawić <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> i <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości w kodzie.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]  
  
<a name="opacity_animation_step2"></a>   
### <a name="part-2-create-a-storyboard"></a>Część 2: Tworzenie scenorysu  
 Aby zastosować animacji do obiektu, należy utworzyć <xref:System.Windows.Media.Animation.Storyboard> i użyj <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> dołączonych właściwości, aby określić obiekt i właściwości animacji.  
  
1.  Utwórz <xref:System.Windows.Media.Animation.Storyboard> i Dodaj animacji jako podrzędnej. Poniżej pokazano, jak utworzyć <xref:System.Windows.Media.Animation.Storyboard> w języku XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]    
  
     Aby utworzyć <xref:System.Windows.Media.Animation.Storyboard> w kodzie, należy zadeklarować <xref:System.Windows.Media.Animation.Storyboard> zmiennej na poziomie klasy.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]  
  
     Następnie zainicjuj <xref:System.Windows.Media.Animation.Storyboard> i Dodaj animacji jako podrzędnej.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]  
  
2.  <xref:System.Windows.Media.Animation.Storyboard> Musi wiedzieć, gdzie zastosowania animacji. Użyj <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> dołączonych właściwości w celu określenia obiektu animacji. Poniżej pokazano, jak ustawić nazwę docelowej <xref:System.Windows.Media.Animation.DoubleAnimation> do `MyRectangle` w języku XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]  
  
     Poniżej pokazano, jak ustawić nazwę docelowej <xref:System.Windows.Media.Animation.DoubleAnimation> do `MyRectangle` w kodzie.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]  
  
3.  Użyj <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> dołączona właściwość, aby określić właściwości animacji. Poniżej pokazano, jak animacji jest skonfigurowany do docelowego <xref:System.Windows.UIElement.Opacity%2A> właściwość <xref:System.Windows.Shapes.Rectangle> w języku XAML.
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]  
  
     Poniżej pokazano, jak animacji jest skonfigurowany do docelowego <xref:System.Windows.UIElement.Opacity%2A> właściwość <xref:System.Windows.Shapes.Rectangle> w kodzie.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> składni oraz dodatkowe przykłady, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="opacity_animation_step3"></a>   
### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Część 3 (XAML): Kojarzenie scenorysu z wyzwalaczem  
 Najprostszym sposobem zastosowania i uruchomić <xref:System.Windows.Media.Animation.Storyboard> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest użycie wyzwalacz zdarzeń. W tej sekcji przedstawiono sposób skojarzenia <xref:System.Windows.Media.Animation.Storyboard> z wyzwalaczem w języku XAML.  
  
1.  Utwórz <xref:System.Windows.Media.Animation.BeginStoryboard> obiektu i skojarzyć z nią użytkownika scenorysu. A <xref:System.Windows.Media.Animation.BeginStoryboard> jest typem <xref:System.Windows.TriggerAction> który stosuje i uruchamia <xref:System.Windows.Media.Animation.Storyboard>.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]  
  
2.  Utwórz <xref:System.Windows.EventTrigger> i Dodaj <xref:System.Windows.Media.Animation.BeginStoryboard> do jego <xref:System.Windows.EventTrigger.Actions%2A> kolekcji. Ustaw <xref:System.Windows.EventTrigger.RoutedEvent%2A> właściwość <xref:System.Windows.EventTrigger> do kierowanego zdarzenia, który chcesz uruchomić <xref:System.Windows.Media.Animation.Storyboard>. (Aby uzyskać więcej informacji na temat kierowane zdarzenia, zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).)  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]  
  
3.  Dodaj <xref:System.Windows.EventTrigger> do <xref:System.Windows.FrameworkElement.Triggers%2A> kolekcji prostokąta.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]  
  
<a name="opacity_animation_step3code"></a>   
### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Część 3 (kod): Kojarzenie scenorysu z obsługi zdarzeń  
 Najprostszym sposobem zastosowania i uruchomić <xref:System.Windows.Media.Animation.Storyboard> w kodzie jest użycie programu obsługi zdarzeń. W tej sekcji przedstawiono sposób skojarzenia <xref:System.Windows.Media.Animation.Storyboard> z obsługi zdarzeń w kodzie.  
  
1.  Zarejestruj się w celu <xref:System.Windows.FrameworkElement.Loaded> zdarzeń prostokąta.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]  
  
2.  Zadeklaruj procedury obsługi zdarzeń. W obsłudze zdarzeń użyj <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> stosowaną scenorysu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]  
  
### <a name="complete-example"></a>Kompletny przykład  
 Poniżej przedstawiono sposób tworzenia prostokąt stopniowo i widoku w języku XAML.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]  
  
 Poniżej przedstawiono sposób tworzenia prostokąt stopniowo i widoku w kodzie.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]  
  
<a name="animationtypes"></a>   
## <a name="animation-types"></a>Typy animacji  
 Animacje generować wartości właściwości, dlatego w różnych typach właściwości istnieją typy innej animacji. Aby animować właściwości, która przyjmuje <xref:System.Double>, takich jak <xref:System.Windows.FrameworkElement.Width%2A> właściwości elementu, użyj animacji tworzącego <xref:System.Double> wartości. Aby animować właściwości, która przyjmuje <xref:System.Windows.Point>, użyj animacji tworzącego <xref:System.Windows.Point> wartości i tak dalej. Ze względu na liczbę różnych typach właściwości są szereg klas animacji <xref:System.Windows.Media.Animation> przestrzeni nazw. Na szczęście one postępuj zgodnie z ograniczeniami konwencji nazewnictwa, która ułatwia rozróżnianie między nimi:  
  
-   \<*Typ*> animacji  
  
     Znana jako "Z lub do/przez" lub "basic" animacji, te animować między wartości początkowa i docelowego lub przez dodanie przesunięcia wartości na wartość początkową.  
  
    -   Aby określić wartości początkowej, ustaw właściwość From animacji.  
  
    -   Aby określić wartości końcowej, ustaw właściwość do animacji.  
  
    -   Aby określić wartość przesunięcia, ustaw właściwość By animacji.  
  
     Przykłady w tym omówieniu użyć tych animacji, ponieważ są one najprostszym do użycia. FROM lub do/przez animacje są szczegółowo opisane w From/To/By omówienie animacji.  
  
-   \<*Typ*> AnimationUsingKeyFrames  
  
     Klatek kluczowych animacji są bardziej efektywne niż z lub do/przez animacji, ponieważ mogą określić dowolną liczbę wartości docelowej i nawet kontrolę nad ich metodę interpolacji. Niektóre typy może być tylko animowany klatek kluczowych animacji. Klatek kluczowych animacji są szczegółowo opisane w [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
-   \<*Typ*> AnimationUsingPath  
  
     Ścieżka animacje umożliwiają korzystanie geometrycznych ścieżki w celu uzyskania wartości animowany.  
  
-   \<*Typ*> podstawy animacji  
  
     Abstrakcyjna klasa, która podczas implementowania, animuje \< *typu*> wartość. Ta klasa służy jako klasa podstawowa dla \< *typu*> animacji i \< *typu*> AnimationUsingKeyFrames klasy. Należy uwzględniać bezpośrednio z tych klas, tylko wtedy, gdy chcesz utworzyć animacji niestandardowej. W przeciwnym razie użyj \< *typu*> animacji lub klatki kluczowej\<*typu*> animacji.  
  
 W większości przypadków należy użyć \< *typu*> animacji klas, takich jak <xref:System.Windows.Media.Animation.DoubleAnimation> i <xref:System.Windows.Media.Animation.ColorAnimation>.  
  
 W poniższej tabeli przedstawiono kilka typowych animacji i niektóre właściwości, które są używane.  
  
|Typ właściwości|Odpowiednie animacji basic (z lub do/przez)|Odpowiadającego klatek kluczowych animacji|Odpowiednie animacji ścieżki|Przykład użycia|  
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Brak|Animacja <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> lub <xref:System.Windows.Media.GradientStop>.|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animacja <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.Button>.|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Animacja <xref:System.Windows.Media.EllipseGeometry.Center%2A> pozycji <xref:System.Windows.Media.EllipseGeometry>.|  
|<xref:System.String>|Brak|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Brak|Animacja <xref:System.Windows.Controls.TextBlock.Text%2A> z <xref:System.Windows.Controls.TextBlock> lub <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.Button>.|  
  
<a name="animationsaretimelines"></a>   
### <a name="animations-are-timelines"></a>Animacje są osi czasu  
 Wszystkie typy animacji dziedziczyć <xref:System.Windows.Media.Animation.Timeline> klasy, w związku z tym wszystkie animacje są specjalne rodzaje osi czasu. A <xref:System.Windows.Media.Animation.Timeline> definiuje odcinka czasu. Można określić *zachowania chronometrażu* osi czasu: jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, ile razy jest powtarzane, a także czas szybkość postępu dla niego.  
  
 Ponieważ animacji jest <xref:System.Windows.Media.Animation.Timeline>, również reprezentuje segment czasu. Animacja również oblicza wartości dane wyjściowe jako jednak postępu jego określony segment czasu (lub <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). Animacja postępu lub "odgrywa" aktualizuje właściwości, która jest skojarzona z.  
  
 Są trzy właściwości często używanych chronometrażu <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, i <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.  
  
#### <a name="the-duration-property"></a>Wartość właściwości Duration  
 Jak wcześniej wspomniano osi czasu reprezentuje segment czasu. Długość danego segmentu jest określany przez <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na osi czasu jest zazwyczaj określana za pomocą <xref:System.Windows.Duration.TimeSpan%2A> wartości. Gdy osi czasu osiągnie koniec jego czas trwania, ukończenia iteracji.  
  
 Używa animacji jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości, aby określić bieżącą wartość. Jeśli nie określisz <xref:System.Windows.Media.Animation.Timeline.Duration%2A> wartość dla animacji używa 1 sekundę, która jest ustawiona domyślnie.  
  
 Następującą składnię uproszczonej wersji [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Składnia atrybutu <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości.  
  
*Liczba godzin korzystania z* `:` *minut* `:` *sekund*
  
 W poniższej tabeli przedstawiono kilka <xref:System.Windows.Duration> ustawienia i ich wartości wynikowej.  
  
|Ustawienie|Wynikowej wartości|  
|-------------|---------------------|  
|0:0:5.5|5.5 sekund.|  
|0:30:5.5|30 minut i 5.5 sekund.|  
|1:30:5.5|1 godzinę, 30 minut, a 5.5 sekund.|  
  
 Aby określić <xref:System.Windows.Duration> w kodzie jest użycie <xref:System.TimeSpan.FromSeconds%2A> metodę w celu utworzenia <xref:System.TimeSpan>, następnie zadeklarować nowe <xref:System.Windows.Duration> struktury, która <xref:System.TimeSpan>.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Duration> wartości i pełną [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] składni, zobacz <xref:System.Windows.Duration> struktury.  
  
#### <a name="autoreverse"></a>AutoReverse  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Właściwość określa, czy oś czasu odtwarza z poprzednimi wersjami po dotarciu serwerów do końca jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Jeśli ustawisz tę właściwość animacji `true`, animacji odwraca po dotarciu serwerów do końca jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, odtwarzania z jego wartości końcowej do swojej wartości początkowej. Domyślnie ta właściwość jest `false`.  
  
#### <a name="repeatbehavior"></a>RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Właściwość określa, ile razy odgrywa osi czasu. Domyślnie osiach czasu mają iteracji liczba `1.0`, co oznacza, że jeden odtwarzania czasu i nie powtarzaj wcale.  
  
 Aby uzyskać więcej informacji o tych właściwości i innych użytkowników, zobacz [omówienie zachowania chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md).  
  
<a name="applyanimationstoproperty"></a>   
## <a name="applying-an-animation-to-a-property"></a>Stosowanie animacji do właściwości  
 W poprzednich sekcjach opisano różne typy animacji i ich właściwości chronometrażu. W tej sekcji przedstawiono sposób zastosowania animacji dla właściwości, które mają być animowane. <xref:System.Windows.Media.Animation.Storyboard>obiekty Podaj jedną z metod do zastosowania animacji do właściwości. A <xref:System.Windows.Media.Animation.Storyboard> jest *osi czasu kontenera* zawierające informacje określania wartości docelowej dla animacji zawiera.  
  
### <a name="targeting-objects-and-properties"></a>Obiekty docelowe i właściwości  
 <xref:System.Windows.Media.Animation.Storyboard> Klasa udostępnia <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> dołączone właściwości. Przez ustawienie tych właściwości dla animacji, można sprawdzić animacji co animacji. Jednak przed animacji można wybrać obiektu, obiekt muszą zwykle mieć nazwę.  
  
 Przypisanie nazwy do <xref:System.Windows.FrameworkElement> różni się od nazwy do przypisywania <xref:System.Windows.Freezable> obiektu. Większość formantów i panele są elementami framework; Jednak większość czysto graficzne obiekty, takie jak pędzle, transformacji i mają geometrię, są obiektami obiektu freezable. Jeśli nie masz pewności, czy typ jest <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.Freezable>, zapoznaj się **hierarchii dziedziczenia** sekcji jego dokumentacji.  
  
-   Aby <xref:System.Windows.FrameworkElement> obiektu docelowego animacji można nadać mu nazwę, ustawiając jego <xref:System.Windows.FrameworkElement.Name%2A> właściwości. W kodzie, należy również użyć <xref:System.Windows.FrameworkElement.RegisterName%2A> metodę, aby zarejestrować nazwę elementu na stronie, do którego należy.  
  
-   Aby <xref:System.Windows.Freezable> obiekt docelowy animacji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], możesz użyć [x: Name — dyrektywa](../../../../docs/framework/xaml-services/x-name-directive.md) go przypisać nazwę. W kodzie, użycia <xref:System.Windows.FrameworkElement.RegisterName%2A> metodę, aby zarejestrować obiektu ze stroną, do którego on należy.  
  
 W kolejnych sekcjach przedstawiono przykładową nazwy elementu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kod. Aby uzyskać bardziej szczegółowe informacje na temat nazewnictwa i elementów docelowych, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### <a name="applying-and-starting-storyboards"></a>Stosowanie i uruchamianie Scenorys  
 Aby uruchomić scenorysu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy skojarzyć go z <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> Jest obiektem, który opisuje jakie kroki należy podjąć, gdy wystąpi określone zdarzenie. Może być jedną z tych akcji <xref:System.Windows.Media.Animation.BeginStoryboard> akcji, która służy do zainicjowania z scenorysu. Wyzwalacze zdarzeń są podobne do programów obsługi zdarzeń, ponieważ umożliwiają one Określ sposób odpowiadania przez aplikację do konkretnego zdarzenia. W odróżnieniu od programów obsługi zdarzeń, wyzwalacze zdarzeń może być szczegółowo opisane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; żadnego innego kodu jest wymagane.  
  
 Aby uruchomić <xref:System.Windows.Media.Animation.Storyboard> w kodzie, można użyć <xref:System.Windows.EventTrigger> lub użyj <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody <xref:System.Windows.Media.Animation.Storyboard> klasy.  
  
<a name="controllingstoryboards"></a>   
## <a name="interactively-control-a-storyboard"></a>Interaktywnie sterować scenorysu  
 W poprzednim przykładzie pokazano sposób uruchamiania <xref:System.Windows.Media.Animation.Storyboard> po wystąpieniu zdarzenia. Można również interaktywnie sterować <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu: można wstrzymać, wznowić, Zatrzymaj, jego dojściu do okresu, wyszukiwanie i Usuń <xref:System.Windows.Media.Animation.Storyboard>. Więcej informacji oraz przykład pokazujący sposób sterowania interaktywnego <xref:System.Windows.Media.Animation.Storyboard>, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="fillbehaviorsection"></a>   
## <a name="what-happens-after-an-animation-ends"></a>Co się stanie po zakończeniu animacji?  
 <xref:System.Windows.Media.Animation.FillBehavior> Właściwość określa zachowania osi czasu po jej zakończeniu. Domyślnie uruchamia osi czasu <xref:System.Windows.Media.Animation.ClockState.Filling> zakończenia. Animacja będący <xref:System.Windows.Media.Animation.ClockState.Filling> przechowuje wartość ostateczne dane wyjściowe.  
  
 <xref:System.Windows.Media.Animation.DoubleAnimation> w poprzednim przykładzie nie zakończyć, ponieważ jego <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość jest ustawiona na <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Poniższy przykład animuje prostokąt przy użyciu podobnych animacji. W przeciwieństwie do poprzedniego przykładu <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> i <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> pozostało właściwości animacji tej wartości domyślne. W związku z tym Animacja postępu z 1 na 0 ponad pięć sekund, a następnie zatrzymuje.  
  
 [!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]  
  
 [!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
 [!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]  
  
 Ponieważ jego <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> nie został zmieniony z jego wartość domyślna, czyli <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, animacji posiada ona końcowej, 0, po jej zakończeniu. W związku z tym <xref:System.Windows.UIElement.Opacity%2A> pozostaje prostokąt w lokalizacji 0 po animacji kończy się. Jeśli ustawisz <xref:System.Windows.UIElement.Opacity%2A> prostokąta z inną wartością kodu, wydaje się nie przyniosło żadnego skutku, ponieważ animacji, nadal ma wpływ na <xref:System.Windows.UIElement.Opacity%2A> właściwości.  
  
 Jednym ze sposobów odzyskania kontroli animowanej właściwości w kodzie jest użycie <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metodę i określić wartości null dla <xref:System.Windows.Media.Animation.AnimationTimeline> parametru. Aby uzyskać więcej informacji i przykład zobacz [Ustaw właściwości po animacji scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
 Należy zauważyć, że chociaż ustawiania wartości właściwości, która ma <xref:System.Windows.Media.Animation.ClockState.Active> lub <xref:System.Windows.Media.Animation.ClockState.Filling> animacja wydaje się nie mają żadnego skutku, zmień wartość właściwości. Aby uzyskać więcej informacji, zobacz [animacji i Przegląd systemu chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="databindingAndAnimatingAnimationsSection"></a>   
## <a name="data-binding-and-animating-animations"></a>Powiązanie danych i animowanie animacji  
 Większość właściwości animacji może być danych powiązany lub animowany; na przykład można animować <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation>. Ze względu na sposób działania systemu chronometrażu, dane, które powiązane lub animowany animacji nie zachowują się podobnie jak inne dane powiązany lub Animowanie obiektów. Aby zrozumieć ich zachowanie, pomaga zrozumieć, co oznacza do zastosowania animacji do właściwości.  
  
 Zobacz przykład w poprzedniej sekcji, która pokazano, jak animować <xref:System.Windows.UIElement.Opacity%2A> prostokąta. Po załadowaniu prostokąt w poprzednim przykładzie, jego wyzwalacza zdarzenia stosuje <xref:System.Windows.Media.Animation.Storyboard>. System chronometrażu tworzy kopię <xref:System.Windows.Media.Animation.Storyboard> i animacji. Te kopie są zablokowane (tylko do odczytu) i <xref:System.Windows.Media.Animation.Clock> obiekty są tworzone z nich. Zegary wykonują rzeczywistą pracę z animowania właściwości docelowej.  
  
 System chronometrażu tworzy zegara dla <xref:System.Windows.Media.Animation.DoubleAnimation> i stosuje je do obiektu i właściwości, która jest określona przez <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> z <xref:System.Windows.Media.Animation.DoubleAnimation>. W takim przypadku system chronometrażu zastosuje zegara, aby <xref:System.Windows.UIElement.Opacity%2A> właściwości obiektu o nazwie "MyRectangle."  
  
 Mimo że zegar jest również tworzone jako <xref:System.Windows.Media.Animation.Storyboard>, zegar nie ma zastosowania do żadnych właściwości. Jej celem jest kontrolowanie jego zegara podrzędnych zegara, dla którego utworzono <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Dla animacji uwzględnić zmiany w animacji lub powiązania danych należy ponownie wygenerować jego zegara. Zegary nie są automatycznie generowane automatycznie. Aby odzwierciedlały zmiany animacji, zastosuj ponownie jego scenorysu przy użyciu <xref:System.Windows.Media.Animation.BeginStoryboard> lub <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody. Użycie jednej z tych metod, uruchamia ponownie animacji. W kodzie, można użyć <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody, które mają zostać przesunięte scenorysu z powrotem do jego poprzedniej pozycji.  
  
 Na przykład dane powiązane animacji, zobacz [próbki animacji krzywej składanej klucza](http://go.microsoft.com/fwlink/?LinkID=160011). Aby uzyskać więcej informacji na temat działania systemu synchronizację, zobacz [animacji i Przegląd systemu chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="otherWaysToAnimateSection"></a>   
## <a name="other-ways-to-animate"></a>Inne sposoby animować  
 Przykłady w tym omówieniu przedstawiają sposób animować przy użyciu scenorys. Gdy używasz kodu można animować w inny sposób. Aby uzyskać więcej informacji, zobacz [— Przegląd właściwości animacji techniki](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_samples"></a>   
## <a name="animation-samples"></a>Animacja — przykłady  
 Poniższe przykłady może pomóc rozpocząć dodawanie animacji do aplikacji.  
  
-   [Z, aby i przykładowe wartości docelowej animacji](http://go.microsoft.com/fwlink/?LinkID=159988)  
  
     Przedstawia różne z lub do/przez ustawienia.  
  
-   [Przykład zachowania chronometrażu animacji](http://go.microsoft.com/fwlink/?LinkID=159970)  
  
     Przedstawia różne sposoby, można kontrolować zachowanie chronometrażu animacji. W tym przykładzie również przedstawia sposób danych powiązać wartości docelowej animacji.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Animacja i chronometrażu Przegląd systemu](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)|W tym artykule opisano, jak system chronometrażu używa <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Clock> klasy, które pozwalają tworzyć animacji.|  
|[Animacja porady i wskazówki](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)|Wyświetla listę przydatne porady dotyczące rozwiązywania problemów z animacji, takich jak wydajność.|  
|[Omówienie animacji niestandardowej](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)|Opisuje sposób rozszerzyć systemu animacji klatek kluczowych, klasy animacji lub wywołań zwrotnych na ramki.|  
|Przegląd Cechy animacji od/do/przez|Opisuje sposób tworzenia animacji, który przechodzi między dwiema wartościami.|  
|[Omówienie klucza poklatkowych](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)|Opisuje sposób tworzenia animacji z wielu wartości docelowych, w tym możliwość kontrolowania metodę interpolacji.|  
|[Funkcji sterowania tempem zmian](../../../../docs/framework/wpf/graphics-multimedia/easing-functions.md)|Wyjaśniono, jak dotyczą matematycznymi realistyczne zachowanie, takich jak odbijania animacji.|  
|[Omówienie animacje ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)|Opisuje sposób przenieść ani obrócić obiekt złożony ścieżce.|  
|[Omówienie techniki animacji właściwość](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)|Opisuje animacji właściwość przy użyciu scenorys, lokalne animacje zegary i na poklatkowych.|  
|[Scenorys — omówienie](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)|Informacje dotyczące używania scenorys z wielu osiach czasu tworzenia złożonych animacji.|  
|[Omówienie zachowania chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)|W tym artykule opisano <xref:System.Windows.Media.Animation.Timeline> typy i właściwości używane w animacji.|  
|[Przegląd zdarzeń chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)|Opisuje zdarzenia dostępne na <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Clock> obiekty do wykonywania kodu w punktach na osi czasu, takich jak rozpocząć, wstrzymać, wznowić, Pomiń lub zatrzymać.|  
|[Tematy porad](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)|Zawiera przykłady kodu dla przy użyciu animacji i osi czasu w aplikacji.|  
|[Zegary — tematy porad](../../../../docs/framework/wpf/graphics-multimedia/clocks-how-to-topics.md)|Zawiera przykłady kodu dla przy użyciu <xref:System.Windows.Media.Animation.Clock> obiektów w aplikacji.|  
|[Klucz ramki — tematy porad](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)|Zawiera przykłady kodu dla przy użyciu klucza poklatkowych w aplikacji.|  
|[Ścieżka animacji — tematy porad](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)|Zawiera przykłady kodu w aplikacji przy użyciu ścieżki animacji.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Media.Animation.Timeline>  
  
 <xref:System.Windows.Media.Animation.Storyboard>  
  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
  
 <xref:System.Windows.Media.Animation.Clock>
