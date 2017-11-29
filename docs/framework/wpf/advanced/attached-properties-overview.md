---
title: "Przegląd Właściwości dołączone"
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
helpviewer_keywords: attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1c33dc50d028dbe818d531ffac1d24b7152a2538
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="attached-properties-overview"></a>Przegląd Właściwości dołączone
Dołączona właściwość to pojęcie, zdefiniowane przez XAML. Dołączona właściwość jest przeznaczona do użycia jako typ właściwości globalnych można ustawić dla dowolnego obiektu. W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], dołączone właściwości są zazwyczaj definiowane jako specjalna forma właściwości zależności, która nie ma właściwości konwencjonalnych "otoki".  
  
   
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono zrozumieć właściwości zależności z punktu widzenia użytkownika istniejących właściwości zależności na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klas i przeczytanie [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Aby użyć przykłady w tym temacie, należy również zrozumieć XAML i wiedzieć, jak napisać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
<a name="attached_properties_usage"></a>   
## <a name="why-use-attached-properties"></a>Dlaczego warto używać dołączone właściwości  
 Jeden cel dołączona właściwość jest umożliwienie podrzędnych różne elementy, aby określić unikatowe wartości dla właściwości, która faktycznie jest zdefiniowany w elemencie nadrzędnym. Określonej aplikacji w tym scenariuszu ma elementy podrzędne powiadamia element nadrzędny jak są one przedstawiane w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Przykładem jest <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> właściwości. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Właściwość zostanie utworzona jako dołączona właściwość, ponieważ ma ona można ustawić dla elementów, które są zawarte w <xref:System.Windows.Controls.DockPanel>, a nie na <xref:System.Windows.Controls.DockPanel> samej siebie. <xref:System.Windows.Controls.DockPanel> Klasa definiuje statycznych <xref:System.Windows.DependencyProperty> pola o nazwie <xref:System.Windows.Controls.DockPanel.DockProperty>, a następnie oferuje <xref:System.Windows.Controls.DockPanel.GetDock%2A> i <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody jako publiczny akcesor dołączona właściwość.  
  
<a name="attached_properties_xaml"></a>   
## <a name="attached-properties-in-xaml"></a>Dołączone właściwości w języku XAML  
 W języku XAML, dołączone właściwości można ustawić przy użyciu składni *AttachedPropertyProvider*. *PropertyName*  
  
 Poniżej przedstawiono przykład sposobu można ustawić <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> w języku XAML:  
  
 [!code-xaml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]  
  
 Należy pamiętać, że użycie nieco podobnie jak właściwość statyczna; zawsze odwołanie do typu <xref:System.Windows.Controls.DockPanel> który jest właścicielem i rejestruje dołączona właściwość zamiast odwołujących się do dowolnego wystąpienia określonego przez nazwę.  
  
 Ponadto ponieważ dołączona właściwość w języku XAML jest atrybut, który można ustawić w znaczniku, tylko operacji set ma wszelkie znaczenie. Nie można bezpośrednio uzyskać właściwości w języku XAML, chociaż są niektóre pośrednie mechanizmy do porównywania wartości, takich jak wyzwalacze w stylach (Aby uzyskać więcej informacji, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)).  
  
### <a name="attached-property-implementation-in-wpf"></a>Dołączona właściwość wdrożenia na platformie WPF  
 W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], większość dołączone właściwości, które istnieją na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typów, które są powiązane z prezentacją interfejsu użytkownika są zaimplementowane jako właściwości zależności. Dołączone właściwości są pojęcie XAML właściwości zależności są [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koncepcji. Ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości zależności są dołączone właściwości, obsługuje pojęcia dotyczące właściwości zależności, takich jak metadanych właściwości i wartości z tych metadanych właściwości domyślnych.  
  
<a name="howused"></a>   
## <a name="how-attached-properties-are-used-by-the-owning-type"></a>W jaki sposób dołączone właściwości są używane przez typ będący właścicielem  
 Choć dołączone właściwości można ustawić dla dowolnego obiektu, który nie automatycznie oznacza, że ustawienie właściwości da wynik wymierne, lub czy wartość kiedykolwiek będzie używany przez inny obiekt. Ogólnie rzecz biorąc dołączone właściwości mają tak, aby każdy raport informacji wspólnych do typu, który definiuje dołączona właściwość można obiektów pochodzących z szeroką gamę możliwości klasy hierarchie lub relacje logiczne. Typ, który definiuje dołączona właściwość zwykle stosowany jest jeden z tych modeli:  
  
-   Typ, który definiuje dołączona właściwość zaprojektowano tak, aby może być elementem nadrzędnym elementów, które spowoduje ustawienie wartości dla właściwości dołączone. Następnie typ iteruje po jego obiektów podrzędnych za pomocą wewnętrznej logiki względem niektórych strukturę drzewa obiektów, uzyskuje wartości i działa na tych wartości w jakikolwiek sposób.  
  
-   Typ, który definiuje dołączona właściwość będzie służyć jako element podrzędny dla różnych elementy nadrzędne możliwe i modele zawartości.  
  
-   Typ, który definiuje dołączona właściwość reprezentuje usługi. Inne typy Ustaw wartości dołączona właściwość. Następnie gdy element ustaw właściwość jest obliczane w kontekście usługi, dołączona właściwość wartości są uzyskiwane za pośrednictwem wewnętrznego logiki klasy usługi.  
  
### <a name="an-example-of-a-parent-defined-attached-property"></a>Przykład zdefiniowane nadrzędnego dołączona właściwość  
 Najbardziej typowym scenariuszem gdzie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definiuje dołączona właściwość jest, gdy element nadrzędny obsługuje kolekcji elementów podrzędnych, a także implementuje zachowanie gdzie szczegółowe informacje na temat zachowania są raportowane osobno dla każdego elementu podrzędnego.  
  
 <xref:System.Windows.Controls.DockPanel>definiuje <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączonych właściwości, oraz <xref:System.Windows.Controls.DockPanel> ma kod poziomie klas w ramach swojej logiki renderowania (w szczególności <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> i <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). A <xref:System.Windows.Controls.DockPanel> wystąpienie będzie zawsze Sprawdź, czy ustawiono żadnego z jego elementów podrzędnych natychmiastowego wartość <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Jeśli tak, te wartości stają się dane wejściowe dla logiki renderowania stosowane do tego elementu podrzędnego określonego. Zagnieżdżone <xref:System.Windows.Controls.DockPanel> wystąpień każdej Traktuj własnych bezpośrednio podrzędne elementu kolekcji, ale to zachowanie jest konkretnej implementacji jak <xref:System.Windows.Controls.DockPanel> procesów <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> wartości. Użytkownik może teoretycznie dołączono właściwości wpływające na elementów poza natychmiastowego obiektu nadrzędnego. Jeśli <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączona właściwość jest ustawiona na element, który nie ma <xref:System.Windows.Controls.DockPanel> elementu nadrzędnego działanie go nie błąd lub wyjątek jest wywoływane. Oznacza to po prostu czy ustawiono wartość właściwości globalnej, ale nie ma bieżącej <xref:System.Windows.Controls.DockPanel> nadrzędnej, czy można korzystać z informacji.  
  
<a name="attached_properties_code"></a>   
## <a name="attached-properties-in-code"></a>Dołączone właściwości w kodzie  
 Dołączone właściwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie ma typowe [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "otoki" metod get/set łatwy dostęp. Jest to spowodowane dołączona właściwość nie jest częścią niekoniecznie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzeń nazw dla wystąpień, gdy właściwość jest ustawiona. Jednak procesora XAML musi mieć możliwość ustawienia tych wartości, gdy zostanie przeanalizowany XAML. Do obsługi użycia skutecznego dołączonej właściwości, typ właściciela dołączona właściwość musi implementować metody dostępu dedykowanych w formie `Get` *PropertyName* i `Set` *PropertyName*. Te metody dostępu dedykowanych są także przydatne do pobierania lub ustawiania dołączona właściwość w kodzie. Z punktu widzenia kodu dołączona właściwość jest podobne do pola zapasowy, która ma metody dostępu metody zamiast metod dostępu do właściwości i że kopii pola może istnieć na dowolny obiekt zamiast konieczności specjalnie zdefiniowania.  
  
 W poniższym przykładzie pokazano, jak można ustawić właściwości dołączonej w kodzie. W tym przykładzie `myCheckBox` jest wystąpieniem <xref:System.Windows.Controls.CheckBox> klasy.  
  
 [!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
 [!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]  
  
 Przypadek podobny do pliku XAML, jeśli `myCheckBox` nie była już dodana jako element podrzędny elementu `myDockPanel` przez trzeciego wiersza kodu, czwartego wiersza kodu nie może zgłosić wyjątek, ale wartość właściwości nie może współpracować z <xref:System.Windows.Controls.DockPanel> nadrzędnego, dlatego czy nic nie rób. Tylko <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> wartość zestaw w połączeniu z obecności elementu podrzędnego <xref:System.Windows.Controls.DockPanel> elementu nadrzędnego spowoduje zachowanie skuteczne w renderowanym aplikacji. (W takim przypadku użytkownik może ustawić dołączona właściwość, a następnie dołącz do drzewa. Lub możesz można dołączyć do drzewa, a następnie ustaw dołączona właściwość. Albo kolejność akcji zawiera ten sam rezultat.)  
  
<a name="attached_properties_metadata"></a>   
## <a name="attached-property-metadata"></a>Dołączona właściwość metadanych  
 Podczas rejestrowania właściwości <xref:System.Windows.FrameworkPropertyMetadata> ma ustawioną wartość określ cechy właściwości, takie jak czy właściwość wpływa na renderowanie, miary i tak dalej. Metadane dla właściwości dołączonej zazwyczaj nie różni się od we właściwości zależności. Jeśli w zastąpieniu metadanych dołączona właściwość określać wartość domyślną, wartość staje się wartością domyślną niejawne dołączonych właściwości wystąpienia klasy nadrzędne. W szczególności wartość domyślna jest zgłaszany, gdy niektóre przetwarzania zapytań dla wartości właściwości dołączonej za pośrednictwem `Get` akcesor — metoda dla tej właściwości, określając wystąpienia klasy, w którym określone metadanych i wartości dla tej dołączona właściwość był w przeciwnym razie nie jest ustawiona.  
  
 Jeśli chcesz włączyć dziedziczenie wartości właściwości dla właściwości, należy używać dołączone właściwości zamiast właściwości zależności nie jest dołączony. Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
<a name="custom"></a>   
## <a name="custom-attached-properties"></a>Niestandardowe dołączone właściwości  
  
<a name="create_attached_properties"></a>   
### <a name="when-to-create-an-attached-property"></a>Kiedy należy utworzyć dołączona właściwość  
 Dołączona właściwość można utworzyć po Przyczyna mieć właściwość ustawienie mechanizm dostępne dla klasy niż klasa definiującego. Najbardziej typowym scenariuszem dla tego jest układu. Przykłady istniejącej właściwości układu <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>, i <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>. Scenariusz włączona w tym miejscu jest to, że elementów, które istnieją jako elementy podrzędne do sterowania układem elementy będą mogli express układu wymagania dotyczące ich elementów nadrzędnych układu pojedynczo, każdego ustawienia wartości właściwości nadrzędnego jest zdefiniowany jako podłączone Właściwość.  
  
 Inny scenariusz użycia dołączona właściwość jest, gdy klasa reprezentuje usługę, a użytkownik chce klas, aby można było więcej niewidocznie zintegrować usługę.  
  
 Jeszcze inny scenariusz ma otrzymywać [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] pomocy technicznej, takich jak **właściwości** okno edycji. Aby uzyskać więcej informacji, zobacz [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Jak wspomniano wcześniej, jeśli chcesz użyć wartości dziedziczenia należy zarejestrować jako dołączona właściwość.  
  
<a name="how_do_i_create_attached_properties"></a>   
### <a name="how-to-create-an-attached-property"></a>Jak utworzyć dołączona właściwość  
 Jeśli klasa jest zdefiniowanie dołączona właściwość wyłącznie do użytku dla innych typów, a następnie klasy nie musi pochodzić od <xref:System.Windows.DependencyObject>. Jednak muszą pochodzić z <xref:System.Windows.DependencyObject> Jeśli wykonujesz ogólnych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelu o Twojej dołączona właściwość również być właściwością zależności.  
  
 Definiowanie sieci dołączonej właściwości jako właściwość zależności od zadeklarowania `public` `static` `readonly` pole typu <xref:System.Windows.DependencyProperty>. To pole jest definiowane za pomocą wartość zwracaną <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody. Nazwa pola musi odpowiadać nazwie dołączona właściwość, dołączony ciąg `Property`, które należy wykonać w ustalonych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wzorzec nazewnictwa identyfikacji pola i właściwości, które reprezentują. Dołączona właściwość dostawcy należy również podać statyczne `Get` *PropertyName* i `Set` *PropertyName* metody jako metody dostępu dla dołączona właściwość; się niepowodzeniem, spowoduje to zrobić wynikiem właściwości systemu nie będą mogli korzystać z dołączona właściwość.  
  
> [!NOTE]
>  Pominięcie metody dostępu get dołączona właściwość powiązania danych we właściwości nie będzie działać w narzędzi projektowania, takich jak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] i Expression Blend.  
  
#### <a name="the-get-accessor"></a>Metoda dostępu Get  
 Podpis dla `Get` *PropertyName* akcesora musi być:  
  
 `public static object Get`*PropertyName* `(object` `target`  `)`  
  
-   `target` Obiektu można określić jako bardziej określonego typu w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> metody typy jako parametr <xref:System.Windows.UIElement>, ponieważ dołączona właściwość jest przeznaczona tylko do można ustawić na <xref:System.Windows.UIElement> wystąpień.  
  
-   Wartość zwracana można określić jako bardziej określonego typu w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.GetDock%2A> metody typy go jako <xref:System.Windows.Controls.Dock>, ponieważ wartość można ustawić tylko do tego wyliczenia.  
  
#### <a name="the-set-accessor"></a>Metody dostępu Set  
 Podpis dla `Set` *PropertyName* akcesora musi być:  
  
 `public static void Set`*PropertyName* `(object` `target` `, object` `value`    `)`  
  
-   `target` Obiektu można określić jako bardziej określonego typu w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody typy go jako <xref:System.Windows.UIElement>, ponieważ dołączona właściwość jest przeznaczona tylko do można ustawić na <xref:System.Windows.UIElement> wystąpień.  
  
-   `value` Obiektu można określić jako bardziej określonego typu w implementacji. Na przykład <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody typy go jako <xref:System.Windows.Controls.Dock>, ponieważ wartość można ustawić tylko do tego wyliczenia. Należy pamiętać, że wartość ta metoda jest danych wejściowych przesyłanych przez moduł ładujący XAML po napotkaniu Twojej dołączona właściwość wykorzystania dołączona właściwość w znaczniku. Czy dane wejściowe jest podana jako wartość atrybutu XAML w znaczniku. W związku z tym musi istnieć konwersji typu, wartość serializator lub obsługa rozszerzenia znaczników dla typu używanego taki sposób, że można tworzyć odpowiedniego typu na podstawie wartości atrybutu (co ostatecznie jest po prostu określonym ciągiem).  
  
 W poniższym przykładzie przedstawiono rejestracji właściwości zależności (przy użyciu <xref:System.Windows.DependencyProperty.RegisterAttached%2A> — metoda), a także `Get` *PropertyName* i `Set` *PropertyName* metody dostępu . W tym przykładzie nazwa dołączonej właściwości jest `IsBubbleSource`. W związku z tym musi mieć nazwę metody dostępu `GetIsBubbleSource` i `SetIsBubbleSource`.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
#### <a name="attached-property-attributes"></a>Dołączona właściwość atrybutów  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]definiuje kilka [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] które są przeznaczone do dostarczania informacji dotyczących dołączonych właściwości do procesów odbicia i użytkownikom typowych informacji odbicia i właściwości, takie jak projektantów. Ponieważ dołączonych właściwości Typ nieograniczonego zakresu, projektantów muszą sposobem uniknięcia utrudnione użytkowników z globalnej listy wszystkich dołączonych właściwości, które są zdefiniowane w implementacji określonej technologii, która używa języka XAML. [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] Który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definiuje dla dołączone właściwości może służyć do określania zakresu w sytuacjach, gdy dana właściwość dołączone powinny być wyświetlane w oknie właściwości. Warto również zastosowanie atrybutów dla własnego niestandardowego dołączone właściwości. Cel i składnia [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] opisano na stronach odpowiednie odwołanie:  
  
-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>  
  
<a name="more"></a>   
## <a name="learning-more-about-attached-properties"></a>Dowiedzieć się więcej na temat dołączone właściwości  
  
-   Aby uzyskać więcej informacji na temat tworzenia dołączona właściwość, zobacz [zarejestrować dołączonych właściwości](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md).  
  
-   Aby uzyskać więcej zaawansowane scenariusze użycia dotyczące właściwości zależności i dołączone do właściwości, zobacz [właściwości zależności niestandardowe](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
-   Możesz też zarejestrować właściwość jako dołączona właściwość, a jako właściwość zależności, ale nadal następnie uwidaczniaj implementacje "otoki". W takim przypadku właściwość można ustawić w tym elemencie, lub w dowolnym elemencie za pośrednictwem XAML dołączony składni właściwości. Na przykład właściwość o to odpowiedni scenariusz dotyczący użycia standardowe i dołączone <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.DependencyProperty>  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Właściwości niestandardowe zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Zarejestruj dołączona właściwość](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)
