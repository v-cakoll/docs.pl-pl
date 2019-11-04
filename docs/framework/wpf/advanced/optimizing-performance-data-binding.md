---
title: 'Optymalizacja wydajności: powiązanie danych'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 31fdc3c31c8792fea5f3e71dedb7370ebd63c98e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458547"
---
# <a name="optimizing-performance-data-binding"></a>Optymalizacja wydajności: powiązanie danych
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] powiązania danych zapewnia prosty i spójny sposób, w jaki aplikacje mogą być obecne i współpracujące z danymi. Elementy mogą być powiązane z danymi z różnych źródeł danych w postaci obiektów CLR i [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Ten temat zawiera zalecenia dotyczące wydajności powiązań danych.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Jak są rozwiązywane odwołania do powiązań danych  
 Przed przeprowadzeniem omówienia problemów z wydajnością powiązań danych wartościowa się, jak aparat powiązań danych [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] rozpoznaje odwołania do obiektów dla powiązania.  
  
 Źródłem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] powiązania danych może być dowolny obiekt CLR. Można powiązać z właściwościami, podrzędnymi lub indeksatorami obiektu CLR. Odwołania do powiązań są rozwiązywane przy użyciu odbicia Microsoft .NET Framework lub <xref:System.ComponentModel.ICustomTypeDescriptor>. Oto trzy metody rozpoznawania odwołań do obiektów do powiązania.  
  
 Pierwsza metoda polega na użyciu odbicia. W takim przypadku obiekt <xref:System.Reflection.PropertyInfo> jest używany do odnajdywania atrybutów właściwości i zapewnia dostęp do metadanych właściwości. Korzystając z interfejsu <xref:System.ComponentModel.ICustomTypeDescriptor>, aparat powiązań danych używa tego interfejsu do uzyskiwania dostępu do wartości właściwości. Interfejs <xref:System.ComponentModel.ICustomTypeDescriptor> jest szczególnie przydatny w przypadkach, gdy obiekt nie ma statycznego zestawu właściwości.  
  
 Powiadomienia o zmianie właściwości można podać przez implementację interfejsu <xref:System.ComponentModel.INotifyPropertyChanged> lub przy użyciu powiadomień o zmianach skojarzonych z <xref:System.ComponentModel.TypeDescriptor>. Jednak preferowaną strategią implementowania powiadomień o zmianach właściwości jest użycie <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Jeśli obiekt źródłowy jest obiektem CLR i Właściwość Source jest właściwością CLR, aparat powiązań danych [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] musi najpierw użyć odbicia w obiekcie źródłowym w celu uzyskania <xref:System.ComponentModel.TypeDescriptor>, a następnie wykonać zapytanie o <xref:System.ComponentModel.PropertyDescriptor>. Ta sekwencja operacji odbicia jest potencjalnie bardzo czasochłonna z perspektywy wydajności.  
  
 Druga metoda rozpoznawania odwołań do obiektów obejmuje obiekt źródłowy CLR, który implementuje interfejs <xref:System.ComponentModel.INotifyPropertyChanged> i Właściwość Source, która jest właściwością CLR. W takim przypadku aparat powiązań danych używa odbicia bezpośrednio w typie źródłowym i pobiera wymaganą właściwość. Nadal nie jest to optymalna Metoda, ale koszt ten będzie tańszy niż w przypadku pierwszej metody.  
  
 Trzecia metoda rozpoznawania odwołań do obiektów obejmuje obiekt źródłowy, który jest <xref:System.Windows.DependencyObject> i Właściwość Source, która jest <xref:System.Windows.DependencyProperty>. W takim przypadku aparat powiązań danych nie musi używać odbicia. Zamiast tego aparat właściwości i aparat powiązań danych wspólnie rozwiązują odwołania do właściwości. Jest to optymalna metoda rozpoznawania odwołań do obiektów używanych na potrzeby powiązania danych.  
  
 W poniższej tabeli porównano szybkość powiązania danych z właściwością <xref:System.Windows.Controls.TextBlock.Text%2A> z 1000 <xref:System.Windows.Controls.TextBlock> elementów przy użyciu tych trzech metod.  
  
|**Wiązanie właściwości text bloku**|**Czas powiązania (MS)**|**Czas renderowania — zawiera powiązanie (MS)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Do właściwości obiektu CLR|115|314|  
|Do właściwości obiektu CLR, który implementuje <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|<xref:System.Windows.DependencyProperty> <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Powiązanie z dużymi obiektami CLR  
 Istnieje znaczny wpływ na wydajność, gdy dane są powiązane z pojedynczym obiektem CLR z tysiącami właściwości. Możesz zminimalizować ten wpływ, dzieląc pojedynczy obiekt na wiele obiektów CLR o mniejszej liczbie właściwości. W tabeli przedstawiono czasy powiązania i renderowania dla powiązania danych z pojedynczym dużym obiektem CLR a wieloma mniejszymi obiektami.  
  
|**Powiązania danych 1000 obiektów TextBlock**|**Czas powiązania (MS)**|**Czas renderowania — zawiera powiązanie (MS)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|Do obiektu CLR z właściwościami 1000|950|1200|  
|Do 1000 obiektów CLR z jedną właściwością|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Powiązanie z ItemsSource  
 Rozważmy scenariusz, w którym znajduje się obiekt <xref:System.Collections.Generic.List%601> CLR, który przechowuje listę pracowników, którzy mają być wyświetlani w <xref:System.Windows.Controls.ListBox>. Aby utworzyć związek między tymi dwoma obiektami, należy powiązać listę pracowników z właściwością <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox>. Załóżmy jednak, że masz nowego pracownika dołączenia do grupy. Możesz zastanowić się, że w celu wstawienia tej nowej osoby do powiązanych wartości <xref:System.Windows.Controls.ListBox> możesz po prostu dodać tę osobę do listy pracowników i spodziewać się, że ta zmiana zostanie uznana za automatycznie przez aparat powiązań danych. To założenie będzie miało wartość FAŁSZ; w rzeczywistości zmiana nie zostanie odzwierciedlona automatycznie w <xref:System.Windows.Controls.ListBox>. Wynika to z faktu, że obiekt CLR <xref:System.Collections.Generic.List%601> nie zgłasza zdarzenia zmiany kolekcji. Aby uzyskać <xref:System.Windows.Controls.ListBox> w celu pobrania zmian, należy ponownie utworzyć listę pracowników i podłączyć ją do właściwości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox>u programu. W trakcie działania tego rozwiązania wprowadzono ogromny wpływ na wydajność. Za każdym razem, gdy ponownie przypiszesz <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> do nowego obiektu, <xref:System.Windows.Controls.ListBox> najpierw wyrzuca poprzednie elementy i ponownie generuje całą listę. Ten wpływ na wydajność jest powiększony, jeśli <xref:System.Windows.Controls.ListBox> jest mapowany na złożoną <xref:System.Windows.DataTemplate>.  
  
 Bardzo wydajne rozwiązanie tego problemu polega na tym, że pracownik wystawia <xref:System.Collections.ObjectModel.ObservableCollection%601>. Obiekt <xref:System.Collections.ObjectModel.ObservableCollection%601> zgłasza powiadomienie o zmianie, które może odbierać aparat powiązań danych. Zdarzenie dodaje lub usuwa element z <xref:System.Windows.Controls.ItemsControl> bez konieczności ponownego generowania całej listy.  
  
 W poniższej tabeli przedstawiono czas potrzebny do zaktualizowania <xref:System.Windows.Controls.ListBox> (z włączoną wirtualizacją interfejsu użytkownika) po dodaniu jednego elementu. Liczba w pierwszym wierszu reprezentuje czas, który upłynął, gdy obiekt <xref:System.Collections.Generic.List%601> CLR jest powiązany z <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>elementu <xref:System.Windows.Controls.ListBox>. Liczba w drugim wierszu reprezentuje czas, który upłynął, gdy <xref:System.Collections.ObjectModel.ObservableCollection%601> jest powiązany z <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>elementu <xref:System.Windows.Controls.ListBox>. Zanotuj znaczne oszczędności czasu, korzystając z strategii powiązań danych <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
|**Powiązanie danych ItemsSource**|**Aktualizacja czasu dla 1 elementu (MS)**|  
|--------------------------------------|---------------------------------------|  
|Do obiektu <xref:System.Collections.Generic.List%601> CLR|1656|  
|Do <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Powiąż IList z ItemsControl nie IEnumerable  
 Jeśli masz wybór między wiązaniem <xref:System.Collections.Generic.IList%601> lub <xref:System.Collections.IEnumerable> do obiektu <xref:System.Windows.Controls.ItemsControl>, wybierz obiekt <xref:System.Collections.Generic.IList%601>. Powiązanie <xref:System.Collections.IEnumerable> ze <xref:System.Windows.Controls.ItemsControl> wymusza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do utworzenia obiektu <xref:System.Collections.Generic.IList%601> otoki, co oznacza, że na wydajność ma wpływ niepotrzebne obciążenie drugiego obiektu.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Nie należy konwertować obiektów CLR do formatu XML tylko dla powiązania danych.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pozwala na powiązanie danych z [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] zawartością; jednak powiązanie danych z [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] zawartością jest wolniejsze niż wiązanie danych z obiektami CLR. Nie Konwertuj danych obiektu CLR do formatu XML, jeśli jedynym celem jest powiązanie danych.  
  
## <a name="see-also"></a>Zobacz także

- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Wykorzystanie możliwości sprzętu](optimizing-performance-taking-advantage-of-hardware.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Grafika 2D i obrazowanie](optimizing-performance-2d-graphics-and-imaging.md)
- [Zachowanie obiektu](optimizing-performance-object-behavior.md)
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Tekst](optimizing-performance-text.md)
- [Inne zalecenia dotyczące wydajności](optimizing-performance-other-recommendations.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
