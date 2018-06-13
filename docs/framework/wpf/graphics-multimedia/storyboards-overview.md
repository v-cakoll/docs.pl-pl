---
title: Przegląd Scenorysy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 36922dce795443a4c1136f6442eff1c297f3c641
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566902"
---
# <a name="storyboards-overview"></a>Przegląd Scenorysy
W tym temacie przedstawiono sposób użycia <xref:System.Windows.Media.Animation.Storyboard> obiekty do organizowania i zastosowania animacji. Opis interaktywnie manipulowania <xref:System.Windows.Media.Animation.Storyboard> obiektów oraz opis właściwości pośrednie przeznaczonych dla składni.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy zapoznać się z animacji różnych typów i ich funkcje podstawowe. Wprowadzenie do animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Należy również wiedzieć, jak używać dołączone właściwości. Aby uzyskać więcej informacji na temat dołączone właściwości, zobacz [dołączony Przegląd właściwości](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>Co to jest scenorysu?  
 Animacji nie są przydatne tylko typ osi czasu. Innych klas osi czasu są dostarczane, aby ułatwić organizowanie zestawy osi czasu i zastosować do właściwości osi czasu. Kontener osiach czasu pochodzi od <xref:System.Windows.Media.Animation.TimelineGroup> klasy, a obejmują <xref:System.Windows.Media.Animation.ParallelTimeline> i <xref:System.Windows.Media.Animation.Storyboard>.  
  
 A <xref:System.Windows.Media.Animation.Storyboard> jest typem oś czasu kontenera, która zawiera informacje o docelowych dla osi czasu, zawiera. Scenorysu może zawierać dowolne typy <xref:System.Windows.Media.Animation.Timeline>, oraz inne osiach czasu kontenera animacji. <xref:System.Windows.Media.Animation.Storyboard> obiekty umożliwiają łączenie osi czasu, które mają wpływ na wiele obiektów i właściwości w drzewie jedną oś czasu, co ułatwia organizowanie i kontrolowania zachowania złożonych chronometrażu. Na przykład załóżmy, że ma przycisku, który wykonuje te trzy elementy.  
  
-   Wzrostu i rozwoju kolor, gdy użytkownik wybierze przycisk.  
  
-   Zmniejszanie optymalizacji i następnie rozwój przywracając jego oryginalny rozmiar po kliknięciu.  
  
-   Zmniejszanie i stopniowe do nieprzezroczystość 50 procent, gdy zostanie ona wyłączona.  
  
 W tym przypadku masz wiele zestawów animacji, które dotyczą tego samego obiektu, a ma być odtwarzany w różnym czasie, zależny od stanu przycisku. <xref:System.Windows.Media.Animation.Storyboard> obiekty umożliwiają organizowanie animacji i zastosować je w grupach co najmniej jeden obiekt.  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>Gdzie można użyć scenorysu?  
 A <xref:System.Windows.Media.Animation.Storyboard> może służyć do animowania właściwości zależności można animować klas (Aby uzyskać więcej informacji na temat co sprawia, że klasa można animować, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)). Jednak ponieważ storyboarding jest funkcją poziomie struktury, obiekt musi należeć do <xref:System.Windows.NameScope> z <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>.  
  
 Na przykład można użyć <xref:System.Windows.Media.Animation.Storyboard> wykonać następujące czynności:  
  
-   Animacja <xref:System.Windows.Media.SolidColorBrush> (inne niż framework element), który rysują tło przycisku (typu <xref:System.Windows.FrameworkElement>),  
  
-   Animacja <xref:System.Windows.Media.SolidColorBrush> (inne niż framework element), który rysują wypełnienia <xref:System.Windows.Media.GeometryDrawing> (inne niż framework element) wyświetlane przy użyciu <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).  
  
-   W kodzie, animować <xref:System.Windows.Media.SolidColorBrush> zadeklarowane przez klasę, która zawiera także <xref:System.Windows.FrameworkElement>, jeśli <xref:System.Windows.Media.SolidColorBrush> zarejestrowane z tym jego nazwa <xref:System.Windows.FrameworkElement>.  
  
 Jednak nie można użyć <xref:System.Windows.Media.Animation.Storyboard> do animowania <xref:System.Windows.Media.SolidColorBrush> który nie może zarejestrować swojej nazwy z <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, lub nie został użyty do ustawić właściwość <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>.  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>Jak stosować animacje scenorysu  
 Aby użyć <xref:System.Windows.Media.Animation.Storyboard> do organizowania i zastosowania animacji, Dodaj animacji jako osiach czasu podrzędnego z <xref:System.Windows.Media.Animation.Storyboard>. <xref:System.Windows.Media.Animation.Storyboard> Klasa udostępnia <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> dołączone właściwości. Animacji, aby określić jego obiekt docelowy i właściwości ustawiania tych właściwości.  
  
 Aby zastosować animacje ich celów, Rozpocznij <xref:System.Windows.Media.Animation.Storyboard> przy użyciu akcji wyzwalacza lub metody. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], możesz użyć <xref:System.Windows.Media.Animation.BeginStoryboard> obiekt z <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>, lub <xref:System.Windows.DataTrigger>. W kodzie, można również użyć <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody.  
  
 W poniższej tabeli przedstawiono różnych miejscach gdzie każdy <xref:System.Windows.Media.Animation.Storyboard> rozpocząć technika jest obsługiwany: poszczególnych wystąpień, style, szablon formantu i szablon danych. "Dla wystąpienia" odwołuje się do technika zastosowania animacji lub scenorysu bezpośrednio do wystąpienia obiektu, a nie w stylu, szablon formantu lub w szablonie danych.  
  
|Scenorysu rozpoczyna się przy użyciu...|Na wystąpienia|Styl|Szablon formantu|Szablon danych|Przykład|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> i <xref:System.Windows.EventTrigger>|Tak|Tak|Tak|Tak|[Animowanie właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> i właściwości <xref:System.Windows.Trigger>|Nie|Tak|Tak|Tak|[Wyzwalanie animacji w przypadku zmiany wartości właściwości](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.DataTrigger>|Nie|Tak|Tak|Tak|[Porady: wyzwalanie animacji po zmianie danych](http://msdn.microsoft.com/library/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> — Metoda|Tak|Nie|Nie|Nie|[Animowanie właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Storyboard> do animowania <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> elementu i <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> używany do rysowania, który <xref:System.Windows.Shapes.Rectangle>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 W poniższych sekcjach opisano <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> dołączone właściwości bardziej szczegółowo.  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Docelowe elementy Framework, elementy zawartości Framework i obiektów Freezable  
 Poprzedniej sekcji wspomniano, że dla animacji można znaleźć jego docelowy musi o tym, element docelowy nazwy i właściwości animacji. Określenie właściwości animacji jest wprost do przodu: Ustaw <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> o nazwie właściwości animacji.  Określ nazwę obiektu, którego właściwości chcesz animować przez ustawienie <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> właściwości animacji.  
  
 Aby uzyskać <xref:System.Windows.Setter.TargetName%2A> właściwości do pracy, obiekt docelowy musi mieć nazwę. Przypisanie nazwy do <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] różni się od nazwy do przypisywania <xref:System.Windows.Freezable> obiektu.  
  
 Elementy Framework są tych klas, które dziedziczą z <xref:System.Windows.FrameworkElement> klasy. Przykłady elementów framework <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>, i <xref:System.Windows.Shapes.Rectangle>. Zasadniczo wszystkie systemu windows, paneli i formanty są elementami. Elementy zawartości Framework są tych klas, które dziedziczą z <xref:System.Windows.FrameworkContentElement> klasy. Przykłady elementów zawartości w ramach <xref:System.Windows.Documents.FlowDocument> i <xref:System.Windows.Documents.Paragraph>. Jeśli nie masz pewności, czy typ jest framework element lub framework elementu zawartości, sprawdź, czy ma właściwość Name. Jeśli tak, jest prawdopodobnie framework element lub framework elementu zawartości. Aby upewnić się Sprawdź sekcję hierarchii dziedziczenia, strony typu.  
  
 Aby włączyć przeznaczonych dla elementu struktury lub zawartości elementu framework w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można ustawić jej <xref:System.Windows.FrameworkElement.Name%2A> właściwości. W kodzie, należy również użyć <xref:System.Windows.NameScope.RegisterName%2A> metodę, aby zarejestrować nazwę elementu z elementu, dla którego utworzono <xref:System.Windows.NameScope>.  
  
 W poniższym przykładzie, pobranych z poprzednim przykładzie przypisano nazwę `MyRectangle` <xref:System.Windows.Shapes.Rectangle>, typ <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 Po jego nazwie można animować właściwości tego elementu.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable> typy tych klas, które dziedziczą z <xref:System.Windows.Freezable> klasy. Przykłady <xref:System.Windows.Freezable> obejmują <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>, i <xref:System.Windows.Media.GradientStop>.  
  
 Aby włączyć wartości docelowej <xref:System.Windows.Freezable> przez animacji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], możesz użyć [x: Name — dyrektywa](../../../../docs/framework/xaml-services/x-name-directive.md) go przypisać nazwę. W kodzie, użyj <xref:System.Windows.NameScope.RegisterName%2A> metodę, aby zarejestrować swojej nazwy elementu, dla którego utworzono <xref:System.Windows.NameScope>.  
  
 Poniższy przykład przypisuje nazwę <xref:System.Windows.Freezable> obiektu.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 Następnie obiekt może być celem animacji.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> obiekty używają obszarów nazw, aby rozwiązać <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> właściwości. Aby uzyskać więcej informacji na temat obszarów nazw WPF, zobacz [WPF XAML Namescopes](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md). Jeśli <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> właściwość została pominięta, animacji celem element, na którym jest zdefiniowany lub, w przypadku style, styl elementu.  
  
 Czasami nie można przypisać nazwy do <xref:System.Windows.Freezable> obiektu. Na przykład jeśli <xref:System.Windows.Freezable> jest zadeklarowany jako zasób lub używany do ustawiania wartości właściwości w stylu, nie można nadać nazwy. Ponieważ nie ma nazwy, nie może być celem bezpośrednio, ale może być celem pośrednio. W poniższych sekcjach opisano, jak korzystać z pośrednich elementów docelowych.  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>Pośrednie elementów docelowych  
 Czasami <xref:System.Windows.Freezable> nie może być celem bezpośrednio przez animację, takie jak kiedy <xref:System.Windows.Freezable> jest zadeklarowany jako zasób lub używany do ustawiania wartości właściwości w stylu. W takich przypadkach, nawet jeśli użytkownik nie może wskazać bezpośrednio, można nadal animować <xref:System.Windows.Freezable> obiektu. Zamiast ustawienie <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> właściwość o nazwie <xref:System.Windows.Freezable>, nadajesz nazwę elementu, do którego <xref:System.Windows.Freezable> "należy". Na przykład <xref:System.Windows.Media.SolidColorBrush> służy do określania <xref:System.Windows.Shapes.Shape.Fill%2A> prostokąta element należy do tego prostokąta. Aby animować pędzla, należy ustawić animacji <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> przy użyciu łańcucha właściwości, która rozpoczyna się od właściwości elementu framework lub element zawartości w ramach <xref:System.Windows.Freezable> była używana do ustawiania i kończy się wyrazem <xref:System.Windows.Freezable> właściwości animacji.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 Należy zauważyć, że jeśli <xref:System.Windows.Freezable> jest zablokowane, klon zostaną wprowadzone i że klonowania zostanie animowany. W takim wypadku oryginalny obiekt <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> właściwości w dalszym ciągu zwraca `false`, ponieważ oryginalny obiekt nie jest w rzeczywistości animowany. Aby uzyskać więcej informacji na temat klonowania, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Należy również zauważyć, używając przeznaczonych dla właściwości pośrednie, istnieje możliwość obiektów docelowych, które nie istnieją. Na przykład użytkownik może założyć, że <xref:System.Windows.Controls.Control.Background%2A> określonego przycisku ustawiono z <xref:System.Windows.Media.SolidColorBrush> , a następnie spróbuj animacji kolorów, gdy w rzeczywistości <xref:System.Windows.Media.LinearGradientBrush> został użyty do ustawienia tło przycisku. W takich przypadkach nie wyjątek; animacji nie może mieć widocznego efektu, ponieważ <xref:System.Windows.Media.LinearGradientBrush> nie reaguje na zmiany we <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwości.  
  
 W poniższych sekcjach opisano pośrednie właściwości elementów docelowych składni bardziej szczegółowo.  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Pośrednio przeznaczonych dla właściwości obiektu Freezable w języku XAML  
 Pod kątem właściwości obiektu freezable w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy użyć następującej składni.  
  
||  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 Gdzie  
  
-   *ElementPropertyName* jest właściwość <xref:System.Windows.FrameworkElement> którego <xref:System.Windows.Freezable> jest używana do ustawienia, a  
  
-   *FreezablePropertyName* jest właściwość <xref:System.Windows.Freezable> animacji.  
  
 Poniższy kod przedstawia sposób animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> służy do określania  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 Czasami trzeba docelowego obiektu freezable, znajdujący się w kolekcji lub tablicy.  
  
 Aby skierować je do obiektu freezable, zawartych w kolekcji, należy użyć następującej składni ścieżki.  
  
||  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 Gdzie *CollectionIndex* jest indeks obiektu w kolekcji lub tablicy.  
  
 Na przykład, załóżmy, że ma prostokąt <xref:System.Windows.Media.TransformGroup> zasobów stosowane do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości i chcesz animować jedną przekształcenia zawiera.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 Poniższy kod przedstawia sposób animować <xref:System.Windows.Media.RotateTransform.Angle%2A> właściwość <xref:System.Windows.Media.RotateTransform> w poprzednim przykładzie.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Pośrednio przeznaczonych dla właściwości obiektu Freezable w kodzie  
 W kodzie, możesz utworzyć <xref:System.Windows.PropertyPath> obiektu. Po utworzeniu <xref:System.Windows.PropertyPath>, należy określić <xref:System.Windows.PropertyPath.Path%2A> i <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 Aby utworzyć <xref:System.Windows.PropertyPath.PathParameters%2A>, można utworzyć tablicy typu <xref:System.Windows.DependencyProperty> zawierający listę pola identyfikatora właściwości zależności. Jest pierwsze pole identyfikatora właściwości <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> który <xref:System.Windows.Freezable> jest używana do ustawienia. Następnego pola identyfikator reprezentuje właściwość <xref:System.Windows.Freezable> do obiektu docelowego. Pomyśl o tym, jako łańcuch właściwości łączy <xref:System.Windows.Freezable> do <xref:System.Windows.FrameworkElement> obiektu.  
  
 Poniżej przedstawiono przykład łańcucha właściwości zależności, którego celem jest <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> służy do określania <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta.  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 Należy również określić <xref:System.Windows.PropertyPath.Path%2A>. A <xref:System.Windows.PropertyPath.Path%2A> jest <xref:System.String> , który zawiadamia <xref:System.Windows.PropertyPath.Path%2A> interpretowanie jego <xref:System.Windows.PropertyPath.PathParameters%2A>. Używa następującej składni.  
  
||  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|  
  
 Gdzie  
  
-   *OwnerPropertyArrayIndex* jest indeksem <xref:System.Windows.DependencyProperty> tablicy, która zawiera identyfikator <xref:System.Windows.FrameworkElement> właściwości obiektu który <xref:System.Windows.Freezable> służy do ustawiania, i  
  
-   *FreezablePropertyArrayIndex* jest indeksem <xref:System.Windows.DependencyProperty> tablicy, która zawiera identyfikator właściwości do obiektu docelowego.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.PropertyPath.Path%2A> który będzie towarzyszyć <xref:System.Windows.PropertyPath.PathParameters%2A> zdefiniowane w poprzednim przykładzie.
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 Poniższy przykład łączy kod w poprzednich przykładach, aby animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> służy do określania <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta.  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 Czasami trzeba docelowego obiektu freezable, znajdujący się w kolekcji lub tablicy. Na przykład, załóżmy, że ma prostokąt <xref:System.Windows.Media.TransformGroup> zasobów stosowane do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości i chcesz animować jedną przekształcenia zawiera.  
  
 [!code-xaml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 Do obiektu docelowego <xref:System.Windows.Freezable> zawartych w kolekcji, użyj następującej składni ścieżki.  
  
||  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|  
  
 Gdzie *CollectionIndex* jest indeks obiektu w kolekcji lub tablicy.  
  
 Do obiektu docelowego <xref:System.Windows.Media.RotateTransform.Angle%2A> właściwość <xref:System.Windows.Media.RotateTransform>, drugi przekształcenie w <xref:System.Windows.Media.TransformGroup>, należy użyć następujących <xref:System.Windows.PropertyPath.Path%2A> i <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 Poniższy przykład przedstawia kompletny kod dla animacji <xref:System.Windows.Media.RotateTransform.Angle%2A> z <xref:System.Windows.Media.RotateTransform> zawartych w <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Pośrednio korzystających z obiektu Freezable jako punkt początkowy  
 Przedstawione w poprzednich sekcjach opisano sposób pośrednio target <xref:System.Windows.Freezable> , zaczynając od <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> i tworzenie łańcucha właściwości <xref:System.Windows.Freezable> właściwości podrzędnych. Można również użyć <xref:System.Windows.Freezable> jako początkowy punkt i pośrednio docelowych jednego z jego <xref:System.Windows.Freezable> właściwości podrzędnych. Jeden dodatkowe ograniczenie ma zastosowanie, gdy za pomocą <xref:System.Windows.Freezable> jako punktu wyjścia do użycia z pośrednich: początkowe <xref:System.Windows.Freezable> , a następnie co <xref:System.Windows.Freezable> między nim a pośrednio docelowa właściwość podrzędne muszą nie zostać zablokowany.  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Kontrolowanie interaktywnie scenorysu w języku XAML  
 Aby uruchomić scenorysu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], możesz użyć <xref:System.Windows.Media.Animation.BeginStoryboard> akcja wyzwalacza. <xref:System.Windows.Media.Animation.BeginStoryboard> dystrybuuje animacje obiektów i właściwości animacji i uruchamia scenorysu. (Aby uzyskać szczegółowe informacje o tym procesie, zobacz [animacji i Przegląd systemu chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).) Jeśli zostanie nadana <xref:System.Windows.Media.Animation.BeginStoryboard> nazwę przez określenie jego <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> właściwości, można ustawić, którymi można sterować scenorysu. Użytkownik może interakcyjnie wybrać scenorysu po jej uruchomieniu. Poniżej znajduje się lista akcji sterowane scenorysu korzystać z wyzwalaczy zdarzeń do kontrolowania scenorysu.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Wstrzymuje scenorysu.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Wznawia działanie wstrzymanej scenorysu.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Zmienia szybkość scenorysu.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Przesuwa scenorysu do końca okresu, jeśli istnieje.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Przestaje scenorysu.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Usuwa scenorysu.  
  
 W poniższym przykładzie sterowane scenorysu akcje są używane do sterowania interaktywnego scenorysu.  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Interaktywnie kontrolowanie scenorysu przy użyciu kodu  
 Poprzednich przykładach wykazały, jak animować przy użyciu akcje wyzwalacza. W kodzie, może też kontrolować scenorysu interakcyjne metod <xref:System.Windows.Media.Animation.Storyboard> klasy. Dla <xref:System.Windows.Media.Animation.Storyboard> aby zapewnić interakcyjnego w kodzie, należy użyć odpowiedniego przeciążenia scenorysu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> — metoda i określ `true` dokonanie kontroli. Zobacz <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> strony, aby uzyskać więcej informacji.  
  
 Na poniższej liście przedstawiono metody, które mogą służyć do modyfikowania <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 Zaletą używania tych metod jest, że nie trzeba tworzyć <xref:System.Windows.Trigger> lub <xref:System.Windows.TriggerAction> obiektów; wystarczy, że odwołanie do sterowane <xref:System.Windows.Media.Animation.Storyboard> należy modyfikować.  
  
 **Uwaga:** wszystkie interaktywnego działania podjęte w <xref:System.Windows.Media.Animation.Clock>i w związku z tym również na <xref:System.Windows.Media.Animation.Storyboard> zostanie przeprowadzona na następny znaczników aparatu czasu, który odbędzie się tuż przed następnym renderowania. Na przykład, jeśli używasz <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody, aby przejść do innego punktu animacji, wartość właściwości nie zmienia się natychmiast, raczej wartość zmieni się w następnym znaczników czasu aparatu.  
  
 Poniższy przykład pokazuje, jak zastosować i sterowanie animacji przy użyciu metody interakcyjne <xref:System.Windows.Media.Animation.Storyboard> klasy.  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>Animuj w stylu  
 Można użyć <xref:System.Windows.Media.Animation.Storyboard> obiektów, aby zdefiniować animacji <xref:System.Windows.Style>. Animacja przy <xref:System.Windows.Media.Animation.Storyboard> w <xref:System.Windows.Style> jest podobny do sposobu używania <xref:System.Windows.Media.Animation.Storyboard> w innym miejscu, z następującymi wyjątkami trzy:  
  
-   Nie można określić <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; <xref:System.Windows.Media.Animation.Storyboard> zawsze celem element, do którego <xref:System.Windows.Style> została zastosowana. Do obiektu docelowego <xref:System.Windows.Freezable> obiektów, należy użyć pośrednie elementów docelowych. Aby uzyskać więcej informacji o przeznaczonych dla pośredniego, zobacz [przeznaczonych dla pośredniego](#pathsyntaxforchangeable) sekcji.  
  
-   Nie można określić <xref:System.Windows.EventTrigger.SourceName%2A> dla <xref:System.Windows.EventTrigger> lub <xref:System.Windows.Trigger>.  
  
-   Nie można ustawić za pomocą wyrażenia wiązania odwołania lub danych dynamicznych zasobów <xref:System.Windows.Media.Animation.Storyboard> lub wartości właściwości animacji. Jest to spowodowane tym cała jego zawartość <xref:System.Windows.Style> musi być bezpieczne wątkowo, i musi systemu chronometrażu <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> obiektów, aby były bezpieczne wątkowo. A <xref:System.Windows.Media.Animation.Storyboard> nie można zablokować, jeśli jego lub jej podrzędnych osi czasu zawierają wyrażenia wiązania odwołania lub danych dynamicznych zasobów. Aby uzyskać więcej informacji o zamrażanie i inne <xref:System.Windows.Freezable> funkcji, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nie można zadeklarować obsługę zdarzeń <xref:System.Windows.Media.Animation.Storyboard> lub zdarzenia animacji.  
  
 Na przykład przedstawiający sposób definiowania scenorysu w stylu, zobacz [Animuj w stylu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md) przykład.  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>Animuj w ControlTemplate  
 Można użyć <xref:System.Windows.Media.Animation.Storyboard> obiektów, aby zdefiniować animacji <xref:System.Windows.Controls.ControlTemplate>. Animacja przy <xref:System.Windows.Media.Animation.Storyboard> w <xref:System.Windows.Controls.ControlTemplate> jest podobny do sposobu używania <xref:System.Windows.Media.Animation.Storyboard> w innym miejscu, z wyjątkiem dwóch następujących sytuacji:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Mogą odwoływać się tylko do obiektów podrzędnych <xref:System.Windows.Controls.ControlTemplate>. Jeśli <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> nie zostanie określony, element, do którego jest przeznaczony dla animacji <xref:System.Windows.Controls.ControlTemplate> została zastosowana.  
  
-   <xref:System.Windows.EventTrigger.SourceName%2A> Dla <xref:System.Windows.EventTrigger> lub <xref:System.Windows.Trigger> mogą odwoływać się tylko do obiektów podrzędnych <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Nie można ustawić za pomocą wyrażenia wiązania odwołania lub danych dynamicznych zasobów <xref:System.Windows.Media.Animation.Storyboard> lub wartości właściwości animacji. Jest to spowodowane tym cała jego zawartość <xref:System.Windows.Controls.ControlTemplate> musi być bezpieczne wątkowo, i musi systemu chronometrażu <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> obiektów, aby były bezpieczne wątkowo. A <xref:System.Windows.Media.Animation.Storyboard> nie można zablokować, jeśli jego lub jej podrzędnych osi czasu zawierają wyrażenia wiązania odwołania lub danych dynamicznych zasobów. Aby uzyskać więcej informacji o zamrażanie i inne <xref:System.Windows.Freezable> funkcji, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nie można zadeklarować obsługę zdarzeń <xref:System.Windows.Media.Animation.Storyboard> lub zdarzenia animacji.  
  
 Na przykład przedstawiający sposób definiowania scenorysu w <xref:System.Windows.Controls.ControlTemplate>, zobacz [Animuj w ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md) przykład.  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>Wtedy, gdy wartość właściwości zostanie zmieniona  
 Style i szablony formantu można użyć obiektów wyzwalacza zacząć scenorysu podczas zmiany właściwości. Aby uzyskać przykłady, zobacz [wyzwalanie animacji podczas zmian wartości właściwości](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md) i [Animuj w ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md).  
  
 Animacje zastosowane przez właściwość <xref:System.Windows.Trigger> obiekty zachowują się w sposób bardziej złożone niż <xref:System.Windows.EventTrigger> animacje lub animacje uruchomić za pomocą <xref:System.Windows.Media.Animation.Storyboard> metod.  Ich "przekazaniem" animacji zdefiniowany przez inne <xref:System.Windows.Trigger> obiektów, ale tworzą z <xref:System.Windows.EventTrigger> i animacje wyzwalane metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Techniki animacji właściwości — przegląd](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
