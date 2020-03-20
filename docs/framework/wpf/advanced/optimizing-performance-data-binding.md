---
title: 'Optymalizacja wydajności: powiązanie danych'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 3128f453378f9d74f867b571e30f2be4e8add8a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186760"
---
# <a name="optimizing-performance-data-binding"></a>Optymalizacja wydajności: powiązanie danych
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Wiązanie danych zapewnia prosty i spójny sposób prezentowania danych i interakcji z nimi. Elementy mogą być powiązane z danymi z różnych źródeł danych w postaci obiektów CLR i XML.  
  
 Ten temat zawiera zalecenia dotyczące wydajności wiązania danych.  

<a name="HowDataBindingReferencesAreResolved"></a>
## <a name="how-data-binding-references-are-resolved"></a>Jak rozwiązywane są odwołania do wiązania danych  
 Przed omówieniem problemów z wydajnością wiązania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] danych warto zbadać, jak aparat wiązania danych rozwiązuje odwołania do obiektów dla powiązania.  
  
 Źródłem powiązania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] danych może być dowolny obiekt CLR. Można powiązać z właściwości, właściwości podrzędnych lub indeksatorów obiektu CLR. Odwołania do powiązania są rozpoznawane przy użyciu odbicia programu <xref:System.ComponentModel.ICustomTypeDescriptor>Microsoft .NET Framework lub . Oto trzy metody rozpoznawania odwołań do obiektów dla powiązania.  
  
 Pierwsza metoda polega na użyciu odbicia. W takim przypadku <xref:System.Reflection.PropertyInfo> obiekt jest używany do odnajdywać atrybuty właściwości i zapewnia dostęp do metadanych właściwości. Podczas korzystania <xref:System.ComponentModel.ICustomTypeDescriptor> z interfejsu aparat wiązania danych używa tego interfejsu, aby uzyskać dostęp do wartości właściwości. Interfejs <xref:System.ComponentModel.ICustomTypeDescriptor> jest szczególnie przydatny w przypadkach, gdy obiekt nie ma statycznego zestawu właściwości.  
  
 Powiadomienia o zmianie właściwości mogą być dostarczane <xref:System.ComponentModel.INotifyPropertyChanged> poprzez implementację interfejsu lub za <xref:System.ComponentModel.TypeDescriptor>pomocą powiadomień o zmianie skojarzonych z programem . Jednak preferowaną strategią wdrażania powiadomień o <xref:System.ComponentModel.INotifyPropertyChanged>zmianie właściwości jest użycie .  
  
 Jeśli obiekt źródłowy jest obiektem CLR, a właściwość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] źródło jest właściwością CLR, aparat wiązania <xref:System.ComponentModel.TypeDescriptor>danych musi najpierw <xref:System.ComponentModel.PropertyDescriptor>użyć odbicia na obiekcie źródłowym, aby uzyskać , a następnie kwerendę dla . Ta sekwencja operacji odbicia jest potencjalnie bardzo czasochłonne z punktu widzenia wydajności.  
  
 Druga metoda rozpoznawania odwołań do obiektów obejmuje obiekt źródłowy <xref:System.ComponentModel.INotifyPropertyChanged> CLR, który implementuje interfejs i właściwość źródło, która jest właściwością CLR. W takim przypadku aparat wiązania danych używa odbicia bezpośrednio na typ źródła i pobiera wymaganą właściwość. Nadal nie jest to optymalna metoda, ale będzie kosztować mniej w wymaganiach zestawu roboczego niż pierwsza metoda.  
  
 Trzecia metoda rozpoznawania odwołań do obiektów obejmuje obiekt <xref:System.Windows.DependencyObject> źródłowy, który jest <xref:System.Windows.DependencyProperty>a i właściwością źródłową, która jest . W takim przypadku aparat wiązania danych nie musi używać odbicia. Zamiast tego aparat właściwości i aparat wiązania danych razem rozwiązać odwołanie do właściwości niezależnie. Jest to optymalna metoda rozpoznawania odwołań do obiektów używanych do wiązania danych.  
  
 W poniższej tabeli porównano <xref:System.Windows.Controls.TextBlock.Text%2A> szybkość powiązania <xref:System.Windows.Controls.TextBlock> danych właściwości tysiąca elementów przy użyciu tych trzech metod.  
  
|**Powiązanie text właściwości TextBlock**|**Czas wiązania (ms)**|**Czas renderowania - zawiera powiązanie (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Do właściwości obiektu CLR|115|314|  
|Do właściwości obiektu CLR implementuj, który implementuje<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|Do <xref:System.Windows.DependencyProperty> a <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>
## <a name="binding-to-large-clr-objects"></a>Powiązanie z dużymi obiektami CLR  
 Istnieje znaczący wpływ na wydajność podczas powiązania danych z pojedynczym obiektem CLR z tysiącami właściwości. Można zminimalizować ten wpływ, dzieląc pojedynczy obiekt na wiele obiektów CLR o mniejszej liczbie właściwości. Tabela pokazuje czas wiązania i renderowania dla powiązania danych do pojedynczego dużego obiektu CLR w porównaniu do wielu mniejszych obiektów.  
  
|**Powiązanie danych 1000 TextBlock obiektów**|**Czas wiązania (ms)**|**Czas renderowania - zawiera powiązanie (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|Do obiektu CLR z 1000 właściwościami|950|1200|  
|Do 1000 obiektów CLR z jedną właściwością|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>
## <a name="binding-to-an-itemssource"></a>Powiązanie z źródłem elementów  
 Rozważmy scenariusz, w którym <xref:System.Collections.Generic.List%601> masz obiekt CLR, który zawiera listę pracowników, które mają być wyświetlane w programie <xref:System.Windows.Controls.ListBox>. Aby utworzyć korespondencję między tymi dwoma obiektami, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> należy powiązać listę pracowników z właściwością <xref:System.Windows.Controls.ListBox>pliku . Załóżmy jednak, że do grupy dołączy nowy pracownik. Można by pomyśleć, że aby wstawić <xref:System.Windows.Controls.ListBox> tę nową osobę do wartości powiązanych, wystarczy dodać tę osobę do listy pracowników i oczekiwać, że ta zmiana zostanie automatycznie rozpoznana przez aparat wiązania danych. Założenie to okazałoby się fałszywe; w rzeczywistości zmiana nie zostanie automatycznie odzwierciedlona. <xref:System.Windows.Controls.ListBox> Dzieje się tak, <xref:System.Collections.Generic.List%601> ponieważ obiekt CLR nie automatycznie podnieść zdarzenie zmiany kolekcji. Aby uzyskać <xref:System.Windows.Controls.ListBox> odebrać zmiany, trzeba by odtworzyć listę pracowników i ponownie dołączyć go do <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości <xref:System.Windows.Controls.ListBox>. Chociaż to rozwiązanie działa, wprowadza ogromny wpływ na wydajność. Za każdym razem, gdy <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> ponownie przypisać do <xref:System.Windows.Controls.ListBox> nowego obiektu, pierwszy wyrzuca jego poprzednich elementów i regeneruje całą listę. Wpływ na wydajność jest powiększony, jeśli mapy <xref:System.Windows.Controls.ListBox> do złożonych <xref:System.Windows.DataTemplate>.  
  
 Bardzo skutecznym rozwiązaniem tego problemu jest uczynienie <xref:System.Collections.ObjectModel.ObservableCollection%601>listy pracowników . Obiekt <xref:System.Collections.ObjectModel.ObservableCollection%601> wywołuje powiadomienie o zmianie, które może odbierać aparat wiązania danych. Zdarzenie dodaje lub usuwa element <xref:System.Windows.Controls.ItemsControl> z bez konieczności ponownego generowania całej listy.  
  
 W poniższej tabeli przedstawiono <xref:System.Windows.Controls.ListBox> czas potrzebny do aktualizacji (z wyłączonej wirtualizacji interfejsu użytkownika) po dodaniu jednego elementu. Liczba w pierwszym wierszu reprezentuje czas, jaki upłynął, gdy obiekt CLR <xref:System.Collections.Generic.List%601> jest powiązany z <xref:System.Windows.Controls.ListBox> elementem <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Liczba w drugim wierszu reprezentuje czas, który <xref:System.Collections.ObjectModel.ObservableCollection%601> upłynął, <xref:System.Windows.Controls.ListBox> gdy <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>jest powiązany z elementem . Należy zwrócić uwagę na <xref:System.Collections.ObjectModel.ObservableCollection%601> znaczne oszczędności czasu przy użyciu strategii wiązania danych.  
  
|**Powiązanie danych z usługą ItemsSource**|**Czas aktualizacji dla 1 elementu (ms)**|  
|--------------------------------------|---------------------------------------|  
|Do obiektu <xref:System.Collections.Generic.List%601> CLR|1656|  
|Do<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Lista powiązań z elementamiControl nie jest liczna  
 Jeśli masz wybór między <xref:System.Collections.Generic.IList%601> powiązaniem <xref:System.Collections.IEnumerable> lub <xref:System.Windows.Controls.ItemsControl> do obiektu, wybierz <xref:System.Collections.Generic.IList%601> obiekt. Powiązanie <xref:System.Collections.IEnumerable> <xref:System.Windows.Controls.ItemsControl> z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] siłami, <xref:System.Collections.Generic.IList%601> aby utworzyć obiekt otoki, co oznacza, że na wydajność ma wpływ niepotrzebne obciążenie drugiego obiektu.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Nie należy konwertować obiektów CLR na XML tylko dla powiązania danych.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pozwala na powiązanie danych z zawartością XML; jednak powiązanie danych z zawartością XML jest wolniejsze niż powiązanie danych z obiektami CLR. Nie należy konwertować danych obiektu CLR na XML, jeśli jedynym celem jest powiązanie danych.  
  
## <a name="see-also"></a>Zobacz też

- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Wykorzystanie możliwości sprzętu](optimizing-performance-taking-advantage-of-hardware.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Grafika 2D i obrazowanie](optimizing-performance-2d-graphics-and-imaging.md)
- [Zachowanie obiektu](optimizing-performance-object-behavior.md)
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Tekst](optimizing-performance-text.md)
- [Inne zalecenia dotyczące wydajności](optimizing-performance-other-recommendations.md)
- [Przegląd Wiązanie danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
