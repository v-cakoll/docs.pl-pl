---
title: Przegląd Właściwości dołączone
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 2eacb0ff49b868f144bf35af4bb64b7d049b30cb
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401389"
---
# <a name="attached-properties-overview"></a>Przegląd Właściwości dołączone

Dołączona właściwość jest pojęciem zdefiniowanym przez język XAML. Dołączona właściwość jest przeznaczona do użycia jako typ właściwości globalnej, która jest settable dla dowolnego obiektu. W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]programie dołączone właściwości są zwykle definiowane jako wyspecjalizowana forma właściwości zależności, która nie ma konwencjonalnej właściwości "otoka".

## Wymagany<a name="prerequisites"></a>

W tym temacie przyjęto założenie, że właściwości zależności są rozpoznawane w perspektywie odbiorcy istniejących [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości zależności w klasach i odczytywane są [Przegląd właściwości zależności](dependency-properties-overview.md). Aby postępować zgodnie z przykładami w tym temacie, należy również zrozumieć język XAML i wiedzieć, jak pisać aplikacje WPF.

## Dlaczego warto używać dołączonych właściwości<a name="attached_properties_usage"></a>

Jednym z celów dołączonej właściwości jest umożliwienie różnym elementom podrzędnym określenie unikatowych wartości właściwości, która jest w rzeczywistości zdefiniowana w elemencie nadrzędnym. Określona aplikacja tego scenariusza ma elementy podrzędne, które informują element nadrzędny o tym, w jaki sposób mają być prezentowane [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]w. Przykładem jest <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> właściwość. Właściwość jest tworzona jako dołączona właściwość, ponieważ została zaprojektowana tak <xref:System.Windows.Controls.DockPanel>, aby była ustawiona dla elementów, które znajdują się w <xref:System.Windows.Controls.DockPanel> elemencie, a nie na samym siebie. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> <xref:System.Windows.DependencyProperty> <xref:System.Windows.Controls.DockPanel.DockProperty> <xref:System.Windows.Controls.DockPanel.GetDock%2A> Klasa definiuje pole statyczne o nazwie, a następnie udostępnia metody i <xref:System.Windows.Controls.DockPanel.SetDock%2A> jako publiczne dostęp do dołączonej właściwości. <xref:System.Windows.Controls.DockPanel>

## Dołączone właściwości w języku XAML<a name="attached_properties_xaml"></a>

W języku XAML ustawiasz dołączone właściwości przy użyciu składni *AttachedPropertyProvider*. Funkcja *PropertyName*

Poniżej przedstawiono przykład sposobu ustawienia <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> w języku XAML:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Należy zauważyć, że użycie jest nieco podobne do właściwości statycznej; zawsze należy odwołać się <xref:System.Windows.Controls.DockPanel> do typu, który jest właścicielem i rejestruje załączoną właściwość, zamiast odwoływać się do żadnego wystąpienia określonego przez nazwę.

Ponadto, ponieważ dołączona właściwość w języku XAML jest atrybutem ustawionym w znaczniku, tylko operacja ustawiania ma wszelkie istotność. Nie można bezpośrednio uzyskać właściwości w języku XAML, chociaż istnieją pewne mechanizmy pośrednie do porównywania wartości, takich jak Wyzwalacze w stylach (Aby uzyskać szczegółowe informacje, zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md)).

### <a name="attached-property-implementation-in-wpf"></a>Załączona implementacja właściwości w WPF

W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]programie większość załączonych właściwości, które istnieją w typach WPF, które są powiązane z prezentacją interfejsu użytkownika, są implementowane jako właściwości zależności. Dołączone właściwości są koncepcją języka XAML, podczas gdy właściwości zależności są koncepcją WPF. Ponieważ właściwości dołączone do platformy WPF są właściwościami zależności, obsługują one koncepcje właściwości zależności, takie jak metadane właściwości i wartości domyślne z tego metadanych właściwości.

## Jak dołączone właściwości są używane przez typ będącego właścicielem<a name="howused"></a>

Mimo że dołączone właściwości są ustawiane na dowolnym obiekcie, który nie oznacza, że ustawienie właściwości spowoduje wygenerowanie wyniku materialnego lub że wartość będzie kiedykolwiek używana przez inny obiekt. Ogólnie rzecz biorąc, dołączone właściwości są zamierzone, aby obiekty pochodzące z szerokiej gamy hierarchii klas lub relacje logiczne mogły raportować typowe informacje do typu, który definiuje przyłączoną właściwość. Typ, który definiuje załączoną Właściwość zwykle jest zgodny z jednym z następujących modeli:

- Typ, który definiuje załączoną właściwość jest zaprojektowana tak, aby mógł być elementem nadrzędnym elementów, które będą ustawiać wartości dla dołączonej właściwości. Typ, a następnie wykonuje iterację obiektów podrzędnych za pomocą logiki wewnętrznej względem niektórych struktur drzewa obiektów, uzyskuje wartości i działa na tych wartości w jakiś sposób.

- Typ, który definiuje załączoną właściwość, będzie używany jako element podrzędny dla różnych możliwych elementów nadrzędnych i modeli zawartości.

- Typ, który definiuje załączoną właściwość, reprezentuje usługę. Inne typy ustawiają wartości dla dołączonej właściwości. Następnie, gdy element ustawiający właściwość jest oceniany w kontekście usługi, wartości dołączonych właściwości są uzyskiwane za pomocą wewnętrznej logiki klasy usługi.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Przykład właściwości dołączonej do elementu nadrzędnego

Typowy scenariusz, w którym WPF definiuje dołączoną właściwość, gdy element nadrzędny obsługuje kolekcję elementów podrzędnych, a także implementuje zachowanie w przypadku, gdy szczegółowe informacje o zachowaniu są raportowane osobno dla każdego elementu podrzędnego.

<xref:System.Windows.Controls.DockPanel>definiuje załączoną Właściwość i <xref:System.Windows.Controls.DockPanel> ma kod na poziomie klasy jako część logiki <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> renderowania (w odniesieniu i <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Wystąpienie będzie zawsze sprawdzać, czy którykolwiek z jego bezpośrednich elementów podrzędnych ustawił wartość dla <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. <xref:System.Windows.Controls.DockPanel> Jeśli tak, te wartości staną się danymi wejściowymi dla logiki renderowania zastosowanej do danego elementu podrzędnego. Wystąpienia <xref:System.Windows.Controls.DockPanel> zagnieżdżone każda traktują swoje własne bezpośrednie kolekcje elementów, ale takie zachowanie jest specyficzne <xref:System.Windows.Controls.DockPanel> dla implementacji dla procesów <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> . Teoretycznie możliwe jest dołączenie właściwości, które mają wpływ na elementy poza bezpośrednim elementem nadrzędnym. Jeśli dołączona właściwość jest ustawiona dla elementu, który nie <xref:System.Windows.Controls.DockPanel> ma elementu nadrzędnego do działania, żaden błąd lub wyjątek nie zostanie zgłoszony. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Oznacza to po prostu, że wartość właściwości globalnej została ustawiona, ale nie ma bieżącego <xref:System.Windows.Controls.DockPanel> elementu nadrzędnego, który mógłby wykorzystać te informacje.

## Dołączone właściwości w kodzie<a name="attached_properties_code"></a>

Dołączone właściwości w WPF nie mają typowych metod "otoki" środowiska CLR w celu ułatwienia dostępu do usługi get/set. Wynika to z faktu, że dołączona właściwość nie musi być częścią przestrzeni nazw CLR dla wystąpień, w których właściwość jest ustawiona. Jednak procesor XAML musi mieć możliwość ustawiania tych wartości podczas analizowania kodu XAML. Aby można było obsługiwać efektywne dołączone właściwości, typ właściciela dołączonej właściwości musi implementować metody dostępu dedykowanego w postaci **Get_PropertyName_** i **Set_PropertyName_** . Te dedykowane metody dostępu są również przydatne do pobierania lub ustawiania dołączonej właściwości w kodzie. W perspektywie kodu dołączona właściwość jest podobna do pola zapasowego, które ma metody dostępu do właściwości, i że pole zapasowe może istnieć na dowolnym obiekcie, a nie musi być jawnie zdefiniowane.

Poniższy przykład pokazuje, jak można ustawić przyłączoną właściwość w kodzie. W tym przykładzie `myCheckBox` jest wystąpieniem <xref:System.Windows.Controls.CheckBox> klasy.

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

Podobnie jak w przypadku języka XAML, `myCheckBox` Jeśli nie został jeszcze dodany jako `myDockPanel` element podrzędny przez trzeci wiersz kodu, czwarty wiersz kodu nie zgłosi wyjątku, ale wartość właściwości nie <xref:System.Windows.Controls.DockPanel> będzie współdziałać z elementem nadrzędnym i w ten sposób nic nie rób. Tylko wartość ustawiona w elemencie podrzędnym, w połączeniu z obecność <xref:System.Windows.Controls.DockPanel> elementu nadrzędnego, spowoduje efektywne zachowanie w renderowanej aplikacji. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> (W tym przypadku można ustawić przyłączoną właściwość, a następnie dołączyć do drzewa. Możesz też dołączyć do drzewa, a następnie ustawić przyłączoną właściwość. Każda kolejność akcji daje ten sam wynik.)

## Dołączone metadane właściwości<a name="attached_properties_metadata"></a>

Podczas rejestrowania właściwości, <xref:System.Windows.FrameworkPropertyMetadata> jest ustawione na określanie właściwości właściwości, na przykład czy właściwość wpływa na renderowanie, pomiar i tak dalej. Metadane dołączonej właściwości zwykle nie są inne niż w przypadku właściwości zależności. Jeśli określisz wartość domyślną w metadanych przesłonięcia do dołączonej właściwości, ta wartość będzie wartością domyślną niejawnej dołączonej właściwości w wystąpieniach klasy zastępującej. W zależności od `Get` tego wartość domyślna jest raportowana, jeśli niektóre zapytania procesu dla wartości właściwości dołączonej są używane przez metodę dostępu metody dla tej właściwości, określając wystąpienie klasy, w której określono metadane, oraz wartość dla tego dołączona właściwość nie została ustawiona w inny sposób.

Aby włączyć dziedziczenie wartości właściwości dla właściwości, należy użyć dołączonych właściwości, a nie niedołączonych właściwości zależności. Aby uzyskać szczegółowe informacje, zobacz [dziedziczenie wartości właściwości](property-value-inheritance.md).

## Niestandardowe dołączone właściwości<a name="custom"></a>

### Kiedy należy utworzyć dołączoną Właściwość<a name="create_attached_properties"></a>

Można utworzyć przyłączoną właściwość, gdy istnieje powód, dla którego jest dostępny mechanizm ustawienia właściwości dla klas innych niż Klasa definiująca. Najbardziej typowym scenariuszem tego jest układ. Przykłady istniejących właściwości układu to <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>, i <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>. Scenariusz włączony tutaj polega na tym, że elementy, które istnieją jako elementy podrzędne do układu sterujące elementy, są w stanie wyznaczać wymagania układu dla elementów nadrzędnych układu osobno, każde ustawienie wartości właściwości, która została zdefiniowana przez element nadrzędny jako dołączony wartość.

Innym scenariuszem korzystania z dołączonej właściwości jest to, że Klasa reprezentuje usługę, i chcesz, aby klasy mogły zintegrować usługę w sposób bardziej niewidoczny.

Jeszcze innym scenariuszem jest otrzymanie obsługi projektanta Visual Studio WPF, takich jak edytowanie okna **Właściwości** . Aby uzyskać więcej informacji, zobacz temat [Tworzenie kontroli — przegląd](../controls/control-authoring-overview.md).

Jak wspomniano wcześniej, należy zarejestrować się jako właściwość dołączona, jeśli chcesz użyć dziedziczenia wartości właściwości.

### Jak utworzyć dołączoną Właściwość<a name="how_do_i_create_attached_properties"></a>

Jeśli klasa definiuje dołączoną Właściwość wyłącznie do użycia w innych typach, Klasa nie musi dziedziczyć od <xref:System.Windows.DependencyObject>. Jednak należy utworzyć wynik z <xref:System.Windows.DependencyObject> , jeśli spełniasz ogólny model WPF, że dołączona właściwość również jest właściwością zależności.

Zdefiniuj załączoną właściwość jako właściwość zależności przez zadeklarowanie `public static readonly` pola typu. <xref:System.Windows.DependencyProperty> To pole jest definiowane przy użyciu wartości <xref:System.Windows.DependencyProperty.RegisterAttached%2A> zwracanej przez metodę. Nazwa pola musi być zgodna z nazwą dołączonej właściwości, dołączoną do ciągu `Property`, aby postępować zgodnie z ustalonym wzorcem WPF określającym nazwy pól identyfikujących i właściwości, które reprezentują. Dostawca dołączonej właściwości musi także podawać statyczne metody **Get_PropertyName_** i **Set_PropertyName_** jako metod dostępu dla dołączonej właściwości; Niewykonanie tej czynności spowoduje, że system właściwości nie będzie mógł użyć dołączonej właściwości.

> [!NOTE]
> Jeśli pominięto metodę dostępu get dołączonej właściwości, powiązanie danych dla właściwości nie będzie działało w narzędziach projektowania, takich jak Visual Studio i Expression Blend.

#### <a name="the-get-accessor"></a>Metoda dostępu get

Sygnatura metody dostępu **Get_PropertyName_** musi być:

`public static object GetPropertyName(object target)`

- `target` Obiekt może być określony jako bardziej konkretny typ w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> Metoda określa parametr jako <xref:System.Windows.UIElement>, ponieważ dołączona właściwość jest przeznaczona tylko do ustawiania w <xref:System.Windows.UIElement> wystąpieniach.

- Wartość zwracana może być określona jako bardziej konkretny typ w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.GetDock%2A> Metoda ta jest określana jako <xref:System.Windows.Controls.Dock>, ponieważ wartość może być ustawiona tylko na to wyliczenie.

#### <a name="the-set-accessor"></a>Metoda dostępu set

Sygnatura metody dostępu **Set_PropertyName_** musi być:

`public static void SetPropertyName(object target, object value)`

- `target` Obiekt może być określony jako bardziej konkretny typ w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.SetDock%2A> Metoda ta jest typu <xref:System.Windows.UIElement>, ponieważ dołączona właściwość jest przeznaczona tylko do ustawiania w <xref:System.Windows.UIElement> wystąpieniach.

- `value` Obiekt może być określony jako bardziej konkretny typ w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.SetDock%2A> Metoda ta jest określana jako <xref:System.Windows.Controls.Dock>, ponieważ wartość może być ustawiona tylko na to wyliczenie. Należy pamiętać, że wartość tej metody jest wartością wejściową pochodzącą z modułu ładującego XAML podczas napotkania dołączonej właściwości we właściwości użycie dołączonej w znaczniku. To dane wejściowe to wartość określona jako wartość atrybutu XAML w znaczniku. W związku z tym, należy dokonać konwersji typu, serializatora wartości lub rozszerzenia znacznika dla używanego typu, aby można było utworzyć odpowiedni typ na podstawie wartości atrybutu (która jest ostatecznie tylko ciągiem).

Poniższy przykład przedstawia rejestrację właściwości zależności (przy użyciu <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody), a także metod dostępu **Get_PropertyName_** i **Set_PropertyName_** . W przykładzie nazwa dołączonej właściwości to `IsBubbleSource`. W związku z tym, metody dostępu muszą `GetIsBubbleSource` mieć `SetIsBubbleSource`nazwę i.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>Atrybuty dołączonej właściwości

WPF definiuje kilka [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] , które są przeznaczone do dostarczania informacji o właściwościach dołączonych do procesów odbicia, oraz do typowych użytkowników odbicia i informacji o właściwościach, takich jak projektanci. Ponieważ dołączone właściwości mają typ nieograniczonego zakresu, projektanci muszą mieć możliwość uniknięcia przeciążania użytkowników z globalną listą wszystkich dołączonych właściwości, które są zdefiniowane w określonej implementacji technologicznej, która używa języka XAML. [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] Ta funkcja WPF definiuje dla dołączonych właściwości może służyć do określania zakresu sytuacji, w których dana dołączona właściwość powinna być wyświetlana w oknie właściwości. Można rozważyć zastosowanie tych atrybutów do własnych niestandardowych właściwości dołączanych. Składnia [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] jest opisana na odpowiednich stronach odniesienia:

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## Dowiedz się więcej na temat dołączonych właściwości<a name="more"></a>

- Aby uzyskać więcej informacji na temat tworzenia dołączonej właściwości, zobacz [Rejestrowanie dołączonej właściwości](how-to-register-an-attached-property.md).

- Aby uzyskać bardziej zaawansowane scenariusze użycia dla właściwości zależności i dołączonych właściwości, zobacz [niestandardowe właściwości zależności](custom-dependency-properties.md).

- Możesz również zarejestrować właściwość jako właściwość dołączoną, a jako właściwość zależności, a następnie nadal ujawniać implementacje "otoka". W takim przypadku Właściwość można ustawić na tym elemencie lub w dowolnym elemencie za pomocą składni właściwości dołączonej XAML. Przykładem właściwości z odpowiednim scenariuszem dla standardowych i dołączonych użycia jest <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.DependencyProperty>
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rejestrowanie dołączonej właściwości](how-to-register-an-attached-property.md)
