---
title: Przegląd Właściwości dołączone
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: bcf218efeb7bff5f7457164411efed796314ba82
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129483"
---
# <a name="attached-properties-overview"></a>Przegląd Właściwości dołączone

Dołączona właściwość to pojęcie z definicją XAML. Dołączona właściwość jest przeznaczona do użycia jako typ właściwości globalnych, które można ustawić dla dowolnego obiektu. W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], dołączone właściwości są zazwyczaj definiowane jako formą specjalistyczne właściwość zależności, która nie ma właściwości konwencjonalne "otoki".

## Wymagania wstępne <a name="prerequisites"></a>

W tym temacie założono, że rozumiesz właściwości zależności z punktu widzenia użytkownika istniejących właściwości zależności na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klasy, a po ich przeczytaniu [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Aby skorzystać z przykładów w tym temacie, należy również zrozumieć XAML i wiedzieć, jak pisać aplikacje WPF.

## Dlaczego warto korzystać z właściwości dołączone <a name="attached_properties_usage"></a>

Jeden cel dołączoną właściwość jest umożliwienie z różnych podrzędne elementy, aby określić unikatowe wartości dla właściwości, która faktycznie jest zdefiniowany w elemencie nadrzędnym. Określona aplikacja w tym scenariuszu ma elementy podrzędne, które powiadamia element nadrzędny, jak są przedstawiane w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Przykładem jest <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> właściwości. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Właściwość zostanie utworzona jako dołączona właściwość, ponieważ jest przeznaczona do ustawienia dla elementów, które są zawarte w <xref:System.Windows.Controls.DockPanel>, a nie na <xref:System.Windows.Controls.DockPanel> sam. <xref:System.Windows.Controls.DockPanel> Klasa definiuje statyczne <xref:System.Windows.DependencyProperty> pole o nazwie <xref:System.Windows.Controls.DockPanel.DockProperty>, a następnie oferuje <xref:System.Windows.Controls.DockPanel.GetDock%2A> i <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody publiczne metody dostępu dla dołączonych właściwości.

## Właściwości dołączone w XAML <a name="attached_properties_xaml"></a>

W XAML, ustaw właściwości dołączone przy użyciu składni *AttachedPropertyProvider*. *PropertyName*

Oto przykład, jak można ustawić <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> w XAML:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Należy pamiętać, że użycie przypomina nieco właściwość statyczna; Zawsze sprawdzaj typ <xref:System.Windows.Controls.DockPanel> który jest właścicielem i rejestruje dołączona właściwość zamiast odwołujące się do dowolnego wystąpienia określonego przez nazwę.

Ponadto ponieważ dołączoną właściwość w XAML jest atrybut, który jest ustawiony w znacznikach, ustalonej operacji ma wszystkie znaczenie. Nie można bezpośrednio pobrać właściwość w XAML, chociaż istnieją pewne mechanizmy pośrednich do porównywania wartości, takich jak wyzwalacze w stylach (Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)).

### <a name="attached-property-implementation-in-wpf"></a>Dołączona właściwość wdrożenia na platformie WPF

W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], większość dołączone właściwości, które istnieją na typy WPF, that are related to prezentacji interfejsu użytkownika są implementowane jako właściwości zależności. Właściwości dołączone są koncepcja XAML, a właściwości zależności koncepcja WPF. Ponieważ właściwości WPF dołączonych właściwości zależności, obsługują pojęć właściwość zależności, takich jak metadane właściwości i wartości domyślne, które z tych właściwości metadanych.

## W jaki sposób dołączone właściwości są używane przez typ będącej właścicielem <a name="howused"></a>

Chociaż dołączone właściwości można ustawić dla dowolnego obiektu, który nie automatycznie oznacza to, ustawiając właściwość będzie rezultatów materialne lub że wartość nigdy nie będzie używany przez inny obiekt. Ogólnie rzecz biorąc dołączone właściwości mają tak, aby obiekty pochodzące z różnorodnych hierarchie możliwe klas lub relacji logicznych można każdego raportu typowych informacji z typu, które definiują dołączona właściwość. Typ, który definiuje dołączona właściwość zazwyczaj następuje po jednej z tych modeli:

-   Typ, który definiuje dołączona właściwość zaprojektowano tak, aby można go z elementu nadrzędnego, elementy, które spowoduje ustawienie wartości dla właściwości dołączone. Następnie typ iteruje po jego obiektów podrzędnych za pomocą logika wewnętrzna względem niektórych elementów struktury drzewa obiektów, uzyskuje wartości i działa na te wartości w jakikolwiek sposób.

-   Typ, który definiuje dołączona właściwość będzie służyć jako element podrzędny dla wielu elementów nadrzędnych możliwe i modele zawartości.

-   Typ, który definiuje dołączona właściwość reprezentuje usługę. Inne typy Ustaw wartości dołączona właściwość. Następnie gdy element i ustaw właściwość jest oceniany w kontekście usługi, dołączonej właściwości wartości są uzyskiwane za pośrednictwem logika wewnętrzna klasy usługi.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Przykładem zdefiniowanych przez nadrzędne dołączoną właściwość

Najbardziej typowym scenariuszem, gdzie WPF definiuje dołączoną właściwość jest, gdy element nadrzędny obsługuje kolekcję elementów podrzędnych, a także implementuje zachowanie gdzie szczegółowe informacje na temat działania są zgłaszane osobno dla każdego elementu podrzędnego.

<xref:System.Windows.Controls.DockPanel> definiuje <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączona właściwość, a <xref:System.Windows.Controls.DockPanel> ma kod na poziomie klasy jako część swojej logiki renderowania (w szczególności <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> i <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). A <xref:System.Windows.Controls.DockPanel> wystąpienie będzie zawsze Sprawdź, czy dowolny z jego elementów podrzędnych natychmiastowego ustawiono wartość <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Jeśli tak, te wartości stają się dane wejściowe dla logiki renderowania zastosowane do tego elementu podrzędnego określonego. Zagnieżdżone <xref:System.Windows.Controls.DockPanel> wystąpień traktować ich własnych bezpośrednie podrzędne elementu kolekcji, ale to zachowanie jest specyficzne dla implementacji sposób <xref:System.Windows.Controls.DockPanel> procesy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> wartości. Teoretycznie prawdopodobnie ma dołączonych właściwości, które wpływają na elementy poza elementem nadrzędnym natychmiastowe. Jeśli <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączoną właściwość jest ustawiona na element, który nie ma przypisanego <xref:System.Windows.Controls.DockPanel> elementu nadrzędnego do działania po jej nie błąd lub wyjątek jest zgłaszany. Oznacza to po prostu czy ustawiono wartość właściwości globalnej, ale nie ma bieżącej <xref:System.Windows.Controls.DockPanel> obiektu nadrzędnego, który można skorzystać z informacji.

## Dołączone właściwości w kodzie <a name="attached_properties_code"></a>

Właściwości dołączone w WPF nie masz typowej [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "otoki" metod get/set łatwy dostęp. Jest to spowodowane dołączona właściwość nie jest zawsze częścią [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzeń nazw dla wystąpień, gdy właściwość jest ustawiona. Jednak procesor XAML musi mieć możliwość ustawienia tych wartości, gdy XAML jest analizowany. Do obsługi użycia skuteczne dołączona właściwość, typ właściciela dołączona właściwość musi implementować metody dostępu dedykowanych w formie **Get_PropertyName_** i **Set_PropertyName_**. Te metody dostępu dedykowane są również przydatne do pobierania lub ustawiania dołączona właściwość w kodzie. Z punktu widzenia kodu dołączoną właściwość jest podobne do pola pomocniczego, który ma zamiast metod dostępu do właściwości metod dostępu do metody, że pole pomocnicze może istnieć dla dowolnego obiektu, a nie musi w szczególności można zdefiniować.

Poniższy przykład pokazuje, jak można ustawić dołączonej właściwości w kodzie. W tym przykładzie `myCheckBox` jest wystąpieniem <xref:System.Windows.Controls.CheckBox> klasy.

[!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

Podobnie jak XAML zamierzone, Zapisz, jeśli `myCheckBox` nie była już dodana jako element podrzędny `myDockPanel` przez trzeci wiersz kodu, czwarty wiersz kodu nie może zgłosić wyjątek, ale wartość właściwości nie może mieć interakcji z <xref:System.Windows.Controls.DockPanel> nadrzędną, a tym samym Spowoduje to nic nie rób. Tylko <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> wartość zestawu na nie zawiera elementu podrzędnego w połączeniu z obecności <xref:System.Windows.Controls.DockPanel> elementu nadrzędnego spowoduje zachowanie obowiązujące w renderowanym aplikacji. (W tym przypadku użytkownik może ustawić dołączonej właściwości, a następnie dołączyć do drzewa. Lub możesz można dołączyć do drzewa, a następnie ustaw dołączona właściwość. Kolejność albo akcji zawiera ten sam wynik.)

## Dołączona właściwość metadanych <a name="attached_properties_metadata"></a>

Podczas rejestrowania właściwości <xref:System.Windows.FrameworkPropertyMetadata> jest ustawiona na określ cechy właściwości, takie jak czy właściwość wpływa na renderowanie, miary i tak dalej. Metadane dla dołączoną właściwość jest zwykle nie różni się od właściwości zależności. Jeśli w zastąpieniu dołączonej właściwości metadanych określać wartość domyślną, wartość ta wynosi wartość domyślną niejawne dołączona właściwość w wystąpieniach klas nadrzędnych. W szczególności wartość domyślna jest zgłaszany w przypadku niektórych przetwarzania zapytań dla wartości dołączoną właściwość za pośrednictwem `Get` dostępu metody dla tej właściwości, określając wystąpienie klasy, gdzie określone metadane, a wartość w tym dołączona właściwość była w przeciwnym razie nie jest ustawiona.

Jeśli chcesz włączyć dziedziczenie wartości właściwości we właściwości, należy użyć załączonych właściwości, a nie właściwości niedołączonych zależności. Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

## Niestandardowe dołączone właściwości <a name="custom"></a>

### Kiedy należy utworzyć dołączoną właściwość <a name="create_attached_properties"></a>

Dołączona właściwość możesz utworzyć po przyczynę ma ustawienie mechanizm dostępne klasy niż klasa Definiowanie właściwości. Najbardziej typowym scenariuszem dla tego jest układu. Przykłady istniejących właściwości układu <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>, i <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>. Scenariusz, w tym miejscu włączyć jest to, że elementów, które istnieją jako elementy podrzędne na kontrolowanie układu elementów są w stanie indywidualnie express wymagania związane z układem do ich elementów nadrzędnych, układ, każdego ustawienia wartości właściwości obiektu nadrzędnego jest zdefiniowany jako dołączone Właściwość.

Inny scenariusz użycia dołączoną właściwość jest klasa reprezentuje usługę, gdy chcesz, aby klasy, aby można było zintegrować usługę więcej w sposób przezroczysty.

Jeszcze inny scenariusz polega na otrzymywanie pomocy projektanta WPF w usłudze Visual Studio, takie jak **właściwości** okna do edycji. Aby uzyskać więcej informacji, zobacz [omówienie tworzenia kontrolek](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

Jak wspomniano wcześniej, jeśli chcesz używać dziedziczenie wartości właściwości należy zarejestrować jako dołączona właściwość.

### Jak utworzyć dołączoną właściwość <a name="how_do_i_create_attached_properties"></a>

Jeśli klasa jest zdefiniowanie dołączona właściwość wyłącznie do użytku dla innych typów, a następnie klasy nie musi pochodzić od <xref:System.Windows.DependencyObject>. Ale trzeba dziedziczyć <xref:System.Windows.DependencyObject> dzięki stosowaniu ogólnej model WPF wystąpienia usługi dołączonej właściwości również być właściwość zależności.

Zdefiniuj z dołączoną właściwość jako właściwość zależności od zadeklarowania `public static readonly` pole typu <xref:System.Windows.DependencyProperty>. To pole jest definiowane za pomocą wartość zwracaną przez <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody. Nazwa pola musi odpowiadać nazwie dołączona właściwość, dołączany parametrami `Property`, oparte na wzorcu ustanowionych WPF nazewnictwa identyfikacji pola i właściwości, które reprezentują one. Dostawca dołączonej właściwości należy również podać statyczne **Get_PropertyName_** i **Set_PropertyName_** metod jako Akcesory dla dołączonych właściwości; kończy się niepowodzeniem, w tym celu spowoduje we właściwości System nie będzie w stanie korzystać z dołączoną właściwość.

> [!NOTE]
> Jeżeli pominięto metody dostępu get dołączona właściwość powiązania danych we właściwości nie będzie działać w narzędzia do projektowania, takich jak Visual Studio oraz Expression Blend.

#### <a name="the-get-accessor"></a>Metody dostępu Get

Podpis dla **Get_PropertyName_** metody dostępu muszą być:

`public static object GetPropertyName(object target)`

-   `target` Obiektu może być określony jako bardziej specyficznego typu w danej implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> metoda typów jako parametr <xref:System.Windows.UIElement>, ponieważ dołączona właściwość jest przeznaczona tylko do nelze nastavit <xref:System.Windows.UIElement> wystąpień.

-   Zwracana wartość można określić jako bardziej określonego typu w danej implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.GetDock%2A> metoda typów jako <xref:System.Windows.Controls.Dock>, ponieważ wartość można ustawić tylko do tego wyliczenia.

#### <a name="the-set-accessor"></a>Metody dostępu Set

Podpis dla **Set_PropertyName_** metody dostępu muszą być:

`public static void SetPropertyName(object target, object value)`

-   `target` Obiektu może być określony jako bardziej specyficznego typu w danej implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda typów jako <xref:System.Windows.UIElement>, ponieważ dołączona właściwość jest przeznaczona tylko do nelze nastavit <xref:System.Windows.UIElement> wystąpień.

-   `value` Obiektu może być określony jako bardziej specyficznego typu w danej implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda typów jako <xref:System.Windows.Controls.Dock>, ponieważ wartość można ustawić tylko do tego wyliczenia. Pamiętaj, że wartość ta metoda ma pochodzących z modułu ładującego XAML, po napotkaniu usługi dołączonej właściwości użycia dołączonej właściwości w znaczniku w danych wejściowych. Te dane wejściowe to wartość określona jako wartość atrybutu XAML w znacznikach. W związku z tym musi istnieć konwersji typów, wartość serializatora lub obsługa rozszerzenia znaczników dla typu, którego używasz, takie, że odpowiedni typ można tworzyć na podstawie wartości atrybutu (co ostatecznie to klient jest po prostu określonym ciągiem).

W poniższym przykładzie pokazano rejestrację właściwości zależności (przy użyciu <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody), jak również **Get_PropertyName_** i **Set_PropertyName_** metod dostępu. W tym przykładzie nazwa dołączonych właściwości jest `IsBubbleSource`. W związku z tym, musi nosić nazwę metody dostępu `GetIsBubbleSource` i `SetIsBubbleSource`.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>Atrybuty dołączone właściwości

WPF definiuje kilka [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] , są przeznaczone do dostarczania informacji dotyczących właściwości dołączone procesy odbicia i typowi użytkownicy odbicia i właściwość informacje, takie jak projektantów. Ponieważ dołączonych właściwości Typ nieograniczonego zakresu uprawnień, projektantów muszą mieć możliwość uniknąć przytłaczająca użytkownikom globalną listę wszystkich dołączonych właściwości, które są zdefiniowane w implementacji określonej technologii, która używa XAML. [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] Tego WPF definiuje dla dołączonych właściwości może służyć do określania zakresu w sytuacjach, w którym dołączonych właściwości powinny być wyświetlane w taki sposób, w oknie właściwości. Można rozważyć zastosowanie również te atrybuty dla własnego niestandardowego dołączone właściwości. Cel i składnię [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] opisano na stronach odpowiednie odwołania:

-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## Dowiedz się więcej na temat dołączone właściwości <a name="more"></a>

-   Aby uzyskać więcej informacji na temat tworzenia dołączoną właściwość, zobacz [rejestrowanie dołączonych właściwości](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md).

-   Zobacz więcej zaawansowanych scenariuszy użycia dla właściwości zależności i dołączonych właściwości [niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).

-   Możesz także zarejestrować właściwość dołączonej właściwości, jak i właściwość zależności, ale nadal następnie udostępnić implementacje "otoki". W tym przypadku właściwość można ustawić w tym elemencie lub dowolnego elementu przy użyciu XAML dołączonych właściwości składni. Na przykład właściwość o odpowiedni scenariusz użycia zarówno standardowe, jak i dołączonych <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.DependencyProperty>
- [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Rejestrowanie dołączonej właściwości](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)