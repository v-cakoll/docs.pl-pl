---
title: Nowości w WPF w wersji 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 5e9194dc4dc8ef3246870dc1fd71fa53d3ad143f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227486"
---
# <a name="whats-new-in-wpf-version-45"></a>Nowości w WPF w wersji 4.5
<a name="introduction"></a> Ten temat zawiera informacje o nowych i ulepszonych funkcji w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] w wersji 4.5.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Formantu wstążki](#ribbon_control)  
  
-   [Zwiększona wydajność podczas wyświetlania dużych zestawów zgrupowanych danych](#grouped_virtualization)  
  
-   [Nowe funkcje VirtualizingPanel](#VirtualizingPanel)  
  
-   [Powiązanie z właściwościami statycznymi](#static_properties)  
  
-   [Uzyskiwanie dostępu do kolekcji w wątkach bez interfejsu użytkownika](#xthread_access)  
  
-   [Synchroniczne i asynchroniczne sprawdzanie poprawności danych](#INotifyDataErrorInfo)  
  
-   [Automatyczne aktualizowanie źródło powiązania danych](#delay)  
  
-   [Wiązać z typami ICustomTypeProvider tej implementacji](#ICustomTypeProvider)  
  
-   [Trwa pobieranie informacji o wiązaniach danych z wyrażenia wiązania](#binding_state)  
  
-   [Sprawdzanie prawidłowego obiektu DataContext](#DisconnectedSource)  
  
-   [Zmiana położenia danych, jak zmieniają się dane wartości (kształtowanie na bieżąco)](#live_shaping)  
  
-   [Ulepszona obsługa ustanawiania słabe odwołanie do zdarzenia](#weak_event_pattern)  
  
-   [Nowe metody dla klasy dyspozytora](#async)  
  
-   [Rozszerzenia znaczników dla zdarzeń](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Formantu wstążki  
 WPF 4.5 jest dostarczany z <xref:System.Windows.Controls.Ribbon.Ribbon> formant, który jest hostem kart, Menu aplikacji i paska narzędzi Szybki dostęp.  Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Zwiększona wydajność podczas wyświetlania dużych zestawów zgrupowanych danych  
 Wirtualizacja interfejsu użytkownika występuje, gdy podzestaw interfejsu użytkownika (UI) elementy są generowane na podstawie większej liczby elementów danych, w oparciu o elementy, które są widoczne na ekranie. <xref:System.Windows.Controls.VirtualizingPanel> Definiuje <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> dołączona właściwość, która umożliwia wirtualizację interfejsu użytkownika dla zgrupowanych danych.  Aby uzyskać więcej informacji na temat grupowania danych, zobacz jak: Sortuj i Grupuj dane przy użyciu widoku w XAML.  Aby uzyskać więcej informacji na temat wirtualizowania pogrupowanych danych, zobacz <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> dołączona właściwość.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>Nowe funkcje VirtualizingPanel  
  
1.  Można określić czy <xref:System.Windows.Controls.VirtualizingPanel>, takich jak <xref:System.Windows.Controls.VirtualizingStackPanel>, wyświetla elementy częściowe za pomocą <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> dołączona właściwość. Jeśli <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> ustawiono <xref:System.Windows.Controls.ScrollUnit.Item>, <xref:System.Windows.Controls.VirtualizingPanel> będą wyświetlane tylko elementy, które są całkowicie widoczna. Jeśli <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> ustawiono <xref:System.Windows.Controls.ScrollUnit.Pixel>, <xref:System.Windows.Controls.VirtualizingPanel> może wyświetlać elementy częściowo widoczny.  
  
2.  Można określić rozmiar pamięci podręcznej przed i po nim okienka ekranu podczas <xref:System.Windows.Controls.VirtualizingPanel> jest wirtualizacja za pomocą <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> dołączona właściwość.  Pamięć podręczna jest ilość miejsca na powyżej lub poniżej okienka ekranu, w której elementy są bez wirtualizacji.  Używanie pamięci podręcznej, aby uniknąć generowania elementów interfejsu użytkownika, ponieważ są one przewijane do widoku może poprawić wydajność. Pamięć podręczna jest wypełniana z niższym priorytetem, dzięki czemu aplikacja nie przestać odpowiadać podczas operacji. <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> Właściwość określa jednostkę miary, który jest używany przez <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Powiązanie z właściwościami statycznymi  
 Właściwości statyczne służy jako źródło powiązania danych. Aparat powiązania danych rozpoznaje po zmianie wartości właściwości, jeśli statyczne zdarzenie jest zgłaszane.  Na przykład jeśli klasa `SomeClass` definiuje statyczne właściwość o nazwie `MyProperty`, `SomeClass` można zdefiniować zdarzeń statycznych, który jest wywołane, gdy wartość `MyProperty` zmiany.  Zdarzenia statyczne można użyć jednej z następujących podpisów.  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Uwaga w pierwszym przypadku klasa udostępnia zdarzeń statycznych o nazwie *PropertyName* `Changed` , który przekazuje <xref:System.EventArgs> do narzędzia obsługi zdarzeń.  W drugim przypadku klasa udostępnia zdarzeń statycznych o nazwie `StaticPropertyChanged` , który przekazuje <xref:System.ComponentModel.PropertyChangedEventArgs> do narzędzia obsługi zdarzeń. Klasa, która implementuje właściwość statyczną można wybrać wywoływanie powiadomień o zmianie właściwości przy użyciu jednej z metod.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Uzyskiwanie dostępu do kolekcji w wątkach bez interfejsu użytkownika  
 WPF umożliwia dostępu i modyfikowania danych kolekcji w wątkach, innej niż ta, która utworzyła kolekcję.  Pozwala na użycie wątku w tle na odbieranie danych z zewnętrznego źródła, takich jak bazy danych i wyświetlić dane w wątku interfejsu użytkownika.  Za pomocą innego wątku, aby zmodyfikować kolekcji, interfejs użytkownika reaguje na interakcję z użytkownikiem.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Synchroniczne i asynchroniczne sprawdzanie poprawności danych  
 <xref:System.ComponentModel.INotifyDataErrorInfo> Interfejs umożliwia klas jednostek danych implementować niestandardowe reguły sprawdzania poprawności oraz udostępnianie wyników weryfikacji asynchronicznie. Ten interfejs obsługuje również obiekty błędów niestandardowych, wiele błędów na właściwość, właściwości wielu błędów i błędy na poziomie jednostki.  Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Automatyczne aktualizowanie źródło powiązania danych  
 Jeśli używasz powiązanie danych można zaktualizować źródła danych, możesz użyć <xref:System.Windows.Data.BindingBase.Delay%2A> właściwość, aby określić ilość czasu, aby przekazać po zmianie właściwości w elemencie docelowym przed aktualizacji źródła.  Na przykład załóżmy, że masz <xref:System.Windows.Controls.Slider> zawierający jego <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> dwukierunkowe danych właściwości powiązane z właściwością obiektu danych i <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwość jest ustawiona na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  W tym przykładzie, kiedy użytkownik przesunie <xref:System.Windows.Controls.Slider>, aktualizacje źródła dla każdego piksela, <xref:System.Windows.Controls.Slider> przenosi.  Obiekt źródłowy musi zazwyczaj wartość suwaka tylko wtedy, gdy suwaka <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> zatrzymuje się zmiana.  Aby zapobiec, zbyt często aktualizowania źródła, użyj <xref:System.Windows.Data.BindingBase.Delay%2A> do określenia, czy źródło nie powinny być aktualizowane, dopóki określoną ilość czasu, liczonego od przycisku suwaka zatrzymuje przenoszenia.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Wiązać z typami ICustomTypeProvider tej implementacji  
 WPF obsługuje powiązanie danych do obiektów, które implementują <xref:System.Reflection.ICustomTypeProvider>, znanego również jako niestandardowych typów.  Można użyć niestandardowych typów w następujących przypadkach.  
  
1.  Jako <xref:System.Windows.PropertyPath> w powiązaniu danych. Na przykład <xref:System.Windows.Data.Binding.Path%2A> właściwość <xref:System.Windows.Data.Binding> można odwoływać się do właściwości typu niestandardowego.  
  
2.  Jako wartość <xref:System.Windows.DataTemplate.DataType%2A> właściwości.  
  
3.  Jako typ, który określa automatycznie wygenerowanych kolumn w <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Trwa pobieranie informacji o wiązaniach danych z wyrażenia wiązania  
 W niektórych przypadkach możesz otrzymać <xref:System.Windows.Data.BindingExpression> z <xref:System.Windows.Data.Binding> i potrzebujesz informacji na temat obiektów źródłowych i docelowych wiązania.  Nowe interfejsy API zostały dodane do pozwalają użytkownikom czerpać źródła lub obiektu docelowego lub właściwości skojarzonej.  Jeśli masz <xref:System.Windows.Data.BindingExpression>, uzyskać informacje na temat źródłowe i docelowe przy użyciu następujących interfejsów API.  
  
|Aby znaleźć tę wartość powiązania|Za pomocą tego interfejsu API|  
|---------------------------------------|------------------|  
|Obiekt docelowy|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Właściwość docelowa|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Obiekt źródłowy|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Właściwość source|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Czy <xref:System.Windows.Data.BindingExpression> należy do <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Właściciel <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>Sprawdzanie prawidłowego obiektu DataContext  
 Istnieją przypadki, gdzie <xref:System.Windows.FrameworkElement.DataContext%2A> kontenera elementu w <xref:System.Windows.Controls.ItemsControl> zostanie rozłączony.  Kontenera elementu jest elementem interfejsu użytkownika, który wyświetla element <xref:System.Windows.Controls.ItemsControl>.  Gdy <xref:System.Windows.Controls.ItemsControl> dane powiązane z kolekcją, kontenera elementu jest generowany dla każdego elementu. W niektórych przypadkach kontenerów elementów są usuwane z drzewa wizualnego. Są dwa typowe przypadki, gdzie kontenera elementu jest usuwany, gdy element zostanie usunięty z kolekcji źródłowej, a gdy włączona jest wirtualizacja <xref:System.Windows.Controls.ItemsControl>. W takich przypadkach <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość kontenera elementu zostanie ustawiona na obiekt wartownik, który jest zwracany przez <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> właściwość statyczna.  Należy sprawdzić, czy <xref:System.Windows.FrameworkElement.DataContext%2A> jest równa <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> obiektu przed uzyskaniem dostępu do <xref:System.Windows.FrameworkElement.DataContext%2A> kontenera elementu.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Zmiana położenia danych, jak zmieniają się dane wartości (kształtowanie na bieżąco)  
 Zbierania danych mogą być grupowane, sortowane lub filtrowane. WPF 4.5 umożliwia danych można zmieniać kolejności po zmodyfikowaniu danych. Na przykład załóżmy, że aplikacja używa <xref:System.Windows.Controls.DataGrid> Aby wyświetlić listę zasobów w giełdowych i zasoby są sortowane według wartości zapasów. Jeśli sortowanie na żywo jest włączona na temat zasobów <xref:System.Windows.Data.CollectionView>, położenie akcji w <xref:System.Windows.Controls.DataGrid> przenoszone, gdy wartość zasobów staje się większą lub wartość poniżej innej akcji.   Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.ICollectionViewLiveShaping> interfejsu.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Ulepszona obsługa ustanawiania słabe odwołanie do zdarzenia  
 Implementacja wzorca zdarzeń słabych jest teraz łatwiejsze, ponieważ subskrybentów zdarzeń mogą brać udział w jej bez implementacji interfejsu dodatkowe.  Ogólny <xref:System.Windows.WeakEventManager> klasy umożliwia także subskrybentów do udziału w słaby wzorzec zdarzeń, jeśli jest to dedykowana <xref:System.Windows.WeakEventManager> nie istnieje dla określonych zdarzeń.  Aby uzyskać więcej informacji, zobacz [słabe wzorce zdarzeń](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Nowe metody dla klasy dyspozytora  
 Klasa dyspozytora definiuje nowych metod operacje synchroniczne i asynchroniczne.  Synchronicznej <xref:System.Windows.Threading.Dispatcher.Invoke%2A> metoda definiuje przeciążeń, które przyjmują <xref:System.Action> lub <xref:System.Func%601> parametru. Nowe metody asynchronicznej <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, pobiera również <xref:System.Action> lub <xref:System.Func%601> jako parametr wywołania zwrotnego i zwraca <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>.   <xref:System.Windows.Threading.DispatcherOperation> i <xref:System.Windows.Threading.DispatcherOperation%601> klasy definiują <xref:System.Threading.Tasks.Task> właściwości.  Gdy wywołujesz <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, możesz użyć `await` — słowo kluczowe z oboma <xref:System.Windows.Threading.DispatcherOperation> lub skojarzonego <xref:System.Threading.Tasks.Task>. Jeśli musisz czekać synchronicznie <xref:System.Threading.Tasks.Task> zwracanym przez <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>, wywołaj <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> — metoda rozszerzenia. Wywoływanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> spowoduje zakleszczenia Jeśli operacja jest kolejkowana w wątku wywołującego. Aby uzyskać więcej informacji o korzystaniu z <xref:System.Threading.Tasks.Task> do wykonywania operacji asynchronicznych, zobacz [równoległość zadań (Biblioteka zadań równoległych)](../../../standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Rozszerzenia znaczników dla zdarzeń  
 WPF 4.5 obsługuje rozszerzenia znaczników dla zdarzeń.  WPF nie definiuje rozszerzeniem znacznika ma być używany dla zdarzeń, może utworzyć rozszerzenie znaczników, który może służyć do zdarzeń są stron trzecich.  
  
## <a name="see-also"></a>Zobacz także

- [Co nowego w programie .NET Framework](../../whats-new/index.md)
