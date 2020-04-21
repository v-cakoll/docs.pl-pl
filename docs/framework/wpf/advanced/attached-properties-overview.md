---
title: Przegląd Właściwości dołączone
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: b207db459776c9f8fa7ea247d01071eeb8c995cf
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739295"
---
# <a name="attached-properties-overview"></a>Przegląd Właściwości dołączone

Załączona właściwość jest pojęciem zdefiniowanym przez XAML. Dołączona właściwość jest przeznaczona do użycia jako typ właściwości globalnej, która jest ustawiona na dowolnym obiekcie. W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], dołączone właściwości są zazwyczaj definiowane jako wyspecjalizowana forma właściwości zależności, która nie ma konwencjonalnej właściwości "otoka".

## <a name="prerequisites"></a>Wymagania wstępne<a name="prerequisites"></a>

W tym artykule przyjęto założenie, że rozumiesz właściwości zależności z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] perspektywy konsumenta istniejących właściwości zależności w klasach i przeczytałeś [przegląd właściwości zależności.](dependency-properties-overview.md) Aby postępować zgodnie z przykładami w tym artykule, należy również zrozumieć XAML i wiedzieć, jak pisać aplikacje WPF.

## <a name="why-use-attached-properties"></a>Dlaczego warto używać dołączonych właściwości<a name="attached_properties_usage"></a>

Jednym z celów dołączonej właściwości jest zezwolenie na różne elementy podrzędne, aby określić unikatowe wartości dla właściwości, która jest zdefiniowana w elemencie nadrzędnym. Konkretne zastosowanie tego scenariusza jest o elementy podrzędne poinformować element [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]nadrzędny, w jaki sposób mają być przedstawione w . Jednym z <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> przykładów jest właściwość. Właściwość <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> jest tworzona jako dołączonej właściwości, ponieważ jest przeznaczony do <xref:System.Windows.Controls.DockPanel> zestawu <xref:System.Windows.Controls.DockPanel> na elementy, które są zawarte w, a nie na siebie. Klasa <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.DependencyProperty> definiuje pole statyczne <xref:System.Windows.Controls.DockPanel.DockProperty>o nazwie , <xref:System.Windows.Controls.DockPanel.GetDock%2A> <xref:System.Windows.Controls.DockPanel.SetDock%2A> a następnie udostępnia i metody jako publiczne akcesory dla dołączonej właściwości.

## <a name="attached-properties-in-xaml"></a>Dołączone właściwości w języku XAML<a name="attached_properties_xaml"></a>

W języku XAML można ustawić dołączone właściwości przy użyciu składni *AttachedPropertyProvider*. *Nazwa właściwości*

Poniżej przedstawiono przykład sposobu <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ustawiania w języku XAML:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Użycie jest nieco podobne do właściwości statycznej; zawsze odwołujesz <xref:System.Windows.Controls.DockPanel> się do typu, który jest właścicielem i rejestruje dołączoną właściwość, zamiast odwoływać się do dowolnego wystąpienia określonego przez nazwę.

Ponadto ponieważ dołączona właściwość w XAML jest atrybutem ustawionym w znacznikach, tylko operacja zestawu ma jakiekolwiek znaczenie. Nie można bezpośrednio uzyskać właściwości w języku XAML, chociaż istnieją pewne mechanizmy pośrednie do porównywania wartości, takie jak wyzwalacze w stylach (szczegółowe informacje można znaleźć [w stylizacji i szablonach).](../../../desktop-wpf/fundamentals/styles-templates-overview.md)

### <a name="attached-property-implementation-in-wpf"></a>Załączona implementacja właściwości w WPF

W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], większość właściwości dołączonych do interfejsu użytkownika dołączone są implementowane jako właściwości zależności. Dołączone właściwości są koncepcją XAML, podczas gdy właściwości zależności są koncepcją WPF. Ponieważ WPF dołączone właściwości są właściwości zależności, obsługują one pojęcia właściwości zależności, takie jak metadane właściwości i wartości domyślne z tych metadanych właściwości.

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>Sposób, w jaki dołączone właściwości są używane przez typ posiadania<a name="howused"></a>

Chociaż dołączone właściwości są settable na dowolnym obiekcie, nie oznacza to automatycznie, że ustawienie właściwości przyniesie namacalny wynik lub że wartość będzie kiedykolwiek używana przez inny obiekt. Ogólnie rzecz biorąc dołączone właściwości są przeznaczone tak, aby obiekty pochodzące z wielu możliwych hierarchii klas lub relacji logicznych można każdy raport wspólne informacje do typu, który definiuje dołączone właściwości. Typ, który definiuje dołączoną właściwość zazwyczaj następuje jeden z następujących modeli:

- Typ, który definiuje dołączonej właściwości jest zaprojektowany tak, że może być elementem nadrzędnym elementów, które będą ustawiać wartości dla dołączonej właściwości. Typ następnie iteruje jego obiektów podrzędnych za pośrednictwem logiki wewnętrznej względem niektórych struktur drzewa obiektów, uzyskuje wartości i działa na te wartości w jakiś sposób.

- Typ, który definiuje dołączone właściwość będzie używany jako element podrzędny dla różnych możliwych elementów nadrzędnych i modeli zawartości.

- Typ, który definiuje dołączoną właściwość reprezentuje usługę. Inne typy ustawiają wartości dołączonej właściwości. Następnie, gdy element, który ustawia właściwość jest oceniany w kontekście usługi, dołączone wartości właściwości są uzyskiwane za pomocą wewnętrznej logiki klasy usługi.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Przykład dołączonej właściwości zdefiniowanej przez rodzica

Najbardziej typowy scenariusz, w którym WPF definiuje dołączonej właściwości jest, gdy element nadrzędny obsługuje kolekcji elementu podrzędnego, a także implementuje zachowanie, gdzie specyfika zachowania są zgłaszane indywidualnie dla każdego elementu podrzędnego.

<xref:System.Windows.Controls.DockPanel>definiuje <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączoną właściwość <xref:System.Windows.Controls.DockPanel> i ma kod na poziomie klasy jako część <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>jego logiki renderowania (w szczególności i ). Wystąpienie <xref:System.Windows.Controls.DockPanel> zawsze sprawdzi, czy którykolwiek z jego bezpośrednich elementów podrzędnych ustawił wartość dla <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Jeśli tak, te wartości stają się dane wejściowe dla logiki renderowania stosowane do tego elementu podrzędnego określonego. Zagnieżdżone <xref:System.Windows.Controls.DockPanel> wystąpienia każdego traktować własne kolekcje elementu podrzędnego <xref:System.Windows.Controls.DockPanel> bezpośredniego, ale to zachowanie jest specyficzne dla implementacji, jak przetwarza <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> wartości. Teoretycznie możliwe jest dołączone właściwości, które wpływają na elementy wykraczające poza bezpośredni element nadrzędny. Jeśli <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączone właściwość jest ustawiona na <xref:System.Windows.Controls.DockPanel> element, który nie ma elementu nadrzędnego do działania na nim, nie błąd lub wyjątek jest wywoływana. Oznacza to po prostu, że wartość właściwości globalnej została ustawiona, ale nie ma bieżącego <xref:System.Windows.Controls.DockPanel> obiektu nadrzędnego, który mógłby zużywać informacje.

## <a name="attached-properties-in-code"></a>Dołączone właściwości w kodzie<a name="attached_properties_code"></a>

Dołączone właściwości w WPF nie mają typowych metod "otoki" CLR dla łatwego dostępu do zestawu.Attached properties in WPF nie have the typical CLR "wrapper" methods for easy get/set access. Dzieje się tak, ponieważ dołączona właściwość nie musi być częścią obszaru nazw CLR dla wystąpień, w których właściwość jest ustawiona. Jednak procesor XAML musi być w stanie ustawić te wartości podczas analizowanie XAML. Aby obsługiwać efektywne użycie dołączonej właściwości, typ właściciela dołączonej właściwości musi implementować dedykowane metody akcesora w formularzu **Get_PropertyName_** i **Set_PropertyName_**. Te metody akcesor dedykowane są również przydatne, aby uzyskać lub ustawić dołączone właściwości w kodzie. Z punktu widzenia kodu dołączone właściwość jest podobna do pola zapasowego, które ma akcesory metod zamiast akcesorów właściwości i że pole zapasowe może istnieć na dowolnym obiekcie, a nie muszą być specjalnie zdefiniowane.

Poniższy przykład pokazuje, jak można ustawić dołączoną właściwość w kodzie. W tym `myCheckBox` przykładzie jest <xref:System.Windows.Controls.CheckBox> wystąpieniem klasy.

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

Podobnie jak w przypadku XAML, jeśli `myCheckBox` nie został `myDockPanel` już dodany jako element podrzędny przez czwarty wiersz kodu, piąty wiersz kodu nie <xref:System.Windows.Controls.DockPanel> spowoduje wyjątek, ale wartość właściwości nie będzie współdziałać z elementem nadrzędnym i w związku z tym nie zrobi nic. Tylko <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> wartość ustawiona na elemencie <xref:System.Windows.Controls.DockPanel> podrzędnym w połączeniu z obecnością elementu nadrzędnego spowoduje skuteczne zachowanie w renderowanych aplikacji. (W takim przypadku można ustawić dołączoną właściwość, a następnie dołączyć do drzewa. Lub można dołączyć do drzewa, a następnie ustawić dołączone właściwości. Każda z tych akcji zapewnia ten sam wynik.)

## <a name="attached-property-metadata"></a>Dołączone metadane właściwości<a name="attached_properties_metadata"></a>

Podczas rejestrowania właściwości, jest ustawiony, <xref:System.Windows.FrameworkPropertyMetadata> aby określić cechy właściwości, takie jak czy właściwość wpływa na renderowanie, pomiar i tak dalej. Metadane dla dołączonej właściwości zazwyczaj nie różni się od właściwości zależności. Jeśli określisz wartość domyślną w zastąpieniu dołączonych metadanych właściwości, ta wartość staje się domyślną wartością niejawnej dołączonej właściwości w wystąpieniach klasy nadrzędnej. W szczególności wartość domyślna jest raportowana, jeśli niektóre zapytania procesowe `Get` dla wartości dołączonej właściwości za pośrednictwem akcesora metody dla tej właściwości, określając wystąpienie klasy, w którym określono metadane, a wartość dla tej dołączonej właściwości nie została ustawiona.

Jeśli chcesz włączyć dziedziczenie wartości właściwości we właściwości, należy użyć dołączonych właściwości, a nie nie dołączone właściwości zależności. Aby uzyskać szczegółowe informacje, zobacz [Dziedziczenie wartości właściwości](property-value-inheritance.md).

## <a name="custom-attached-properties"></a>Niestandardowe dołączone właściwości<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>Kiedy utworzyć dołączoną właściwość<a name="create_attached_properties"></a>

Można utworzyć dołączoną właściwość, gdy istnieje powód, aby mechanizm ustawiania właściwości był dostępny dla klas innych niż klasa definiująca. Najbardziej typowym scenariuszem dla tego jest układ. Przykładami istniejących właściwości układu <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>są <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, i . Scenariusz włączony w tym miejscu jest, że elementy, które istnieją jako elementy podrzędne do elementów sterujących układem są w stanie wyrazić wymagania układu do ich elementów nadrzędnych układu indywidualnie, każdy ustawienie wartości właściwości, że element nadrzędny zdefiniowane jako dołączone właściwości.

Innym scenariuszem przy użyciu dołączonej właściwości jest, gdy klasa reprezentuje usługę i chcesz, aby klasy mogły integrować usługę bardziej niewidoczniej.

Jeszcze inny scenariusz jest odbieranie visual studio WPF Designer pomocy technicznej, takich jak **właściwości** edycji okna. Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia formantu](../controls/control-authoring-overview.md).

Jak wspomniano wcześniej, należy zarejestrować się jako dołączonej właściwości, jeśli chcesz użyć dziedziczenia wartości właściwości.

### <a name="how-to-create-an-attached-property"></a>Jak utworzyć dołączoną właściwość<a name="how_do_i_create_attached_properties"></a>

Jeśli klasa definiuje dołączoną właściwość wyłącznie do użytku na innych typach, <xref:System.Windows.DependencyObject>klasa nie musi pochodzić od . Ale musisz wyprowadzić z <xref:System.Windows.DependencyObject> jeśli należy wykonać ogólny model WPF o dołączonej właściwości również właściwości zależności.

Zdefiniuj dołączoną właściwość jako `public static readonly` właściwość <xref:System.Windows.DependencyProperty>zależności, deklarując pole typu . To pole można zdefiniować przy <xref:System.Windows.DependencyProperty.RegisterAttached%2A> użyciu zwracanej wartości metody. Nazwa pola musi być zgodna z dołączoną nazwą `Property`właściwości, dołączoną do ciągu , aby postępować zgodnie z ustalonym wzorcem WPF nazewnictwa pól identyfikujących w stosunku do właściwości, które reprezentują. Załączony dostawca właściwości musi również podać statyczne **metody Get_PropertyName_** i **Set_PropertyName_** jako akcesory dla dołączonej właściwości; nie jest to spowodowało, że system nieruchomości nie może korzystać z dołączonej właściwości.

> [!NOTE]
> Jeśli pominięto dołączonego akcesora get właściwości, powiązanie danych właściwości nie będzie działać w narzędziach projektowych, takich jak Visual Studio i Blend for Visual Studio.

#### <a name="the-get-accessor"></a>Akcesor Pobierz

Podpis dla **Get_PropertyName_** akcesora musi być:

`public static object GetPropertyName(object target)`

- Obiekt `target` można określić jako bardziej szczegółowy typ w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> metoda typuje <xref:System.Windows.UIElement>parametr jako , ponieważ dołączona właściwość <xref:System.Windows.UIElement> jest przeznaczona tylko do ustawiania w wystąpieniach.

- Zwracana wartość może być określona jako bardziej szczegółowy typ w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.GetDock%2A> metoda typów <xref:System.Windows.Controls.Dock>go jako , ponieważ wartość można ustawić tylko do tego wyliczenia.

#### <a name="the-set-accessor"></a>Akcesor zestawu

Podpis dla **Set_PropertyName_** akcesora musi być:

`public static void SetPropertyName(object target, object value)`

- Obiekt `target` można określić jako bardziej szczegółowy typ w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda typów <xref:System.Windows.UIElement>go jako , ponieważ dołączona właściwość <xref:System.Windows.UIElement> jest przeznaczona tylko do ustawiania na wystąpieniach.

- Obiekt `value` można określić jako bardziej szczegółowy typ w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda typów <xref:System.Windows.Controls.Dock>go jako , ponieważ wartość można ustawić tylko do tego wyliczenia. Należy pamiętać, że wartość dla tej metody jest dane wejściowe pochodzące z modułu ładującego XAML, gdy napotka dołączone właściwości w użyciu dołączonej właściwości w znacznikach. To dane wejściowe są wartością określoną jako wartość atrybutu XAML w znacznikach. W związku z tym musi istnieć konwersja typu, serializator wartości lub obsługa rozszerzenia znaczników dla typu, którego używasz, tak aby można było utworzyć odpowiedni typ z wartości atrybutu (która ostatecznie jest tylko ciągiem).

Poniższy przykład przedstawia rejestrację właściwości <xref:System.Windows.DependencyProperty.RegisterAttached%2A> zależności (przy użyciu metody), a także **Get_PropertyName_** i **Set_PropertyName_** akcesorów. W tym przykładzie nazwa dołączonej właściwości to `IsBubbleSource`. W związku z tym akcesory muszą mieć nazwę `GetIsBubbleSource` i `SetIsBubbleSource`.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>Dołączone atrybuty właściwości

WPF WPF definiuje kilka atrybutów .NET, które są przeznaczone do dostarczania informacji o dołączonych właściwości do procesów odbicia i typowych użytkowników odbicia i informacji o właściwościach, takich jak projektanci. Ponieważ dołączone właściwości mają typ nieograniczony zakres, projektanci potrzebują sposobu, aby uniknąć przytłaczające użytkowników z globalnej listy wszystkich dołączonych właściwości, które są zdefiniowane w implementacji określonej technologii, która używa XAML. Atrybuty .NET, które WPF definiuje dla dołączonych właściwości może służyć do zakresu sytuacji, w których dana dołączona właściwość powinna być wyświetlana w oknie właściwości. Można rozważyć zastosowanie tych atrybutów dla własnych właściwości dołączone niestandardowe również. Cel i składnia atrybutów .NET jest opisana na odpowiednich stronach referencyjnych:

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>Dowiedz się więcej o dołączonych właściwościach<a name="more"></a>

- Aby uzyskać więcej informacji na temat tworzenia dołączonej właściwości, zobacz [Rejestrowanie dołączonej właściwości](how-to-register-an-attached-property.md).

- Aby uzyskać bardziej zaawansowane scenariusze użycia właściwości zależności i dołączonych właściwości, zobacz [Właściwości zależności niestandardowej](custom-dependency-properties.md).

- Można również zarejestrować właściwość jako właściwości dołączone i jako właściwość zależności, ale następnie nadal uwidaczniać "otoki" implementacje. W takim przypadku właściwość można ustawić na tym elemencie lub na dowolnym elemencie za pośrednictwem składni właściwości dołączonej XAML. Przykładem właściwości z odpowiednim scenariuszem zarówno dla standardowych, <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>jak i dołączonych użycia jest .

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.DependencyProperty>
- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rejestrowanie dołączonej właściwości](how-to-register-an-attached-property.md)
