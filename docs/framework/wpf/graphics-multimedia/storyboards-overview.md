---
title: Przegląd Scenorysy
desription: Organize and apply animations in storyboards. Use property-targeting syntax and combine timelines in Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 50f45953da3801bf73016c09b78a6a1b54878bc0
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853636"
---
# <a name="storyboards-overview"></a>Przegląd Scenorysy

W tym temacie pokazano, jak używać <xref:System.Windows.Media.Animation.Storyboard> obiektów do organizowania i stosowania animacji. Opisano w nim sposób interakcyjnego manipulowania <xref:System.Windows.Media.Animation.Storyboard> obiektami i opisywania składni docelowej właściwości.

## <a name="prerequisites"></a>Wymagania wstępne

Aby zrozumieć ten temat, należy zapoznać się z różnymi typami animacji i ich podstawowymi funkcjami. Aby zapoznać się z wprowadzeniem do animacji, zobacz [Omówienie animacji](animation-overview.md). Należy również wiedzieć, jak używać dołączonych właściwości. Aby uzyskać więcej informacji na temat dołączonych właściwości, zobacz [Omówienie dołączonych właściwości](../advanced/attached-properties-overview.md).

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>Co to jest scenorys?

Animacje nie są jedynym przydatnym typem osi czasu. Podane są inne klasy osi czasu, które ułatwiają organizowanie zestawów osi czasu oraz stosowanie osi czasu do właściwości. Osie czasu kontenera pochodzą od <xref:System.Windows.Media.Animation.TimelineGroup> klasy i obejmują <xref:System.Windows.Media.Animation.ParallelTimeline> i <xref:System.Windows.Media.Animation.Storyboard> .

A <xref:System.Windows.Media.Animation.Storyboard> to typ osi czasu kontenera, który zawiera informacje dotyczące określania docelowych osi czasu, które zawiera. Scenorys może zawierać dowolnego typu, w <xref:System.Windows.Media.Animation.Timeline> tym inne osie czasu kontenera i animacje. <xref:System.Windows.Media.Animation.Storyboard>obiekty umożliwiają łączenie osi czasu, które mają wpływ na wiele obiektów i właściwości na jedno drzewo osi czasu, co ułatwia organizowanie i kontrolowanie złożonych zachowań chronometrażu. Załóżmy na przykład, że chcesz, aby przycisk przerobił te trzy rzeczy.

- Powiększ i Zmień kolor, gdy użytkownik wybierze przycisk.

- Po kliknięciu Zmniejsz rozmiar do oryginalnego rozmiaru.

- Zmniejsz i zwiększ poziom przezroczystości do 50 procent, gdy zostanie on wyłączony.

W takim przypadku istnieje wiele zestawów animacji, które mają zastosowanie do tego samego obiektu i chcesz odtwarzać w różnych godzinach zależnie od stanu przycisku. <xref:System.Windows.Media.Animation.Storyboard>obiekty umożliwiają organizowanie animacji i stosowanie ich w grupach do co najmniej jednego obiektu.

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>Gdzie można używać scenorysu?

A <xref:System.Windows.Media.Animation.Storyboard> może służyć do animowania właściwości zależności klas animowanych (Aby uzyskać więcej informacji na temat tego, co ułatwia animowanie klasy, zobacz [Omówienie animacji](animation-overview.md)). Jednak ponieważ scenorysowanie jest funkcją poziomu platformy, obiekt musi należeć do <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> .

Na przykład można użyć, <xref:System.Windows.Media.Animation.Storyboard> Aby wykonać następujące czynności:

- Animuj a <xref:System.Windows.Media.SolidColorBrush> (element inny niż Framework), który maluje tło przycisku (typ <xref:System.Windows.FrameworkElement> ),

- Animuj a <xref:System.Windows.Media.SolidColorBrush> (element niebędący strukturą), który maluje wypełnienie <xref:System.Windows.Media.GeometryDrawing> (element inny niż Framework) wyświetlany przy użyciu <xref:System.Windows.Controls.Image> ( <xref:System.Windows.FrameworkElement> ).

- W kodzie, Animuj obiekt <xref:System.Windows.Media.SolidColorBrush> zadeklarowany przez klasę, która również zawiera <xref:System.Windows.FrameworkElement> , jeśli <xref:System.Windows.Media.SolidColorBrush> zarejestrowano jej nazwę <xref:System.Windows.FrameworkElement> .

Nie można jednak użyć <xref:System.Windows.Media.Animation.Storyboard> do animacji <xref:System.Windows.Media.SolidColorBrush> , która nie zarejestrowała jego nazwy z <xref:System.Windows.FrameworkElement> lub lub <xref:System.Windows.FrameworkContentElement> nie została użyta do ustawienia właściwości <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> .

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>Jak zastosować animacje z Scenorysem

Aby użyć programu <xref:System.Windows.Media.Animation.Storyboard> do organizowania i stosowania animacji, należy dodać animacje jako podrzędne osie czasu <xref:System.Windows.Media.Animation.Storyboard> . <xref:System.Windows.Media.Animation.Storyboard>Klasa zawiera <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> właściwości i dołączone. Te właściwości można ustawić dla animacji, aby określić jej obiekt docelowy i właściwość.

Aby zastosować animacje do ich elementów docelowych, należy rozpocząć <xref:System.Windows.Media.Animation.Storyboard> Korzystanie z akcji wyzwalacza lub metody. W programie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używasz <xref:System.Windows.Media.Animation.BeginStoryboard> obiektu z <xref:System.Windows.EventTrigger> , <xref:System.Windows.Trigger> lub <xref:System.Windows.DataTrigger> . W kodzie można również użyć <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody.

W poniższej tabeli przedstawiono różne miejsca, w których <xref:System.Windows.Media.Animation.Storyboard> jest obsługiwana każda technika BEGIN: na wystąpienie, styl, szablon formantu i szablon danych. "Na wystąpienie" odnosi się do techniki stosowania animacji lub scenorysu bezpośrednio do wystąpień obiektu, a nie w stylu, szablonie kontrolki lub szablonie danych.

|Trwa Rozpoczynanie korzystania z scenorysu...|Na wystąpienie|Styl|Szablon kontrolki|Szablon danych|Przykład|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard>i<xref:System.Windows.EventTrigger>|Tak|Tak|Tak|Tak|[Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>i właściwość<xref:System.Windows.Trigger>|Nie|Tak|Tak|Tak|[Wyzwalanie animacji w przypadku zmiany wartości właściwości](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>i a<xref:System.Windows.DataTrigger>|Nie|Tak|Tak|Tak|[Instrukcje: wyzwalanie animacji w przypadku zmiany danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|Metoda <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Yes|Nie|Nie|Nie|[Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md)|

W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Storyboard> do animowania <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> elementu i obiektu <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> używanego do malowania <xref:System.Windows.Shapes.Rectangle> .

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

W poniższych sekcjach opisano <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> dołączono właściwości bardziej szczegółowo.

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Elementy platformy docelowej, elementy zawartości struktury i obiektów Freezable platformie

W poprzedniej sekcji wymienionej przez, aby uzyskać animację, aby znaleźć jej obiekt docelowy, musi znać nazwę obiektu docelowego i właściwość do animacji. Określanie właściwości do animacji jest proste do przodu: po prostu ustaw <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> nazwę właściwości do animacji.  Należy określić nazwę obiektu, którego właściwość ma być animowana przez ustawienie <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> właściwości animacji.

Aby <xref:System.Windows.Setter.TargetName%2A> Właściwość działała, obiekt Target musi mieć nazwę. Przypisanie nazwy do <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest inne niż przypisanie nazwy do <xref:System.Windows.Freezable> obiektu.

Elementy struktury są tymi klasami, które dziedziczą z <xref:System.Windows.FrameworkElement> klasy. Przykłady elementów struktury obejmują <xref:System.Windows.Window> , <xref:System.Windows.Controls.DockPanel> , <xref:System.Windows.Controls.Button> , i <xref:System.Windows.Shapes.Rectangle> . Zasadniczo wszystkie okna, panele i kontrolki są elementami. Elementy zawartości struktury są tymi klasami, które dziedziczą z <xref:System.Windows.FrameworkContentElement> klasy. Przykłady elementów zawartości struktury obejmują <xref:System.Windows.Documents.FlowDocument> i <xref:System.Windows.Documents.Paragraph> . Jeśli nie masz pewności, czy typem jest element struktury lub element zawartości platformy, sprawdź, czy ma on Właściwość Name. Jeśli tak, jest to prawdopodobnie element struktury lub element zawartości platformy. Aby się upewnić, sprawdź sekcję Hierarchia dziedziczenia na stronie Typ.

Aby włączyć Określanie wartości docelowej elementu Framework lub elementu zawartości Framework w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , należy ustawić jego <xref:System.Windows.FrameworkElement.Name%2A> Właściwość. W kodzie, należy również użyć <xref:System.Windows.NameScope.RegisterName%2A> metody do zarejestrowania nazwy elementu z elementem, dla którego został utworzony <xref:System.Windows.NameScope> .

Poniższy przykład, który został pobrany z poprzedniego przykładu, przypisuje nazwę `MyRectangle` a <xref:System.Windows.Shapes.Rectangle> , typ <xref:System.Windows.FrameworkElement> .

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

Po jego nazwie można animować Właściwość tego elementu.

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

<xref:System.Windows.Freezable>typy są tymi klasami, które dziedziczą z <xref:System.Windows.Freezable> klasy. Przykłady <xref:System.Windows.Freezable> include <xref:System.Windows.Media.SolidColorBrush> , <xref:System.Windows.Media.RotateTransform> i <xref:System.Windows.Media.GradientStop> .

Aby włączyć Określanie wartości docelowej <xref:System.Windows.Freezable> przez animację w programie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , należy użyć [dyrektywy x:Name](../../../desktop-wpf/xaml-services/xname-directive.md) w celu przypisania jej nazwy. W kodzie, używasz <xref:System.Windows.NameScope.RegisterName%2A> metody do rejestrowania jej nazwy z elementem, dla którego został utworzony <xref:System.Windows.NameScope> .

Poniższy przykład przypisuje nazwę do <xref:System.Windows.Freezable> obiektu.

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

Obiekt może być następnie wskazywany przez animację.

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

<xref:System.Windows.Media.Animation.Storyboard>obiekty używają zakresów nazw do rozpoznawania <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> właściwości. Aby uzyskać więcej informacji na temat zakresów nazw WPF, zobacz [WPF XAML Zakresy nazw WPF](../advanced/wpf-xaml-namescopes.md). Jeśli <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Właściwość zostanie pominięta, animacja odwołuje się do elementu, w którym jest zdefiniowany, lub, w przypadku stylów, elementu style.

Czasami nazwa nie może być przypisana do <xref:System.Windows.Freezable> obiektu. Na przykład jeśli obiekt <xref:System.Windows.Freezable> jest zadeklarowany jako zasób lub używany do ustawiania wartości właściwości w stylu, nie może mieć nazwy. Ponieważ nie ma nazwy, nie może być wskazywany bezpośrednio, ale może być wskazywany pośrednio. W poniższych sekcjach opisano sposób używania pośredniego określania wartości docelowej.

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>Pośrednie Określanie wartości docelowej

Istnieją przypadki, w których <xref:System.Windows.Freezable> nie mogą być wskazywane bezpośrednio przez animację, na przykład gdy <xref:System.Windows.Freezable> jest zadeklarowany jako zasób lub używany do ustawiania wartości właściwości w stylu. W takich przypadkach, mimo że nie można kierować do niego bezpośrednio, można nadal animować <xref:System.Windows.Freezable> obiekt. Zamiast ustawić <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Właściwość o nazwie <xref:System.Windows.Freezable> , nadaj jej nazwę elementu, do którego <xref:System.Windows.Freezable> należy ". Na przykład, <xref:System.Windows.Media.SolidColorBrush> używany do ustawiania <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta należy do tego prostokąta. Aby animować pędzla, należy ustawić animację <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> z łańcuchem właściwości, które zaczynają się od właściwości elementu Framework lub elementu zawartości platformy, który <xref:System.Windows.Freezable> został użyty do ustawienia i zakończenia <xref:System.Windows.Freezable> właściwości do animacji.

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

Należy pamiętać, że jeśli <xref:System.Windows.Freezable> jest zablokowany, zostanie utworzony klon, a klon zostanie animowany. Gdy tak się stanie, właściwość oryginalnego obiektu <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> będzie nadal zwracana `false` , ponieważ oryginalny obiekt nie jest w rzeczywistości animowany. Aby uzyskać więcej informacji na temat klonowania, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).

Należy również zauważyć, że w przypadku używania określania wartości docelowej właściwości pośredniej możliwe jest obiekty docelowe, które nie istnieją. Na przykład można założyć, że <xref:System.Windows.Controls.Control.Background%2A> określony przycisk został ustawiony z <xref:System.Windows.Media.SolidColorBrush> i próbować animować jego kolor, gdy w rzeczywistości <xref:System.Windows.Media.LinearGradientBrush> użyto do ustawienia tła przycisku. W takich przypadkach nie jest zgłaszany żaden wyjątek; Animacja nie może mieć widocznego efektu, ponieważ nie <xref:System.Windows.Media.LinearGradientBrush> reaguje na zmiany <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwości.

W poniższych sekcjach szczegółowo opisano składnię określania wartości docelowej właściwości pośredniej.

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Pośrednie Określanie wartości właściwości Freezable w języku XAML

Aby określić właściwość elementu Freezable w, należy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] użyć następującej składni.

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Lokalizacja

- *ElementPropertyName* jest właściwością, <xref:System.Windows.FrameworkElement> która <xref:System.Windows.Freezable> jest używana do ustawiania, i

- *FreezablePropertyName* jest właściwością elementu <xref:System.Windows.Freezable> do animacji.

Poniższy kod pokazuje, jak animować wartość <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> użytą do ustawienia <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta.

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

Czasami musisz wskazać Freezable zawarty w kolekcji lub tablicy.

Aby określić element docelowy Freezable zawarty w kolekcji, należy użyć następującej składni ścieżki.

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

Gdzie *CollectionIndex* jest indeksem obiektu w jego tablicy lub kolekcji.

Załóżmy na przykład, że prostokąt ma <xref:System.Windows.Media.TransformGroup> zastosowany zasób do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości, i chcesz animować jedną z przekształceń, która zawiera.

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

Poniższy kod przedstawia sposób animowania <xref:System.Windows.Media.RotateTransform.Angle%2A> właściwości <xref:System.Windows.Media.RotateTransform> pokazanej w poprzednim przykładzie.

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Pośrednie Określanie wartości docelowej właściwości Freezable w kodzie

W kodzie, tworzysz <xref:System.Windows.PropertyPath> obiekt. Podczas tworzenia należy <xref:System.Windows.PropertyPath> określić <xref:System.Windows.PropertyPath.Path%2A> i <xref:System.Windows.PropertyPath.PathParameters%2A> .

Aby utworzyć <xref:System.Windows.PropertyPath.PathParameters%2A> , należy utworzyć tablicę typu <xref:System.Windows.DependencyProperty> , która zawiera listę pól identyfikatora właściwości zależności. Pole pierwszego identyfikatora jest właściwością <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> , która <xref:System.Windows.Freezable> jest używana do ustawiania. Następne pole identyfikatora reprezentuje właściwość <xref:System.Windows.Freezable> elementu docelowego. Należy traktować go jako łańcuch właściwości, które łączą <xref:System.Windows.Freezable> się z <xref:System.Windows.FrameworkElement> obiektem.

Poniżej znajduje się przykład łańcucha właściwości zależności, który jest <xref:System.Windows.Media.SolidColorBrush.Color%2A> przeznaczony dla elementu typu prostokąt, który jest celem obiektu <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Shapes.Shape.Fill%2A> .

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

Należy również określić <xref:System.Windows.PropertyPath.Path%2A> . A <xref:System.Windows.PropertyPath.Path%2A> to to <xref:System.String> , który informuje, <xref:System.Windows.PropertyPath.Path%2A> jak interpretować <xref:System.Windows.PropertyPath.PathParameters%2A> . Używa następującej składni.

| |
|-|
|`(`*OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex*`)`|

Lokalizacja

- *OwnerPropertyArrayIndex* jest indeksem tablicy zawierającej <xref:System.Windows.DependencyProperty> Identyfikator <xref:System.Windows.FrameworkElement> właściwości obiektu, który <xref:System.Windows.Freezable> jest używany do ustawiania, i

- *FreezablePropertyArrayIndex* jest indeksem tablicy zawierającej <xref:System.Windows.DependencyProperty> Identyfikator właściwości docelowej.

W poniższym przykładzie pokazano, <xref:System.Windows.PropertyPath.Path%2A> że towarzyszy <xref:System.Windows.PropertyPath.PathParameters%2A> zdefiniowanej w poprzednim przykładzie.

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

Poniższy przykład łączy kod w poprzednich przykładach w celu animowania obiektu <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> używanego do ustawiania <xref:System.Windows.Shapes.Shape.Fill%2A> elementu prostokąta.

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

Czasami musisz wskazać Freezable zawarty w kolekcji lub tablicy. Załóżmy na przykład, że prostokąt ma <xref:System.Windows.Media.TransformGroup> zastosowany zasób do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości, i chcesz animować jedną z przekształceń, która zawiera.

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

Aby określić element docelowy <xref:System.Windows.Freezable> zawarty w kolekcji, należy użyć następującej składni ścieżki.

| |
|-|
|`(`*OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex*`)`|

Gdzie *CollectionIndex* jest indeksem obiektu w jego tablicy lub kolekcji.

Aby określić <xref:System.Windows.Media.RotateTransform.Angle%2A> Właściwość <xref:System.Windows.Media.RotateTransform> , drugie przekształcenie w <xref:System.Windows.Media.TransformGroup> , należy użyć następujących elementów <xref:System.Windows.PropertyPath.Path%2A> i <xref:System.Windows.PropertyPath.PathParameters%2A> .

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

Poniższy przykład pokazuje kompletny kod animacji elementu <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform> zawartego w elemencie <xref:System.Windows.Media.TransformGroup> .

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Pośrednie kierowanie przy użyciu Freezable jako punktu początkowego

W poprzednich sekcjach opisano, jak pośrednio skierować obiekt docelowy <xref:System.Windows.Freezable> , rozpoczynając od <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> i tworząc łańcuch właściwości do <xref:System.Windows.Freezable> Właściwości podrzędnej. Można również użyć <xref:System.Windows.Freezable> jako punktu początkowego i pośrednio docelowej jednej z jego <xref:System.Windows.Freezable> właściwości podrzędnych. Jedno dodatkowe ograniczenie ma zastosowanie w przypadku używania <xref:System.Windows.Freezable> jako punktu początkowego do pośredniego określania docelowej: początku <xref:System.Windows.Freezable> i co <xref:System.Windows.Freezable> między nim a bezpośrednią podklasą docelową nie może być zablokowany.

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Interaktywna kontrola scenorysu w języku XAML

Aby rozpocząć scenorys w programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , należy użyć <xref:System.Windows.Media.Animation.BeginStoryboard> akcji wyzwalacza. <xref:System.Windows.Media.Animation.BeginStoryboard>dystrybuuje animacje do obiektów i właściwości, które są animowane, i uruchamia scenorys. (Aby uzyskać szczegółowe informacje o tym procesie, zobacz [Omówienie animacji i systemu chronometrażu](animation-and-timing-system-overview.md)). W przypadku nadania <xref:System.Windows.Media.Animation.BeginStoryboard> nazwy przez określenie jej <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> właściwości można ją przetworzyć w scenorysie. Następnie możesz interaktywnie kontrolować scenorys po jego uruchomieniu. Poniżej znajduje się lista kontrolowanych akcji scenorysu, które są używane z wyzwalaczami zdarzeń do kontrolowania scenorysu.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Wstrzymuje scenorys.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Wznawia wstrzymanie scenorysu.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Zmienia szybkość scenorysu.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Przesuwa scenorys do końca okresu wypełnienia, jeśli go zawiera.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Powoduje zatrzymanie scenorysu.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Usuwa scenorys.

W poniższym przykładzie akcje z kontrolowanego scenorysu są używane do interaktywnego sterowania scenorysem.

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Interaktywna kontrola scenorysu przy użyciu kodu

Poprzednie przykłady pokazują, jak animować przy użyciu akcji wyzwalacza. W kodzie można również kontrolować scenorys przy użyciu interaktywnych metod <xref:System.Windows.Media.Animation.Storyboard> klasy. Aby <xref:System.Windows.Media.Animation.Storyboard> można było interaktywnie wprowadzić kod, należy użyć odpowiedniego przeciążenia metody scenorysu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> i określić, `true` Aby umożliwić jej możliwość kontrolowania. <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>Aby uzyskać więcej informacji, zobacz stronę.

Na poniższej liście przedstawiono metody, których można użyć do manipulowania <xref:System.Windows.Media.Animation.Storyboard> po rozpoczęciu:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

Zalety korzystania z tych metod polegają na tym, że nie musisz <xref:System.Windows.Trigger> tworzyć <xref:System.Windows.TriggerAction> obiektów lub obiekty; wystarczy tylko do kontroli, <xref:System.Windows.Media.Animation.Storyboard> którą chcesz manipulować.

> [!NOTE]
> Wszystkie interaktywne akcje wykonywane w systemie <xref:System.Windows.Media.Animation.Clock> , a tym samym również w <xref:System.Windows.Media.Animation.Storyboard> odniesieniu do następnego taktu aparatu czasu, które będą miały miejsce wkrótce przed następnym renderowaniem. Na przykład, jeśli używasz <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody do przechodzenia do innego punktu w animacji, wartość właściwości nie zmienia się natychmiast, a wartość zmienia się w następnym taktie aparatu czasu.

Poniższy przykład pokazuje, jak zastosować i kontrolować animacje przy użyciu interaktywnych metod <xref:System.Windows.Media.Animation.Storyboard> klasy.

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>Animuj w stylu

Można używać <xref:System.Windows.Media.Animation.Storyboard> obiektów do definiowania animacji w <xref:System.Windows.Style> . Animowanie przy użyciu <xref:System.Windows.Media.Animation.Storyboard> w <xref:System.Windows.Style> i jest podobne do użycia w <xref:System.Windows.Media.Animation.Storyboard> innym miejscu, z następującymi trzema wyjątkami:

- Nie określono <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> elementu; zawsze jest to <xref:System.Windows.Media.Animation.Storyboard> element, do którego <xref:System.Windows.Style> zastosowano. Aby obiekty docelowe były obiektami docelowymi <xref:System.Windows.Freezable> , należy użyć pośredniego określania wartości docelowej. Aby uzyskać więcej informacji na temat pośredniego określania wartości docelowej, zobacz sekcję [Określanie wartości docelowej](#pathsyntaxforchangeable) .

- Nie można określić <xref:System.Windows.EventTrigger.SourceName%2A> dla elementu <xref:System.Windows.EventTrigger> lub <xref:System.Windows.Trigger> .

- Nie można używać odwołań do zasobów dynamicznych ani wyrażeń powiązań danych do ustawiania <xref:System.Windows.Media.Animation.Storyboard> lub animacji wartości właściwości. Dzieje się tak dlatego, że wszystko wewnątrz elementu <xref:System.Windows.Style> musi być bezpieczne wątkowo, a system chronometrażu musi <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> obiekty, aby uczynić je bezpiecznym wątkowo. <xref:System.Windows.Media.Animation.Storyboard>Nie można zamrozić, jeśli lub jego podrzędne osie czasu zawierają odwołania do zasobów dynamicznych lub wyrażenia powiązań danych. Aby uzyskać więcej informacji na temat zamrażania i innych <xref:System.Windows.Freezable> funkcji, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).

- W programie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie można zadeklarować programów obsługi zdarzeń dla <xref:System.Windows.Media.Animation.Storyboard> zdarzeń animacji ani.

Przykład przedstawiający sposób definiowania scenorysu w stylu można znaleźć w przykładzie [animacji w stylu](how-to-animate-in-a-style.md) .

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>Animuj w ControlTemplate

Można używać <xref:System.Windows.Media.Animation.Storyboard> obiektów do definiowania animacji w <xref:System.Windows.Controls.ControlTemplate> . Animowanie przy użyciu <xref:System.Windows.Media.Animation.Storyboard> w programie <xref:System.Windows.Controls.ControlTemplate> jest podobne do użycia w <xref:System.Windows.Media.Animation.Storyboard> innym miejscu, z następującymi dwoma wyjątkami:

- <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>Może odwoływać się tylko do obiektów podrzędnych obiektu <xref:System.Windows.Controls.ControlTemplate> . Jeśli <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> nie jest określony, animacja jest przeznaczona dla elementu, do którego <xref:System.Windows.Controls.ControlTemplate> jest stosowana.

- Element <xref:System.Windows.EventTrigger.SourceName%2A> for <xref:System.Windows.EventTrigger> a lub a <xref:System.Windows.Trigger> może odwoływać się tylko do obiektów podrzędnych obiektu <xref:System.Windows.Controls.ControlTemplate> .

- Nie można używać odwołań do zasobów dynamicznych ani wyrażeń powiązań danych do ustawiania <xref:System.Windows.Media.Animation.Storyboard> lub animacji wartości właściwości. Dzieje się tak dlatego, że wszystko wewnątrz elementu <xref:System.Windows.Controls.ControlTemplate> musi być bezpieczne wątkowo, a system chronometrażu musi <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> obiekty, aby uczynić je bezpiecznym wątkowo. <xref:System.Windows.Media.Animation.Storyboard>Nie można zamrozić, jeśli lub jego podrzędne osie czasu zawierają odwołania do zasobów dynamicznych lub wyrażenia powiązań danych. Aby uzyskać więcej informacji na temat zamrażania i innych <xref:System.Windows.Freezable> funkcji, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).

- W programie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie można zadeklarować programów obsługi zdarzeń dla <xref:System.Windows.Media.Animation.Storyboard> zdarzeń animacji ani.

Aby zapoznać się z przykładem dotyczącym definiowania scenorysu w <xref:System.Windows.Controls.ControlTemplate> , zobacz [Animuj w ControlTemplate](how-to-animate-in-a-controltemplate.md) przykładzie.

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>Animuj po zmianie wartości właściwości

W stylach i szablonach formantów można używać obiektów wyzwalaczy do uruchamiania scenorysu podczas zmiany właściwości. Aby zapoznać się z przykładami, zobacz [wyzwalanie animacji, gdy wartość właściwości zmieni](how-to-trigger-an-animation-when-a-property-value-changes.md) się i [Animuj w ControlTemplate](how-to-animate-in-a-controltemplate.md).

Animacje stosowane przez <xref:System.Windows.Trigger> obiekty właściwości zachowują się w sposób bardziej skomplikowany niż <xref:System.Windows.EventTrigger> animacje i animacje rozpoczęte przy użyciu <xref:System.Windows.Media.Animation.Storyboard> metod.  Są one "przekazanie" z animacjami zdefiniowanymi przez inne <xref:System.Windows.Trigger> obiekty, ale tworzą animacje z użyciem <xref:System.Windows.EventTrigger> metody i wyzwalane metodami.

## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja](animation-overview.md)
- [Przegląd Techniki animacji właściwości](property-animation-techniques-overview.md)
- [Przegląd Obiekty Freezable](../advanced/freezable-objects-overview.md)
