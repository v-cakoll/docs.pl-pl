---
title: 'Optymalizacja wydajności: powiązanie danych'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4b21089ea3f3aef8a934c78187b30f2576b8d39b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="optimizing-performance-data-binding"></a>Optymalizacja wydajności: powiązanie danych
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Powiązanie danych zapewnia prosty i spójny sposób dla aplikacji przedstawić i interakcji z danymi. Elementy mogą być powiązane z danych z różnych źródeł danych w formie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów i [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Ten temat zawiera zalecenia dotyczące wydajności powiązania danych.  
  

  
<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Jak są rozwiązywane odwołania do powiązania danych  
 Przed omówieniem powiązanie problemy z wydajnością danych, warto zapoznać jak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aparat wiązania danych usuwa odwołania do obiektów dla powiązania.  
  
 Źródło [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] powiązanie danych może być dowolną [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu. Można powiązać właściwości podrzędnej, właściwości lub indeksatory z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu. Odwołania do powiązania są rozpoznawane przy użyciu odbicia albo programu Microsoft .NET Framework lub <xref:System.ComponentModel.ICustomTypeDescriptor>. Poniżej przedstawiono trzy metody rozpoznawania odwołań do obiektów dla powiązania.  
  
 Pierwsza metoda polega na użyciu odbicia. W takim przypadku <xref:System.Reflection.PropertyInfo> obiekt służy do odnajdywania atrybuty właściwości i udostępnia metadane właściwości. Korzystając z <xref:System.ComponentModel.ICustomTypeDescriptor> interfejsu, aparat wiązania danych korzysta z tego interfejsu dostęp do wartości właściwości. <xref:System.ComponentModel.ICustomTypeDescriptor> Interfejsu jest szczególnie przydatne w przypadku, gdy obiekt nie ma statycznej zbiór właściwości.  
  
 Powiadomienia o zmianie właściwości można podać albo zaimplementowanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu lub przy użyciu powiadomienia o zmianie skojarzone z <xref:System.ComponentModel.TypeDescriptor>. Jednak preferowaną strategię wdrażania powiadomienia o zmianie właściwości jest użycie <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Jeśli obiekt źródłowy jest [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekt i właściwości source jest [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aparat wiązania danych, musi najpierw użyj odbicia w obiekcie źródłowym, aby uzyskać <xref:System.ComponentModel.TypeDescriptor>i następnie wyszukiwać <xref:System.ComponentModel.PropertyDescriptor>. Ta sekwencja operacji odbicia jest potencjalnie bardzo czasochłonne, z punktu widzenia wydajności.  
  
 Druga metoda rozpoznawania odwołań do obiektów obejmuje [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekt źródłowy, który implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu i właściwości source, który jest [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości. W takim przypadku aparat wiązania danych używa odbicia bezpośrednio na typ źródła i pobiera wymaganej właściwości. Nadal nie jest optymalna metoda, ale jego koszt mniej w pracy zestaw wymagań niż pierwsza metoda.  
  
 Trzeci metody rozpoznawania odwołań do obiektów obejmuje obiekt źródłowy, który jest <xref:System.Windows.DependencyObject> i właściwości source, który jest <xref:System.Windows.DependencyProperty>. W takim przypadku aparat wiązania danych nie trzeba używać odbicia. Zamiast tego aparatu właściwości i aparat wiązania danych ze sobą rozpoznać odwołania do właściwości niezależnie. Jest to metoda optymalne dla rozpoznawania odwołań obiekt używany do wiązania danych.  
  
 W poniższej tabeli porównano szybkości wiązania z danymi <xref:System.Windows.Controls.TextBlock.Text%2A> właściwości tysiąca <xref:System.Windows.Controls.TextBlock> elementów za pomocą tych trzech metod.  
  
|**Powiązanie z właściwością Text blok tekstu**|**Czas powiązania (ms)**|**Czas renderowania — zawiera powiązanie (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Właściwości [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu|115|314|  
|Właściwości [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu, który implementuje <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|Aby <xref:System.Windows.DependencyProperty> z <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Powiązanie do obiektów dużych CLR  
 Istnieje negatywny wpływ na wydajność znaczące, gdy dane związane z jedną [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu z tysiącami właściwości. Można zminimalizować wpływ ten dzieląc pojedynczy obiekt na wielu [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekty o mniej właściwości. W tabeli przedstawiono powiązania i czas renderowania dla powiązania danych do jednego dużych [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu w porównaniu z wielu obiektów mniejsze.  
  
|**Obiekty blok tekstu 1000 powiązania danych**|**Czas powiązania (ms)**|**Czas renderowania — zawiera powiązanie (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|Aby [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekt o właściwości 1000|950|1200|  
|Do 1000 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekty z jednej właściwości|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Powiązanie z ItemsSource.  
 Rozważmy scenariusz, w którym zostały [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> obiektu, który zawiera listę pracowników, które mają być wyświetlane w <xref:System.Windows.Controls.ListBox>. Aby utworzyć połączenie między tymi dwoma obiektami, czy powiązanie listy pracowników do <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox>. Jednak zdarzyć, że masz pracownika dołączenie tej grupy. Może uważasz, że aby wstawić tej nowej osoby do użytkownika powiązanych z <xref:System.Windows.Controls.ListBox> wartości, czy po prostu Dodaj tę osobę do listy pracowników i oczekują tej zmiany automatycznie rozpoznane przez aparat wiązania danych. Założenie, że może okazać się false; w rzeczywistości zmiany nie zostaną odzwierciedlone w <xref:System.Windows.Controls.ListBox> automatycznie. Jest to spowodowane [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> obiektu automatycznie nie wygenerował zdarzenie Kolekcja została zmieniona. Aby uzyskać <xref:System.Windows.Controls.ListBox> do zastosowania zmian, będzie trzeba ponownie utworzyć listę pracowników i ponownie podłącz go do <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox>. Podczas działania tego rozwiązania, wprowadza wyraźnego wpływu. Zawsze należy przypisać <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListBox> nowy obiekt, <xref:System.Windows.Controls.ListBox> najpierw zgłasza optymalizacji jego poprzednie elementy i ponownie wygenerować jego całą listę. Wpływ na wydajność jest powiększony, jeśli Twoje <xref:System.Windows.Controls.ListBox> mapuje złożony <xref:System.Windows.DataTemplate>.  
  
 Bardzo wydajny rozwiązanie tego problemu jest zapewnienie listy pracowników <xref:System.Collections.ObjectModel.ObservableCollection%601>. <xref:System.Collections.ObjectModel.ObservableCollection%601> Obiektu zgłasza który aparat wiązania danych może otrzymywać powiadomienia o zmianach. Zdarzenie dodaje lub usuwa element z <xref:System.Windows.Controls.ItemsControl> bez konieczności ponownego generowania całą listę.  
  
 Poniższa tabela pokazuje na czas potrzebny do zaktualizowania <xref:System.Windows.Controls.ListBox> (z interfejsu użytkownika wirtualizacji wyłączona) po dodaniu jeden element. Liczba w pierwszym wierszu określa czas, który upłynął podczas [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> obiektów jest powiązany z <xref:System.Windows.Controls.ListBox> elementu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Liczba w drugim wierszu określa czas, który upłynął podczas <xref:System.Collections.ObjectModel.ObservableCollection%601> jest powiązany z <xref:System.Windows.Controls.ListBox> elementu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Uwaga przy użyciu oszczędności długiego czasu <xref:System.Collections.ObjectModel.ObservableCollection%601> strategii powiązania danych.  
  
|**Właściwość ItemsSource powiązanie danych**|**Zaktualizuj czas 1 elementu (ms)**|  
|--------------------------------------|---------------------------------------|  
|Aby [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> obiektu|1656|  
|Aby <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Powiązać IList ItemsControl nie interfejsu IEnumerable.  
 Jeśli masz wybór między powiązania <xref:System.Collections.Generic.IList%601> lub <xref:System.Collections.IEnumerable> do <xref:System.Windows.Controls.ItemsControl> obiektów, wybierz <xref:System.Collections.Generic.IList%601> obiektu. Powiązanie <xref:System.Collections.IEnumerable> do <xref:System.Windows.Controls.ItemsControl> wymusza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utworzyć otoka <xref:System.Collections.Generic.IList%601> obiektu, który oznacza, że wydajność jest wpływ niepotrzebnego obciążenia innego obiektu.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Czy nie skonwertować CLR obiekty do XML tylko dla powiązania danych.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zezwala na dane powiązać [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] zawartości; jednak powiązania danych [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] zawartości jest mniejsza niż powiązania danych [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów. Nie można konwertować [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] dane do pliku XML obiektu, jeśli jedynym celem jest dla powiązania danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planowanie wydajności aplikacji](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Wykorzystanie możliwości sprzętu](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Zachowanie obiektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Zasoby aplikacji](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Inne zalecenia dotyczące wydajności](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
