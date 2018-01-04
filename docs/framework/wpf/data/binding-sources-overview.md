---
title: "Przegląd Wiązanie źródeł"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88f1a22fc15e85e687c7b7eeb0a6e01445277d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="binding-sources-overview"></a>Przegląd Wiązanie źródeł
W powiązaniu danych powiązania obiekt źródłowy odwołuje się do obiektu, do którego pobrane dane. W tym temacie omówiono typy obiektów, których można użyć jako źródła powiązania.  
  
  
  
<a name="binding_sources"></a>   
## <a name="binding-source-types"></a>Typy źródeł powiązania  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Powiązanie danych obsługuje następujące typy źródeł powiązania:  
  
|Budowanie źródła|Opis|  
|--------------------|-----------------|  
|[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]obiekty|Można powiązać właściwości publiczne, właściwości podrzędnej, a także indeksatory dowolnego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektu. Aparat wiązania używa [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] odbicia można pobrać wartości właściwości. Alternatywnie obiekty, które implementują <xref:System.ComponentModel.ICustomTypeDescriptor> lub ma zarejestrowaną <xref:System.ComponentModel.TypeDescriptionProvider> również współpracować z aparat wiązania.<br /><br /> Aby uzyskać więcej informacji dotyczących sposobu wdrażania klasę, która może służyć jako źródło powiązania, zobacz [Implementacja klasy dla powiązania źródła](#classes) dalszej części tego tematu.|  
|obiekty dynamiczne|Można powiązać z dostępnych właściwości i indeksatorów obiektu, który implementuje <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejsu. Jeśli uzyskujesz dostęp do elementu członkowskiego w kodzie, można go powiązać. Na przykład, jeśli obiekt dynamiczny pozwala na uzyskiwanie dostępu do członka w kodzie za pomocą `someObjet.AProperty`, można powiązać go przez ustawienie ścieżkę wiązania `AProperty`.|  
|[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)]obiekty|Można powiązać [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] obiekty, takie jak <xref:System.Data.DataTable>. [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] <xref:System.Data.DataView> Implementuje <xref:System.ComponentModel.IBindingList> interfejsu, która dostarcza powiadomienia o zmianach, które nasłuchuje aparat wiązania.|  
|[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]obiekty|Możesz powiązać i uruchomić `XPath` zapytanie na <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlDocument>, lub <xref:System.Xml.XmlElement>. Dogodny dostęp do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych, który jest źródłem powiązania w znaczniku jest użycie <xref:System.Windows.Data.XmlDataProvider> obiektu. Aby uzyskać więcej informacji, zobacz [powiązania danych XML przy użyciu XMLDataProvider i kwerendy XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Można także powiązać <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>, lub z wyników zapytania, uruchom na obiektach tego typu za pomocą LINQ do XML. Wygodnym sposobem użycia LINQ do XML do dostępu do danych XML, który jest źródłem powiązania w znaczniku jest użycie <xref:System.Windows.Data.ObjectDataProvider> obiektu. Aby uzyskać więcej informacji, zobacz [powiązanie klasy XDocument, klasy XElement lub LINQ dla wyników zapytania XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|  
|<xref:System.Windows.DependencyObject>obiekty|Można powiązać propertiesof zależności żadnego <xref:System.Windows.DependencyObject>. Na przykład zobacz [powiązanie właściwości formantów dwóch](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md).|  
  
<a name="classes"></a>   
## <a name="implementing-a-class-for-the-binding-source"></a>Implementacja klasy dla powiązania źródła  
 Można utworzyć źródła powiązania. W tej sekcji omówiono rzeczy, o których należy wiedzieć, jeśli są Implementacja klasy służyć jako źródło powiązania.  
  
### <a name="providing-change-notifications"></a>Dostarczanie powiadomień o zmianie  
 Jeśli używasz albo <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> powiązania (ponieważ chcesz, Twoje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] można zaktualizować powiązania właściwości źródła zmiany dynamicznie), musisz zaimplementować mechanizm powiadamiania odpowiednie zmiany właściwości. Mechanizm zalecane jest przeznaczony dla [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] lub dynamiczne klasy do zaimplementowania <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Aby uzyskać więcej informacji, zobacz [powiadomienia o zmianie właściwości wdrożenie](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
 W przypadku utworzenia [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu, który nie implementuje <xref:System.ComponentModel.INotifyPropertyChanged>, a następnie musisz rozmieścić na upewnij się, że dane używane w powiązaniu pozostaje bieżącego własny system powiadomień. Możesz podać powiadomienia o zmianie dzięki obsłudze `PropertyChanged` wzorca dla każdej właściwości, która ma być powiadomienia o zmianach. Aby obsługiwać tego wzorca, należy zdefiniować *PropertyName*zmienione zdarzenie dla każdej właściwości, gdzie *PropertyName* jest nazwą właściwości. Należy zgłosić zdarzenie, każdej zmianie właściwości.  
  
 Jeśli źródłowy powiązanie implementuje jednego z tych mechanizmów powiadomień, kierować aktualizacje wykonywane automatycznie. Zmiana przyczyny źródła powiązanie nie ma prawidłowego właściwości powiadomienia masz możliwość użycia <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> metoda jawnie zaktualizować właściwość target.  
  
### <a name="other-characteristics"></a>Inne właściwości  
 Poniższa lista zawiera inne ważne informacje, należy pamiętać:  
  
-   Jeśli chcesz utworzyć obiekt w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], klasy musi mieć konstruktora domyślnego. W niektórych [!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)] języków, takich jak [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], może być utworzony konstruktora domyślnego.  
  
-   Właściwości służy jako powiązanie właściwości źródła dla powiązania musi być publiczny właściwości klasy. Nie można uzyskać dostępu do właściwości interfejsu jawnie zdefiniowanych dla powiązania celów ani można chronionych, prywatnych, wewnętrznych ani wirtualnego właściwości, które mają żadnej implementacji podstawowej.  
  
-   Nie można powiązać pola publiczne.  
  
-   Typ właściwości zadeklarowana w klasie jest typu, który jest przekazywany do powiązania. Jednak typu ostatecznie używanym przez wiązanie zależy od typu powiązania właściwości docelowej, a nie właściwość powiązania źródła. Jeśli występuje różnica w typie, można zapisać konwerter służący do obsługi, jak właściwości niestandardowej początkowo jest przekazywana do powiązania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.IValueConverter>.  
  
<a name="objects"></a>   
## <a name="using-entire-objects-as-a-binding-source"></a>Przy użyciu całej obiektów jako źródło powiązania  
 Cały obiekt może być używany jako źródło powiązania. Można określić źródło powiązania za pomocą <xref:System.Windows.Data.Binding.Source%2A> lub <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości, a następnie podaj deklaracji puste powiązania: `{Binding}`. Scenariusze, w których jest to przydatne obejmują powiązanie do obiektów, które są typu ciąg powiązanie do obiektów z wielu właściwości, które planuje się lub powiązanie z kolekcji obiektów. Na przykład powiązanie z obiektem całą kolekcję zobacz [Użyj wzorca wzorzec-szczegół z danymi hierarchicznymi](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Należy pamiętać, że może być konieczne zastosowanie niestandardowej logiki tak, aby dane były zrozumiałą dla użytkownika właściwość target powiązane. Niestandardowej logiki może być w formie konwertera niestandardowe (Jeśli nie istnieje konwersja typu domyślne) lub <xref:System.Windows.DataTemplate>. Aby uzyskać więcej informacji na temat konwerterów, zobacz sekcję Konwersja danych [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md). Aby uzyskać więcej informacji na temat szablonów danych, zobacz [omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="collections"></a>   
## <a name="using-collection-objects-as-a-binding-source"></a>Za pomocą kolekcji obiektów jako źródło powiązania  
 Często obiekt, który ma być używany jako źródło powiązania jest kolekcją obiektów niestandardowych. Każdy obiekt służy jako źródło dla jedno wystąpienie elementu powtarzanego powiązania. Na przykład może być `CustomerOrders` kolekcji, która składa się z `CustomerOrder` obiektów, w którym aplikacja wykonuje iterację na kolekcji, aby określić, ile zamówień istnieje i dane zawarte w każdej.  
  
 Można wyliczać za pośrednictwem kolekcji, która implementuje <xref:System.Collections.IEnumerable> interfejsu. Jednak aby skonfigurować dynamiczne powiązania, aby zaktualizować wstawienia lub usunięć w kolekcji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automatycznie, Kolekcja musi zawierać <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejsu. Ten interfejs przedstawia zdarzenie musi wywoływane zawsze, gdy zmienia się kolekcja źródłowa.  
  
 <xref:System.Collections.ObjectModel.ObservableCollection%601> Klasy jest wbudowane implementacji zbierania danych, który ujawnia <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejsu. Obiekty danych poszczególnych w kolekcji musi spełniać wymagania opisane w poprzednich sekcjach. Na przykład zobacz [tworzą i Powiązują do obiektu ObservableCollection](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md). Przed wdrożeniem swojej kolekcji, należy rozważyć użycie <xref:System.Collections.ObjectModel.ObservableCollection%601> lub jeden z istniejącą kolekcję klas, takich jak <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, i <xref:System.ComponentModel.BindingList%601>, wśród wielu innych.  
  
 WPF nigdy nie powoduje bezpośrednie powiązanie z kolekcji. Jeśli określisz kolekcji jako źródło powiązania WPF faktycznie wiąże widok domyślny kolekcji. Aby uzyskać informacje o widokach domyślnych, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Jeśli masz zaawansowanego scenariusza i implementowania swojej kolekcji, należy rozważyć użycie <xref:System.Collections.IList> interfejsu. <xref:System.Collections.IList>udostępnia kolekcja nierodzajową obiektów, które mogą być indywidualnie uzyskać dostęp przez indeks, co może poprawić wydajność.  
  
<a name="permissions"></a>   
## <a name="permission-requirements-in-data-binding"></a>Wymagania dotyczące uprawnień w powiązaniu danych  
 Podczas wiązania z danymi należy rozważyć poziom zaufania aplikacji. Poniższa tabela zawiera podsumowanie właściwości, jakie typy może być powiązana w aplikacji, która jest wykonywany w trybie pełnego zaufania lub częściowej relacji zaufania:  
  
|Typ właściwości<br /><br /> (wszystkie modyfikatory dostępu)|Właściwości obiektu dynamicznego|Właściwości obiektu dynamicznego|Właściwość CLR|Właściwość CLR|Właściwości zależności|Właściwości zależności|  
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|  
|**Poziom zaufania**|**Pełne zaufanie**|**Częściowa relacja zaufania**|**Pełne zaufanie**|**Częściowa relacja zaufania**|**Pełne zaufanie**|**Częściowa relacja zaufania**|  
|Klasa publiczna|Tak|Tak|Tak|Tak|Tak|Tak|  
|Niepubliczne — klasa|Tak|Nie|Tak|Nie|Tak|Tak|  
  
 Ta tabela zawiera opis o następujących kwestiach dotyczących wymagania dotyczące uprawnień w powiązaniu danych:  
  
-   Aby uzyskać [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości powiązania danych działa pod warunkiem, aparat wiązania jest w stanie uzyskać dostępu do właściwości source powiązania za pomocą odbicia. W przeciwnym razie aparat wiązania ostrzeżenie, którego nie można odnaleźć właściwości i używa rezerwowej wartość lub wartość domyślną, jeśli jest dostępna.  
  
-   Można powiązać właściwości na obiekty dynamiczne, które są zdefiniowane w kompilacji w czasie lub w czasie wykonywania.  
  
-   Zawsze można powiązać właściwości zależności.  
  
 Wymaganie uprawnienia [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] przypomina powiązania. W bibliotece częściowego zaufania <xref:System.Windows.Data.XmlDataProvider> nie powiedzie się, gdy nie ma uprawnień dostępu do określonych danych.  
  
 Obiekty typu anonimowego są wewnętrzne. Właściwości typu anonimowego można powiązać tylko wtedy, gdy uruchomiony w trybie pełnego zaufania. Aby uzyskać więcej informacji na temat typów anonimowych, zobacz [typy anonimowe (C# przewodnik programowania w języku)](~/docs/csharp/programming-guide/classes-and-structs/anonymous-types.md) lub [typy anonimowe (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic).  
  
 Aby uzyskać więcej informacji o zabezpieczeniach częściowego zaufania, zobacz [WPF częściowego zaufania zabezpieczeń](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.ObjectDataProvider>  
 <xref:System.Windows.Data.XmlDataProvider>  
 [Określanie obiektu źródłowego powiązania](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Powiązanie danych WPF za pomocą LINQ to XML — omówienie](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)
