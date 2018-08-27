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
ms.openlocfilehash: a7f9539cd3ac571977a91cd4e7dce07d641af3b6
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932324"
---
# <a name="storyboards-overview"></a>Przegląd Scenorysy
W tym temacie pokazano, jak używać <xref:System.Windows.Media.Animation.Storyboard> obiekty do organizowania i stosowanie animacji. Opis interaktywnie manipulowania <xref:System.Windows.Media.Animation.Storyboard> obiektów i opisuje właściwość pośrednich, przeznaczone dla składni.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy zapoznać się z inną animację typów i ich podstawowych funkcji. Aby zapoznać się z wprowadzeniem do animacji, zobacz [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Możesz również wiedzieć, jak użyć załączonych właściwości. Aby uzyskać więcej informacji na temat właściwości dołączone zobacz [Przegląd właściwości dołączonych](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>Co to jest scenorysu?  
 Animacje nie są przydatne tylko typ osi czasu. Innych klas osi czasu są udostępniane ułatwia organizowanie zestawy osie czasu i dotyczą właściwości osi czasu. Osie czasu kontenerów pochodzi od <xref:System.Windows.Media.Animation.TimelineGroup> klasy i obejmują <xref:System.Windows.Media.Animation.ParallelTimeline> i <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Element <xref:System.Windows.Media.Animation.Storyboard> jest typem kontenera osi czasu, który dostarcza informacje określania wartości docelowej dla osi czasu zawiera. Scenorysu może zawierać dowolny typ <xref:System.Windows.Media.Animation.Timeline>, w tym innych kontenerów osie czasu i animacji. <xref:System.Windows.Media.Animation.Storyboard> obiekty umożliwiają łączenie osi czasu, które mają wpływ na różne obiekty i właściwości w drzewie jedną oś czasu, co ułatwia organizowanie i kontrolowania zachowania chronometrażu złożonych. Na przykład załóżmy, że chcesz, aby przycisk, który wykona te trzy rzeczy.  
  
-   Rozwijaj i zmienić kolor, gdy użytkownik wybierze przycisk.  
  
-   Zmniejszanie natychmiast, a następnie przejść do jego oryginalny rozmiar po kliknięciu.  
  
-   Zmniejszanie i stopniowe do 50 procent krycia, gdy zostanie ona wyłączona.  
  
 W tym przypadku masz wiele zestawów animacji, które są stosowane do tego samego obiektu, a ma być odtwarzany w różnym czasie, zależy od stanu przycisku. <xref:System.Windows.Media.Animation.Storyboard> obiekty umożliwiają organizowanie animacji i zastosować je w grupach na co najmniej jeden obiekt.  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>Gdzie można używać scenorysu?  
 A <xref:System.Windows.Media.Animation.Storyboard> można animować właściwości zależności animatable klas (Aby uzyskać więcej informacji na temat co sprawia, że klasa animatable zobacz [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)). Jednak ponieważ storyboarding jest funkcją poziomie struktury, obiekt musi należeć do <xref:System.Windows.NameScope> z <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>.  
  
 Na przykład można użyć <xref:System.Windows.Media.Animation.Storyboard> wykonać następujące czynności:  
  
-   Animowanie <xref:System.Windows.Media.SolidColorBrush> (inne niż framework element), który maluje tło przycisku (typ <xref:System.Windows.FrameworkElement>),  
  
-   Animowanie <xref:System.Windows.Media.SolidColorBrush> (inne niż framework element), który maluje wypełnienie <xref:System.Windows.Media.GeometryDrawing> (inne niż framework element) wyświetlana przy użyciu <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).  
  
-   W kodzie, animować <xref:System.Windows.Media.SolidColorBrush> zadeklarowane przez klasę, która zawiera również <xref:System.Windows.FrameworkElement>, jeśli <xref:System.Windows.Media.SolidColorBrush> zarejestrowane nazwy, <xref:System.Windows.FrameworkElement>.  
  
 Jednak nie można użyć <xref:System.Windows.Media.Animation.Storyboard> animować <xref:System.Windows.Media.SolidColorBrush> nie zarejestrował takiej samej nazwy <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, lub nie był używany do ustawiania właściwości z <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>.  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>Jak zastosować animacje przy użyciu scenorysu  
 Aby użyć <xref:System.Windows.Media.Animation.Storyboard> do organizowania i Zastosuj animacje, Dodaj animacji jako podrzędnych osi czasu z <xref:System.Windows.Media.Animation.Storyboard>. <xref:System.Windows.Media.Animation.Storyboard> Klasa udostępnia <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> dołączonych właściwości. Te właściwości są nastavit animacji, aby określić jego obiekt docelowy i właściwości.  
  
 Aby zastosować animacje do celów, możesz rozpocząć <xref:System.Windows.Media.Animation.Storyboard> przy użyciu metody lub akcję wyzwalacza. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], możesz użyć <xref:System.Windows.Media.Animation.BeginStoryboard> obiekt z <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>, lub <xref:System.Windows.DataTrigger>. W kodzie, można również użyć <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody.  
  
 W poniższej tabeli przedstawiono różnych miejscach gdzie każdy <xref:System.Windows.Media.Animation.Storyboard> rozpocząć techniką jest obsługiwany: poszczególnych wystąpień, style, szablon kontrolki i szablon danych. "Na wystąpienie" odnosi się do technika stosowania animacji lub scenorysu bezpośrednio do wystąpienia obiektu, a nie w stylu, szablon kontrolki lub szablon danych.  
  
|Rozpoczyna się scenorysu, za pomocą...|Na wystąpienie|Styl|Szablon kontrolki|Szablon danych|Przykład|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> i <xref:System.Windows.EventTrigger>|Tak|Tak|Tak|Tak|[Animowanie właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> i właściwości <xref:System.Windows.Trigger>|Nie|Tak|Tak|Tak|[Wyzwalanie animacji w przypadku zmiany wartości właściwości](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.DataTrigger>|Nie|Tak|Tak|Tak|[Porady: wyzwalanie animacji w przypadku zmiany danych](http://msdn.microsoft.com/library/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> — Metoda|Tak|Nie|Nie|Nie|[Animowanie właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Storyboard> animować <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> elementu i <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> używany do rysowania, które <xref:System.Windows.Shapes.Rectangle>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 W poniższych sekcjach opisano <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> dołączonych właściwości bardziej szczegółowo.  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Przeznaczone dla elementów Framework, elementy zawartości Framework i obiektów Freezable  
 Poprzedniej sekcji wspomnieć, że dla animacji, aby znaleźć jego element docelowy, należy o tym, nazwa obiektu docelowego i właściwości, aby animować. Określenie właściwości, aby animować jest bardzo proste: wystarczy ustawić <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> nazwą właściwości animować.  Należy określić nazwę obiektu, którego właściwości chcesz animować, ustawiając <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> właściwość animacji.  
  
 Aby uzyskać <xref:System.Windows.Setter.TargetName%2A> właściwość działała, obiekt docelowy musi mieć nazwę. Przypisywanie nazwę <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] różni się od nazwy do przypisywania <xref:System.Windows.Freezable> obiektu.  
  
 Elementy Framework są tych klas, które dziedziczą z <xref:System.Windows.FrameworkElement> klasy. Przykłady elementów framework <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>, i <xref:System.Windows.Shapes.Rectangle>. Zasadniczo wszystkich okien, panele i formanty są elementami. Elementy zawartości Framework są tych klas, które dziedziczą z <xref:System.Windows.FrameworkContentElement> klasy. Przykłady elementów zawartości w ramach <xref:System.Windows.Documents.FlowDocument> i <xref:System.Windows.Documents.Paragraph>. Jeśli nie masz pewności, czy typ jest elementu struktury lub zawartości elementu framework, sprawdź, czy ma właściwość Name. Jeśli tak jest, to prawdopodobnie elementu struktury lub zawartości elementu framework. Aby upewnić się Sprawdź w hierarchii dziedziczenia części jego typ strony.  
  
 Aby włączyć przeznaczonych dla elementu struktury lub zawartości elementu framework w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można ustawić jego <xref:System.Windows.FrameworkElement.Name%2A> właściwości. W kodzie, należy również użyć <xref:System.Windows.NameScope.RegisterName%2A> metodę, aby zarejestrować nazwę elementu z elementu, dla którego utworzono <xref:System.Windows.NameScope>.  
  
 Poniższy przykład przekierowanie z poprzedniego przykładu, przypisuje nazwę `MyRectangle` <xref:System.Windows.Shapes.Rectangle>, typem <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 Po jego nazwie można animować właściwości tego elementu.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable> typy są tych klas, które dziedziczą z <xref:System.Windows.Freezable> klasy. Przykłady <xref:System.Windows.Freezable> obejmują <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>, i <xref:System.Windows.Media.GradientStop>.  
  
 Aby włączyć wartości docelowej <xref:System.Windows.Freezable> przez animacji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], możesz użyć [x: Name — dyrektywa](../../../../docs/framework/xaml-services/x-name-directive.md) go przypisać nazwę. W kodzie, należy użyć <xref:System.Windows.NameScope.RegisterName%2A> metodę, aby zarejestrować swojej nazwy elementu, dla którego utworzono <xref:System.Windows.NameScope>.  
  
 Poniższy przykład przypisuje nazwę <xref:System.Windows.Freezable> obiektu.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 Następnie można zastosować obiekt przez animację.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> obiekty rozwiązywania za pomocą nazwy zakresy <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> właściwości. Aby uzyskać więcej informacji na temat zakresy nazw WPF, zobacz [zakresy WPF XAML nazw](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md). Jeśli <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> właściwość zostanie pominięty, animacji jest przeznaczony dla elementu, na którym jest zdefiniowany lub, w przypadku stylów, element ze stylem.  
  
 Czasami nie można przypisać nazwę <xref:System.Windows.Freezable> obiektu. Na przykład jeśli <xref:System.Windows.Freezable> jest zadeklarowany jako zasób lub używane do ustawiania wartości właściwości w stylu, nie można nadać nazwę. Ponieważ nie ma nazwę, nie można przeprowadzić bezpośrednio —, ale może być celem pośrednio. Poniżej opisano sposób używania przeznaczonych dla pośredniego.  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>Celem pośrednich  
 Czasami <xref:System.Windows.Freezable> nie będzie można wykonywać bezpośrednio przez animację, takie jak czas <xref:System.Windows.Freezable> jest zadeklarowany jako zasób lub używane do ustawiania wartości właściwości w stylu. W takich przypadkach, nawet jeśli użytkownik nie może wskazać bezpośrednio, można nadal animować <xref:System.Windows.Freezable> obiektu. Zamiast ustawiać <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> właściwość o nazwie <xref:System.Windows.Freezable>, tworzonemu elementowi nadawana nazwa elementu, do którego <xref:System.Windows.Freezable> "należy". Na przykład <xref:System.Windows.Media.SolidColorBrush> używane do ustawiania <xref:System.Windows.Shapes.Shape.Fill%2A> prostokąta element należy do tego prostokąta. Aby animować pędzla, należy ustawić animacji <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> przy użyciu łańcucha właściwości, która rozpoczyna się od właściwości elementu struktury lub element zawartości w ramach <xref:System.Windows.Freezable> była używana do ustawiania i kończy się <xref:System.Windows.Freezable> właściwość animować.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 Należy zauważyć, że jeśli <xref:System.Windows.Freezable> jest zamrożone, klonowanie jest zostaną wprowadzone i że klonowania będzie animowana. W takim przypadku, oryginalnym obiekcie <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> właściwość w dalszym ciągu zwraca `false`, ponieważ nie jest faktycznie animowany oryginalnego obiektu. Aby uzyskać więcej informacji na temat klonowania, zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Należy również zauważyć, że, korzystając z pośrednich właściwość określania wartości docelowej, jest możliwe obiektów docelowych, które nie istnieją. Na przykład można zakładać, że <xref:System.Windows.Controls.Control.Background%2A> określonego przycisku została ustawiona za pomocą <xref:System.Windows.Media.SolidColorBrush> , a następnie spróbuj animować kolor, gdy w rzeczywistości <xref:System.Windows.Media.LinearGradientBrush> zostało użyte do ustawienia tło przycisku. W takich przypadkach jest zgłaszany żaden wyjątek; animacja nie może mieć wpływ widoczne, ponieważ <xref:System.Windows.Media.LinearGradientBrush> nie reaguje na zmiany <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwości.  
  
 W poniższych sekcjach opisano pośrednich właściwość przeznaczonych dla składni bardziej szczegółowo.  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Pośrednio przeznaczonych dla właściwości Freezable w XAML  
 Pod kątem właściwości freezable w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy użyć następującej składni.  
  
| |  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 Gdzie  
  
-   *ElementPropertyName* jest właściwość <xref:System.Windows.FrameworkElement> który <xref:System.Windows.Freezable> służy do ustawiania, i  
  
-   *FreezablePropertyName* jest właściwość <xref:System.Windows.Freezable> animować.  
  
 Poniższy kod pokazuje, jak animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> używane do ustawiania  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 Czasami zachodzi potrzeba docelowe freezable znajdujących się w kolekcji lub tablicy.  
  
 Pod kątem freezable znajdujących się w kolekcji, użyj następujących składni ścieżki.  
  
| |  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 Gdzie *CollectionIndex* jest indeksem obiektów w tablicy lub kolekcji.  
  
 Na przykład, załóżmy, że prostokąt ma <xref:System.Windows.Media.TransformGroup> zasobów stosowane do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości i chcesz animować jeden przekształcenia zawiera.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 Poniższy kod pokazuje, jak animować <xref:System.Windows.Media.RotateTransform.Angle%2A> właściwość <xref:System.Windows.Media.RotateTransform> pokazano w poprzednim przykładzie.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Pośrednio przeznaczonych dla właściwości Freezable w kodzie  
 W kodzie, Utwórz <xref:System.Windows.PropertyPath> obiektu. Po utworzeniu <xref:System.Windows.PropertyPath>, należy określić <xref:System.Windows.PropertyPath.Path%2A> i <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 Aby utworzyć <xref:System.Windows.PropertyPath.PathParameters%2A>, utworzyć tablicę typu <xref:System.Windows.DependencyProperty> zawierający listę pól identyfikatora właściwości zależności. Pierwsze pole identyfikatora jest właściwości <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> , <xref:System.Windows.Freezable> służy do ustawiania. Następne pole identyfikatora reprezentuje właściwość <xref:System.Windows.Freezable> do obiektu docelowego. Ją traktować jako łańcuch właściwości, które łączy <xref:System.Windows.Freezable> do <xref:System.Windows.FrameworkElement> obiektu.  
  
 Oto przykład łańcuch właściwość zależności, który jest przeznaczony dla <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> używane do ustawiania <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta.  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 Należy także określić <xref:System.Windows.PropertyPath.Path%2A>. A <xref:System.Windows.PropertyPath.Path%2A> jest <xref:System.String> informuje, że <xref:System.Windows.PropertyPath.Path%2A> jak interpretować jego <xref:System.Windows.PropertyPath.PathParameters%2A>. Używa następującej składni.  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|  
  
 Gdzie  
  
-   *OwnerPropertyArrayIndex* jest indeksem <xref:System.Windows.DependencyProperty> tablicę, która zawiera identyfikator <xref:System.Windows.FrameworkElement> właściwości obiektu, <xref:System.Windows.Freezable> służy do ustawiania, i  
  
-   *FreezablePropertyArrayIndex* jest indeksem <xref:System.Windows.DependencyProperty> tablicy, która zawiera identyfikator właściwości do obiektu docelowego.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.PropertyPath.Path%2A> , będzie towarzyszyć <xref:System.Windows.PropertyPath.PathParameters%2A> zdefiniowane w poprzednim przykładzie.
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 Poniższy przykład łączy kod w poprzednich przykładach, aby animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> używane do ustawiania <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta.  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 Czasami zachodzi potrzeba docelowe freezable znajdujących się w kolekcji lub tablicy. Na przykład, załóżmy, że prostokąt ma <xref:System.Windows.Media.TransformGroup> zasobów stosowane do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości i chcesz animować jeden przekształcenia zawiera.  
  
 [!code-xaml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 Do obiektu docelowego <xref:System.Windows.Freezable> znajdujących się w kolekcji, użyj następującej składni ścieżki.  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|  
  
 Gdzie *CollectionIndex* jest indeksem obiektów w tablicy lub kolekcji.  
  
 Do obiektu docelowego <xref:System.Windows.Media.RotateTransform.Angle%2A> właściwość <xref:System.Windows.Media.RotateTransform>, drugi przekształcenia w <xref:System.Windows.Media.TransformGroup>, należy użyć następujących <xref:System.Windows.PropertyPath.Path%2A> i <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 Poniższy przykład pokazuje kompletny kod dla animowanie <xref:System.Windows.Media.RotateTransform.Angle%2A> z <xref:System.Windows.Media.RotateTransform> zawartych w <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Pośrednio określania wartości docelowej z Freezable jako punktu wyjścia  
 Przedstawione w poprzednich sekcjach opisano sposób pośrednio docelowe <xref:System.Windows.Freezable> , zaczynając od <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> i tworzenie łańcucha własności <xref:System.Windows.Freezable> właściwości podrzędnych. Można również użyć <xref:System.Windows.Freezable> jako początkowy punkt i pośrednio docelowe jeden z jego <xref:System.Windows.Freezable> właściwości podrzędnych. Jedno dodatkowe ograniczenie ma zastosowanie, gdy za pomocą <xref:System.Windows.Freezable> jako punktu wyjścia języka pośredniego: początkowy <xref:System.Windows.Freezable> , a następnie co <xref:System.Windows.Freezable> między nim a pośrednio docelowe właściwości podrzędnej musi nie nelze zmrazit.  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Kontrolowanie interaktywnie scenorysu w XAML  
 Aby rozpocząć scenorysu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], możesz użyć <xref:System.Windows.Media.Animation.BeginStoryboard> wyzwalanie akcji. <xref:System.Windows.Media.Animation.BeginStoryboard> dystrybuuje animacji do obiektów i właściwości, animować i uruchamia scenorysu. (Aby uzyskać szczegółowe informacje o tym procesie, zobacz [Animacja i System chronometrażu w — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).) Jeśli nadasz <xref:System.Windows.Media.Animation.BeginStoryboard> nazwę, określając jego <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> właściwości, możesz obejrzeć sterowane scenorysu. Możesz następnie interaktywnie kontrolować scenorys po uruchomieniu. Oto lista czynności scenorysu musi używać przy użyciu wyzwalaczy zdarzeń, aby kontrolować scenorys.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Zatrzymuje scenorysu.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Wznawia działanie wstrzymanej scenorysu.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Zmienia szybkość scenorysu.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Prowadzi scenorysu do końca okresu wypełnienia, jeśli taki istnieje.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Zatrzymuje scenorysu.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Usuwa scenorysu.  
  
 W poniższym przykładzie sterowane scenorysu akcji są używane do interaktywnie kontrolować scenorys.  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Interakcyjne sterowanie scenorysu przy użyciu kodu  
 Poprzednie przykłady wykazały, jak animować przy użyciu akcji wyzwalacza. W kodzie, mogą również kontrolować scenorys przy użyciu metod interaktywnych <xref:System.Windows.Media.Animation.Storyboard> klasy. Dla <xref:System.Windows.Media.Animation.Storyboard> interaktywnymi w kodzie, należy korzystać tylko odpowiednie przeciążenie scenorysu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodę i określić `true` zapewnienie kontrolowania. Zobacz <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> strony, aby uzyskać więcej informacji.  
  
 Na poniższej liście przedstawiono metody, które mogą służyć do manipulowania <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 Zaletą używania tych metod jest, że nie trzeba tworzyć <xref:System.Windows.Trigger> lub <xref:System.Windows.TriggerAction> obiektów; po prostu potrzebujesz odwołania do kontrolowania <xref:System.Windows.Media.Animation.Storyboard> należy modyfikować.  
  
 **Uwaga:** wszystkie interaktywne działania podjęte w <xref:System.Windows.Media.Animation.Clock>i w związku z tym również na <xref:System.Windows.Media.Animation.Storyboard> będzie miała miejsce przy następnym znaczników aparat czasu, który będzie miało miejsce wkrótce przed następnym renderowania. Na przykład, jeśli używasz <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metodę, aby przejść do innego punktu w animacji, wartość właściwości nie zmienia się natychmiast, zamiast wartość zmieni się w następnym znaczników aparatu chronometrażu.  
  
 Poniższy przykład pokazuje, jak zastosować i kontrolowanie animacji przy użyciu metod interaktywnych <xref:System.Windows.Media.Animation.Storyboard> klasy.  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>Animuj w stylu  
 Możesz użyć <xref:System.Windows.Media.Animation.Storyboard> obiektów, aby zdefiniować animacje w <xref:System.Windows.Style>. Animowanie za pomocą <xref:System.Windows.Media.Animation.Storyboard> w <xref:System.Windows.Style> jest podobne do <xref:System.Windows.Media.Animation.Storyboard> w innym miejscu, z wyjątkiem trzy:  
  
-   Nie określaj <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; <xref:System.Windows.Media.Animation.Storyboard> zawsze jest przeznaczony dla elementu, do którego <xref:System.Windows.Style> jest stosowany. Do obiektu docelowego <xref:System.Windows.Freezable> obiektów, należy użyć pośrednich określania wartości docelowej. Aby uzyskać więcej informacji na temat pośrednich przeznaczonych dla zobacz [przeznaczonych dla pośredniego](#pathsyntaxforchangeable) sekcji.  
  
-   Nie można określić <xref:System.Windows.EventTrigger.SourceName%2A> dla <xref:System.Windows.EventTrigger> lub <xref:System.Windows.Trigger>.  
  
-   Nie można użyć wyrażenia wiązania odwołania lub danych dynamicznych zasobów można ustawić <xref:System.Windows.Media.Animation.Storyboard> lub wartości właściwości animacji. To dlatego, że wszystko wewnątrz <xref:System.Windows.Style> musi być metodą o bezpiecznych wątkach, i system chronometrażu musi <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> obiektów, aby były one metodą o bezpiecznych wątkach. Element <xref:System.Windows.Media.Animation.Storyboard> nie można zablokować, jeśli on lub jego podrzędnych osi czasu zawiera zasób dynamiczny odwołania lub danych wyrażenia wiązania. Aby uzyskać więcej informacji o zamrażanie i inne <xref:System.Windows.Freezable> funkcje, zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nie można zadeklarować obsługę zdarzeń dla <xref:System.Windows.Media.Animation.Storyboard> lub zdarzenia animacji.  
  
 Na przykład przedstawiający sposób definiowania scenorysu w stylu zobacz [Animuj w stylu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md) przykład.  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>Animuj w ControlTemplate  
 Możesz użyć <xref:System.Windows.Media.Animation.Storyboard> obiektów, aby zdefiniować animacje w <xref:System.Windows.Controls.ControlTemplate>. Animowanie za pomocą <xref:System.Windows.Media.Animation.Storyboard> w <xref:System.Windows.Controls.ControlTemplate> jest podobne do <xref:System.Windows.Media.Animation.Storyboard> w innym miejscu, z wyjątkiem dwóch następujących sytuacji:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Mogą odwoływać się tylko do obiektów podrzędnych <xref:System.Windows.Controls.ControlTemplate>. Jeśli <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> nie zostanie określony, animacji jest przeznaczony dla elementu, do którego <xref:System.Windows.Controls.ControlTemplate> jest stosowany.  
  
-   <xref:System.Windows.EventTrigger.SourceName%2A> Dla <xref:System.Windows.EventTrigger> lub <xref:System.Windows.Trigger> mogą odwoływać się tylko do obiektów podrzędnych <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Nie można użyć wyrażenia wiązania odwołania lub danych dynamicznych zasobów można ustawić <xref:System.Windows.Media.Animation.Storyboard> lub wartości właściwości animacji. To dlatego, że wszystko wewnątrz <xref:System.Windows.Controls.ControlTemplate> musi być metodą o bezpiecznych wątkach, i system chronometrażu musi <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> obiektów, aby były one metodą o bezpiecznych wątkach. Element <xref:System.Windows.Media.Animation.Storyboard> nie można zablokować, jeśli on lub jego podrzędnych osi czasu zawiera zasób dynamiczny odwołania lub danych wyrażenia wiązania. Aby uzyskać więcej informacji o zamrażanie i inne <xref:System.Windows.Freezable> funkcje, zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nie można zadeklarować obsługę zdarzeń dla <xref:System.Windows.Media.Animation.Storyboard> lub zdarzenia animacji.  
  
 Aby uzyskać przykład pokazujący sposób definiowania scenorysu w <xref:System.Windows.Controls.ControlTemplate>, zobacz [Animuj w ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md) przykład.  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>Animowanie po zmianie wartości właściwości  
 Style i szablony kontrolek można użyć wyzwalacza obiektów można uruchomić scenorysu po zmianie właściwości. Aby uzyskać przykłady, zobacz [wyzwalanie animacji po zmianie wartości właściwości](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md) i [Animuj w ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md).  
  
 Animacje stosowane przez właściwość <xref:System.Windows.Trigger> obiekty zachowują się w sposób bardziej skomplikowane niż <xref:System.Windows.EventTrigger> animacji lub animacje pracę, przy użyciu <xref:System.Windows.Media.Animation.Storyboard> metody.  One "przekazywanie" z animacjami zdefiniowane przez inne <xref:System.Windows.Trigger> obiektów, ale narzędzia compose z <xref:System.Windows.EventTrigger> i animacje wyzwalane przez metodę.  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Techniki animacji właściwości — przegląd](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
