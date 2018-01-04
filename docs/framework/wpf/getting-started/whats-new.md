---
title: "Jaki &#39; s Nowość w wersji WPF 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
caps.latest.revision: "55"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8de8725bc48f69cdd18100d90a1bc610caa7ecfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="what39s-new-in-wpf-version-45"></a>Jaki &#39; s Nowość w wersji WPF 4.5
<a name="introduction"></a>Ten temat zawiera informacje o nowych i ulepszonych funkcjach [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] wersji 4.5.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Formant wstążki](#ribbon_control)  
  
-   [Zwiększona wydajność podczas wyświetlania dużych zestawów danych grupowanych](#grouped_virtualization)  
  
-   [Nowe funkcje VirtualizingPanel](#VirtualizingPanel)  
  
-   [Powiązanie z właściwości statyczne](#static_properties)  
  
-   [Uzyskiwanie dostępu do kolekcji na wątków bez interfejsu użytkownika](#xthread_access)  
  
-   [Synchronicznego i asynchronicznego sprawdzanie poprawności danych](#INotifyDataErrorInfo)  
  
-   [Automatyczne aktualizowanie źródła powiązanie danych](#delay)  
  
-   [Powiązanie z typów tej ICustomTypeProvider wdrożenie](#ICustomTypeProvider)  
  
-   [Pobieranie informacje o powiązaniu danych z wyrażenia powiązania](#binding_state)  
  
-   [Sprawdzanie, czy prawidłowy obiekt DataContext](#DisconnectedSource)  
  
-   [Zmienianie położenia danych po zmianie wartości danych (kształtowania na żywo)](#live_shaping)  
  
-   [Ulepszona obsługa ustanawianie słabe odwołanie do zdarzenia](#weak_event_pattern)  
  
-   [Nowe metody dla klasy dyspozytora](#async)  
  
-   [Rozszerzenia znaczników dla zdarzenia](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Formant wstążki  
 WPF 4.5 jest dostarczany z <xref:System.Windows.Controls.Ribbon.Ribbon> formant, który obsługuje kart, aplikacji Menu i paska narzędzi Szybki dostęp.  Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Zwiększona wydajność podczas wyświetlania dużych zestawów danych grupowanych  
 Wirtualizacji interfejsu użytkownika występuje, gdy podzestaw interfejsu użytkownika (UI) elementy zostaną wygenerowane na podstawie większą liczbę elementów danych oparte na elementy, które są widoczne na ekranie. <xref:System.Windows.Controls.VirtualizingPanel> Definiuje <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> dołączona właściwość, która umożliwia wirtualizacji interfejsu użytkownika dla zgrupowanych danych.  Aby uzyskać więcej informacji na temat grupowania danych, zobacz porady: sortowanie i grupy danych przy użyciu widoku w języku XAML.  Aby uzyskać więcej informacji na temat wirtualizacji pogrupowanych danych, zobacz <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> dołączona właściwość.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>Nowe funkcje VirtualizingPanel  
  
1.  Można określić czy <xref:System.Windows.Controls.VirtualizingPanel>, takich jak <xref:System.Windows.Controls.VirtualizingStackPanel>, wyświetla elementy częściowe za pomocą <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> dołączona właściwość. Jeśli <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> ustawiono <xref:System.Windows.Controls.ScrollUnit.Item>, <xref:System.Windows.Controls.VirtualizingPanel> będą wyświetlane tylko elementy, które są całkowicie widoczne. Jeśli <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> ustawiono <xref:System.Windows.Controls.ScrollUnit.Pixel>, <xref:System.Windows.Controls.VirtualizingPanel> można wyświetlić częściowo widocznych elementów.  
  
2.  Można określić rozmiar pamięci podręcznej przed i po okienka ekranu po <xref:System.Windows.Controls.VirtualizingPanel> jest wirtualizacji za pomocą <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> dołączona właściwość.  Pamięć podręczna jest ilość miejsca powyżej lub poniżej okienka ekranu, w którym nie są zwirtualizowane elementy.  Aby uniknąć generowania elementy interfejsu użytkownika, ponieważ są one przewijane w widoku przy użyciu pamięci podręcznej może poprawić wydajność. Pamięci podręcznej jest wypełniana z niższym priorytetem, dzięki czemu aplikacja nie przestała odpowiadać podczas operacji. <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> Właściwość określa jednostki miary, która jest używana przez <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Powiązanie z właściwości statyczne  
 Właściwości statyczne można użyć jako źródła danych powiązania. Aparat wiązania danych rozpoznaje, gdy wartość właściwości Jeśli statyczne zdarzenia.  Na przykład jeśli klasa `SomeClass` definiuje właściwości statycznej o nazwie `MyProperty`, `SomeClass` można zdefiniować statyczne zdarzenie, które jest wywoływane, gdy wartość `MyProperty` zmiany.  Zdarzenia statyczne można użyć jednej z następujących podpisów.  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Uwaga w pierwszym przypadku klasa przedstawia zdarzenia statycznej o nazwie *PropertyName* `Changed` , który przekazuje <xref:System.EventArgs> do obsługi zdarzeń.  W drugim przypadku klasa przedstawia zdarzenia statycznej o nazwie `StaticPropertyChanged` , który przekazuje <xref:System.ComponentModel.PropertyChangedEventArgs> do obsługi zdarzeń. Klasa, która implementuje statycznej właściwości można podnieść powiadomień zmiany właściwości przy użyciu jednej z metod.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Uzyskiwanie dostępu do kolekcji na wątków bez interfejsu użytkownika  
 WPF umożliwia zbierania danych w wątkach innego niż utworzony kolekcji modyfikacji i dostępu.  Pozwala na użycie wątku w tle, aby odbierać dane ze źródła zewnętrznego, takie jak bazy danych i wyświetlić dane w wątku interfejsu użytkownika.  Za pomocą inny wątek, aby zmodyfikować kolekcję, do interakcji z użytkownikiem reaguje interfejsu użytkownika.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Synchronicznego i asynchronicznego sprawdzanie poprawności danych  
 <xref:System.ComponentModel.INotifyDataErrorInfo> Interfejs umożliwia klas jednostek danych do wdrożenia niestandardowych reguł walidacji i ujawnia asynchronicznie wyniki sprawdzania poprawności. Ten interfejs obsługuje również błędów niestandardowych obiektów, wiele błędów według właściwości, właściwość między błędy i błędy na poziomie jednostki.  Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Automatyczne aktualizowanie źródła powiązanie danych  
 Jeśli używasz wiązanie danych do aktualizowania źródła danych, możesz użyć <xref:System.Windows.Data.BindingBase.Delay%2A> właściwość, aby określić ilość czasu, aby przekazać po zmianie właściwości w elemencie docelowym przed aktualizacji źródła.  Na przykład, załóżmy, że masz <xref:System.Windows.Controls.Slider> mający jego <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> dwukierunkowe danych właściwości powiązany z właściwości obiektu danych i <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwość jest ustawiona na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  W tym przykładzie, gdy użytkownik przesuwa <xref:System.Windows.Controls.Slider>, aktualizacje źródła dla każdego piksela który <xref:System.Windows.Controls.Slider> przenosi.  Obiekt źródłowy potrzebuje zazwyczaj wartość suwaka tylko wtedy, gdy suwak <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> zatrzymuje zmiana.  Aby zapobiec zbyt często aktualizowanie źródła, użyj <xref:System.Windows.Data.BindingBase.Delay%2A> do określenia, czy źródło nie powinny być aktualizowane, dopóki nie upłynie określoną ilość czasu po stronie przycisku suwaka zatrzymuje przenoszenia.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Powiązanie z typów tej ICustomTypeProvider wdrożenie  
 WPF obsługuje powiązanie danych do obiektów, które implementują <xref:System.Reflection.ICustomTypeProvider>, znanej również jako typów niestandardowych.  Niestandardowych typów można używać w następujących przypadkach.  
  
1.  Jako <xref:System.Windows.PropertyPath> w powiązaniu danych. Na przykład <xref:System.Windows.Data.Binding.Path%2A> właściwość <xref:System.Windows.Data.Binding> może odwoływać się właściwość typu niestandardowego.  
  
2.  Jako wartość <xref:System.Windows.DataTemplate.DataType%2A> właściwości.  
  
3.  Typem, który określa automatycznie generowanych kolumn w <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Pobieranie informacje o powiązaniu danych z wyrażenia powiązania  
 W niektórych przypadkach może uzyskać <xref:System.Windows.Data.BindingExpression> z <xref:System.Windows.Data.Binding> i potrzebują informacji dotyczących obiektu źródłowego i docelowego powiązania.  Umożliwiają uzyskanie źródłowy lub docelowy obiekt lub właściwości skojarzonej, ponieważ zostały dodane nowe interfejsy API.  Jeśli masz <xref:System.Windows.Data.BindingExpression>, użyj następujących interfejsów API, aby uzyskać informacje o źródłowe i docelowe.  
  
|Aby znaleźć tę wartość powiązania|Użyj tego interfejsu API|  
|---------------------------------------|------------------|  
|Obiekt docelowy|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Właściwość target|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Obiekt źródłowy|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Właściwość źródła|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Czy <xref:System.Windows.Data.BindingExpression> należy do<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Właściciel<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>Sprawdzanie, czy prawidłowy obiekt DataContext  
 Istnieją przypadki, gdzie <xref:System.Windows.FrameworkElement.DataContext%2A> elementu kontenera w <xref:System.Windows.Controls.ItemsControl> zostanie rozłączony.  Kontener elementu jest element interfejsu użytkownika, który zawiera element <xref:System.Windows.Controls.ItemsControl>.  Gdy <xref:System.Windows.Controls.ItemsControl> dane powiązane z kolekcją, kontener elementu jest generowany dla każdego elementu. W niektórych przypadkach kontenery elementu są usuwane z drzewa wizualnego. Są typowe przypadków, gdy kontener element zostanie usunięty po usunięciu elementu z kolekcji źródłowej i gdy jest włączona wirtualizacja na <xref:System.Windows.Controls.ItemsControl>. W takich przypadkach <xref:System.Windows.FrameworkElement.DataContext%2A> obiektu kontenera elementu zostanie ustawiona do obiektu wskaźnikowych, który jest zwracany przez <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> właściwości statycznej.  Należy sprawdzić, czy <xref:System.Windows.FrameworkElement.DataContext%2A> jest równa <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> obiektu przed uzyskaniem dostępu do <xref:System.Windows.FrameworkElement.DataContext%2A> kontenera elementu.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Zmienianie położenia danych po zmianie wartości danych (kształtowania na żywo)  
 Zbierania danych można grupowane, sortowane lub filtrowane. WPF 4.5 umożliwia danych można przestawiać modyfikacji danych. Na przykład załóżmy, że aplikacja używa <xref:System.Windows.Controls.DataGrid> do listy zasobów w rynku zapasów i zasobów są sortowane według wartości zapasów. Jeśli sortowanie na żywo jest włączona na temat zasobów <xref:System.Windows.Data.CollectionView>, stock pozycja w <xref:System.Windows.Controls.DataGrid> przenosi, gdy wartość zasobów staje się większa lub mniejsza niż innym magazynie wartości.   Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.ICollectionViewLiveShaping> interfejsu.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Ulepszona obsługa ustanawianie słabe odwołanie do zdarzenia  
 Implementacja wzorca słabe zdarzeń jest teraz łatwiejsze, ponieważ subskrybentów zdarzeń mogą uczestniczyć w nim bez stosowania dodatkowy interfejs.  Ogólnego <xref:System.Windows.WeakEventManager> klasa umożliwia również subskrybentów udziału we wzorcu słabe zdarzeń, jeśli jest to dedykowana <xref:System.Windows.WeakEventManager> nie istnieje dla określone zdarzenie.  Aby uzyskać więcej informacji, zobacz [słabe wzorce zdarzeń](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Nowe metody dla klasy dyspozytora  
 Klasa dyspozytora definiuje nowych metod operacje synchroniczne i asynchroniczne.  Synchroniczne <xref:System.Windows.Threading.Dispatcher.Invoke%2A> metoda definiuje przeciążeń, które przyjmują <xref:System.Action> lub <xref:System.Func%601> parametru. Nowych metod asynchronicznych <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, ma także <xref:System.Action> lub <xref:System.Func%601> jako parametru wywołania zwrotnego i zwraca <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>.   <xref:System.Windows.Threading.DispatcherOperation> i <xref:System.Windows.Threading.DispatcherOperation%601> klasy definiują <xref:System.Threading.Tasks.Task> właściwości.  Podczas wywoływania <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, można użyć `await` — słowo kluczowe przy użyciu jednej <xref:System.Windows.Threading.DispatcherOperation> lub skojarzony <xref:System.Threading.Tasks.Task>. Jeśli musisz poczekać synchronicznie <xref:System.Threading.Tasks.Task> zwróconego przez <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>, wywołaj <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> — metoda rozszerzenia. Wywoływanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> spowoduje zakleszczenie, jeśli operacja jest w kolejce w wątku wywołującym. Aby uzyskać więcej informacji o korzystaniu z <xref:System.Threading.Tasks.Task> do wykonywania asynchronicznych operacji, zobacz [równoległość zadań (Biblioteka zadań równoległych)](../../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Rozszerzenia znaczników dla zdarzenia  
 WPF 4.5 obsługuje rozszerzenia znaczników dla zdarzeń.  WPF nie definiuje rozszerzenie znacznika do użycia dla zdarzeń, można utworzyć rozszerzenia znaczników, który może służyć do zdarzeń są stron trzecich.  
  
## <a name="see-also"></a>Zobacz też  
 [Co nowego w programie .NET Framework](../../../../docs/framework/whats-new/index.md)
