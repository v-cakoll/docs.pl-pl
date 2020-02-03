---
title: Nowości w WPF w wersji 4.5
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 8eff8da7746047c450b2e23af63d43b13f3b970c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746923"
---
# <a name="whats-new-in-wpf-version-45"></a>Nowości w WPF w wersji 4.5
<a name="introduction"></a>Ten temat zawiera informacje o nowych i ulepszonych funkcjach w programie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] w wersji 4,5.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Kontrolka wstążki](#ribbon_control)  
  
- [Zwiększona wydajność podczas wyświetlania dużych zestawów pogrupowanych danych](#grouped_virtualization)  
  
- [Nowe funkcje VirtualizingPanel](#VirtualizingPanel)  
  
- [Powiązanie z właściwościami statycznymi](#static_properties)  
  
- [Uzyskiwanie dostępu do kolekcji w wątkach innych niż interfejs użytkownika](#xthread_access)  
  
- [Synchroniczne i asynchroniczne Weryfikowanie danych](#INotifyDataErrorInfo)  
  
- [Automatyczne aktualizowanie źródła powiązania danych](#delay)  
  
- [Powiązanie z typami, które implementują ICustomTypeProvider](#ICustomTypeProvider)  
  
- [Pobieranie informacji o powiązaniu danych z wyrażenia powiązania](#binding_state)  
  
- [Sprawdzanie prawidłowego obiektu DataContext](#DisconnectedSource)  
  
- [Zmiana położenia danych w miarę zmiany wartości danych (kształtowanie na żywo)](#live_shaping)  
  
- [Ulepszona obsługa tworzenia słabego odwołania do zdarzenia](#weak_event_pattern)  
  
- [Nowe metody dla klasy dyspozytora](#async)  
  
- [Rozszerzenia znaczników dla zdarzeń](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Kontrolka wstążki  
 WPF 4,5 jest dostarczany z kontrolką <xref:System.Windows.Controls.Ribbon.Ribbon>, która obsługuje pasek narzędzi Szybki dostęp, menu aplikacji i karty.  Aby uzyskać więcej informacji, zobacz [Omówienie wstążki](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Zwiększona wydajność podczas wyświetlania dużych zestawów pogrupowanych danych  
 Wirtualizacja interfejsu użytkownika występuje, gdy podzbiór elementów interfejsu (UI) jest generowany na podstawie większej liczby elementów danych, na podstawie których elementy są widoczne na ekranie. <xref:System.Windows.Controls.VirtualizingPanel> definiuje przyłączoną Właściwość <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A>, która umożliwia wirtualizację interfejsu użytkownika dla pogrupowanych danych.  Aby uzyskać więcej informacji na temat grupowania danych, zobacz jak: sortowanie i grupowanie danych przy użyciu widoku w języku XAML.  Aby uzyskać więcej informacji na temat wirtualizacji pogrupowanych danych, zobacz <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> dołączonej właściwości.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>Nowe funkcje VirtualizingPanel  
  
1. Można określić, czy <xref:System.Windows.Controls.VirtualizingPanel>, takie jak <xref:System.Windows.Controls.VirtualizingStackPanel>, Wyświetla częściowe elementy przy użyciu właściwości dołączone <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>. Jeśli <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> jest ustawiona na <xref:System.Windows.Controls.ScrollUnit.Item>, <xref:System.Windows.Controls.VirtualizingPanel> będzie wyświetlał tylko elementy, które są całkowicie widoczne. Jeśli <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> jest ustawiona na <xref:System.Windows.Controls.ScrollUnit.Pixel>, <xref:System.Windows.Controls.VirtualizingPanel> może wyświetlać częściowo widoczne elementy.  
  
2. Podczas wirtualizacji <xref:System.Windows.Controls.VirtualizingPanel> można określić rozmiar pamięci podręcznej przed i po jej wyświetleniu przy użyciu dołączonej właściwości <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A>.  Pamięć podręczna to ilość miejsca powyżej lub poniżej okienka ekranu, w którym elementy nie są zwirtualizowane.  Użycie pamięci podręcznej w celu uniknięcia generowania elementów interfejsu użytkownika w miarę ich przewijania do widoku może zwiększyć wydajność. Pamięć podręczna jest wypełniana niższym priorytetem, dzięki czemu aplikacja nie reaguje w trakcie operacji. Właściwość <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> określa jednostkę miary, która jest używana przez <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Powiązanie z właściwościami statycznymi  
 Można użyć właściwości statycznych jako źródła powiązania danych. Aparat powiązań danych jest rozpoznawany, gdy wartość właściwości ulega zmianie, gdy zostanie zgłoszone zdarzenie statyczne.  Na przykład, jeśli Klasa `SomeClass` definiuje Właściwość statyczną o nazwie `MyProperty`, `SomeClass` może zdefiniować zdarzenie statyczne, które jest zgłaszane w przypadku zmiany wartości `MyProperty`.  Zdarzenie statyczne może używać jednego z następujących sygnatur.  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Należy zauważyć, że w pierwszym przypadku Klasa ujawnia statyczne zdarzenie o nazwie *PropertyName*`Changed`, które przekazuje <xref:System.EventArgs> do programu obsługi zdarzeń.  W drugim przypadku Klasa ujawnia statyczne zdarzenie o nazwie `StaticPropertyChanged`, które przekazuje <xref:System.ComponentModel.PropertyChangedEventArgs> do programu obsługi zdarzeń. Klasa, która implementuje Właściwość statyczną, może wybrać do wywołania powiadomień o zmianach właściwości przy użyciu dowolnej metody.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Uzyskiwanie dostępu do kolekcji w wątkach innych niż interfejs użytkownika  
 WPF pozwala uzyskać dostęp do kolekcji danych i modyfikować je w wątkach innych niż te, które utworzyły kolekcję.  Dzięki temu można używać wątku w tle do odbierania danych z zewnętrznego źródła, takiego jak baza danych, i wyświetlania danych w wątku interfejsu użytkownika.  Użycie innego wątku w celu zmodyfikowania kolekcji powoduje, że interfejs użytkownika będzie odpowiadać na interakcję użytkownika.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Synchroniczne i asynchroniczne Weryfikowanie danych  
 Interfejs <xref:System.ComponentModel.INotifyDataErrorInfo> umożliwia klasom jednostek danych implementowanie niestandardowych reguł walidacji i ujawnianie wyników walidacji asynchronicznie. Ten interfejs obsługuje również niestandardowe obiekty błędów, wiele błędów na właściwość, błędy między właściwościami i błędy na poziomie jednostki.  Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Automatyczne aktualizowanie źródła powiązania danych  
 Jeśli użyjesz powiązania danych do zaktualizowania źródła danych, możesz użyć właściwości <xref:System.Windows.Data.BindingBase.Delay%2A>, aby określić ilość czasu do przekazania po zmianie właściwości w obiekcie docelowym przed aktualizacją źródła.  Załóżmy na przykład, że masz <xref:System.Windows.Controls.Slider>, która ma swoją <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> dane właściwości, które są powiązane z właściwością obiektu danych, a właściwość <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> jest ustawiona na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  W tym przykładzie, gdy użytkownik przesunie <xref:System.Windows.Controls.Slider>, Źródło aktualizuje dla każdego piksela, który przejdzie <xref:System.Windows.Controls.Slider>.  Obiekt źródłowy zwykle wymaga wartości suwaka tylko wtedy, gdy suwak <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> przestanie ulegać zmianie.  Aby zapobiec aktualizacji źródła zbyt często, użyj <xref:System.Windows.Data.BindingBase.Delay%2A>, aby określić, że źródło nie powinno być aktualizowane do momentu upływu pewnego czasu, gdy przesuwanie zakończy się.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Powiązanie z typami, które implementują ICustomTypeProvider  
 WPF obsługuje powiązanie danych z obiektami, które implementują <xref:System.Reflection.ICustomTypeProvider>, znane także jako typy niestandardowe.  Typów niestandardowych można używać w następujących przypadkach.  
  
1. Jako <xref:System.Windows.PropertyPath> w powiązaniu danych. Na przykład właściwość <xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Data.Binding> może odwoływać się do właściwości typu niestandardowego.  
  
2. Jako wartość właściwości <xref:System.Windows.DataTemplate.DataType%2A>.  
  
3. Jako typ, który określa automatycznie generowane kolumny w <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Pobieranie informacji o powiązaniu danych z wyrażenia powiązania  
 W niektórych przypadkach można uzyskać <xref:System.Windows.Data.BindingExpression> <xref:System.Windows.Data.Binding> i potrzebować informacji na temat obiektów źródłowych i docelowych powiązania.  Dodano nowe interfejsy API umożliwiające uzyskanie obiektu źródłowego lub docelowego albo powiązanej właściwości.  Gdy masz <xref:System.Windows.Data.BindingExpression>, użyj następujących interfejsów API, aby uzyskać informacje o miejscu docelowym i źródle.  
  
|Aby znaleźć tę wartość powiązania|Użyj tego interfejsu API|  
|---------------------------------------|------------------|  
|Obiekt docelowy|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Właściwość Target|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Obiekt źródłowy|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Właściwość Source|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Czy <xref:System.Windows.Data.BindingExpression> należy do <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Właściciel <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>Sprawdzanie prawidłowego obiektu DataContext  
 Istnieją przypadki, w których <xref:System.Windows.FrameworkElement.DataContext%2A> kontenera elementów w <xref:System.Windows.Controls.ItemsControl> zostanie odłączony.  Kontener elementu to element UI, który wyświetla element w <xref:System.Windows.Controls.ItemsControl>.  Gdy <xref:System.Windows.Controls.ItemsControl> to dane powiązane z kolekcją, kontener elementu jest generowany dla każdego elementu. W niektórych przypadkach kontenery elementów są usuwane z drzewa wizualnego. Dwa typowe przypadki, w których kontener elementu jest usuwany, jest usuwany z kolekcji źródłowej i w przypadku włączenia wirtualizacji na <xref:System.Windows.Controls.ItemsControl>. W takich przypadkach Właściwość <xref:System.Windows.FrameworkElement.DataContext%2A> kontenera elementów zostanie ustawiona na obiekt wskaźnikowy, który jest zwracany przez <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> właściwość statyczna.  Przed uzyskaniem dostępu do <xref:System.Windows.FrameworkElement.DataContext%2A> kontenera elementów należy sprawdzić, czy <xref:System.Windows.FrameworkElement.DataContext%2A> jest równa obiektowi <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A>.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Zmiana położenia danych w miarę zmiany wartości danych (kształtowanie na żywo)  
 Kolekcja danych może być zgrupowana, posortowana lub filtrowana. WPF 4,5 umożliwia zmianę układu danych podczas modyfikowania danych. Załóżmy na przykład, że aplikacja używa <xref:System.Windows.Controls.DataGrid>, aby wyświetlić listę zasobów na rynku giełdowym, a zapasy są posortowane według wartości zapasowej. Jeśli dla <xref:System.Windows.Data.CollectionView>zasobów jest włączona funkcja sortowania na żywo, pozycja zapasów w <xref:System.Windows.Controls.DataGrid> zostanie przeniesiona, gdy wartość zasobu stanie się większa lub mniejsza niż wartość innego zapasu.   Aby uzyskać więcej informacji, zobacz Interfejs <xref:System.ComponentModel.ICollectionViewLiveShaping>.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Ulepszona obsługa tworzenia słabego odwołania do zdarzenia  
 Zaimplementowanie słabego wzorca zdarzeń jest teraz łatwiejsze, ponieważ Subskrybenci do zdarzeń mogą uczestniczyć w nim bez implementowania dodatkowego interfejsu.  Klasa generyczna <xref:System.Windows.WeakEventManager> umożliwia również subskrybentom uczestnictwo w słabym wzorcu zdarzeń, jeśli dedykowany <xref:System.Windows.WeakEventManager> nie istnieje dla pewnego zdarzenia.  Aby uzyskać więcej informacji, zobacz [słabe wzorce zdarzeń](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Nowe metody dla klasy dyspozytora  
 Klasa dyspozytora definiuje nowe metody dla operacji synchronicznych i asynchronicznych.  Metoda synchroniczna <xref:System.Windows.Threading.Dispatcher.Invoke%2A> definiuje przeciążenia przyjmujące <xref:System.Action> lub <xref:System.Func%601> parametr. Nowa Metoda asynchroniczna, <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, również przyjmuje <xref:System.Action> lub <xref:System.Func%601> jako parametr wywołania zwrotnego i zwraca <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>.   Klasy <xref:System.Windows.Threading.DispatcherOperation> i <xref:System.Windows.Threading.DispatcherOperation%601> definiują Właściwość <xref:System.Threading.Tasks.Task>.  Podczas wywoływania <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>można użyć słowa kluczowego `await` z <xref:System.Windows.Threading.DispatcherOperation> lub skojarzonym <xref:System.Threading.Tasks.Task>. Jeśli musisz odczekać synchronicznie dla <xref:System.Threading.Tasks.Task> zwracanych przez <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>, wywołaj metodę rozszerzenia <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A>. Wywołanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> spowoduje zakleszczenie, jeśli operacja zostanie umieszczona w kolejce wywołującego wątku. Aby uzyskać więcej informacji na temat używania <xref:System.Threading.Tasks.Task> do wykonywania operacji asynchronicznych, zobacz [równoległość zadań (Biblioteka zadań równoległych)](../../../standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Rozszerzenia znaczników dla zdarzeń  
 WPF 4,5 obsługuje rozszerzenia znaczników dla zdarzeń.  Podczas gdy WPF nie definiuje rozszerzenia znaczników, które ma być używane dla zdarzeń, inne strony mogą tworzyć rozszerzenia znaczników, które mogą być używane z zdarzeniami.  
  
## <a name="see-also"></a>Zobacz także

- [Co nowego w programie .NET Framework](../../whats-new/index.md)
