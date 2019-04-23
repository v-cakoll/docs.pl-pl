---
title: Przegląd Wiązanie źródeł
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
ms.openlocfilehash: 72ef84cb53c6eff1fc2fb9459b40e780869243a1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145928"
---
# <a name="binding-sources-overview"></a>Przegląd Wiązanie źródeł
W powiązaniu danych obiektu źródłowego powiązania odnosi się do obiektu, który można uzyskać danych z. W tym temacie omówiono typy obiektów, których można użyć jako źródło wiążące.  

<a name="binding_sources"></a>   
## <a name="binding-source-types"></a>Typy źródeł powiązania  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Powiązanie danych obsługuje następujące typy źródło powiązania:  
  
|Źródło wiążące|Opis|  
|--------------------|-----------------|  
|[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] Obiekty|Można powiązać właściwości publiczne, właściwości podrzędnych, a także indeksatory dowolnego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektu. Korzysta z aparatu powiązania [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] odbicia w celu uzyskania wartości właściwości. Alternatywnie, obiekty, które implementują <xref:System.ComponentModel.ICustomTypeDescriptor> lub masz zarejestrowany <xref:System.ComponentModel.TypeDescriptionProvider> również współpracować z aparatem powiązania.<br /><br /> Aby uzyskać więcej informacji na temat implementacji klasy, który może służyć jako źródło powiązania, zobacz [Implementowanie klasy źródło wiążące](#classes) w dalszej części tego tematu.|  
|obiekty dynamiczne|Możesz powiązać dostępnych właściwości i indeksatorów obiektu, który implementuje <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejsu. Jeśli uzyskujesz dostęp do elementu członkowskiego w kodzie, można ją powiązać. Na przykład, jeśli obiekt dynamiczny pozwala na uzyskiwanie dostępu do członka w kodzie za pomocą `someObjet.AProperty`, można powiązać je, ustawiając ścieżka powiązania `AProperty`.|  
|[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] Obiekty|Możesz powiązać [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] obiekty, takie jak <xref:System.Data.DataTable>. [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] <xref:System.Data.DataView> Implementuje <xref:System.ComponentModel.IBindingList> interfejs, który zawiera powiadomienia o zmianach, które wykrywa aparat powiązania.|  
|[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] Obiekty|Możesz powiązać i uruchomić `XPath` zapytanie na <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlDocument>, lub <xref:System.Xml.XmlElement>. Wygodny sposób, aby uzyskać dostęp do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane źródło wiążące w znacznikach jest użycie <xref:System.Windows.Data.XmlDataProvider> obiektu. Aby uzyskać więcej informacji, zobacz [powiązania danych XML przy użyciu XMLDataProvider i zapytań XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Możesz również powiązać <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>, lub powiązać z wynikami zapytania uruchamiane na obiektach tego typu za pomocą LINQ to XML. Wygodny sposób używania składnika LINQ to XML z danymi XML dostępu, który jest źródłem powiązania w znacznikach jest użycie <xref:System.Windows.Data.ObjectDataProvider> obiektu. Aby uzyskać więcej informacji, zobacz [Powiąż z dokumentem, elementem x lub LINQ dla wyników zapytań XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|  
|<xref:System.Windows.DependencyObject> Obiekty|Można powiązać właściwości zależności dowolnego <xref:System.Windows.DependencyObject>. Aby uzyskać przykład, zobacz [powiązywanie właściwości dwóch formantów](how-to-bind-the-properties-of-two-controls.md).|  
  
<a name="classes"></a>   
## <a name="implementing-a-class-for-the-binding-source"></a>Implementowanie klasy źródło wiążące  
 Możesz tworzyć własne źródła powiązania. W tej sekcji omówiono czynności, musisz wiedzieć, w przypadku wdrażania klasę, która będzie służyć jako źródło wiążące.  
  
### <a name="providing-change-notifications"></a>Dostarczanie powiadomień o zmianach  
 Jeśli używasz albo <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> powiązania (ponieważ chcesz, aby usługi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aktualizacji podczas dynamicznie zmieniać właściwości źródła powiązania), musisz zaimplementować mechanizm powiadamiania odpowiednie zmiany właściwości. Mechanizm zalecane jest [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] lub dynamicznej klasy do zaimplementowania <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Aby uzyskać więcej informacji, zobacz [powiadomienie o zmianie właściwości Implementowanie](how-to-implement-property-change-notification.md).  
  
 Jeśli tworzysz [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu, który nie implementuje <xref:System.ComponentModel.INotifyPropertyChanged>, a następnie musisz przyrostowo rozmieścić dla własnego systemu powiadomień upewnić się, że dane używane w powiązaniu pozostaje bieżącego. Możesz podać powiadomienia o zmianie dzięki obsłudze `PropertyChanged` wzorca dla każdej właściwości, który ma być powiadomienia o zmianach. Aby obsługiwać tego wzorca, należy zdefiniować *PropertyName*zmieniono zdarzenia dla każdej właściwości, gdzie *PropertyName* jest nazwą właściwości. Możesz zgłosić zdarzenie, za każdym razem, gdy zmieni się właściwość.  
  
 Jeśli Twoje źródło wiążące implementuje jedną z tych mechanizmów wysyłania powiadomień, kierować aktualizacje następują automatycznie. Jeśli jakiegokolwiek powodu, Twoje źródło powiązania nie udostępnia odpowiednich właściwości zmienione powiadomienia, masz możliwość użycia <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> metodę, aby zaktualizować właściwości docelowej jawnie.  
  
### <a name="other-characteristics"></a>Inne właściwości  
 Na poniższej liście przedstawiono inne ważne punkty, które należy zwrócić uwagę:  
  
-   Jeśli chcesz utworzyć obiekt w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], klasa musi mieć domyślnego konstruktora. W niektórych [!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)] języków, takich jak C#, Konstruktor domyślny może być utworzona.  
  
-   Właściwości służy jako powiązania właściwości źródła powiązania musi być publicznymi właściwościami klasy. Interfejs jawnie zdefiniowanych właściwości nie są dostępne dla powiązania celów, ani nie może chronione, prywatne, wewnętrzne lub wirtualnych właściwości, które nie mają podstawowej implementacji.  
  
-   Nie można powiązać pola publiczne.  
  
-   Typ właściwości zadeklarowana w klasie jest typ, który jest przekazywany do powiązania. Typ ostatecznie używanym przez wiązanie zależy jednak od tego, jaki typ powiązania właściwości docelowej, a nie właściwości źródła powiązania. Istnieje następująca różnica w typie, można napisać konwerter służący do obsługi, jak właściwości niestandardowej początkowo jest przekazywany do powiązania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.IValueConverter>.  
  
<a name="objects"></a>   
## <a name="using-entire-objects-as-a-binding-source"></a>Przy użyciu całe obiekty jako źródło wiążące  
 Cały obiekt służy jako źródło wiążące. Należy określić źródło wiążące za pomocą <xref:System.Windows.Data.Binding.Source%2A> lub <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości, a następnie podaj deklaracji powiązania puste: `{Binding}`. Scenariusze, w których jest to przydatne obejmują obsługę powiązań do obiektów, które są typu ciąg, powiązanie do obiektów z wieloma właściwościami, który Cię interesuje, lub powiązanie z kolekcji obiektów. Na przykład powiązanie z obiektem całą kolekcję zobacz [Użyj wzorca szczegółowego z danymi hierarchicznymi](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Należy pamiętać, że może być konieczne stosowanie logiki niestandardowej tak, aby dane były zrozumiałe dla z powiązanej własności docelowej. Niestandardowej logiki może być w formie konwertera niestandardowych (Jeśli nie ma domyślnej konwersji typów) lub <xref:System.Windows.DataTemplate>. Aby uzyskać więcej informacji na temat konwerterów, zobacz sekcję Konwersja danych [Przegląd wiązanie danych](data-binding-overview.md). Aby uzyskać więcej informacji na temat szablonów danych zobacz [Przegląd Szablonowanie danych](data-templating-overview.md).  
  
<a name="collections"></a>   
## <a name="using-collection-objects-as-a-binding-source"></a>Przy użyciu kolekcji obiektów jako źródło wiążące  
 Często obiekt, który ma być używany jako źródło wiążące to zbiór obiektów niestandardowych. Każdy obiekt służy jako źródło dla jednego wystąpienia powtarzanych powiązania. Na przykład, Niewykluczone, że `CustomerOrders` kolekcji, która składa się z `CustomerOrder` obiektów, w którym aplikacja iteruje po kolekcji, aby stwierdzić, jak wiele zamówień i danych znajdujących się w każdym.  
  
 Można wyliczyć za pośrednictwem kolekcji, która implementuje <xref:System.Collections.IEnumerable> interfejsu. Jednak aby skonfigurować dynamiczne powiązania tak, aby zaktualizować wstawienia i usunięcia w kolekcji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automatycznie, Kolekcja musi implementować <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejsu. Ten interfejs przedstawia zdarzenie, które musi zostać wywołane, zawsze wtedy, gdy zmienia się kolekcja bazowego.  
  
 <xref:System.Collections.ObjectModel.ObservableCollection%601> Klasa jest wbudowanych implementacji zbierania danych, która udostępnia <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejsu. Obiekty danych w kolekcji musi spełniać wymagania opisane w poprzednich sekcjach. Aby uzyskać przykład, zobacz [Utwórz i powiąż z ObservableCollection](how-to-create-and-bind-to-an-observablecollection.md). Przed wdrożeniem własną kolekcję, należy wziąć pod uwagę przy użyciu <xref:System.Collections.ObjectModel.ObservableCollection%601> lub jeden z istniejących kolekcji klasy takie jak <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, i <xref:System.ComponentModel.BindingList%601>, wiele innych.  
  
 WPF nigdy nie wiąże się bezpośrednio do kolekcji. Jeśli określisz kolekcji jako źródło powiązania WPF faktycznie wiąże się do widoku domyślnego kolekcji. Aby uzyskać informacje o widokach domyślnych, zobacz [Przegląd wiązanie danych](data-binding-overview.md).  
  
 Jeśli chcesz zaimplementować własną kolekcję mają zaawansowany scenariusz, należy rozważyć użycie <xref:System.Collections.IList> interfejsu. <xref:System.Collections.IList> udostępnia nieogólna kolekcja obiektów, które mogą być udostępniane oddzielnie za pomocą indeksu, co może poprawić wydajność.  
  
<a name="permissions"></a>   
## <a name="permission-requirements-in-data-binding"></a>Wymagania dotyczące uprawnień w powiązaniu danych  
 Gdy powiązania danych, należy rozważyć poziom zaufania aplikacji. Poniższa tabela zawiera podsumowanie właściwości, jakie typy mogą być powiązane w aplikacji, które jest wykonywane w trybie pełnego zaufania lub częściowej relacji zaufania:  
  
|Typ właściwości<br /><br /> (wszystkie modyfikatory dostępu)|Właściwości dynamiczne obiektu|Właściwości dynamiczne obiektu|Właściwość CLR|Właściwość CLR|Właściwości zależności|Właściwości zależności|  
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|  
|**Poziom zaufania**|**Pełne zaufanie**|**Częściowej relacji zaufania**|**Pełne zaufanie**|**Częściowej relacji zaufania**|**Pełne zaufanie**|**Częściowej relacji zaufania**|  
|Klasa publiczna|Yes|Yes|Yes|Yes|Yes|Tak|  
|Klasa niepubliczne|Tak|Nie|Yes|Nie|Yes|Tak|  
  
 W tej tabeli opisano następujące ważne kwestie dotyczące wymagania dotyczące uprawnień w powiązaniu danych:  
  
-   Aby uzyskać [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości powiązania danych działa tak długo, jak długo silnik powiązania jest mogli korzystać z właściwości źródła powiązania przy użyciu odbicia. W przeciwnym razie aparat powiązania generuje ostrzeżenie, że nie można odnaleźć właściwości i używa rezerwowej wartość lub wartość domyślną, jeśli jest ona dostępna.  
  
-   Można powiązać właściwości obiektów dynamicznych, które są zdefiniowane podczas kompilacji w czasie lub w czasie wykonywania.  
  
-   Zawsze można powiązać właściwości zależności.  
  
 Wymagane uprawnienia dla [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] powiązania jest podobny. W piaskownicy częściowego zaufania <xref:System.Windows.Data.XmlDataProvider> zakończy się niepowodzeniem, gdy nie ma uprawnień dostępu określone dane.  
  
 Obiekty typu anonimowego są wewnętrzne. Tylko wtedy, gdy jest uruchomiona w trybie pełnego zaufania, można powiązać właściwości anonimowych typów. Aby uzyskać więcej informacji na temat typów anonimowych, zobacz [typy anonimowe (C# Programming Guide)](~/docs/csharp/programming-guide/classes-and-structs/anonymous-types.md) lub [typy anonimowe (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic).  
  
 Aby uzyskać więcej informacji o zabezpieczeniach częściowego zaufania, zobacz [zabezpieczenie z częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.ObjectDataProvider>
- <xref:System.Windows.Data.XmlDataProvider>
- [Określanie obiektu źródłowego powiązania](how-to-specify-the-binding-source.md)
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
- [Powiązanie danych WPF za pomocą LINQ to XML — omówienie](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [Powiązanie danych](../advanced/optimizing-performance-data-binding.md)
