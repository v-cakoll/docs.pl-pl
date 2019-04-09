---
title: 'Optymalizacja wydajności: Powiązanie danych'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: ac7ca815bedf180c8a680840f585d08f7018d6ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087836"
---
# <a name="optimizing-performance-data-binding"></a>Optymalizacja wydajności: Powiązanie danych
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Powiązanie danych zapewnia prosty i spójny sposób w przypadku aplikacji, umożliwiające zaprezentowanie i interakcję z danymi. Elementy może być powiązana z danymi z różnych źródeł danych w formie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów i [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Ten temat zawiera zalecenia dotyczące wydajności powiązanie danych.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Jak są rozwiązywane odwołania do powiązania danych  
 Przed omówieniem problemy z wydajnością powiązania danych, warto Eksplorowanie sposób, w jaki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aparat wiązanie danych jest rozpoznawana jako odwołania do obiektu dla powiązania.  
  
 Źródło [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] powiązanie danych może być dowolnym [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu. Można powiązać właściwości, właściwości podrzędnych lub indeksatory programu [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu. Odwołań do powiązań są rozpoznawane przy użyciu odbicia albo programu Microsoft .NET Framework lub <xref:System.ComponentModel.ICustomTypeDescriptor>. Poniżej przedstawiono trzy metody rozpoznawania odwołania do obiektu dla powiązania.  
  
 Pierwsza metoda polega na tym, za pomocą odbicia. W tym przypadku <xref:System.Reflection.PropertyInfo> obiekt służy do odnajdywania atrybuty właściwości i zapewnia dostęp do metadanych właściwości modelu. Korzystając z <xref:System.ComponentModel.ICustomTypeDescriptor> interfejsu, aparat powiązania danych korzysta z tego interfejsu, aby uzyskać dostęp do wartości właściwości. <xref:System.ComponentModel.ICustomTypeDescriptor> Interfejs jest szczególnie przydatna w sytuacji, gdy obiekt nie ma statyczny zestaw właściwości.  
  
 Powiadomienia o zmianie właściwości może być dostarczona przez wdrażanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejs lub przy użyciu skojarzonych z powiadomień o zmianie <xref:System.ComponentModel.TypeDescriptor>. Jednak preferowaną strategię wykonywania powiadomienia o zmianie właściwości jest użycie <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Jeśli obiekt źródłowy jest [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów i właściwości source [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aparat powiązania danych musi najpierw używać odbicia w obiekcie źródłowym, aby uzyskać <xref:System.ComponentModel.TypeDescriptor>i wykonywanie zapytania skierowanego do <xref:System.ComponentModel.PropertyDescriptor>. Ta sekwencja operacji odbicie jest potencjalnie bardzo czasochłonne, z punktu widzenia wydajności.  
  
 Obejmuje to druga metoda rozpoznawania odwołań do obiektów [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekt źródłowy, który implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu i właściwości source, który jest [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości. W tym przypadku aparat powiązania danych używa odbicia bezpośrednio na typ źródła i pobiera wymaganej właściwości. Nie jest to nadal optymalnej metody, ale jego koszt mniej w pracy zestaw wymagania niż pierwsza metoda.  
  
 Trzecia metoda rozpoznawania odwołań do obiektów obejmuje obiekt źródłowy, który jest <xref:System.Windows.DependencyObject> i właściwości source, który jest <xref:System.Windows.DependencyProperty>. W tym przypadku aparat powiązań danych nie trzeba używać odbicia. Zamiast tego aparat właściwości i aparat powiązania danych ze sobą rozpoznać odwołania do właściwości niezależnie. Jest to optymalnej metody rozpoznawania odwołań do obiektów używane dla wiązania danych.  
  
 W poniższej tabeli porównano szybkości powiązanie danych <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość tysiąca <xref:System.Windows.Controls.TextBlock> elementów za pomocą tych trzech metod.  
  
|**Wiązanie właściwości Text TextBlock**|**Powiązanie czas (ms)**|**Czas na renderowanie — zawiera powiązania (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Właściwości [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu|115|314|  
|Właściwości [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu, który implementuje <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|Aby <xref:System.Windows.DependencyProperty> z <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Powiązania do obiektów dużych CLR  
 Gdy dane związane z jedną jest wpływ istotnie poprawiającą wydajność [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu z tysiącami właściwości. Można zminimalizować wpływ, dzieląc pojedynczy obiekt na wielu [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów z mniej właściwości. W tabeli przedstawiono powiązania i czas renderowania dla powiązania danych z jedną dużą [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu w porównaniu z wielu obiektów mniejsze.  
  
|**Obiekty TextBlock 1000 powiązania danych**|**Powiązanie czas (ms)**|**Czas na renderowanie — zawiera powiązania (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|Aby [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekt z właściwościami 1000|950|1200|  
|Na 1000 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekty z jednej właściwości|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Powiązanie z ItemsSource  
 Rozważmy scenariusz, w którym masz [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> obiekt, który zawiera listę pracownicy, którzy mają być wyświetlane w <xref:System.Windows.Controls.ListBox>. Aby utworzyć połączenie między tymi dwoma obiektami, czy powiązanie listę pracowników w celu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox>. Jednak Załóżmy, że masz nowych pracowników, dołączenie do grupy. Może się wydawać, że aby można było wstawić tej nowej osoby do usługi powiązane z <xref:System.Windows.Controls.ListBox> wartości, czy po prostu dodać tę osobę do listy pracowników i oczekują ta zmiana została automatycznie rozpoznawane przez aparat powiązanie danych. Założenie, że może okazać się false; w rzeczywistości zmiany nie zostaną odzwierciedlone w <xref:System.Windows.Controls.ListBox> automatycznie. Jest to spowodowane [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> obiektu automatycznie zgłaszaj zdarzeń kolekcji zmienione. Aby uzyskać <xref:System.Windows.Controls.ListBox> do pobrania zmiany, trzeba ponownie utworzyć listę pracowników i ponownie podłącz go do <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox>. Chociaż to rozwiązanie działa, wprowadzono dużego wpływu. Zawsze należy ponownie przypisać <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListBox> do nowego obiektu <xref:System.Windows.Controls.ListBox> najpierw zgłasza natychmiast swoich poprzednich elementów i ponownie wygenerować jego całą listę. Wpływ na wydajność jest powiększony, jeśli Twoja <xref:System.Windows.Controls.ListBox> mapuje złożony <xref:System.Windows.DataTemplate>.  
  
 Wydajne rozwiązanie tego problemu jest zapewnienie listy pracowników <xref:System.Collections.ObjectModel.ObservableCollection%601>. <xref:System.Collections.ObjectModel.ObservableCollection%601> Obiektu zgłasza którego aparat powiązania danych może odbierać powiadomienia o zmianach. Zdarzenie dodaje lub usuwa element z <xref:System.Windows.Controls.ItemsControl> bez konieczności ponownego generowania całej listy.  
  
 Poniższa tabela zawiera czas potrzebny do zaktualizowania <xref:System.Windows.Controls.ListBox> (z wirtualizacja interfejsu użytkownika, wyłączona) po dodaniu jeden element. Liczba w pierwszym wierszu reprezentuje czas, który upłynął podczas [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> obiekt jest powiązany z <xref:System.Windows.Controls.ListBox> elementu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Numer w drugim wierszu reprezentuje czas, który upłynął podczas <xref:System.Collections.ObjectModel.ObservableCollection%601> jest powiązany z <xref:System.Windows.Controls.ListBox> elementu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Uwaga znaczne oszczędności przy użyciu <xref:System.Collections.ObjectModel.ObservableCollection%601> strategii powiązanie danych.  
  
|**ItemsSource powiązania danych**|**Zaktualizuj czas 1 elementu (ms)**|  
|--------------------------------------|---------------------------------------|  
|Aby [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> obiektu|1656|  
|Aby <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Powiązywanie IList elementu ItemsControl nie IEnumerable  
 Jeśli masz do wyboru między powiązania <xref:System.Collections.Generic.IList%601> lub <xref:System.Collections.IEnumerable> do <xref:System.Windows.Controls.ItemsControl> obiektu, wybierz polecenie <xref:System.Collections.Generic.IList%601> obiektu. Powiązanie <xref:System.Collections.IEnumerable> do <xref:System.Windows.Controls.ItemsControl> wymusza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utworzyć otokę <xref:System.Collections.Generic.IList%601> obiektu, co oznacza, że wydajność jest wpływ niepotrzebne obciążenie związane z drugiego obiektu.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Czy nie Konwertuj CLR obiekty do XML tylko dla powiązania danych.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umożliwia danych można powiązać [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] zawartości; jednak powiązania danych [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] zawartości jest mniejsza niż powiązania danych [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów. Nie można konwertować [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekt danych do pliku XML, jeśli jedynym celem jest przeznaczony dla wiązania danych.  
  
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
- [Przegląd Wiązanie danych](../data/data-binding-overview.md)
- [Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
