---
title: 'Optymalizacja wydajności: Powiązanie danych'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 25c0906e9f23948476732b10b2c5fb10fe4eb55f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401453"
---
# <a name="optimizing-performance-data-binding"></a>Optymalizacja wydajności: Powiązanie danych
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]powiązanie danych zapewnia prosty i spójny sposób, w jaki aplikacje mogą być obecne i współpracujące z danymi. Elementy mogą być powiązane z danymi z różnych źródeł danych w postaci obiektów CLR i [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Ten temat zawiera zalecenia dotyczące wydajności powiązań danych.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Jak są rozwiązywane odwołania do powiązań danych  
 Przed przeprowadzeniem omawiania problemów z wydajnością powiązań danych wartościowa się, jak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aparat powiązań danych rozpoznaje odwołania do obiektów dla powiązania.  
  
 Źródłem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] powiązania danych może być dowolny obiekt CLR. Można powiązać z właściwościami, podrzędnymi lub indeksatorami obiektu CLR. Odwołania do powiązań są rozwiązywane przy użyciu odbicia struktury Microsoft .NET Framework <xref:System.ComponentModel.ICustomTypeDescriptor>lub. Oto trzy metody rozpoznawania odwołań do obiektów do powiązania.  
  
 Pierwsza metoda polega na użyciu odbicia. W tym przypadku <xref:System.Reflection.PropertyInfo> obiekt jest używany do odnajdywania atrybutów właściwości i zapewnia dostęp do metadanych właściwości. W przypadku korzystania <xref:System.ComponentModel.ICustomTypeDescriptor> z interfejsu aparat powiązań danych używa tego interfejsu, aby uzyskać dostęp do wartości właściwości. <xref:System.ComponentModel.ICustomTypeDescriptor> Interfejs jest szczególnie przydatny w przypadkach, gdy obiekt nie ma statycznego zestawu właściwości.  
  
 Powiadomienia o zmianie właściwości można podać przez implementację <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu lub przy użyciu powiadomień o zmianach skojarzonych <xref:System.ComponentModel.TypeDescriptor>z. Jednak preferowaną strategią implementowania powiadomień o zmianach właściwości jest <xref:System.ComponentModel.INotifyPropertyChanged>użycie.  
  
 Jeśli obiekt źródłowy jest obiektem CLR, a właściwość source jest właściwością CLR, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aparat powiązań danych musi najpierw użyć odbicia w obiekcie źródłowym <xref:System.ComponentModel.TypeDescriptor>, aby uzyskać, a następnie wykonać zapytanie dla elementu <xref:System.ComponentModel.PropertyDescriptor>. Ta sekwencja operacji odbicia jest potencjalnie bardzo czasochłonna z perspektywy wydajności.  
  
 Druga metoda rozpoznawania odwołań do obiektów obejmuje obiekt źródłowy CLR, który implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejs, oraz Właściwość Source, która jest właściwością CLR. W takim przypadku aparat powiązań danych używa odbicia bezpośrednio w typie źródłowym i pobiera wymaganą właściwość. Nadal nie jest to optymalna Metoda, ale koszt ten będzie tańszy niż w przypadku pierwszej metody.  
  
 Trzecia metoda rozpoznawania odwołań do obiektów obejmuje obiekt źródłowy, który jest <xref:System.Windows.DependencyObject> i Właściwość źródłową, która <xref:System.Windows.DependencyProperty>jest. W takim przypadku aparat powiązań danych nie musi używać odbicia. Zamiast tego aparat właściwości i aparat powiązań danych wspólnie rozwiązują odwołania do właściwości. Jest to optymalna metoda rozpoznawania odwołań do obiektów używanych na potrzeby powiązania danych.  
  
 W poniższej tabeli porównano szybkość danych wiążących <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość elementów 1000 <xref:System.Windows.Controls.TextBlock> przy użyciu tych trzech metod.  
  
|**Wiązanie właściwości text bloku**|**Czas powiązania (MS)**|**Czas renderowania — zawiera powiązanie (MS)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Do właściwości obiektu CLR|115|314|  
|Do właściwości obiektu CLR, który implementuje<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|Na a <xref:System.Windows.DependencyProperty> <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Powiązanie z dużymi obiektami CLR  
 Istnieje znaczny wpływ na wydajność, gdy dane są powiązane z pojedynczym obiektem CLR z tysiącami właściwości. Możesz zminimalizować ten wpływ, dzieląc pojedynczy obiekt na wiele obiektów CLR o mniejszej liczbie właściwości. W tabeli przedstawiono czasy powiązania i renderowania dla powiązania danych z pojedynczym dużym obiektem CLR a wieloma mniejszymi obiektami.  
  
|**Powiązania danych 1000 obiektów TextBlock**|**Czas powiązania (MS)**|**Czas renderowania — zawiera powiązanie (MS)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|Do obiektu CLR z właściwościami 1000|950|1200|  
|Do 1000 obiektów CLR z jedną właściwością|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Powiązanie z ItemsSource  
 Rozważmy scenariusz, w którym znajduje się obiekt <xref:System.Collections.Generic.List%601> CLR, który zawiera listę pracowników, którzy mają być wyświetlani <xref:System.Windows.Controls.ListBox>w. Aby utworzyć związek między tymi dwoma obiektami, należy powiązać listę pracowników z <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwością. <xref:System.Windows.Controls.ListBox> Załóżmy jednak, że masz nowego pracownika dołączenia do grupy. Możesz zastanowić się, że aby wstawić tę nową osobę do wartości <xref:System.Windows.Controls.ListBox> powiązanych, wystarczy dodać tę osobę do listy pracowników i spodziewać się, że ta zmiana zostanie uznana za automatycznie przez aparat powiązań danych. To założenie będzie miało wartość FAŁSZ; w rzeczywistości zmiana nie zostanie odzwierciedlona <xref:System.Windows.Controls.ListBox> automatycznie. Dzieje się tak, ponieważ <xref:System.Collections.Generic.List%601> obiekt CLR nie zgłasza automatycznie zdarzenia zmiany kolekcji. Aby można było pobrać <xref:System.Windows.Controls.ListBox> zmiany, należy ponownie utworzyć listę pracowników, a następnie dołączyć ją <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> do właściwości <xref:System.Windows.Controls.ListBox>... W trakcie działania tego rozwiązania wprowadzono ogromny wpływ na wydajność. Za każdym razem, gdy ponownie <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> przypiszesz <xref:System.Windows.Controls.ListBox> do nowego obiektu, <xref:System.Windows.Controls.ListBox> najpierw zwraca poprzednie elementy i generuje całą listę. Wpływ na wydajność jest powiększony, jeśli <xref:System.Windows.Controls.ListBox> mapa jest złożona. <xref:System.Windows.DataTemplate>  
  
 Bardzo wydajne rozwiązanie tego problemu polega na tym, <xref:System.Collections.ObjectModel.ObservableCollection%601>że pracownik będzie miał listę. <xref:System.Collections.ObjectModel.ObservableCollection%601> Obiekt zgłasza powiadomienie o zmianie, które może odbierać aparat powiązań danych. Zdarzenie dodaje lub usuwa element z <xref:System.Windows.Controls.ItemsControl> bez konieczności ponownego generowania całej listy.  
  
 W poniższej tabeli przedstawiono czas potrzebny do zaktualizowania <xref:System.Windows.Controls.ListBox> (z wyłączonym wirtualizacją interfejsu użytkownika) po dodaniu jednego elementu. Liczba w pierwszym wierszu reprezentuje czas, który upłynął, gdy obiekt CLR <xref:System.Collections.Generic.List%601> jest powiązany z <xref:System.Windows.Controls.ListBox> elementem <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Liczba w drugim wierszu reprezentuje czas, który upłynął, gdy <xref:System.Collections.ObjectModel.ObservableCollection%601> jest powiązany <xref:System.Windows.Controls.ListBox> z elementem <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Zwróć uwagę na znaczne oszczędności czasu przy <xref:System.Collections.ObjectModel.ObservableCollection%601> użyciu strategii powiązań danych.  
  
|**Powiązanie danych ItemsSource**|**Aktualizacja czasu dla 1 elementu (MS)**|  
|--------------------------------------|---------------------------------------|  
|Do obiektu CLR <xref:System.Collections.Generic.List%601>|1656|  
|Na<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Powiąż IList z ItemsControl nie IEnumerable  
 Jeśli masz wybór między <xref:System.Collections.Generic.IList%601> wiązaniem <xref:System.Windows.Controls.ItemsControl> obiektu <xref:System.Collections.IEnumerable> a obiektem, wybierz <xref:System.Collections.Generic.IList%601> obiekt. Powiązanie <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IList%601> z siłami ,[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aby utworzyć obiekt otoki, co oznacza, że na wydajność ma wpływ niepotrzebne obciążenie drugiego obiektu. <xref:System.Windows.Controls.ItemsControl>  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Nie należy konwertować obiektów CLR do formatu XML tylko dla powiązania danych.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umożliwia powiązanie danych z [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] zawartością, ale powiązanie danych z [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] zawartością jest wolniejsze niż wiązanie danych z obiektami CLR. Nie Konwertuj danych obiektu CLR do formatu XML, jeśli jedynym celem jest powiązanie danych.  
  
## <a name="see-also"></a>Zobacz także

- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Wykorzystanie możliwości sprzętu](optimizing-performance-taking-advantage-of-hardware.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Grafika 2D i obrazowanie](optimizing-performance-2d-graphics-and-imaging.md)
- [Zachowanie obiektu](optimizing-performance-object-behavior.md)
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Inne zalecenia dotyczące wydajności](optimizing-performance-other-recommendations.md)
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Przewodnik: Buforowanie danych aplikacji w aplikacji WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
