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
ms.openlocfilehash: 870fc1d1f02dca7d4488a27385fcfeaec8098ced
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039186"
---
# <a name="animation-overview"></a>Przegląd Animacja

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferuje zaawansowany zestaw funkcji graficznych i układów, które umożliwiają tworzenie atrakcyjnych interfejsów użytkownika i atrakcyjnych dokumentów. Animacja może zwiększyć atrakcyjny interfejs użytkownika, jeszcze bardziej spektakularnych i użyteczny. Po prostu animacją koloru tła lub zastosowaniem animowanych <xref:System.Windows.Media.Transform>można tworzyć znaczące przejścia ekranu lub udostępniać pomocne podpowiedzi wizualne.

To omówienie zawiera wprowadzenie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji i systemu chronometrażu. Koncentruje się na animacji obiektów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] za pomocą scenorysów.

<a name="introducinganimations"></a>

## <a name="introducing-animations"></a>Wprowadzenie do animacji

Animacja jest złudzeniem, który jest tworzony przez szybkie przechodzenie przez serię obrazów, z których każdy nieco się różni od ostatniego. Mózg postrzega grupę obrazów jako pojedynczą zmianę sceny. W folii to iluzja jest tworzona przy użyciu kamer, które nagrywają wiele fotografii lub klatek, w każdej sekundzie. Gdy klatki są odtwarzane przez rzutnik, odbiorcy widzą przenoszony obraz.

Animacja na komputerze jest podobna. Na przykład program, który sprawia, że rysowanie prostokąta zanika z widoku może funkcjonować w następujący sposób.

- Program tworzy czasomierz.

- Program sprawdza czasomierz w ustalonych odstępach czasu, aby sprawdzić, ile czasu upłynął.

- Za każdym razem, gdy program sprawdzi czasomierz, oblicza bieżącą wartość nieprzezroczystości dla prostokąta na podstawie czasu, jaki upłynął.

- Program zaktualizuje prostokąt przy użyciu nowej wartości i ponownie narysuje.

Przed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]deweloperzy systemu Microsoft Windows musieli utworzyć własne systemy chronometrażu i zarządzać nimi lub użyć specjalnych bibliotek niestandardowych. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obejmuje wydajny system czasu, który jest udostępniany za pomocą kodu zarządzanego i [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i jest głęboko zintegrowany z platformą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Animacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ułatwia animowanie kontrolek i innych obiektów graficznych.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje całą pracę w tle w celu zarządzania systemem chronometrażu i wydajnego rysowania ekranu. Zawiera klasy chronometrażu, które umożliwiają skoncentrowanie się na efektach, które chcesz utworzyć, zamiast Mechanics z nich. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ułatwia również tworzenie własnych animacji, uwidaczniając klasy bazowe animacji, z których klasy mogą dziedziczyć, aby generować niestandardowe animacje. Te niestandardowe animacje uzyskują wiele zalet wydajności standardowych klas animacji.

<a name="thewpftimingsystem"></a>

## <a name="wpf-property-animation-system"></a>System animacji właściwości WPF

W przypadku zrozumienia kilku ważnych koncepcji dotyczących systemu chronometrażu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacje mogą być łatwiejsze w użyciu. Najważniejsze jest to, że w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]animowanie obiektów przez zastosowanie animacji do poszczególnych właściwości. Na przykład, aby zwiększyć strukturę elementu struktury, można animować <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości. Aby zmienić obiekt z widoku, można animować jego właściwość <xref:System.Windows.UIElement.Opacity%2A>.

Aby Właściwość miała możliwości animacji, musi spełniać następujące trzy wymagania:

- Musi to być właściwość zależności.

- Musi należeć do klasy, która dziedziczy po <xref:System.Windows.DependencyObject> i implementuje interfejs <xref:System.Windows.Media.Animation.IAnimatable>.

- Musi być dostępny zgodny typ animacji. (Jeśli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie zapewnia takiego, możesz utworzyć własne. Zobacz [Omówienie niestandardowych animacji](custom-animations-overview.md).)

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wiele obiektów, które mają <xref:System.Windows.Media.Animation.IAnimatable> właściwości. Kontrolki, takie jak <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.TabControl>, a także <xref:System.Windows.Controls.Panel> i <xref:System.Windows.Shapes.Shape> obiektów dziedziczą z <xref:System.Windows.DependencyObject>. Większość ich właściwości to właściwości zależności.

Możesz używać animacji niemal wszędzie, które obejmują style i szablony kontrolek. Animacje nie muszą być wizualizacją; można animować obiekty, które nie są częścią interfejsu użytkownika, jeśli spełniają kryteria opisane w tej sekcji.

<a name="storyboardwalkthrough"></a>

## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Przykład: zwiększanie i wyewidencjonowywanie elementu

Ten przykład pokazuje, jak używać animacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do animowania wartości właściwości zależności. Używa <xref:System.Windows.Media.Animation.DoubleAnimation>, który jest typem animacji generującej <xref:System.Double> wartości, aby animować Właściwość <xref:System.Windows.UIElement.Opacity%2A> <xref:System.Windows.Shapes.Rectangle>. W efekcie <xref:System.Windows.Shapes.Rectangle> zanika i wychodzi z widoku.

Pierwsza część przykładu tworzy element <xref:System.Windows.Shapes.Rectangle>. Poniższe kroki pokazują, jak utworzyć animację i zastosować ją do właściwości <xref:System.Windows.UIElement.Opacity%2A> prostokąta.

Poniżej przedstawiono sposób tworzenia elementu <xref:System.Windows.Shapes.Rectangle> w <xref:System.Windows.Controls.StackPanel> w języku XAML.

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]

Poniżej przedstawiono sposób tworzenia elementu <xref:System.Windows.Shapes.Rectangle> w <xref:System.Windows.Controls.StackPanel> w kodzie.

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]

<a name="opacity_animation_step1"></a>

### <a name="part-1-create-a-doubleanimation"></a>Część 1. Tworzenie elementu DoubleAnimation

Jednym ze sposobów stopniowego zanikania elementu w widoku jest animowanie jego właściwości <xref:System.Windows.UIElement.Opacity%2A>. Ponieważ właściwość <xref:System.Windows.UIElement.Opacity%2A> jest typu <xref:System.Double>, potrzebna jest animacja, która generuje wartości podwójne. <xref:System.Windows.Media.Animation.DoubleAnimation> to taka animacja. <xref:System.Windows.Media.Animation.DoubleAnimation> tworzy przejście między dwoma wartościami podwójnej precyzji. Aby określić wartość początkową, należy ustawić jej Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>. Aby określić jej wartość końcową, należy ustawić jej Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.

1. Wartość przezroczystości `1.0` sprawia, że obiekt całkowicie nieprzezroczysty, a wartość nieprzezroczystości `0.0` powoduje, że jest ona całkowicie niewidoczna. Aby przejść animacji z `1.0` do `0.0` ustawisz jej Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> na `1.0` i jej Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> `0.0`. Poniżej przedstawiono sposób tworzenia <xref:System.Windows.Media.Animation.DoubleAnimation> w języku XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]

    Poniżej przedstawiono sposób tworzenia <xref:System.Windows.Media.Animation.DoubleAnimation> w kodzie.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]

2. Następnie należy określić <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animacji określa, jak długo ma przebiegać od wartości początkowej do wartości docelowej. Poniżej pokazano, jak ustawić <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na pięć sekund w języku XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]

    Poniżej pokazano, jak ustawić <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na pięć sekund w kodzie.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]

3. Poprzedni kod wykazał animację przechodzenia z `1.0` do `0.0`, co sprawia, że element docelowy zmienia się z całkowicie nieprzezroczyste na całkowicie niewidoczny. Aby element był stopniowo przewracany do widoku po jego wyznikaniu, ustaw właściwość <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> animacji na `true`. Aby animacja była powtarzana w nieskończoność, ustaw jej Właściwość <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> na <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Poniżej przedstawiono sposób ustawiania właściwości <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> i <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> w języku XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]

    Poniżej przedstawiono sposób ustawiania właściwości <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> i <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> w kodzie.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]

<a name="opacity_animation_step2"></a>

### <a name="part-2-create-a-storyboard"></a>Część 2. Tworzenie scenorysu

Aby zastosować animację do obiektu, należy utworzyć <xref:System.Windows.Media.Animation.Storyboard> i użyć właściwości dołączone <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty>, aby określić obiekt i właściwość do animacji.

1. Utwórz <xref:System.Windows.Media.Animation.Storyboard> i Dodaj animację jako jej element podrzędny. Poniżej przedstawiono sposób tworzenia <xref:System.Windows.Media.Animation.Storyboard> w języku XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]

    Aby utworzyć <xref:System.Windows.Media.Animation.Storyboard> w kodzie, zadeklaruj zmienną <xref:System.Windows.Media.Animation.Storyboard> na poziomie klasy.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]

    Następnie zainicjuj <xref:System.Windows.Media.Animation.Storyboard> i Dodaj animację jako jej element podrzędny.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]

2. <xref:System.Windows.Media.Animation.Storyboard> musi wiedzieć, gdzie zastosować animację. Użyj <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> dołączonej właściwości, aby określić obiekt do animacji. Poniżej pokazano, jak ustawić nazwę docelową <xref:System.Windows.Media.Animation.DoubleAnimation> `MyRectangle` w języku XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]

    Poniżej pokazano, jak ustawić nazwę docelową <xref:System.Windows.Media.Animation.DoubleAnimation>, aby `MyRectangle` w kodzie.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]

3. Użyj <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> dołączonej właściwości, aby określić właściwość do animacji. Poniżej przedstawiono sposób skonfigurowania animacji jako docelowej właściwości <xref:System.Windows.UIElement.Opacity%2A> <xref:System.Windows.Shapes.Rectangle> w języku XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]

    Poniżej przedstawiono sposób skonfigurowania animacji jako docelowej właściwości <xref:System.Windows.UIElement.Opacity%2A> <xref:System.Windows.Shapes.Rectangle> w kodzie.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]

Aby uzyskać więcej informacji na temat składni <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> i dodatkowe przykłady, zobacz [Omówienie scenorysów](storyboards-overview.md).

<a name="opacity_animation_step3"></a>

### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Część 3 (XAML): Kojarzenie scenorysu z wyzwalaczem

Najprostszym sposobem zastosowania i uruchomienia <xref:System.Windows.Media.Animation.Storyboard> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest użycie wyzwalacza zdarzeń. W tej sekcji pokazano, jak skojarzyć <xref:System.Windows.Media.Animation.Storyboard> z wyzwalaczem w języku XAML.

1. Utwórz obiekt <xref:System.Windows.Media.Animation.BeginStoryboard> i skojarz z nim scenorys. <xref:System.Windows.Media.Animation.BeginStoryboard> jest typem <xref:System.Windows.TriggerAction>, który ma zastosowanie i uruchamia <xref:System.Windows.Media.Animation.Storyboard>.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]

2. Utwórz <xref:System.Windows.EventTrigger> i Dodaj <xref:System.Windows.Media.Animation.BeginStoryboard> do swojej kolekcji <xref:System.Windows.EventTrigger.Actions%2A>. Ustaw właściwość <xref:System.Windows.EventTrigger.RoutedEvent%2A> <xref:System.Windows.EventTrigger> na zdarzenie kierowane, które ma zostać uruchomione <xref:System.Windows.Media.Animation.Storyboard>. (Aby uzyskać więcej informacji na temat zdarzeń kierowanych, zobacz [Omówienie zdarzeń kierowanych](../advanced/routed-events-overview.md)).

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]

3. Dodaj <xref:System.Windows.EventTrigger> do kolekcji <xref:System.Windows.FrameworkElement.Triggers%2A> prostokąta.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]

<a name="opacity_animation_step3code"></a>

### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Część 3 (kod): Kojarzenie scenorysu z programem obsługi zdarzeń

Najprostszym sposobem zastosowania i uruchomienia <xref:System.Windows.Media.Animation.Storyboard> w kodzie jest użycie programu obsługi zdarzeń. W tej sekcji przedstawiono sposób kojarzenia <xref:System.Windows.Media.Animation.Storyboard> z programem obsługi zdarzeń w kodzie.

1. Zarejestruj się dla zdarzenia <xref:System.Windows.FrameworkElement.Loaded> prostokąta.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]

2. Zadeklaruj procedurę obsługi zdarzeń. W programie obsługi zdarzeń Użyj metody <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>, aby zastosować scenorys.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]

### <a name="complete-example"></a>Kompletny przykład

Poniżej pokazano, jak utworzyć prostokąt, który zanika i wyświetlona w języku XAML.

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]

Poniżej pokazano, jak utworzyć prostokąt, który stopniowo rozjaśnia się i wyświetla w kodzie.

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]

<a name="animationtypes"></a>

## <a name="animation-types"></a>Typy animacji

Ponieważ animacje generują wartości właściwości, istnieją różne typy animacji dla różnych typów właściwości. Aby animować właściwość, która pobiera <xref:System.Double>, na przykład właściwość <xref:System.Windows.FrameworkElement.Width%2A> elementu, użyj animacji, która generuje wartości <xref:System.Double>. Aby animować właściwość, która pobiera <xref:System.Windows.Point>, użyj animacji, która generuje wartości <xref:System.Windows.Point> i tak dalej. Ze względu na liczbę różnych typów właściwości w przestrzeni nazw <xref:System.Windows.Media.Animation> istnieje kilka klas animacji. Na szczęście są one zgodne z ścisłą konwencją nazewnictwa, która ułatwia odróżnienie między nimi:

- *typ*\<> animacji

  Animacja między wartością początkową i docelową, nazywana animacją "od/do/przez" lub "podstawowa", powoduje, że są to animacje między wartościami początkowymi i docelowymi lub przez dodanie wartości przesunięcia do wartości początkowej.

  - Aby określić wartość początkową, należy ustawić właściwość from animacji.

  - Aby określić wartość końcową, ustaw właściwość na animacji.

  - Aby określić wartość przesunięcia, ustaw właściwość według animacji.

  Przykłady w tym omówieniu używają tych animacji, ponieważ są one najprostsze do użycia. Animacje z/do/według animacji są szczegółowo opisane w Omówienie animacji od/do/przez.

- *typ*\<> AnimationUsingKeyFrames

  Animacje klatek kluczowych są bardziej wydajne niż animacje między nimi, ponieważ można określić dowolną liczbę wartości docelowych, a także kontrolować metodę interpolacji. Niektóre typy można animować tylko przy użyciu animacji klatek kluczowych. Animacje klatek kluczowych są szczegółowo opisane w temacie [Omówienie animacji klatek](key-frame-animations-overview.md)kluczowych.

- *typ*\<> AnimationUsingPath

  Animacje ścieżki umożliwiają użycie ścieżki geometrycznej w celu wygenerowania animowanych wartości.

- *typ*\<> Podstawy animacji

  Klasa abstrakcyjna, która podczas jej implementowania Animuj > wartość *typu*\<. Ta klasa służy jako klasa bazowa dla *typu*\<> Animacja i *typ*\<> klasy AnimationUsingKeyFrames. Musisz poradzić sobie bezpośrednio z tymi klasami tylko wtedy, gdy chcesz utworzyć własne animacje niestandardowe. W przeciwnym razie użyj *typu*\<> Animacja lub klatka *kluczowa\<>* animacji.

W większości przypadków należy użyć \<*typu*> klas animacji, takich jak <xref:System.Windows.Media.Animation.DoubleAnimation> i <xref:System.Windows.Media.Animation.ColorAnimation>.

W poniższej tabeli przedstawiono kilka typowych typów animacji oraz niektóre właściwości, z których są używane.

|Typ właściwości|Odpowiadająca animacja podstawowa (od/do/z)|Animacja odpowiedniej ramki klucza|Animacja odpowiedniej ścieżki|Przykład użycia|
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Brak|Animuj <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> lub <xref:System.Windows.Media.GradientStop>.|
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animuj <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.Button>.|
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Animuj <xref:System.Windows.Media.EllipseGeometry.Center%2A> pozycję <xref:System.Windows.Media.EllipseGeometry>.|
|<xref:System.String>|Brak|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Brak|Animuj <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock> lub <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Button>.|

<a name="animationsaretimelines"></a>

### <a name="animations-are-timelines"></a>Animacje to osie czasu

Wszystkie typy animacji dziedziczą z klasy <xref:System.Windows.Media.Animation.Timeline>; w związku z tym wszystkie animacje są wyspecjalizowanymi typami osi czasu. <xref:System.Windows.Media.Animation.Timeline> definiuje segment czasu. Można określić *zachowanie chronometrażu* osi czasu: jej <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, ile razy jest powtarzany, a nawet szybkość szybkiego postępu dla niego.

Ponieważ animacja jest <xref:System.Windows.Media.Animation.Timeline>, reprezentuje również segment czasu. Animacja oblicza również wartości wyjściowe w miarę postępu przez określony segment czasu (lub <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). Gdy animacja postępuje lub "odtwarza", aktualizuje właściwość, z którą jest skojarzona.

Trzy często używane właściwości chronometrażu są <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>i <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.

#### <a name="the-duration-property"></a>Właściwość Duration

Jak wspomniano wcześniej, oś czasu reprezentuje segment czasu. Długość tego segmentu jest określana na podstawie <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osi czasu, która jest zwykle określona przy użyciu wartości <xref:System.Windows.Duration.TimeSpan%2A>. Gdy oś czasu osiągnie koniec jego czasu trwania, zakończył iterację.

Animacja używa swojej właściwości <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, aby określić jej bieżącą wartość. Jeśli nie określisz wartości <xref:System.Windows.Media.Animation.Timeline.Duration%2A> dla animacji, zostanie użyta 1 sekunda, która jest wartością domyślną.

Poniższa składnia przedstawia uproszczoną wersję składni [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] atrybutu właściwości <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.

*godz* . `:` *min* `:` *sekund*

W poniższej tabeli przedstawiono kilka ustawień <xref:System.Windows.Duration> i ich wartości wyniki.

|Ustawienie|Wartość wyników|
|-------------|---------------------|
|0:0:5.5|5,5 sekund.|
|0:30:5.5|30 minut i 5,5 sekund.|
|1:30:5.5|1 godzina, 30 minut i 5,5 sekund.|

Jednym ze sposobów określenia <xref:System.Windows.Duration> w kodzie jest użycie metody <xref:System.TimeSpan.FromSeconds%2A> w celu utworzenia <xref:System.TimeSpan>, a następnie zadeklarować nową strukturę <xref:System.Windows.Duration> przy użyciu tego <xref:System.TimeSpan>.

Aby uzyskać więcej informacji na temat wartości <xref:System.Windows.Duration> i kompletnej składni [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], zobacz strukturę <xref:System.Windows.Duration>.

#### <a name="autoreverse"></a>AutoReverse

Właściwość <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> określa, czy oś czasu jest odtwarzana wstecz po osiągnięciu końca jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Jeśli ustawisz tę właściwość animacji na `true`, animacja zostanie odwrócona po osiągnięciu jej końca <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, co spowoduje odtwarzanie od jej wartości końcowej z powrotem do jej wartości początkowej. Domyślnie ta właściwość jest `false`.

#### <a name="repeatbehavior"></a>RepeatBehavior

Właściwość <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> określa, ile razy jest odtwarzany oś czasu. Domyślnie osie czasu mają liczbę iteracji `1.0`, co oznacza, że są one odtwarzane jeden raz i nie powtarzają się w ogóle.

Aby uzyskać więcej informacji o tych właściwościach i innych, zobacz [Omówienie zachowań chronometrażu](timing-behaviors-overview.md).

<a name="applyanimationstoproperty"></a>

## <a name="applying-an-animation-to-a-property"></a>Stosowanie animacji do właściwości

W poprzednich sekcjach opisano różne typy animacji i ich właściwości chronometrażu. W tej sekcji pokazano, jak zastosować animację do właściwości, która ma zostać poddana animacji. obiekty <xref:System.Windows.Media.Animation.Storyboard> umożliwiają zastosowanie animacji do właściwości. <xref:System.Windows.Media.Animation.Storyboard> to *oś czasu kontenera* , która zawiera informacje dotyczące docelowej animacji, które zawiera.

### <a name="targeting-objects-and-properties"></a>Obiekty docelowe i właściwości

Klasa <xref:System.Windows.Media.Animation.Storyboard> udostępnia właściwości dołączone <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty>. Ustawiając te właściwości dla animacji, poinformujesz animację, co ma być animowane. Jednak zanim animacja będzie mogła wskazywać obiekt, obiekt musi być zwykle podaną nazwą.

Przypisanie nazwy do <xref:System.Windows.FrameworkElement> różni się od przypisywania nazwy do obiektu <xref:System.Windows.Freezable>. Większość formantów i paneli to elementy struktury; Jednak większość czystych obiektów graficznych, takich jak pędzle, przekształcenia i geometrie, to Freezable obiekty. Jeśli nie masz pewności, czy typem jest <xref:System.Windows.FrameworkElement> czy <xref:System.Windows.Freezable>, zapoznaj się z sekcją **Hierarchia dziedziczenia** dokumentacji referencyjnej.

- Aby utworzyć <xref:System.Windows.FrameworkElement> celu animacji, nadaj mu nazwę, ustawiając jej Właściwość <xref:System.Windows.FrameworkElement.Name%2A>. W kodzie, należy również użyć metody <xref:System.Windows.FrameworkElement.RegisterName%2A>, aby zarejestrować nazwę elementu ze stroną, do której należy.

- Aby nadać obiektowi <xref:System.Windows.Freezable> element docelowy animacji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy użyć [dyrektywy x:Name](../../xaml-services/x-name-directive.md) w celu przypisania jej nazwy. W kodzie, wystarczy użyć metody <xref:System.Windows.FrameworkElement.RegisterName%2A>, aby zarejestrować obiekt ze stroną, do której należy.

Poniższe sekcje zawierają przykład nazewnictwa elementu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kodzie. Aby uzyskać bardziej szczegółowe informacje o nazewnictwie i określaniu elementów docelowych, zobacz [Omówienie scenorysów](storyboards-overview.md).

### <a name="applying-and-starting-storyboards"></a>Stosowanie i uruchamianie scenorysów

Aby rozpocząć scenorys w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy skojarzyć go z <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> jest obiektem opisującym działania podejmowane po wystąpieniu określonego zdarzenia. Jedną z tych akcji może być akcja <xref:System.Windows.Media.Animation.BeginStoryboard>, która służy do uruchamiania scenorysu. Wyzwalacze zdarzeń są podobne do programów obsługi zdarzeń, ponieważ umożliwiają określenie, w jaki sposób aplikacja reaguje na określone zdarzenie. W przeciwieństwie do programów obsługi zdarzeń, wyzwalacze zdarzeń można w pełni opisać w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; żaden inny kod nie jest wymagany.

Aby uruchomić <xref:System.Windows.Media.Animation.Storyboard> w kodzie, można użyć <xref:System.Windows.EventTrigger> lub użyć metody <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> klasy <xref:System.Windows.Media.Animation.Storyboard>.

<a name="controllingstoryboards"></a>

## <a name="interactively-control-a-storyboard"></a>Interaktywna kontrola scenorysu

W poprzednim przykładzie pokazano, jak uruchomić <xref:System.Windows.Media.Animation.Storyboard> w przypadku wystąpienia zdarzenia. Możesz również interaktywnie kontrolować <xref:System.Windows.Media.Animation.Storyboard> po jej uruchomieniu: Możesz wstrzymywać, wznawiać, zatrzymywać, przełączać do jego okresu wypełniania, wyszukiwać i usuwać <xref:System.Windows.Media.Animation.Storyboard>. Aby uzyskać więcej informacji oraz przykład, który pokazuje, jak interaktywnie sterować <xref:System.Windows.Media.Animation.Storyboard>, zobacz [Omówienie scenorysów](storyboards-overview.md).

<a name="fillbehaviorsection"></a>

## <a name="what-happens-after-an-animation-ends"></a>Co się stanie po zakończeniu animacji?

Właściwość <xref:System.Windows.Media.Animation.FillBehavior> określa, jak działa oś czasu po zakończeniu. Domyślnie oś czasu zaczyna <xref:System.Windows.Media.Animation.ClockState.Filling> po zakończeniu. Animacja <xref:System.Windows.Media.Animation.ClockState.Filling> przechowuje końcową wartość wyjściową.

<xref:System.Windows.Media.Animation.DoubleAnimation> w poprzednim przykładzie nie kończy się, ponieważ jego właściwość <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> jest ustawiona na <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Poniższy przykład Animuj prostokąt przy użyciu podobnej animacji. W przeciwieństwie do poprzedniego przykładu właściwości <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> i <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> tej animacji są pozostawione z wartościami domyślnymi. W związku z tym animacja postępuje od 1 do 0 przez pięć sekund, a następnie zostaje zatrzymana.

[!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]

[!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
[!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]

Ponieważ jej <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> nie został zmieniony z wartości domyślnej, która jest <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, animacja utrzymuje końcową wartość 0, gdy zostanie zakończona. W związku z tym <xref:System.Windows.UIElement.Opacity%2A> prostokąt pozostanie 0 po zakończeniu animacji. Jeśli ustawisz <xref:System.Windows.UIElement.Opacity%2A> prostokąta na inną wartość, kod prawdopodobnie nie będzie miał żadnego efektu, ponieważ animacja nadal wpływa na Właściwość <xref:System.Windows.UIElement.Opacity%2A>.

Jednym ze sposobów na odzyskanie kontroli nad animowaną właściwością w kodzie jest użycie metody <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> i określenie wartości null dla parametru <xref:System.Windows.Media.Animation.AnimationTimeline>. Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [Ustawianie właściwości po animacji przy użyciu scenorysu](how-to-set-a-property-after-animating-it-with-a-storyboard.md).

Należy zauważyć, że mimo że ustawienie wartości właściwości, która ma <xref:System.Windows.Media.Animation.ClockState.Active> lub animacja <xref:System.Windows.Media.Animation.ClockState.Filling> wydaje się nieefektowa, wartość właściwości zostanie zmieniona. Aby uzyskać więcej informacji, zobacz [Omówienie animacji i systemu chronometrażu](animation-and-timing-system-overview.md).

<a name="databindingAndAnimatingAnimationsSection"></a>

## <a name="data-binding-and-animating-animations"></a>Powiązanie danych i animacje animacji

Większość właściwości animacji można powiązać lub animować dane; na przykład można animować <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości <xref:System.Windows.Media.Animation.DoubleAnimation>. Jednak ze względu na sposób działania systemu chronometrażu animacja związana z danymi lub animowane animacje nie zachowuje się jak inne powiązane z danymi lub obiekty animowane. Aby zrozumieć ich zachowanie, można zrozumieć, co to znaczy, aby zastosować animację do właściwości.

Zapoznaj się z przykładem w poprzedniej sekcji, w którym pokazano, jak animować <xref:System.Windows.UIElement.Opacity%2A> prostokąta. Gdy zostanie załadowany prostokąt w poprzednim przykładzie, jego wyzwalacz zdarzeń stosuje <xref:System.Windows.Media.Animation.Storyboard>. System chronometrażu tworzy kopię <xref:System.Windows.Media.Animation.Storyboard> i jej animację. Te kopie są zamrożone (tylko do odczytu) i obiekty <xref:System.Windows.Media.Animation.Clock> są tworzone z nich. Te zegary służą do poprawnego działania animowania właściwości.

System chronometrażu tworzy zegar dla <xref:System.Windows.Media.Animation.DoubleAnimation> i stosuje go do obiektu i właściwości, które są określone przez <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> <xref:System.Windows.Media.Animation.DoubleAnimation>. W takim przypadku system chronometrażu stosuje zegar do właściwości <xref:System.Windows.UIElement.Opacity%2A> obiektu o nazwie ".

Chociaż zegar jest tworzony również dla <xref:System.Windows.Media.Animation.Storyboard>, zegar nie jest stosowany do żadnych właściwości. Jego celem jest sterowanie zegarem podrzędnym, zegarem utworzonym dla <xref:System.Windows.Media.Animation.DoubleAnimation>.

Aby animacja odzwierciedlała powiązanie danych lub zmiany animacji, należy ponownie wygenerować zegar. Zegary nie są ponownie generowane automatycznie. Aby animacja odzwierciedlała zmiany, Zastosuj ponownie scenorys przy użyciu <xref:System.Windows.Media.Animation.BeginStoryboard> lub metody <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>. W przypadku korzystania z jednej z tych metod animacja jest uruchamiana ponownie. W kodzie można użyć metody <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>, aby przesunąć scenorys z powrotem do poprzedniej pozycji.

Aby zapoznać się z przykładem animacji powiązanej z danymi, zobacz [przykład animacji z kluczem krzywej łamanej](https://go.microsoft.com/fwlink/?LinkID=160011). Aby uzyskać więcej informacji o tym, jak działa animacja i system chronometrażu, zobacz [Omówienie animacji i systemu chronometrażu](animation-and-timing-system-overview.md).

<a name="otherWaysToAnimateSection"></a>

## <a name="other-ways-to-animate"></a>Inne sposoby animacji

Przykłady w tym omówieniu przedstawiają sposób animacji przy użyciu scenorysów. W przypadku korzystania z kodu można animować różne sposoby. Aby uzyskać więcej informacji, zobacz [Omówienie technik animacji właściwości](property-animation-techniques-overview.md).

<a name="animation_samples"></a>

## <a name="animation-samples"></a>Przykłady animacji

Poniższe przykłady ułatwiają rozpoczęcie dodawania animacji do aplikacji.

- [Przykładowe wartości docelowe od, do i według animacji](https://go.microsoft.com/fwlink/?LinkID=159988)

  Pokazuje różne ustawienia od/do/z.

- [Przykład zachowania chronometrażu animacji](https://go.microsoft.com/fwlink/?LinkID=159970)

  Pokazuje różne sposoby sterowania zachowaniem chronometrażu animacji. Ten przykład pokazuje również, jak dane powiązać wartość docelową animacji.

<a name="related_topics"></a>

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Animacja i system chronometrażu — przegląd](animation-and-timing-system-overview.md)|Opisuje, w jaki sposób system chronometrażu używa klas <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Clock>, co pozwala na tworzenie animacji.|
|[Animacja — porady i wskazówki](animation-tips-and-tricks.md)|Wyświetla listę przydatnych porad dotyczących rozwiązywania problemów z animacjami, takich jak wydajność.|
|[Niestandardowe animacje — przegląd](custom-animations-overview.md)|Opisuje sposób rozbudowania systemu animacji z klatkami kluczowymi, klasami animacji lub wywołaniami zwrotnymi na klatkę.|
|[Animacje od/do/przez — przegląd](from-to-by-animations-overview.md)|Opisuje sposób tworzenia animacji, która przechodzi między dwiema wartościami.|
|[Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)|Opisuje sposób tworzenia animacji z wieloma wartościami docelowymi, w tym możliwość kontrolowania metody interpolacji.|
|[Funkcje easingu](easing-functions.md)|Wyjaśnia, jak zastosować formuły matematyczne do animacji w celu uzyskania realistycznych zachowań, takich jak odbijanie.|
|[Animacje ścieżki — przegląd](path-animations-overview.md)|Opisuje sposób przenoszenia lub obracania obiektu w ścieżce złożonej.|
|[Techniki animacji właściwości — przegląd](property-animation-techniques-overview.md)|Opisuje animacje właściwości przy użyciu scenorysów, animacji lokalnych, zegarów i animacji na klatkę.|
|[Scenorysy — przegląd](storyboards-overview.md)|Opisuje sposób używania scenorysów z wieloma osiami czasu do tworzenia złożonych animacji.|
|[Zachowania chronometrażu — przegląd](timing-behaviors-overview.md)|Opisuje typy <xref:System.Windows.Media.Animation.Timeline> i właściwości używane w animacjach.|
|[Zdarzenia chronometrażu — przegląd](timing-events-overview.md)|Opisuje zdarzenia dostępne dla <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Clock> obiektów do wykonywania kodu w punktach na osi czasu, takich jak BEGIN, Pause, Resume, Skip lub Stop.|
|[Tematy z instrukcjami](animation-and-timing-how-to-topics.md)|Zawiera przykłady kodu służące do używania animacji i osi czasu w aplikacji.|
|[Zegary — tematy z instrukcjami](clocks-how-to-topics.md)|Zawiera przykłady kodu służące do używania obiektu <xref:System.Windows.Media.Animation.Clock> w aplikacji.|
|[Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)|Zawiera przykłady kodu służące do używania animacji klatek kluczowych w aplikacji.|
|[Animacja ścieżki — tematy z instrukcjami](path-animation-how-to-topics.md)|Zawiera przykłady kodu służące do używania animacji Path w aplikacji.|

<a name="reference"></a>

## <a name="reference"></a>Informacje ogólne

- <xref:System.Windows.Media.Animation.Timeline>

- <xref:System.Windows.Media.Animation.Storyboard>

- <xref:System.Windows.Media.Animation.BeginStoryboard>

- <xref:System.Windows.Media.Animation.Clock>
