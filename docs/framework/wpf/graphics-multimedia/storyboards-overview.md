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
ms.openlocfilehash: 5c058dbaf2ae209a198a8299790d4002447ac443
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559697"
---
# <a name="storyboards-overview"></a>Przegląd Scenorysy

W tym temacie pokazano, jak za pomocą obiektów <xref:System.Windows.Media.Animation.Storyboard> organizować i stosować animacje. Opisano w nim sposób interakcyjnego manipulowania obiektami <xref:System.Windows.Media.Animation.Storyboard> i opisywania składni docelowej właściwości.

## <a name="prerequisites"></a>Wymagania wstępne

Aby zrozumieć ten temat, należy zapoznać się z różnymi typami animacji i ich podstawowymi funkcjami. Aby zapoznać się z wprowadzeniem do animacji, zobacz [Omówienie animacji](animation-overview.md). Należy również wiedzieć, jak używać dołączonych właściwości. Aby uzyskać więcej informacji na temat dołączonych właściwości, zobacz [Omówienie dołączonych właściwości](../advanced/attached-properties-overview.md).

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>Co to jest scenorys?

Animacje nie są jedynym przydatnym typem osi czasu. Podane są inne klasy osi czasu, które ułatwiają organizowanie zestawów osi czasu oraz stosowanie osi czasu do właściwości. Osie czasu kontenera pochodzą z klasy <xref:System.Windows.Media.Animation.TimelineGroup> i zawierają <xref:System.Windows.Media.Animation.ParallelTimeline> i <xref:System.Windows.Media.Animation.Storyboard>.

<xref:System.Windows.Media.Animation.Storyboard> jest typem osi czasu kontenera, która zawiera informacje dotyczące docelowej osi czasu, które zawiera. Scenorys może zawierać dowolny typ <xref:System.Windows.Media.Animation.Timeline>, w tym inne osie czasu kontenera i animacje. obiekty <xref:System.Windows.Media.Animation.Storyboard> umożliwiają łączenie osi czasu, które mają wpływ na wiele obiektów i właściwości na jedno drzewo osi czasu, co ułatwia organizowanie i kontrolowanie złożonych zachowań chronometrażu. Załóżmy na przykład, że chcesz, aby przycisk przerobił te trzy rzeczy.

- Powiększ i Zmień kolor, gdy użytkownik wybierze przycisk.

- Po kliknięciu Zmniejsz rozmiar do oryginalnego rozmiaru.

- Zmniejsz i zwiększ poziom przezroczystości do 50 procent, gdy zostanie on wyłączony.

W takim przypadku istnieje wiele zestawów animacji, które mają zastosowanie do tego samego obiektu i chcesz odtwarzać w różnych godzinach zależnie od stanu przycisku. obiekty <xref:System.Windows.Media.Animation.Storyboard> umożliwiają organizowanie animacji i stosowanie ich w grupach do co najmniej jednego obiektu.

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>Gdzie można używać scenorysu?

<xref:System.Windows.Media.Animation.Storyboard> może służyć do animowania właściwości zależności klas animowanych (Aby uzyskać więcej informacji na temat tego, co ułatwia animowanie klasy, zobacz [Omówienie animacji](animation-overview.md)). Jednak ponieważ scenorysowanie jest funkcją poziomu platformy, obiekt musi należeć do <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>.

Na przykład można użyć <xref:System.Windows.Media.Animation.Storyboard>, aby wykonać następujące czynności:

- Animuj <xref:System.Windows.Media.SolidColorBrush> (element niebędący strukturą), który maluje tło przycisku (typ <xref:System.Windows.FrameworkElement>),

- Animuj <xref:System.Windows.Media.SolidColorBrush> (element niebędący strukturą), który maluje wypełnienie <xref:System.Windows.Media.GeometryDrawing> (element inny niż Framework) wyświetlany przy użyciu <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).

- W kodzie, Animuj <xref:System.Windows.Media.SolidColorBrush> zadeklarowane przez klasę, która również zawiera <xref:System.Windows.FrameworkElement>, jeśli <xref:System.Windows.Media.SolidColorBrush> zarejestrował swoją nazwę przy użyciu tego <xref:System.Windows.FrameworkElement>.

Nie można jednak użyć <xref:System.Windows.Media.Animation.Storyboard> do animowania <xref:System.Windows.Media.SolidColorBrush>, które nie zarejestrowały jego nazwy z <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>lub nie została użyta do ustawienia właściwości <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>.

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>Jak zastosować animacje z Scenorysem

Aby użyć <xref:System.Windows.Media.Animation.Storyboard> do organizowania i stosowania animacji, należy dodać animacje jako podrzędne osie czasu <xref:System.Windows.Media.Animation.Storyboard>. Klasa <xref:System.Windows.Media.Animation.Storyboard> udostępnia właściwości dołączone <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType>. Te właściwości można ustawić dla animacji, aby określić jej obiekt docelowy i właściwość.

Aby zastosować animacje do ich obiektów docelowych, należy rozpocząć <xref:System.Windows.Media.Animation.Storyboard> przy użyciu akcji wyzwalacza lub metody. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]należy użyć obiektu <xref:System.Windows.Media.Animation.BeginStoryboard> z <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>lub <xref:System.Windows.DataTrigger>. W kodzie można również użyć metody <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.

W poniższej tabeli przedstawiono różne miejsca, w których każda <xref:System.Windows.Media.Animation.Storyboard> technika begin jest obsługiwana: na wystąpienie, styl, szablon formantu i szablon danych. "Na wystąpienie" odnosi się do techniki stosowania animacji lub scenorysu bezpośrednio do wystąpień obiektu, a nie w stylu, szablonie kontrolki lub szablonie danych.

|Trwa Rozpoczynanie korzystania z scenorysu...|Na wystąpienie|Styl|Szablon kontrolki|Szablon danych|Przykład|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard> i <xref:System.Windows.EventTrigger>|Tak|Tak|Tak|Tak|[Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard> i Właściwość <xref:System.Windows.Trigger>|Nie|Tak|Tak|Tak|[Wyzwalanie animacji w przypadku zmiany wartości właściwości](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard> i <xref:System.Windows.DataTrigger>|Nie|Tak|Tak|Tak|[Instrukcje: wyzwalanie animacji w przypadku zmiany danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|Metoda <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Tak|Nie|Nie|Nie|[Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md)|

W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Storyboard> do animowania <xref:System.Windows.FrameworkElement.Width%2A> elementu <xref:System.Windows.Shapes.Rectangle> i <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> użytego do malowania <xref:System.Windows.Shapes.Rectangle>.

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

W poniższych sekcjach opisano <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> dołączone właściwości bardziej szczegółowo.

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Elementy platformy docelowej, elementy zawartości struktury i obiektów Freezable platformie

W poprzedniej sekcji wymienionej przez, aby uzyskać animację, aby znaleźć jej obiekt docelowy, musi znać nazwę obiektu docelowego i właściwość do animacji. Określanie właściwości do animacji jest proste do przodu: po prostu ustaw <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> z nazwą właściwości do animacji.  Należy określić nazwę obiektu, którego właściwość ma być animowana przez ustawienie właściwości <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> animacji.

Aby Właściwość <xref:System.Windows.Setter.TargetName%2A> działała, obiekt Target musi mieć nazwę. Przypisanie nazwy do <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest inne niż przypisanie nazwy do obiektu <xref:System.Windows.Freezable>.

Elementy struktury są tymi klasami, które dziedziczą z klasy <xref:System.Windows.FrameworkElement>. Przykłady elementów struktury obejmują <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>i <xref:System.Windows.Shapes.Rectangle>. Zasadniczo wszystkie okna, panele i kontrolki są elementami. Elementy zawartości struktury są tymi klasami, które dziedziczą z klasy <xref:System.Windows.FrameworkContentElement>. Przykłady elementów zawartości platformy obejmują <xref:System.Windows.Documents.FlowDocument> i <xref:System.Windows.Documents.Paragraph>. Jeśli nie masz pewności, czy typem jest element struktury lub element zawartości platformy, sprawdź, czy ma on Właściwość Name. Jeśli tak, jest to prawdopodobnie element struktury lub element zawartości platformy. Aby się upewnić, sprawdź sekcję Hierarchia dziedziczenia na stronie Typ.

Aby włączyć Określanie wartości docelowej elementu Framework lub elementu zawartości Framework w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy ustawić jego właściwość <xref:System.Windows.FrameworkElement.Name%2A>. W kodzie, należy również użyć metody <xref:System.Windows.NameScope.RegisterName%2A> do zarejestrowania nazwy elementu z elementem, dla którego utworzono <xref:System.Windows.NameScope>.

Poniższy przykład, który został pobrany z poprzedniego przykładu, przypisuje nazwę `MyRectangle` <xref:System.Windows.Shapes.Rectangle>, typu <xref:System.Windows.FrameworkElement>.

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

Po jego nazwie można animować Właściwość tego elementu.

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

typy <xref:System.Windows.Freezable> są tymi klasami, które dziedziczą z klasy <xref:System.Windows.Freezable>. Przykłady <xref:System.Windows.Freezable> obejmują <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>i <xref:System.Windows.Media.GradientStop>.

Aby włączyć Określanie wartości docelowej <xref:System.Windows.Freezable> przez animację w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy użyć [dyrektywy x:Name](../../../desktop-wpf/xaml-services/xname-directive.md) w celu przypisania jej nazwy. W kodzie można użyć metody <xref:System.Windows.NameScope.RegisterName%2A>, aby zarejestrować jej nazwę z elementem, dla którego utworzono <xref:System.Windows.NameScope>.

Poniższy przykład przypisuje nazwę do obiektu <xref:System.Windows.Freezable>.

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

Obiekt może być następnie wskazywany przez animację.

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

obiekty <xref:System.Windows.Media.Animation.Storyboard> używają zakresów nazw do rozpoznawania właściwości <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>. Aby uzyskać więcej informacji na temat zakresów nazw WPF, zobacz [WPF XAML Zakresy nazw WPF](../advanced/wpf-xaml-namescopes.md). Jeśli właściwość <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> zostanie pominięta, animacja odwołuje się do elementu, w którym jest zdefiniowany, lub, w przypadku stylów, elementu style.

Czasami nie można przypisać nazwy do obiektu <xref:System.Windows.Freezable>. Na przykład jeśli <xref:System.Windows.Freezable> jest zadeklarowana jako zasób lub używana do ustawiania wartości właściwości w stylu, nie może mieć nazwy. Ponieważ nie ma nazwy, nie może być wskazywany bezpośrednio, ale może być wskazywany pośrednio. W poniższych sekcjach opisano sposób używania pośredniego określania wartości docelowej.

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>Pośrednie Określanie wartości docelowej

Czasami <xref:System.Windows.Freezable> nie mogą być wskazywane bezpośrednio przez animację, na przykład gdy <xref:System.Windows.Freezable> jest zadeklarowana jako zasób lub używana do ustawiania wartości właściwości w stylu. W takich przypadkach, mimo że nie można skierować go bezpośrednio do niego, nadal można animować obiekt <xref:System.Windows.Freezable>. Zamiast ustawiania właściwości <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> o nazwie <xref:System.Windows.Freezable>, nadaj jej nazwę elementu, do którego należy <xref:System.Windows.Freezable> ". Na przykład <xref:System.Windows.Media.SolidColorBrush> używany do ustawiania <xref:System.Windows.Shapes.Shape.Fill%2A> elementu Rectangle należy do tego prostokąta. Aby animować pędzla, należy ustawić <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> animacji z łańcuchem właściwości, które zaczynają się od właściwości elementu Framework lub elementu zawartości platformy, <xref:System.Windows.Freezable> został użyty do ustawienia i zakończenia właściwości <xref:System.Windows.Freezable> do animacji.

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

Należy pamiętać, że jeśli <xref:System.Windows.Freezable> jest zamrożona, zostanie utworzony klon, a klon zostanie animowany. W takim przypadku Właściwość <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> oryginalnego obiektu nadal zwraca `false`, ponieważ oryginalny obiekt nie jest w rzeczywistości animowany. Aby uzyskać więcej informacji na temat klonowania, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).

Należy również zauważyć, że w przypadku używania określania wartości docelowej właściwości pośredniej możliwe jest obiekty docelowe, które nie istnieją. Na przykład można założyć, że <xref:System.Windows.Controls.Control.Background%2A> określonego przycisku został ustawiony z <xref:System.Windows.Media.SolidColorBrush> i spróbować animować jego kolor, gdy w rzeczywistości <xref:System.Windows.Media.LinearGradientBrush> został użyty do ustawienia tła przycisku. W takich przypadkach nie jest zgłaszany żaden wyjątek; Animacja nie może mieć widocznego efektu, ponieważ <xref:System.Windows.Media.LinearGradientBrush> nie reaguje na zmiany właściwości <xref:System.Windows.Media.SolidColorBrush.Color%2A>.

W poniższych sekcjach szczegółowo opisano składnię określania wartości docelowej właściwości pośredniej.

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Pośrednie Określanie wartości właściwości Freezable w języku XAML

Aby określić właściwość elementu Freezable w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj następującej składni.

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Gdzie

- *ElementPropertyName* jest właściwością <xref:System.Windows.FrameworkElement>, do której <xref:System.Windows.Freezable> służy do ustawiania, i

- *FreezablePropertyName* jest właściwością <xref:System.Windows.Freezable> do animowania.

Poniższy kod ilustruje sposób animowania <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> używany do ustawiania <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta.

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

Czasami musisz wskazać Freezable zawarty w kolekcji lub tablicy.

Aby określić element docelowy Freezable zawarty w kolekcji, należy użyć następującej składni ścieżki.

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

Gdzie *CollectionIndex* jest indeksem obiektu w jego tablicy lub kolekcji.

Załóżmy na przykład, że prostokąt ma zastosowany zasób <xref:System.Windows.Media.TransformGroup> do jego właściwości <xref:System.Windows.UIElement.RenderTransform%2A> i chcesz animować jedną z przekształceń, która zawiera.

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

Poniższy kod ilustruje sposób animowania właściwości <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform> pokazanej w poprzednim przykładzie.

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Pośrednie Określanie wartości docelowej właściwości Freezable w kodzie

W kodzie można utworzyć obiekt <xref:System.Windows.PropertyPath>. Podczas tworzenia <xref:System.Windows.PropertyPath>należy określić <xref:System.Windows.PropertyPath.Path%2A> i <xref:System.Windows.PropertyPath.PathParameters%2A>.

Aby utworzyć <xref:System.Windows.PropertyPath.PathParameters%2A>, należy utworzyć tablicę typu <xref:System.Windows.DependencyProperty>, która zawiera listę pól identyfikatora właściwości zależności. Pierwsze pole identyfikatora ma właściwość <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, że <xref:System.Windows.Freezable> jest używany do ustawiania. Pole następnego identyfikatora reprezentuje właściwość <xref:System.Windows.Freezable>, która ma być docelowa. Należy traktować go jako łańcuch właściwości, które łączą <xref:System.Windows.Freezable> z obiektem <xref:System.Windows.FrameworkElement>.

Poniżej znajduje się przykład łańcucha właściwości zależności, który jest przeznaczony dla <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> używany do ustawiania <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta.

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

Należy również określić <xref:System.Windows.PropertyPath.Path%2A>. <xref:System.Windows.PropertyPath.Path%2A> jest <xref:System.String>, który informuje <xref:System.Windows.PropertyPath.Path%2A> jak interpretować <xref:System.Windows.PropertyPath.PathParameters%2A>. Używa następującej składni.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|

Gdzie

- *OwnerPropertyArrayIndex* jest indeksem tablicy <xref:System.Windows.DependencyProperty>, która zawiera identyfikator właściwości obiektu <xref:System.Windows.FrameworkElement>, który <xref:System.Windows.Freezable> służy do ustawiania, i

- *FreezablePropertyArrayIndex* jest indeksem tablicy <xref:System.Windows.DependencyProperty>, która zawiera identyfikator właściwości docelowej.

Poniższy przykład pokazuje <xref:System.Windows.PropertyPath.Path%2A>, które mają towarzyszyć <xref:System.Windows.PropertyPath.PathParameters%2A> zdefiniowanym w poprzednim przykładzie.

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

Poniższy przykład łączy kod w poprzednich przykładach, aby animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> używane do ustawiania <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta.

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

Czasami musisz wskazać Freezable zawarty w kolekcji lub tablicy. Załóżmy na przykład, że prostokąt ma zastosowany zasób <xref:System.Windows.Media.TransformGroup> do jego właściwości <xref:System.Windows.UIElement.RenderTransform%2A> i chcesz animować jedną z przekształceń, która zawiera.

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

Aby określić <xref:System.Windows.Freezable>, które znajdują się w kolekcji, należy użyć następującej składni ścieżki.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|

Gdzie *CollectionIndex* jest indeksem obiektu w jego tablicy lub kolekcji.

Aby określić właściwość <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform>, drugi przekształcenie w <xref:System.Windows.Media.TransformGroup>, użyj następujących <xref:System.Windows.PropertyPath.Path%2A> i <xref:System.Windows.PropertyPath.PathParameters%2A>.

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

Poniższy przykład przedstawia pełen kod animowania <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform> zawartej w <xref:System.Windows.Media.TransformGroup>.

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Pośrednie kierowanie przy użyciu Freezable jako punktu początkowego

W poprzednich sekcjach opisano sposób pośredniego ukierunkowania <xref:System.Windows.Freezable> przez rozpoczęcie od <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> i utworzenie łańcucha właściwości do <xref:System.Windows.Freezable> podrzędnej właściwości. Można również użyć <xref:System.Windows.Freezable> jako punktu początkowego i pośrednio, który jest elementem podrzędnym jednej z <xref:System.Windows.Freezable> jego właściwości podrzędnych. Jedno dodatkowe ograniczenie ma zastosowanie w przypadku używania <xref:System.Windows.Freezable> jako punktu początkowego dla pośredniego określania docelowej: <xref:System.Windows.Freezable> początkowy i każdy <xref:System.Windows.Freezable> między nim a niezależną podrzędną podwłaściwością nie może być zablokowany.

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Interaktywna kontrola scenorysu w języku XAML

Aby uruchomić scenorys w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], należy użyć akcji wyzwalacza <xref:System.Windows.Media.Animation.BeginStoryboard>. <xref:System.Windows.Media.Animation.BeginStoryboard> dystrybuuje animacje do obiektów i właściwości, które są animowane, i uruchamia scenorys. (Aby uzyskać szczegółowe informacje o tym procesie, zobacz [Omówienie animacji i systemu chronometrażu](animation-and-timing-system-overview.md)). W przypadku nadania <xref:System.Windows.Media.Animation.BeginStoryboard> nazwą przez określenie jej właściwości <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> można ją przetworzyć na scenorys. Następnie możesz interaktywnie kontrolować scenorys po jego uruchomieniu. Poniżej znajduje się lista kontrolowanych akcji scenorysu, które są używane z wyzwalaczami zdarzeń do kontrolowania scenorysu.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: wstrzymuje scenorys.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: wznawia wstrzymany scenorys.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: zmienia szybkość scenorysu.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: przesuwa scenorys do końca okresu wypełnienia, jeśli go zawiera.

- <xref:System.Windows.Media.Animation.StopStoryboard>: powoduje zatrzymanie scenorysu.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: usuwa scenorys.

W poniższym przykładzie akcje z kontrolowanego scenorysu są używane do interaktywnego sterowania scenorysem.

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Interaktywna kontrola scenorysu przy użyciu kodu

Poprzednie przykłady pokazują, jak animować przy użyciu akcji wyzwalacza. W kodzie można również kontrolować scenorys przy użyciu interaktywnych metod klasy <xref:System.Windows.Media.Animation.Storyboard>. Aby <xref:System.Windows.Media.Animation.Storyboard> był interaktywny w kodzie, należy użyć odpowiedniego przeciążenia metody <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> scenorysu i określić `true`, aby można było go sterować. Aby uzyskać więcej informacji, zobacz stronę <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>.

Na poniższej liście przedstawiono metody, których można użyć do manipulowania <xref:System.Windows.Media.Animation.Storyboard> po jego rozpoczęciu:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

Zalety korzystania z tych metod polegają na tym, że nie trzeba tworzyć obiektów <xref:System.Windows.Trigger> ani <xref:System.Windows.TriggerAction>; Wystarczy tylko do kontrolowanego <xref:System.Windows.Media.Animation.Storyboard>, które chcesz manipulować.

> [!NOTE]
> Wszystkie interaktywne akcje wykonywane na <xref:System.Windows.Media.Animation.Clock>, w związku z czym również na <xref:System.Windows.Media.Animation.Storyboard> będą wykonywane na następnym taktie aparatu czasu, który będzie wkrótce przed następnym renderowaniem. Na przykład, jeśli używasz metody <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>, aby przeskoczyć do innego punktu w animacji, wartość właściwości nie zmienia się natychmiast, a zmiana wartości w następnym taktie aparatu czasu.

Poniższy przykład pokazuje, jak zastosować i kontrolować animacje przy użyciu interaktywnych metod klasy <xref:System.Windows.Media.Animation.Storyboard>.

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>Animuj w stylu

Za pomocą obiektów <xref:System.Windows.Media.Animation.Storyboard> można definiować animacje w <xref:System.Windows.Style>. Animowanie przy użyciu <xref:System.Windows.Media.Animation.Storyboard> w <xref:System.Windows.Style> jest podobne do <xref:System.Windows.Media.Animation.Storyboard> w innym miejscu, z następującymi trzema wyjątkami:

- Nie określisz <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; <xref:System.Windows.Media.Animation.Storyboard> zawsze odwołuje się do elementu, do którego zostanie zastosowany <xref:System.Windows.Style>. Aby docelowa była <xref:System.Windows.Freezable> obiektów, należy użyć pośredniego określania wartości docelowej. Aby uzyskać więcej informacji na temat pośredniego określania wartości docelowej, zobacz sekcję [Określanie wartości docelowej](#pathsyntaxforchangeable) .

- Nie można określić <xref:System.Windows.EventTrigger.SourceName%2A> dla <xref:System.Windows.EventTrigger> lub <xref:System.Windows.Trigger>.

- Nie można używać odwołań do zasobów dynamicznych ani wyrażeń powiązań danych do ustawiania wartości właściwości <xref:System.Windows.Media.Animation.Storyboard> lub animacji. Dzieje się tak dlatego, że wszystkie elementy wewnątrz <xref:System.Windows.Style> muszą być bezpieczne wątkowo, a system chronometrażu musi <xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard> obiektów, aby zapewnić ich bezpieczny wątkowo. Nie można zamrozić <xref:System.Windows.Media.Animation.Storyboard>, jeśli lub jego podrzędne osie czasu zawierają odwołania do zasobów dynamicznych lub wyrażenia powiązań danych. Aby uzyskać więcej informacji na temat zamrażania i innych funkcji <xref:System.Windows.Freezable>, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).

- W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nie można zadeklarować obsługi zdarzeń dla zdarzeń <xref:System.Windows.Media.Animation.Storyboard> lub animacji.

Przykład przedstawiający sposób definiowania scenorysu w stylu można znaleźć w przykładzie [animacji w stylu](how-to-animate-in-a-style.md) .

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>Animuj w ControlTemplate

Za pomocą obiektów <xref:System.Windows.Media.Animation.Storyboard> można definiować animacje w <xref:System.Windows.Controls.ControlTemplate>. Animowanie przy użyciu <xref:System.Windows.Media.Animation.Storyboard> w <xref:System.Windows.Controls.ControlTemplate> jest podobne do <xref:System.Windows.Media.Animation.Storyboard> w innym miejscu, z następującymi dwoma wyjątkami:

- <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> może odwoływać się tylko do obiektów podrzędnych <xref:System.Windows.Controls.ControlTemplate>. Jeśli <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> nie zostanie określony, animacja będzie odnosił się do elementu, do którego zostanie zastosowany <xref:System.Windows.Controls.ControlTemplate>.

- <xref:System.Windows.EventTrigger.SourceName%2A> dla <xref:System.Windows.EventTrigger> lub <xref:System.Windows.Trigger> może odwoływać się tylko do obiektów podrzędnych <xref:System.Windows.Controls.ControlTemplate>.

- Nie można używać odwołań do zasobów dynamicznych ani wyrażeń powiązań danych do ustawiania wartości właściwości <xref:System.Windows.Media.Animation.Storyboard> lub animacji. Dzieje się tak dlatego, że wszystkie elementy wewnątrz <xref:System.Windows.Controls.ControlTemplate> muszą być bezpieczne wątkowo, a system chronometrażu musi <xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard> obiektów, aby zapewnić ich bezpieczny wątkowo. Nie można zamrozić <xref:System.Windows.Media.Animation.Storyboard>, jeśli lub jego podrzędne osie czasu zawierają odwołania do zasobów dynamicznych lub wyrażenia powiązań danych. Aby uzyskać więcej informacji na temat zamrażania i innych funkcji <xref:System.Windows.Freezable>, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).

- W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nie można zadeklarować obsługi zdarzeń dla zdarzeń <xref:System.Windows.Media.Animation.Storyboard> lub animacji.

Aby zapoznać się z przykładem dotyczącym definiowania scenorysu w <xref:System.Windows.Controls.ControlTemplate>, zobacz [animację w ControlTemplate](how-to-animate-in-a-controltemplate.md) przykładzie.

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>Animuj po zmianie wartości właściwości

W stylach i szablonach formantów można używać obiektów wyzwalaczy do uruchamiania scenorysu podczas zmiany właściwości. Aby zapoznać się z przykładami, zobacz [wyzwalanie animacji, gdy wartość właściwości zmieni](how-to-trigger-an-animation-when-a-property-value-changes.md) się i [Animuj w ControlTemplate](how-to-animate-in-a-controltemplate.md).

Animacje stosowane przez obiekty <xref:System.Windows.Trigger> właściwości zachowują się w sposób bardziej skomplikowany niż <xref:System.Windows.EventTrigger> animacje lub animacje rozpoczęte przy użyciu metod <xref:System.Windows.Media.Animation.Storyboard>.  Są one "przekazanie" animacją zdefiniowaną przez inne obiekty <xref:System.Windows.Trigger>, ale tworzą z animacją <xref:System.Windows.EventTrigger> i wyzwalaną metodami.

## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
- [Techniki animacji właściwości — przegląd](property-animation-techniques-overview.md)
- [Przegląd obiektów Freezable](../advanced/freezable-objects-overview.md)
