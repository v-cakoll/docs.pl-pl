---
title: Nowości w WPF w wersji 4.5
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 708b2fc231bfe7a9bc1f52872a0ec41c91931f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174709"
---
# <a name="whats-new-in-wpf-version-45"></a>Nowości w WPF w wersji 4.5
<a name="introduction"></a>Ten temat zawiera informacje o nowych [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] i ulepszonych funkcjach w wersji 4.5.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Kontrolka wstążki](#ribbon_control)  
  
- [Zwiększona wydajność podczas wyświetlania dużych zestawów zgrupowanych danych](#grouped_virtualization)  
  
- [Nowe funkcje panelizacji virtualizacji](#VirtualizingPanel)  
  
- [Powiązanie z właściwościami statycznymi](#static_properties)  
  
- [Uzyskiwanie dostępu do kolekcji w wątkach innych niż interfejs użytkownika](#xthread_access)  
  
- [Synchronicznie i asynchronicznie weryfikując dane](#INotifyDataErrorInfo)  
  
- [Automatyczne aktualizowanie źródła powiązania danych](#delay)  
  
- [Powiązanie z typami implementuuuujymisy ICustomTypeProvider](#ICustomTypeProvider)  
  
- [Pobieranie informacji o powiązaniach danych z wyrażenia wiążącego](#binding_state)  
  
- [Sprawdzanie prawidłowego obiektu DataContext](#DisconnectedSource)  
  
- [Zmiana położenia danych w miarę zmiany wartości danych (kształtowanie na żywo)](#live_shaping)  
  
- [Ulepszona obsługa ustanowienia słabego odniesienia do zdarzenia](#weak_event_pattern)  
  
- [Nowe metody dla klasy Dispatcher](#async)  
  
- [Rozszerzenia znaczników dla zdarzeń](#events_markup_extenions)  
  
<a name="ribbon_control"></a>
## <a name="ribbon-control"></a>Kontrolka wstążki  
 WPF WPF 4.5 jest dostarczany z formantem, <xref:System.Windows.Controls.Ribbon.Ribbon> który obsługuje pasek narzędzi szybki dostęp, menu aplikacji i karty.  Aby uzyskać więcej informacji, zobacz [Omówienie Wstążki](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Zwiększona wydajność podczas wyświetlania dużych zestawów zgrupowanych danych  
 Wirtualizacja interfejsu użytkownika występuje, gdy podzbiór elementów interfejsu użytkownika (UI) są generowane z większej liczby elementów danych, na podstawie których elementy są widoczne na ekranie. Definiuje <xref:System.Windows.Controls.VirtualizingPanel> dołączoną <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> właściwość, która umożliwia wirtualizację interfejsu użytkownika dla zgrupowanych danych.  Aby uzyskać więcej informacji na temat grupowania danych, zobacz Jak: Sortowanie i grupowanie danych przy użyciu widoku w języku XAML.  Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> wirtualizacji zgrupowanych danych, zobacz dołączoną właściwość.  
  
<a name="VirtualizingPanel"></a>
## <a name="new-features-for-the-virtualizingpanel"></a>Nowe funkcje panelizacji virtualizacji  
  
1. Można <xref:System.Windows.Controls.VirtualizingPanel>określić, czy elementy <xref:System.Windows.Controls.VirtualizingStackPanel>częściowe, takie <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> jak , są wyświetlane przy użyciu dołączonej właściwości. Jeśli <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> jest <xref:System.Windows.Controls.ScrollUnit.Item>ustawiona <xref:System.Windows.Controls.VirtualizingPanel> na , będzie wyświetlać tylko elementy, które są całkowicie widoczne. Jeśli <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> jest <xref:System.Windows.Controls.ScrollUnit.Pixel>ustawiona <xref:System.Windows.Controls.VirtualizingPanel> na , może wyświetlać częściowo widoczne elementy.  
  
2. Można określić rozmiar pamięci podręcznej przed i <xref:System.Windows.Controls.VirtualizingPanel> po rzutni, <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> gdy jest wirtualizacji przy użyciu dołączonej właściwości.  Pamięć podręczna to ilość miejsca powyżej lub poniżej rzutni, w której elementy nie są zwirtualizowane.  Korzystanie z pamięci podręcznej, aby uniknąć generowania elementów interfejsu użytkownika, ponieważ są one przewijane do widoku może zwiększyć wydajność. Pamięć podręczna jest wypełniana z niższym priorytetem, dzięki czemu aplikacja nie przestaje odpowiadać podczas operacji. Właściwość <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> określa jednostkę miary, <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>która jest używana przez .  
  
<a name="static_properties"></a>
## <a name="binding-to-static-properties"></a>Powiązanie z właściwościami statycznymi  
 Można użyć właściwości statycznych jako źródła powiązania danych. Aparat wiązania danych rozpoznaje, gdy wartość właściwości zmienia się, jeśli zdarzenie statyczne jest wywoływane.  Na przykład jeśli `SomeClass` klasa definiuje właściwość `MyProperty`statyczną o nazwie , `SomeClass` można zdefiniować `MyProperty` zdarzenie statyczne, które jest wywoływane, gdy wartość zmian.  Zdarzenie statyczne można użyć jednego z następujących podpisów.  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Należy zauważyć, że w pierwszym przypadku klasa udostępnia zdarzenie statyczne <xref:System.EventArgs> o nazwie *PropertyName,* `Changed` który przekazuje do obsługi zdarzeń.  W drugim przypadku klasa udostępnia zdarzenie statyczne `StaticPropertyChanged` o <xref:System.ComponentModel.PropertyChangedEventArgs> nazwie, które przechodzi do programu obsługi zdarzeń. Klasa, która implementuje właściwości statycznej można wybrać do podniesienia powiadomień zmiany właściwości przy użyciu jednej z metod.  
  
<a name="xthread_access"></a>
## <a name="accessing-collections-on-non-ui-threads"></a>Uzyskiwanie dostępu do kolekcji w wątkach innych niż interfejs użytkownika  
 WPF WPF umożliwia dostęp i modyfikowanie kolekcji danych w wątkach innych niż ten, który utworzył kolekcję.  Dzięki temu można użyć wątku w tle do odbierania danych ze źródła zewnętrznego, takiego jak baza danych, i wyświetlanie danych w wątku interfejsu użytkownika.  Za pomocą innego wątku do modyfikowania kolekcji, interfejs użytkownika pozostaje reaguje na interakcję użytkownika.  
  
<a name="INotifyDataErrorInfo"></a>
## <a name="synchronously-and-asynchronously-validating-data"></a>Synchronicznie i asynchronicznie weryfikując dane  
 Interfejs <xref:System.ComponentModel.INotifyDataErrorInfo> umożliwia klas jednostek danych do zaimplementowania niestandardowych reguł sprawdzania poprawności i uwidaczniać wyniki sprawdzania poprawności asynchronicznie. Ten interfejs obsługuje również niestandardowe obiekty błędów, wiele błędów na właściwość, błędy między właściwościami i błędy na poziomie jednostki.  Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Automatyczne aktualizowanie źródła powiązania danych  
 Jeśli używasz powiązania danych do aktualizacji źródła danych, można użyć <xref:System.Windows.Data.BindingBase.Delay%2A> właściwości, aby określić ilość czasu do przekazania po zmianie właściwości na miejsce docelowe przed aktualizacjami źródła.  Załóżmy na przykład, <xref:System.Windows.Controls.Slider> że <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> masz, że ma swoje dane właściwości dwukierunkowe powiązane z właściwością obiektu danych i <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwość jest ustawiona na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  W tym przykładzie, gdy <xref:System.Windows.Controls.Slider>użytkownik przenosi , źródło <xref:System.Windows.Controls.Slider> jest aktualizowane dla każdego piksela, który się porusza.  Obiekt źródłowy zazwyczaj potrzebuje wartości suwaka tylko wtedy, <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> gdy suwak przestaje się zmieniać.  Aby zapobiec aktualizowaniu źródła <xref:System.Windows.Data.BindingBase.Delay%2A> zbyt często, należy użyć, aby określić, że źródło nie powinny być aktualizowane, dopóki nie upłynie określony czas po kciuk przestaje się poruszać.  
  
<a name="ICustomTypeProvider"></a>
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Powiązanie z typami implementuuuujymisy ICustomTypeProvider  
 WPF WPF obsługuje powiązanie danych do obiektów, które implementują <xref:System.Reflection.ICustomTypeProvider>, znany również jako typy niestandardowe.  Typy niestandardowe można używać w następujących przypadkach.  
  
1. Jako <xref:System.Windows.PropertyPath> w powiązaniu danych. Na przykład <xref:System.Windows.Data.Binding.Path%2A> właściwość <xref:System.Windows.Data.Binding> może odwoływać się do właściwości typu niestandardowego.  
  
2. Jako wartość <xref:System.Windows.DataTemplate.DataType%2A> właściwości.  
  
3. Jako typ, który określa automatycznie generowane kolumny <xref:System.Windows.Controls.DataGrid>w pliku .  
  
<a name="binding_state"></a>
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Pobieranie informacji o powiązaniach danych z wyrażenia wiążącego  
 W niektórych przypadkach może <xref:System.Windows.Data.BindingExpression> pojawić <xref:System.Windows.Data.Binding> się informacje o i potrzebujesz informacji o obiektach źródłowych i docelowych powiązania.  Dodano nowe interfejsy API, aby umożliwić uzyskanie obiektu źródłowego lub docelowego lub skojarzonej właściwości.  Jeśli masz <xref:System.Windows.Data.BindingExpression>, użyj następujących interfejsów API, aby uzyskać informacje o celu i źródła.  
  
|Aby znaleźć tę wartość powiązania|Użyj tego interfejsu API|  
|---------------------------------------|------------------|  
|Obiekt docelowy|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Właściwość docelowa|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Obiekt źródłowy|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Właściwość źródłowsza|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Czy <xref:System.Windows.Data.BindingExpression> należy do<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Właściciel<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>
## <a name="checking-for-a-valid-datacontext-object"></a>Sprawdzanie prawidłowego obiektu DataContext  
 Istnieją przypadki, <xref:System.Windows.FrameworkElement.DataContext%2A> gdy kontener elementu <xref:System.Windows.Controls.ItemsControl> w zostanie rozłączony.  Kontener towaru to element interfejsu użytkownika, <xref:System.Windows.Controls.ItemsControl>który wyświetla element w pliku .  Gdy <xref:System.Windows.Controls.ItemsControl> dane są powiązane z kolekcją, kontener towaru jest generowany dla każdego elementu. W niektórych przypadkach kontenery elementów są usuwane z drzewa wizualnego. Dwa typowe przypadki, w których kontener towaru jest usuwany, są wtedy, gdy <xref:System.Windows.Controls.ItemsControl>element jest usuwany z podstawowej kolekcji i gdy wirtualizacja jest włączona w programie . W takich przypadkach <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość kontenera elementu zostanie ustawiona na obiekt <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> wartownika, który jest zwracany przez właściwość statyczną.  Przed dostępem <xref:System.Windows.FrameworkElement.DataContext%2A> do <xref:System.Windows.FrameworkElement.DataContext%2A> kontenera <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> elementu należy sprawdzić, czy jest równa obiektowi.  
  
<a name="live_shaping"></a>
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Zmiana położenia danych w miarę zmiany wartości danych (kształtowanie na żywo)  
 Zbiór danych można grupować, sortować lub filtrować. WPF 4.5 umożliwia dane do zmiany rozmieszczenia, gdy dane są modyfikowane. Załóżmy na przykład, że <xref:System.Windows.Controls.DataGrid> aplikacja używa a do listy zapasów na giełdzie, a akcje są sortowane według wartości zapasów. Jeśli na akcjach włączono sortowanie na żywo, <xref:System.Windows.Data.CollectionView>pozycja <xref:System.Windows.Controls.DataGrid> akcji w ruchach, gdy wartość akcji staje się większa lub mniejsza niż wartość innego magazynu.   Aby uzyskać więcej <xref:System.ComponentModel.ICollectionViewLiveShaping> informacji, zobacz interfejs.  
  
<a name="weak_event_pattern"></a>
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Ulepszona obsługa ustanowienia słabego odniesienia do zdarzenia  
 Implementowanie wzorca zdarzeń słabe jest teraz łatwiejsze, ponieważ subskrybenci zdarzeń mogą uczestniczyć w nim bez implementowania dodatkowego interfejsu.  Klasa <xref:System.Windows.WeakEventManager> ogólna umożliwia również subskrybentów do udziału <xref:System.Windows.WeakEventManager> w wzorzec zdarzeń słabe, jeśli dedykowane nie istnieje dla określonego zdarzenia.  Aby uzyskać więcej informacji, zobacz [Słabe wzorce zdarzeń](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>
## <a name="new-methods-for-the-dispatcher-class"></a>Nowe metody dla klasy Dispatcher  
 Klasa Dyspozytor definiuje nowe metody dla operacji synchronicznych i asynchronicznych.  Metoda synchronicznego <xref:System.Windows.Threading.Dispatcher.Invoke%2A> definiuje przeciążenia, <xref:System.Action> które <xref:System.Func%601> przyjmują lub parametr. Nowa metoda asynchroniza <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, również <xref:System.Action> <xref:System.Func%601> przyjmuje lub jako parametr <xref:System.Windows.Threading.DispatcherOperation> wywołania zwrotnego i zwraca lub <xref:System.Windows.Threading.DispatcherOperation%601>.   Klasy <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Windows.Threading.DispatcherOperation%601> i klasy <xref:System.Threading.Tasks.Task> definiują właściwość.  Podczas <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>wywoływania można użyć `await` słowa kluczowego <xref:System.Windows.Threading.DispatcherOperation> z lub <xref:System.Threading.Tasks.Task>skojarzonym . Jeśli trzeba czekać synchronicznie dla <xref:System.Threading.Tasks.Task> tego, który <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Windows.Threading.DispatcherOperation%601>jest zwracany przez lub , wywołać <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> metodę rozszerzenia. Wywołanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> spowoduje zakleszczenie, jeśli operacja jest w kolejce w wątku wywołującym. Aby uzyskać więcej <xref:System.Threading.Tasks.Task> informacji na temat używania operacji asynchronicznych do wykonywania, zobacz [Równoległość zadań (biblioteka równoległa zadań).](../../../standard/parallel-programming/task-based-asynchronous-programming.md)  
  
<a name="events_markup_extenions"></a>
## <a name="markup-extensions-for-events"></a>Rozszerzenia znaczników dla zdarzeń  
 WPF WPF 4.5 obsługuje rozszerzenia znaczników dla zdarzeń.  Chociaż WPF nie definiuje rozszerzenia znaczników, które mają być używane dla zdarzeń, strony trzecie są w stanie utworzyć rozszerzenie znaczników, które mogą być używane ze zdarzeniami.  
  
## <a name="see-also"></a>Zobacz też

- [Co nowego w platformie .NET Framework](../../whats-new/index.md)
