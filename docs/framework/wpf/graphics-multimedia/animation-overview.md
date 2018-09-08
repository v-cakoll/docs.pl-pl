---
title: Przegląd Animacja
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], animations
- animations [WPF], overview
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
ms.openlocfilehash: 7a783f687dd8c9c21f796f2a8da7e0471a1f0d2b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189478"
---
# <a name="animation-overview"></a>Przegląd Animacja
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia bogaty zestaw funkcji grafiki i układu, które umożliwiają tworzenie interfejsów użytkownika atrakcyjne i atrakcyjne dokumentów. Animacji można wprowadzać interfejsu użytkownika atrakcyjne, jeszcze bardziej spektakularnych i użyteczny. Po prostu animowanie koloru tła lub stosowanie animowany <xref:System.Windows.Media.Transform>, możesz utworzyć ekran znaczne przejścia lub podaj pomocny podpowiedzi wizualne.  
  
 W tym omówieniu przedstawiono wprowadzenie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Animacja i system chronometrażu. Koncentruje się ona na animację [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów przy użyciu scenorysów.  

<a name="introducinganimations"></a>   
## <a name="introducing-animations"></a>Wprowadzenie do animacji  
 Animacja jest wrażenie, który jest tworzony przez szybkie przewijanie szereg obrazów, każdy nieco inne w ciągu ostatnich. Mózg uświadamia sobie grupę obrazów jako pojedynczej zmiany sceny. W filmowa to wrażenie jest tworzona przy użyciu kamery, służące do rejestrowania wielu fotografii, lub ramek, co sekundę. Ramki są odtwarzane przez projektora, odbiorców widzi obraz przenoszenia.  
  
 Przypomina animacji na komputerze. Na przykład program, który sprawia, że Rysowanie prostokąta zanikanie poza widokiem mogą działać w następujący sposób.  
  
-   Program tworzy czasomierz.  
  
-   Program sprawdza timer w ustalonych odstępach czasu, aby zobaczyć, ile czasu upłynęło.  
  
-   Każdorazowo, program sprawdza, czy czasomierz, oblicza bieżącą wartość nieprzezroczystości prostokąta, w oparciu o czas, jaki upłynął.  
  
-   Program następnie aktualizuje prostokąt przy użyciu nowej wartości i ponownie rysuje go.  
  
 Przed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] deweloperzy musieli utworzyć i zarządzać ich własnych systemów czasu lub użyć niestandardowej biblioteki. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera system chronometrażu wydajne, która jest dostępna za pośrednictwem kodu zarządzanego i [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i które głęboko zintegrowana [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji można łatwo animacji, formantów i innych obiektów graficznych.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje całą pracę tle efektywnie ponownego narysowania ekranu oraz zarządzania nim system chronometrażu. Zapewnia klasy czasu, które pozwalają skupić się na temat skutków, który chcesz utworzyć, zamiast mechanika osiągnięcie tych skutków. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ułatwia również tworzenie własnych animacji, zapewniając animacji klas bazowych, z których może dziedziczyć z klas, tworzyć niestandardowe animacje. Te niestandardowe animacje skorzystać z wielu korzyści w zakresie wydajności klas standardowa animacji.  
  
<a name="thewpftimingsystem"></a>   
## <a name="wpf-property-animation-system"></a>System animacji właściwości WPF  
 Jeśli zrozumiesz kilka ważnych pojęć dotyczących system chronometrażu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji może być łatwiejsze w użyciu. Najważniejsze jest fakt, że w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], animowanie obiektów w wyniku zastosowania animacji do ich poszczególne właściwości. Na przykład, aby element framework, rozwoju, animujemy jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości. Aby stopniowe z widoku obiektu, animowanie jego <xref:System.Windows.UIElement.Opacity%2A> właściwości.  
  
 Dla właściwości, aby mieć możliwości animacji musi spełniać następujące wymagania trzy:  
  
-   Musi być właściwość zależności.  
  
-   Musi on należeć do klasy, która dziedziczy po elemencie <xref:System.Windows.DependencyObject> i implementuje <xref:System.Windows.Media.Animation.IAnimatable> interfejsu.  
  
-   Musi być typem zgodne animacji dostępne. (Jeśli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie zapewnia go, możesz utworzyć swój własny. Zobacz [Przegląd niestandardowe animacje](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md).)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wiele obiektów, które mają <xref:System.Windows.Media.Animation.IAnimatable> właściwości. Kontrolki, takie jak <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.TabControl>, a także <xref:System.Windows.Controls.Panel> i <xref:System.Windows.Shapes.Shape> obiekty dziedziczyć <xref:System.Windows.DependencyObject>. Większość jego właściwości są właściwości zależności.  
  
 Możesz użyć animacji niemal dowolnego miejsca, który zawiera style i szablony kontrolek. Animacje musi być wizualizacji można animować obiekty, które nie są częścią interfejsu użytkownika, jeśli spełniają kryteria, które są opisane w tej sekcji.  
  
<a name="storyboardwalkthrough"></a>   
## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Przykład: Wprowadź Fade elementu z widoku  
 W tym przykładzie pokazano, jak używać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji, aby animować wartość właściwości zależności. Używa ona <xref:System.Windows.Media.Animation.DoubleAnimation>, który jest typem animacji, która generuje <xref:System.Double> wartości, aby animować <xref:System.Windows.UIElement.Opacity%2A> właściwość <xref:System.Windows.Shapes.Rectangle>. W rezultacie <xref:System.Windows.Shapes.Rectangle> stopniowo zmienia się z widoku.  
  
 Pierwsza część przykład tworzy <xref:System.Windows.Shapes.Rectangle> elementu. Poniższe kroki pokazują, jak utworzyć animację i zastosować je do prostokąta <xref:System.Windows.UIElement.Opacity%2A> właściwości.
  
 Poniżej pokazano sposób tworzenia <xref:System.Windows.Shapes.Rectangle> element <xref:System.Windows.Controls.StackPanel> w XAML.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]  
  
 Poniżej pokazano sposób tworzenia <xref:System.Windows.Shapes.Rectangle> element <xref:System.Windows.Controls.StackPanel> w kodzie.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]  
  
<a name="opacity_animation_step1"></a>   
### <a name="part-1-create-a-doubleanimation"></a>Część 1: Tworzenie doubleanimation —  
 Jednym ze sposobów zapewnienia zanikanie i Wyświetl element jest animować jego <xref:System.Windows.UIElement.Opacity%2A> właściwości. Ponieważ <xref:System.Windows.UIElement.Opacity%2A> właściwość jest typu <xref:System.Double>, potrzebujesz animacji, który tworzy wartości double. Element <xref:System.Windows.Media.Animation.DoubleAnimation> jest jeden taki animacji. A <xref:System.Windows.Media.Animation.DoubleAnimation> tworzy przejście między dwiema wartościami double. Aby określić jego wartości początkowej, należy ustawić jego <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości. Aby określić wartość końcową, należy ustawić jego <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości.  
  
1.  Wartość `1.0` sprawia, że obiekt całkowicie nieprzezroczysty, a wartość `0.0` sprawia, że całkowicie niewidoczne. Przejście animacji z `1.0` do `0.0` ustawiasz jego <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości `1.0` i jego <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwość `0.0`. Poniżej pokazano sposób tworzenia <xref:System.Windows.Media.Animation.DoubleAnimation> w XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]  
  
     Poniżej pokazano sposób tworzenia <xref:System.Windows.Media.Animation.DoubleAnimation> w kodzie.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]  
  
2.  Następnie należy określić <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Animacji Określa, jak długo trwa przejście ze swojej wartości początkowej do jego wartości docelowej. Poniżej pokazano, jak ustawić <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na pięć sekund w XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]  
  
     Poniżej pokazano, jak ustawić <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na pięć sekund w kodzie.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]  
  
3.  Powyższy kod wykazało, że animacji, które przechodzi z `1.0` do `0.0`, co powoduje, że element docelowy do zastosowania blaknięcia z całkowicie nieprzezroczysty, aby całkowicie niewidoczne. Aby element zanikanie powrót do widoku po nieodpowiedniej, ustaw <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwości animacji `true`. Aby Animacja Powtórz tę procedurę na czas nieokreślony, ustaw jego <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Poniżej pokazano, jak ustawić <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> i <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości w XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]  
  
     Poniżej pokazano, jak ustawić <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> i <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości w kodzie.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]  
  
<a name="opacity_animation_step2"></a>   
### <a name="part-2-create-a-storyboard"></a>Część 2: Utwórz Scenorys  
 Aby zastosować animacje do obiektu, należy utworzyć <xref:System.Windows.Media.Animation.Storyboard> i użyj <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> dołączonych właściwości, aby określić obiekt i właściwości, aby animować.  
  
1.  Utwórz <xref:System.Windows.Media.Animation.Storyboard> i dodać animację jako jego podrzędny. Poniżej pokazano sposób tworzenia <xref:System.Windows.Media.Animation.Storyboard> w XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]    
  
     Aby utworzyć <xref:System.Windows.Media.Animation.Storyboard> w kodzie należy zadeklarować <xref:System.Windows.Media.Animation.Storyboard> zmiennej na poziomie klasy.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]  
  
     Następnie zainicjuj <xref:System.Windows.Media.Animation.Storyboard> i dodać animację jako jego podrzędny.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]  
  
2.  <xref:System.Windows.Media.Animation.Storyboard> Musi wiedzieć, gdzie do zastosowania animacji. Użyj <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> dołączonych właściwości w celu określenia obiektów, aby animować. Poniżej pokazano sposób ustawiania nazwę docelowej <xref:System.Windows.Media.Animation.DoubleAnimation> do `MyRectangle` w XAML.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]  
  
     Poniżej pokazano sposób ustawiania nazwę docelowej <xref:System.Windows.Media.Animation.DoubleAnimation> do `MyRectangle` w kodzie.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]  
  
3.  Użyj <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> dołączona właściwość, aby określić właściwości, aby animować. Poniżej pokazano, jak animacji jest skonfigurowany do obiektu docelowego <xref:System.Windows.UIElement.Opacity%2A> właściwość <xref:System.Windows.Shapes.Rectangle> w XAML.
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]  
  
     Poniżej pokazano, jak animacji jest skonfigurowany do obiektu docelowego <xref:System.Windows.UIElement.Opacity%2A> właściwość <xref:System.Windows.Shapes.Rectangle> w kodzie.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> składni i dodatkowe przykłady, zobacz [Przegląd Scenorysy](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="opacity_animation_step3"></a>   
### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Część 3 (XAML): Skojarz scenorysu z wyzwalaczem  
 Najprostszym sposobem zastosowania i Rozpocznij <xref:System.Windows.Media.Animation.Storyboard> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest użycie wyzwalacz zdarzenia. W tej sekcji pokazano, jak skojarzyć <xref:System.Windows.Media.Animation.Storyboard> wyzwalacza w XAML.  
  
1.  Utwórz <xref:System.Windows.Media.Animation.BeginStoryboard> obiektu i skojarz scenorysu z nią. A <xref:System.Windows.Media.Animation.BeginStoryboard> jest typem <xref:System.Windows.TriggerAction> , stosuje się i rozpoczyna <xref:System.Windows.Media.Animation.Storyboard>.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]  
  
2.  Tworzenie <xref:System.Windows.EventTrigger> i Dodaj <xref:System.Windows.Media.Animation.BeginStoryboard> do jego <xref:System.Windows.EventTrigger.Actions%2A> kolekcji. Ustaw <xref:System.Windows.EventTrigger.RoutedEvent%2A> właściwość <xref:System.Windows.EventTrigger> zdarzenie trasowane, które chcesz uruchomić <xref:System.Windows.Media.Animation.Storyboard>. (Aby uzyskać więcej informacji na temat zdarzenia trasowane, zobacz [Przegląd zdarzeń kierowane](../../../../docs/framework/wpf/advanced/routed-events-overview.md).)  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]  
  
3.  Dodaj <xref:System.Windows.EventTrigger> do <xref:System.Windows.FrameworkElement.Triggers%2A> kolekcji prostokąta.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]  
  
<a name="opacity_animation_step3code"></a>   
### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Część 3 (kod): Skojarz scenorysu, za pomocą programu obsługi zdarzeń  
 Najprostszym sposobem zastosowania i Rozpocznij <xref:System.Windows.Media.Animation.Storyboard> w kodzie jest użycie programu obsługi zdarzeń. W tej sekcji pokazano, jak skojarzyć <xref:System.Windows.Media.Animation.Storyboard> za pomocą programu obsługi zdarzeń w kodzie.  
  
1.  Zarejestruj się, aby <xref:System.Windows.FrameworkElement.Loaded> zdarzeń prostokąta.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]  
  
2.  Zadeklaruj procedury obsługi zdarzeń. W obsłudze zdarzeń użyj <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody do stosowania scenorysu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]  
  
### <a name="complete-example"></a>Kompletny przykład  
 Poniżej przedstawiono sposób tworzenia prostokąt, który stopniowo zmienia się z widoku w XAML.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]  
  
 Poniżej przedstawiono sposób tworzenia prostokąt, który stopniowo zmienia się z widoku w kodzie.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]  
  
<a name="animationtypes"></a>   
## <a name="animation-types"></a>Typy animacji  
 Animacje generować wartości właściwości, dlatego w różnych typach właściwości jest istnieją typy inną animację. Aby animować właściwości, która przyjmuje <xref:System.Double>, takich jak <xref:System.Windows.FrameworkElement.Width%2A> właściwości elementu, użyj animacji, która tworzy <xref:System.Double> wartości. Aby animować właściwości, która przyjmuje <xref:System.Windows.Point>, użyj animacji, która tworzy <xref:System.Windows.Point> wartości i tak dalej. Ze względu na liczbę różnych typach właściwości, istnieje kilka klas animacji w <xref:System.Windows.Media.Animation> przestrzeni nazw. Na szczęście oni zgodnie z ograniczeniami konwencji nazewnictwa, która ułatwia ich rozróżnienie:  
  
-   \<*Typ*> animacji  
  
     Znane jako "Od/do/przez" lub "podstawowa" animacji, te animować między wartości początkowa i docelowy lub dodając wartość przesunięcia do swojej wartości początkowej.  
  
    -   Aby określić wartość początkową, ustaw właściwość From animacji.  
  
    -   Aby określić wartość końcową, ustaw właściwość na animacji.  
  
    -   Aby określić wartość przesunięcia, ustaw właściwości przez animację.  
  
     W przykładach w tym omówieniu użyć tych animacji, ponieważ są one najprostsze w użyciu. Animacje od/do/przez są opisane szczegółowo w temacie animacje — Przegląd From/To/By.  
  
-   \<*Typ*> AnimationUsingKeyFrames  
  
     Klatek kluczowych animacji są bardziej wydajne niż animacji od/do/przez, ponieważ można określić dowolną liczbę wartości docelowych i nawet kontrolować metody ich interpolacji. Niektóre typy mogą być animowane tylko przy użyciu klatek kluczowych animacji. Klatek kluczowych animacji są szczegółowo opisane w [Przegląd Animacja kluczowych klatek](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
-   \<*Typ*> AnimationUsingPath  
  
     Animacje ścieżki umożliwiają być animowany wartości przy użyciu ścieżki geometrycznej.  
  
-   \<*Typ*> podstawy animacji  
  
     Abstrakcyjna klasa, która podczas implementowania, animuje \< *typu*> wartość. Ta klasa służy jako klasa bazowa dla \< *typu*> animacji i \< *typu*> AnimationUsingKeyFrames klasy. Masz do czynienia bezpośrednio z tych klas, tylko wtedy, gdy chcesz utworzyć własne niestandardowe animacje. W przeciwnym razie użyj \< *typu*> animacji lub ramki kluczowej\<*typu*> animacji.  
  
 W większości przypadków można użyć \< *typu*> animacji klasy takie jak <xref:System.Windows.Media.Animation.DoubleAnimation> i <xref:System.Windows.Media.Animation.ColorAnimation>.  
  
 W poniższej tabeli przedstawiono kilka typowych animacji i niektóre właściwości, z którymi są one używane.  
  
|Typ właściwości|Odpowiednie animacji basic (od/do/przez)|Odpowiadające animacji klatek kluczowych|Odpowiednie Animacja ścieżki|Przykład użycia|  
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Brak|Animowanie <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> lub <xref:System.Windows.Media.GradientStop>.|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animowanie <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.Button>.|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Animowanie <xref:System.Windows.Media.EllipseGeometry.Center%2A> pozycji <xref:System.Windows.Media.EllipseGeometry>.|  
|<xref:System.String>|Brak|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Brak|Animowanie <xref:System.Windows.Controls.TextBlock.Text%2A> z <xref:System.Windows.Controls.TextBlock> lub <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.Button>.|  
  
<a name="animationsaretimelines"></a>   
### <a name="animations-are-timelines"></a>Animacje są osi czasu  
 Wszystkie typy animacji dziedziczą z <xref:System.Windows.Media.Animation.Timeline> klasy; dlatego wszystkich animacji są specjalne rodzaje osi czasu. A <xref:System.Windows.Media.Animation.Timeline> definiuje odcinek czasu. Można określić *zachowania chronometrażu* osi czasu: jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, ile razy jest powtarzane, a także jak krótki czas w miarę dla niego.  
  
 Ponieważ animacji <xref:System.Windows.Media.Animation.Timeline>, reprezentuje również odcinek czasu. Animacja oblicza również wartości wyjściowe w miarę jednak jego określony segment czasu (lub <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). Animacja w miarę, lub "odgrywa" aktualizuje właściwość, która jest skojarzony.  
  
 Są trzy właściwości często używanych chronometrażu <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, i <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.  
  
#### <a name="the-duration-property"></a>Właściwość czasu trwania  
 Jak wspomniano wcześniej oś czasu reprezentuje segment czasu. Długość tego segmentu jest określona przez <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osi czasu, który zazwyczaj jest określone przy użyciu <xref:System.Windows.Duration.TimeSpan%2A> wartość. Gdy osi czasu osiągnie koniec jego czas trwania, ukończenia iteracji.  
  
 Używa animacji jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości w celu określenia jej bieżącą wartość. Jeśli nie określisz <xref:System.Windows.Media.Animation.Timeline.Duration%2A> wartość dla animacji, używa ona 1 sekundę, co jest ustawieniem domyślnym.  
  
 Poniższa składnia pokazuje uproszczoną wersję [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Składnia atrybutu <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości.  
  
*godziny* `:` *minut* `:` *sekund*
  
 W poniższej tabeli przedstawiono kilka <xref:System.Windows.Duration> ustawienia i wartości wynikowe.  
  
|Ustawienie|Wartość wynikowa|  
|-------------|---------------------|  
|0:0:5.5|5.5 w ciągu kilku sekund.|  
|0:30:5.5|30 minut i 5.5 sekund.|  
|1:30:5.5|1 godziny, 30 minut, a 5.5 sekund.|  
  
 Jednym ze sposobów, aby określić <xref:System.Windows.Duration> w kodzie jest użycie <xref:System.TimeSpan.FromSeconds%2A> metodę w celu utworzenia <xref:System.TimeSpan>, następnie zadeklarować nową <xref:System.Windows.Duration> struktury za pomocą tego <xref:System.TimeSpan>.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Duration> wartości i pełne [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] składnię, zobacz <xref:System.Windows.Duration> struktury.  
  
#### <a name="autoreverse"></a>AutoReverse  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Właściwość określa, czy oś czasu odtwarza z poprzednimi wersjami, po osiągnięciu końca jej <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Jeśli ustawisz tę właściwość animacji `true`, animacji odwraca po osiągnięciu końca jej <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, odtwarzanie z jego wartości końcowej do swojej wartości początkowej. Domyślnie ta właściwość jest `false`.  
  
#### <a name="repeatbehavior"></a>RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Właściwość określa, ile razy odtwarzania osi czasu. Domyślnie, osie czasu mają iteracji liczbę `1.0`, co oznacza, że jeden grają czasu i powtórz nie od.  
  
 Aby uzyskać więcej informacji na temat tych właściwości i inne osoby, zobacz [zachowania chronometrażu — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md).  
  
<a name="applyanimationstoproperty"></a>   
## <a name="applying-an-animation-to-a-property"></a>Stosowanie animacji do właściwości  
 Różnego rodzaju animacji i ich właściwości czasu można znaleźć w poprzednich sekcjach. W tej sekcji pokazano, jak zastosować animacje do właściwość, która ma być animowany. <xref:System.Windows.Media.Animation.Storyboard> obiekty zapewniają jednym ze sposobów, aby zastosować animacje do właściwości. A <xref:System.Windows.Media.Animation.Storyboard> jest *osi czasu w kontenerze* zawierające informacje określania wartości docelowej dla animacji zawiera.  
  
### <a name="targeting-objects-and-properties"></a>Obiektów docelowych i właściwości  
 <xref:System.Windows.Media.Animation.Storyboard> Klasa udostępnia <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> dołączonych właściwości. Przez ustawienie tych właściwości dla animacji, wskazujemy animacji co animować. Jednak przed animację można wskazać obiektu, obiekt zazwyczaj podaje się nazwę.  
  
 Przypisywanie nazwę <xref:System.Windows.FrameworkElement> różni się od nazwy do przypisywania <xref:System.Windows.Freezable> obiektu. Większość formantów i panele elementów framework; Większość obiektów czysto graficzny, takich jak pędzle, transformacji i geometrii, są jednak obiektów freezable. Jeśli nie masz pewności, czy typ jest <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.Freezable>, można znaleźć **hierarchii dziedziczenia** sekcję dotyczącą go dokumentację.  
  
-   Aby <xref:System.Windows.FrameworkElement> obiektu docelowego animacji, możesz nadać mu nazwę, ustawiając jego <xref:System.Windows.FrameworkElement.Name%2A> właściwości. W kodzie, musisz również użyć <xref:System.Windows.FrameworkElement.RegisterName%2A> metodę, aby zarejestrować nazwę elementu ze stroną, do której należy.  
  
-   Zapewnienie <xref:System.Windows.Freezable> obiektu docelowego animacji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], możesz użyć [x: Name — dyrektywa](../../../../docs/framework/xaml-services/x-name-directive.md) do przypisz mu nazwy. W kodzie, możesz po prostu użyj <xref:System.Windows.FrameworkElement.RegisterName%2A> metodę, aby zarejestrować obiekt ze stroną, do której należy.  
  
 W kolejnych sekcjach podać przykład nazewnictwa element [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kod. Aby uzyskać bardziej szczegółowe informacje dotyczące nazewnictwa i ustawianie elementów docelowych, zobacz [Przegląd Scenorysy](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### <a name="applying-and-starting-storyboards"></a>Stosowanie i uruchomienie scenorysów  
 Aby rozpocząć scenorysu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy skojarzyć go z <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> Jest obiektem, który opisuje jakie akcje do wykonania po wystąpieniu określonego zdarzenia. Jedną z tych akcji może być <xref:System.Windows.Media.Animation.BeginStoryboard> akcji, która służy do zainicjowania scenorysu. Wyzwalacze zdarzeń są podobne do programów obsługi zdarzeń, ponieważ umożliwiają one można określić, jak aplikacja reaguje na określonego zdarzenia. W przeciwieństwie do programów obsługi zdarzeń, wyzwalacze zdarzeń może być w pełni opisane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; nie inny kod jest wymagany.  
  
 Aby rozpocząć <xref:System.Windows.Media.Animation.Storyboard> w kodzie, można użyć <xref:System.Windows.EventTrigger> lub użyj <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody <xref:System.Windows.Media.Animation.Storyboard> klasy.  
  
<a name="controllingstoryboards"></a>   
## <a name="interactively-control-a-storyboard"></a>Interaktywnie kontrolować Scenorys  
 W poprzednim przykładzie pokazano, jak zacząć <xref:System.Windows.Media.Animation.Storyboard> po wystąpieniu zdarzenia. Można również interaktywnie kontrolować <xref:System.Windows.Media.Animation.Storyboard> po uruchomieniu: można wstrzymać, wznowić, zatrzymać, Rozwijaj go do jego okresu wypełnienia, wyszukiwanie i Usuń <xref:System.Windows.Media.Animation.Storyboard>. Aby uzyskać więcej informacji i obejrzeć przykład, który pokazuje, jak interaktywnie kontrolować <xref:System.Windows.Media.Animation.Storyboard>, zobacz [Przegląd Scenorysy](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="fillbehaviorsection"></a>   
## <a name="what-happens-after-an-animation-ends"></a>Co się stanie po zakończeniu animacji?  
 <xref:System.Windows.Media.Animation.FillBehavior> Właściwość określa zachowania osi czasu po jej zakończeniu. Domyślnie uruchamia osi czasu <xref:System.Windows.Media.Animation.ClockState.Filling> po jej zakończeniu. Animacji, który jest <xref:System.Windows.Media.Animation.ClockState.Filling> przechowuje wartość końcowych danych wyjściowych.  
  
 <xref:System.Windows.Media.Animation.DoubleAnimation> w poprzednim przykładzie nie zakończyć, ponieważ jego <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość jest ustawiona na <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Poniższy przykład animuje prostokąt przy użyciu podobnych animacji. Inaczej niż w poprzednim przykładzie <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> i <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwości tą animację pozostaną na wartości domyślne. W związku z tym animacji w miarę z 1 na 0 ponad pięć sekund, a następnie zatrzymuje.  
  
 [!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]  
  
 [!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
 [!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]  
  
 Ponieważ jej <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> nie został zmieniony z wartości domyślnej, która jest <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, animacji posiada ona wartość końcową, 0, po jego zakończeniu. W związku z tym <xref:System.Windows.UIElement.Opacity%2A> pozostaje prostokąt w lokalizacji 0 po animacji kończy. Jeśli ustawisz <xref:System.Windows.UIElement.Opacity%2A> prostokąta z inną wartością kodu wydaje się mieć żadnego efektu, ponieważ animacji, nadal ma wpływ na <xref:System.Windows.UIElement.Opacity%2A> właściwości.  
  
 Jednym ze sposobów odzyskania kontroli animowany właściwości w kodzie jest użycie <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metodę i określić wartość null w przypadku <xref:System.Windows.Media.Animation.AnimationTimeline> parametru. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [ustawić właściwość po Zanimowaniu jej za pomocą scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
 Należy zauważyć, że, mimo że ustawienie wartości właściwości, która ma <xref:System.Windows.Media.Animation.ClockState.Active> lub <xref:System.Windows.Media.Animation.ClockState.Filling> animacja wydaje się nie mają wpływu, zmień wartość właściwości. Aby uzyskać więcej informacji, zobacz [Animacja i System chronometrażu w — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="databindingAndAnimatingAnimationsSection"></a>   
## <a name="data-binding-and-animating-animations"></a>Powiązanie danych oraz animowanie animacji  
 Większość właściwości animacji mogą zawierać dane, powiązany lub animowany; na przykład można animować <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation>. Ze względu na sposób działa system chronometrażu, dane, które są powiązane lub animowany animacji nie zachowywać się podobnie jak inne dane powiązane lub animowany obiektów. Aby zrozumieć ich zachowania, pomaga to zrozumieć, co oznacza stosowanie animacji do właściwości.  
  
 Zobacz przykład w poprzedniej sekcji, jak pokazano, jak animować <xref:System.Windows.UIElement.Opacity%2A> prostokąta. Po załadowaniu prostokąt w poprzednim przykładzie, jego wyzwalacz zdarzenia stosuje <xref:System.Windows.Media.Animation.Storyboard>. System chronometrażu tworzy kopię <xref:System.Windows.Media.Animation.Storyboard> i animacji. Te kopie są zablokowane (wprowadzone w trybie tylko do odczytu) i <xref:System.Windows.Media.Animation.Clock> obiekty są tworzone z nich. Zegary wykonują rzeczywistą pracę z animowanie właściwości docelowych.  
  
 System chronometrażu tworzy zegar dla <xref:System.Windows.Media.Animation.DoubleAnimation> i stosuje je do obiektu i właściwości, który jest określony przez <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> z <xref:System.Windows.Media.Animation.DoubleAnimation>. W takim przypadku system chronometrażu stosuje zegar <xref:System.Windows.UIElement.Opacity%2A> właściwość obiektu, który nosi nazwę "MyRectangle."  
  
 Mimo że zegar jest tworzona dla <xref:System.Windows.Media.Animation.Storyboard>, zegar nie ma zastosowania do dowolne właściwości. Jej celem jest kontrolować jego podrzędnych zegara, zegara, który jest tworzony dla <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Dla animacji, aby uwzględnić zmiany w animacji lub powiązania danych należy ponownie wygenerować jego zegara. Zegary nie są generowane dla Ciebie automatycznie. Aby animacji odzwierciedlać zmiany, należy ponownie zastosować jego scenorysu za pomocą <xref:System.Windows.Media.Animation.BeginStoryboard> lub <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody. Korzystając z jednej z tych metod, ponowne uruchomienie animacji. W kodzie, można użyć <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metodę, aby przenieść scenorysu z powrotem do jego poprzedniej pozycji.  
  
 Na przykład dane powiązane animacji, zobacz [przykład animacji z krzywymi składanymi klucz](https://go.microsoft.com/fwlink/?LinkID=160011). Aby uzyskać więcej informacji na temat działania systemu Animacja i chronometraż zobacz [Animacja i System chronometrażu w — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="otherWaysToAnimateSection"></a>   
## <a name="other-ways-to-animate"></a>Inne sposoby, aby animować  
 W przykładach w tym omówieniu opisano animowanie za pomocą scenorysów. Korzystając z kodu, można animować w inny sposób. Aby uzyskać więcej informacji, zobacz [Przegląd techniki animacji właściwości](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_samples"></a>   
## <a name="animation-samples"></a>Przykłady animacji  
 Poniższe przykłady mogą pomóc rozpocząć dodawanie animacji do aplikacji.  
  
-   [Od, do i przez przykład wartości docelowej animacji](https://go.microsoft.com/fwlink/?LinkID=159988)  
  
     Demonstruje różne od/do/przez ustawienia.  
  
-   [Przykład zachowania chronometrażu animacji](https://go.microsoft.com/fwlink/?LinkID=159970)  
  
     Pokazuje różne sposoby kontrolowania zachowania chronometrażu animacji. W tym przykładzie również pokazuje jak danych powiązać wartości docelowej animacji.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Animacja i system chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)|W tym artykule opisano, jak system chronometrażu używa <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Clock> klasy, które pozwalają na tworzenie animacji.|  
|[Animacja — porady i wskazówki](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)|Wyświetla listę przydatnych porad dotyczących rozwiązywania problemów z animacjami, takich jak wydajność.|  
|[Niestandardowe animacje — przegląd](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)|Opisuje sposób rozszerzyć systemu animacji z klatkami kluczowymi, klasy animacji lub wywołań zwrotnych w poszczególnych klatkach.|  
|Przegląd Cechy animacji od/do/przez|W tym artykule opisano sposób tworzenia animacji, które przechodzi między dwiema wartościami.|  
|[Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)|W tym artykule opisano sposób tworzenia wielu wartości docelowej, w tym możliwość kontrolowania metodę interpolacji animacji.|  
|[Funkcje easingu](../../../../docs/framework/wpf/graphics-multimedia/easing-functions.md)|Wyjaśnia, jak mają dotyczyć wzory matematyczne animacji można pobrać realistyczne zachowania, na przykład odbijania.|  
|[Animacje ścieżki — przegląd](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)|Opisuje sposób przenoszenia lub obrócić obiekt na ścieżce złożone.|  
|[Techniki animacji właściwości — przegląd](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)|W tym artykule opisano animacje tej właściwości przy użyciu scenorysów, lokalne animacji, zegary i animacje w poszczególnych klatkach.|  
|[Scenorysy — przegląd](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)|Opisuje sposób używania scenorysy z wieloma osiami czasu tworzenia złożonych animacji.|  
|[Zachowania chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)|W tym artykule opisano <xref:System.Windows.Media.Animation.Timeline> typów i właściwości używane w animacji.|  
|[Zdarzenia chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)|Opis zdarzenia, które są dostępne na <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Clock> obiektów umożliwiającego wykonywanie kodu w punktach na osi czasu, takich jak rozpocząć, wstrzymać, wznowić, Pomiń lub zatrzymać.|  
|[Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)|Zawiera przykłady kodu za pomocą animacji i osi czasu w aplikacji.|  
|[Zegary — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/clocks-how-to-topics.md)|Zawiera przykłady kodu za pomocą <xref:System.Windows.Media.Animation.Clock> obiektu w aplikacji.|  
|[Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)|Zawiera przykłady kodu w aplikacji przy użyciu Animacja kluczowych klatek.|  
|[Animacja ścieżki — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)|Zawiera przykłady kodu w aplikacji przy użyciu animacje ścieżki.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Media.Animation.Timeline>  
  
 <xref:System.Windows.Media.Animation.Storyboard>  
  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
  
 <xref:System.Windows.Media.Animation.Clock>
