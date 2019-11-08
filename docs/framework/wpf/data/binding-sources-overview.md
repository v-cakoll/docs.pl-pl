---
title: Przegląd Wiązanie źródeł
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
ms.openlocfilehash: e7546021fbfde3fceea7fd4f1eba10cdc90dff8b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740613"
---
# <a name="binding-sources-overview"></a>Przegląd Wiązanie źródeł
W powiązaniu danych obiekt źródłowy powiązania odwołuje się do obiektu, z którego pochodzą dane. W tym temacie omówiono typy obiektów, których można użyć jako źródła powiązań.

<a name="binding_sources"></a>
## <a name="binding-source-types"></a>Typy źródeł powiązań
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] powiązanie danych obsługuje następujące typy źródeł powiązań:

|Źródło powiązania|Opis|
|--------------------|-----------------|
|obiekty środowiska uruchomieniowego języka wspólnego (CLR)|Można powiązać z właściwościami publicznymi, podrzędnymi, a także indeksatorami dowolnego obiektu środowiska uruchomieniowego języka wspólnego (CLR). Aparat powiązań używa odbicia środowiska CLR w celu uzyskania wartości właściwości. Alternatywnie, obiekty implementujące <xref:System.ComponentModel.ICustomTypeDescriptor> lub mające zarejestrowany <xref:System.ComponentModel.TypeDescriptionProvider> również współpracują z aparatem powiązań.<br /><br /> Aby uzyskać więcej informacji na temat implementowania klasy, która może stanowić źródło powiązań, zobacz [implementowanie klasy dla źródła powiązania](#classes) w dalszej części tego tematu.|
|obiekty dynamiczne|Można powiązać z dostępnymi właściwościami i indeksatorami obiektu, który implementuje interfejs <xref:System.Dynamic.IDynamicMetaObjectProvider>. Jeśli masz dostęp do elementu członkowskiego w kodzie, możesz powiązać z nim. Na przykład jeśli obiekt dynamiczny umożliwia dostęp do elementu członkowskiego w kodzie za pośrednictwem `someObjet.AProperty`, można powiązać z nim, ustawiając ścieżkę powiązania do `AProperty`.|
|ADO.NET — obiekty|Można powiązać z obiektami ADO.NET, takimi jak <xref:System.Data.DataTable>. ADO.NET <xref:System.Data.DataView> implementuje interfejs <xref:System.ComponentModel.IBindingList>, który zapewnia powiadomienia o zmianach, dla których aparat powiązania nasłuchuje.|
|Obiekty XML|Można powiązać i uruchamiać zapytania `XPath` na <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlDocument>lub <xref:System.Xml.XmlElement>. Wygodnym sposobem uzyskiwania dostępu do danych XML, które są źródłem powiązań w znaczniku, jest użycie obiektu <xref:System.Windows.Data.XmlDataProvider>. Aby uzyskać więcej informacji, zobacz [Powiązywanie z danymi XML przy użyciu XmlDataProvider i zapytań XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Można również powiązać z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>lub powiązać z wynikami zapytań uruchamianych na obiektach tego typu przy użyciu LINQ to XML. Wygodny sposób używania LINQ to XML dostępu do danych XML, które są źródłem powiązań w znaczniku, to użycie obiektu <xref:System.Windows.Data.ObjectDataProvider>. Aby uzyskać więcej informacji, zobacz [Powiązywanie z wynikami kwerendy XDocument, XElement lub LINQ for XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|
|<xref:System.Windows.DependencyObject> obiektów|Można powiązać z właściwościami zależności dowolnego <xref:System.Windows.DependencyObject>. Aby zapoznać się z przykładem, zobacz [Powiązywanie właściwości dwóch kontrolek](how-to-bind-the-properties-of-two-controls.md).|

<a name="classes"></a>
## <a name="implementing-a-class-for-the-binding-source"></a>Implementowanie klasy dla źródła powiązania
 Możesz tworzyć własne źródła powiązań. W tej sekcji omówiono zagadnienia, które należy poznać w przypadku implementowania klasy, która ma stanowić źródło powiązań.

### <a name="providing-change-notifications"></a>Udostępnianie powiadomień o zmianach
 Jeśli używasz powiązania <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> (ponieważ chcesz, aby Twoja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] była aktualizowana, gdy właściwości źródła powiązań są dynamicznie zmieniane), należy zaimplementować odpowiedni mechanizm powiadamiania o zmianie właściwości. Zalecany mechanizm jest przeznaczony dla środowiska CLR lub klasy dynamicznej do implementowania interfejsu <xref:System.ComponentModel.INotifyPropertyChanged>. Aby uzyskać więcej informacji, zobacz [implementacja powiadomienia o zmianie właściwości](how-to-implement-property-change-notification.md).

 W przypadku utworzenia obiektu CLR, który nie implementuje <xref:System.ComponentModel.INotifyPropertyChanged>, należy rozmieścić własny system powiadomień, aby upewnić się, że dane używane w powiązaniu pozostają aktualne. Możesz dostarczyć powiadomienia o zmianach, obsługując wzorzec `PropertyChanged` dla każdej właściwości, dla której chcesz zmienić powiadomienia. Aby zapewnić obsługę tego wzorca, należy zdefiniować zdarzenie zmiany *PropertyName*dla każdej właściwości, gdzie *PropertyName* jest nazwą właściwości. Zdarzenie jest podniesione za każdym razem, gdy właściwość zostanie zmieniona.

 Jeśli źródło powiązania implementuje jeden z tych mechanizmów powiadomień, aktualizacje docelowe są wykonywane automatycznie. Jeśli z jakiegokolwiek powodu Źródło powiązania nie zapewnia prawidłowej zmiany właściwości, można użyć metody <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A>, aby jawnie zaktualizować Właściwość docelową.

### <a name="other-characteristics"></a>Inne cechy
 Poniższa lista zawiera inne ważne punkty, które należy zwrócić uwagę:

- Jeśli chcesz utworzyć obiekt w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], Klasa musi mieć konstruktora bez parametrów. W niektórych językach .NET, takich jak C#, można utworzyć niezależny od parametrów Konstruktor.

- Właściwości, które są używane jako właściwości źródła powiązań dla powiązania, muszą być publicznymi właściwościami klasy. Nie można uzyskać dostępu do jawnie zdefiniowanych właściwości interfejsu na potrzeby tworzenia powiązań ani właściwości chronionych, prywatnych, wewnętrznych lub wirtualnych, które nie mają podstawowej implementacji.

- Nie można powiązać z polami publicznymi.

- Typ właściwości zadeklarowanej w klasie to typ, który jest przesyłany do powiązania. Jednak typ, który ostatecznie jest używany przez powiązanie, zależy od typu właściwości target powiązania, a nie właściwości source powiązania. W przypadku różnic w typie warto napisać konwerter, aby obsłużyć sposób, w jaki Właściwość niestandardowa jest wstępnie przenoszona do powiązania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.IValueConverter>.

<a name="objects"></a>
## <a name="using-entire-objects-as-a-binding-source"></a>Używanie całych obiektów jako źródła powiązania
 Możesz użyć całego obiektu jako źródła powiązania. Źródło powiązania można określić przy użyciu właściwości <xref:System.Windows.Data.Binding.Source%2A> lub <xref:System.Windows.FrameworkElement.DataContext%2A>, a następnie podać pustą deklarację powiązania: `{Binding}`. Scenariusze, w których jest to przydatne, obejmują powiązanie z obiektami typu String, powiązania z obiektami z wieloma interesującymi się właściwościami lub powiązaniem z obiektami kolekcji. Aby zapoznać się z przykładem powiązania z całym obiektem kolekcji, zobacz [Używanie wzorca wzorzec-szczegóły z danymi hierarchicznymi](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

 Należy pamiętać, że może być konieczne zastosowanie logiki niestandardowej, aby dane były zrozumiałe dla powiązanej właściwości docelowej. Logika niestandardowa może mieć postać niestandardowego konwertera (jeśli konwersja typu domyślnego nie istnieje) lub <xref:System.Windows.DataTemplate>. Aby uzyskać więcej informacji na temat konwerterów, zobacz sekcję konwersja danych — [Omówienie powiązań danych](../../../desktop-wpf/data/data-binding-overview.md). Aby uzyskać więcej informacji na temat szablonów danych, zobacz [tworzenia szablonów danych — omówienie](data-templating-overview.md).

<a name="collections"></a>
## <a name="using-collection-objects-as-a-binding-source"></a>Używanie obiektów kolekcji jako źródła powiązania
 Często obiekt, który ma być używany jako źródło powiązania, jest kolekcją obiektów niestandardowych. Każdy obiekt służy jako źródło dla jednego wystąpienia Powtórzonego powiązania. Na przykład może istnieć Kolekcja `CustomerOrders`, która składa się z obiektów `CustomerOrder`, w których aplikacja wykonuje iterację w kolekcji, aby określić, ile zamówień istnieje i jakie dane są zawarte w każdej z nich.

 Można wyliczyć wszystkie kolekcje, które implementują interfejs <xref:System.Collections.IEnumerable>. Jednak aby skonfigurować powiązania dynamiczne, tak aby wstawienia lub usunięcia w kolekcji automatycznie aktualizować [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], kolekcja musi implementować interfejs <xref:System.Collections.Specialized.INotifyCollectionChanged>. Ten interfejs uwidacznia zdarzenie, które musi zostać zgłoszone za każdym razem, gdy źródłowa kolekcja ulegnie zmianie.

 Klasa <xref:System.Collections.ObjectModel.ObservableCollection%601> to wbudowana implementacja kolekcji danych, która uwidacznia interfejs <xref:System.Collections.Specialized.INotifyCollectionChanged>. Poszczególne obiekty danych w kolekcji muszą spełniać wymagania opisane w poprzednich sekcjach. Aby zapoznać się z przykładem, zobacz [Tworzenie i powiązywanie z ObservableCollection](how-to-create-and-bind-to-an-observablecollection.md). Przed zaimplementowaniem własnej kolekcji należy rozważyć użycie <xref:System.Collections.ObjectModel.ObservableCollection%601> lub jednej z istniejących klas kolekcji, takich jak <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>i <xref:System.ComponentModel.BindingList%601>, wśród wielu innych.

 WPF nigdy nie wiąże się bezpośrednio z kolekcją. Jeśli określisz kolekcję jako źródło powiązań, program WPF rzeczywiście wiąże się z widokiem domyślnym kolekcji. Aby uzyskać informacje o widokach domyślnych, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).

 Jeśli masz zaawansowany scenariusz i chcesz wdrożyć własną kolekcję, rozważ użycie interfejsu <xref:System.Collections.IList>. <xref:System.Collections.IList> zapewnia nieogólną kolekcję obiektów, do których można uzyskać dostęp za pomocą indeksu, co może poprawić wydajność.

<a name="permissions"></a>
## <a name="permission-requirements-in-data-binding"></a>Wymagania dotyczące uprawnień w powiązaniu danych
 Podczas wiązania danych należy wziąć pod uwagę poziom zaufania aplikacji. Poniższa tabela zawiera podsumowanie typów właściwości, do których można powiązać w aplikacji, która jest wykonywana w ramach pełnego zaufania lub częściowego zaufania:

|Typ właściwości<br /><br /> (wszystkie Modyfikatory dostępu)|Właściwość obiektu dynamicznego|Właściwość obiektu dynamicznego|Właściwość CLR|Właściwość CLR|Właściwość zależności|Właściwość zależności|
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|
|**Poziom zaufania**|**Pełne zaufanie**|**Częściowe zaufanie**|**Pełne zaufanie**|**Częściowe zaufanie**|**Pełne zaufanie**|**Częściowe zaufanie**|
|Klasa publiczna|Tak|Tak|Tak|Tak|Tak|Tak|
|Klasa niepubliczna|Tak|Nie|Tak|Nie|Tak|Tak|

 W tej tabeli opisano następujące ważne punkty dotyczące wymagań dotyczących uprawnień w powiązaniu danych:

- W przypadku właściwości CLR powiązanie danych działa tak długo, jak aparat powiązań jest w stanie uzyskać dostęp do właściwości źródła powiązania przy użyciu odbicia. W przeciwnym razie aparat powiązań emituje ostrzeżenie, że nie można odnaleźć właściwości i używa wartości rezerwowej lub wartości domyślnej, jeśli jest ona dostępna.

- Można powiązać z właściwościami obiektów dynamicznych, które są zdefiniowane w czasie kompilacji lub w czasie wykonywania.

- Zawsze możesz powiązać z właściwościami zależności.

 Wymagania dotyczące uprawnień dla powiązania XML są podobne. W piaskownicy z częściowym zaufaniem <xref:System.Windows.Data.XmlDataProvider> nie powiedzie się, gdy nie ma uprawnień dostępu do określonych danych.

 Obiekty z typem anonimowym są wewnętrzne. Można powiązać z właściwościami typów anonimowych tylko w przypadku uruchamiania w trybie pełnego zaufania. Aby uzyskać więcej informacji na temat typów anonimowych, zobacz [Typy anonimoweC# (Przewodnik programowania)](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) lub [Typy anonimowe (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic).

 Aby uzyskać więcej informacji o zabezpieczeniach częściowej relacji zaufania, zobacz informacje o [zabezpieczeniach częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.ObjectDataProvider>
- <xref:System.Windows.Data.XmlDataProvider>
- [Określanie obiektu źródłowego powiązania](how-to-specify-the-binding-source.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Powiązanie danych WPF za pomocą LINQ to XML — omówienie](wpf-data-binding-with-linq-to-xml-overview.md)
- [Optymalizowanie wydajności powiązań danych](../advanced/optimizing-performance-data-binding.md)
