---
title: 'Optymalizacja wydajności: zachowanie obiektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interface virtualization [WPF]
- dependency properties [WPF], performance
- event handlers [WPF]
- object performance considerations [WPF]
- Freezable objects [WPF], performance
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
ms.openlocfilehash: 64e567cd28e9458b483b0963e0dedd924ad23bab
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094491"
---
# <a name="optimizing-performance-object-behavior"></a>Optymalizacja wydajności: zachowanie obiektu
Zrozumienie, że wewnętrzne zachowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów pociąga za pomocne zajęcie odpowiednich kompromisów między funkcjonalnością i wydajnością.  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Nie można usunąć programów obsługi zdarzeń na obiektach, które mogą utrzymać aktywność obiektów  
 Delegat, który obiekt przekazuje do jego zdarzenia, efektywnie jest odwołaniem do tego obiektu. W związku z tym programy obsługi zdarzeń mogą utrzymać aktywność obiektów dłużej niż oczekiwano. Podczas czyszczenia obiektu, który został zarejestrowany w celu nasłuchiwania zdarzenia obiektu, należy usunąć tego delegata przed zwolnieniem obiektu. Utrzymywanie niepotrzebnych obiektów zwiększa użycie pamięci przez aplikację. Jest to szczególnie prawdziwe, gdy obiekt jest elementem głównym drzewa logicznego lub drzewa wizualnego.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wprowadza słaby wzorzec odbiornika zdarzeń dla zdarzeń, które mogą być przydatne w sytuacjach, w których relacje czasu istnienia obiektu między źródłem a odbiornikiem są trudne do śledzenia. Niektóre istniejące zdarzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używają tego wzorca. W przypadku implementowania obiektów ze zdarzeniami niestandardowymi ten wzorzec może być używany przez użytkownika. Aby uzyskać szczegółowe informacje, zobacz [słabe wzorce zdarzeń](weak-event-patterns.md).  
  
 Istnieje kilka narzędzi, takich jak Profiler CLR i przeglądarka zestawu roboczego, które mogą dostarczać informacje dotyczące użycia pamięci przez określony proces. Profiler CLR zawiera wiele przydatnych widoków profilu alokacji, w tym histogramu przydzielone typy, alokacje i wykresy wywołań, wiersz czasu przedstawiający wyrzucanie elementów bezużytecznych różnych generacji i stan wynikający z zarządzanego sterty po Kolekcje te i drzewo wywołań pokazujące alokacje poszczególnych metod i obciążenia zestawu. Aby uzyskać więcej informacji, zobacz [wydajność](https://docs.microsoft.com/previous-versions/aa497289(v=msdn.10)).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Właściwości zależności i obiekty  
 Ogólnie rzecz biorąc, uzyskanie dostępu do właściwości zależności <xref:System.Windows.DependencyObject> nie jest wolniejsze niż dostęp do właściwości CLR. W przypadku niewielkich obciążeń związanych z wydajnością ustawiania wartości właściwości, pobieranie wartości jest tak szybkie jak pobieranie wartości z właściwości CLR. Zmniejszenie kosztów związanych z małą wydajnością jest faktem, że właściwości zależności obsługują niezawodne funkcje, takie jak powiązanie danych, animacja, dziedziczenie i style. Aby uzyskać więcej informacji, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Optymalizacje DependencyProperty  
 Należy uważnie definiować właściwości zależności w aplikacji. Jeśli <xref:System.Windows.DependencyProperty> ma wpływ tylko na opcje metadanych typu renderowania, a nie inne opcje metadanych, takie jak <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, należy oznaczyć je jako takie poprzez zastępowanie metadanych. Aby uzyskać więcej informacji na temat przesłaniania lub uzyskiwania metadanych właściwości, zobacz [metadane właściwości zależności](dependency-property-metadata.md).  
  
 Może być bardziej wydajne, aby program obsługi zmian właściwości unieważnił miarę, rozmieszczać i renderować przebiegi ręcznie, jeśli nie wszystkie zmiany właściwości faktycznie wpływają na miary, Rozmieść i renderowane. Na przykład możesz zdecydować się na ponowne renderowanie tła tylko wtedy, gdy wartość jest większa niż ustalony limit. W takim przypadku program obsługi zmian właściwości tylko unieważnia Render, gdy wartość przekroczy ustawiony limit.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Dziedziczenie klasy DependencyProperty jest niewolne  
 Domyślnie zarejestrowane właściwości zależności nie są dziedziczenia. Można jednak jawnie wprowadzać każdą właściwość dziedziczenia. Chociaż jest to przydatna funkcja, konwertowanie właściwości na dziedziczenie wpływa na wydajność przez zwiększenie czasu ważności właściwości.  
  
### <a name="use-registerclasshandler-carefully"></a>Używaj RegisterClassHandler uważnie  
 Podczas wywoływania <xref:System.Windows.EventManager.RegisterClassHandler%2A> umożliwia zapisanie stanu wystąpienia, należy pamiętać, że program obsługi jest wywoływany dla każdego wystąpienia, co może spowodować problemy z wydajnością. <xref:System.Windows.EventManager.RegisterClassHandler%2A> należy używać tylko wtedy, gdy aplikacja wymaga zapisania stanu wystąpienia.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Ustaw wartość domyślną dla DependencyProperty podczas rejestracji  
 Podczas tworzenia <xref:System.Windows.DependencyProperty>, który wymaga wartości domyślnej, należy ustawić wartość przy użyciu domyślnych metadanych przekazaną jako parametr do metody <xref:System.Windows.DependencyProperty.Register%2A> <xref:System.Windows.DependencyProperty>. Użyj tej techniki zamiast ustawiania wartości właściwości w konstruktorze lub w każdym wystąpieniu elementu.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Ustaw wartość metodę PropertyMetadata przy użyciu rejestru  
 Podczas tworzenia <xref:System.Windows.DependencyProperty>można ustawić <xref:System.Windows.PropertyMetadata> przy użyciu metody <xref:System.Windows.DependencyProperty.Register%2A> lub <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Chociaż obiekt może mieć statyczny Konstruktor do wywoływania <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, to nie jest to optymalne rozwiązanie i będzie miało wpływ na wydajność. Aby uzyskać najlepszą wydajność, ustaw <xref:System.Windows.PropertyMetadata> podczas wywołania <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable — obiekty  
 <xref:System.Windows.Freezable> jest specjalnym typem obiektu, który ma dwa stany: Niezamrożone i zamrożone. Zamrażanie obiektów zawsze, gdy jest to możliwe, zwiększa wydajność aplikacji i zmniejsza jej zestaw roboczy. Aby uzyskać więcej informacji, zobacz [Freezable obiektów — Omówienie](freezable-objects-overview.md).  
  
 Każda <xref:System.Windows.Freezable> ma zdarzenie <xref:System.Windows.Freezable.Changed>, które jest zgłaszane przy każdej zmianie. Powiadomienia o zmianach są jednak kosztowne pod względem wydajności aplikacji.  
  
 Rozważmy następujący przykład, w którym każdy <xref:System.Windows.Shapes.Rectangle> używa tego samego obiektu <xref:System.Windows.Media.Brush>:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Freezable.Changed> obiektu <xref:System.Windows.Media.SolidColorBrush>, aby unieważnić Właściwość <xref:System.Windows.Shapes.Shape.Fill%2A> obiektu <xref:System.Windows.Shapes.Rectangle>. W takim przypadku, za każdym razem, gdy <xref:System.Windows.Media.SolidColorBrush> ma uruchamiać zdarzenie <xref:System.Windows.Freezable.Changed>, jest wymagane wywołanie funkcji wywołania zwrotnego dla każdego <xref:System.Windows.Shapes.Rectangle>u — kumulacja wywołań funkcji wywołania zwrotnego narzuca znaczący spadek wydajności. Ponadto bardzo intensywna wydajność pozwala dodawać i usuwać programy obsługi w tym momencie, ponieważ aplikacja musiałaby przechodzenie przez całą listę. Jeśli scenariusz aplikacji nigdy nie zmienia <xref:System.Windows.Media.SolidColorBrush>, nastąpi zwrócenie kosztu utrzymania <xref:System.Windows.Freezable.Changed> obsługi zdarzeń.  
  
 Zamrożenie <xref:System.Windows.Freezable> może zwiększyć jego wydajność, ponieważ nie jest już potrzebne do obsługi powiadomień o zmianach. W poniższej tabeli przedstawiono rozmiar prostej <xref:System.Windows.Media.SolidColorBrush>, gdy jej Właściwość <xref:System.Windows.Freezable.IsFrozen%2A> jest ustawiona na `true`, w porównaniu z, gdy nie jest. Przyjmuje się, że zastosowano jeden Pędzel do właściwości <xref:System.Windows.Shapes.Shape.Fill%2A> dziesięciu <xref:System.Windows.Shapes.Rectangle> obiektów.  
  
|**Stan**|**Rozmiar**|  
|---------------|--------------|  
|Zamrożone <xref:System.Windows.Media.SolidColorBrush>|212 bajtów|  
|Zamrożone <xref:System.Windows.Media.SolidColorBrush>|972 bajtów|  
  
 Poniższy przykład kodu demonstruje następujące koncepcje:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Zmiany obsługi dla niezamrożonych obiektów Freezable platformie mogą utrzymać aktywność obiektów  
 Delegat, który obiekt przekazuje do zdarzenia <xref:System.Windows.Freezable.Changed> <xref:System.Windows.Freezable> obiektu jest efektywnie odwołanie do tego obiektu. Z tego względu procedury obsługi zdarzeń <xref:System.Windows.Freezable.Changed> mogą utrzymać aktywność obiektów dłużej niż oczekiwano. Podczas czyszczenia obiektu, który został zarejestrowany w celu nasłuchiwania zdarzenia <xref:System.Windows.Freezable.Changed> <xref:System.Windows.Freezable> obiektu, należy usunąć tego delegata przed zwolnieniem obiektu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] również łączy zdarzenia <xref:System.Windows.Freezable.Changed> wewnętrznie. Na przykład wszystkie właściwości zależności, które przyjmują <xref:System.Windows.Freezable> jako wartość, automatycznie nasłuchują <xref:System.Windows.Freezable.Changed> zdarzeń. Właściwość <xref:System.Windows.Shapes.Shape.Fill%2A>, która pobiera <xref:System.Windows.Media.Brush>, ilustruje tę koncepcję.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Na przypisaniu `myBrush` do `myRectangle.Fill`, delegat wskazujący z powrotem do obiektu <xref:System.Windows.Shapes.Rectangle> zostanie dodany do zdarzenia <xref:System.Windows.Freezable.Changed> <xref:System.Windows.Media.SolidColorBrush> obiektu. Oznacza to, że następujący kod nie czyni w rzeczywistości `myRect` uprawniony do wyrzucania elementów bezużytecznych:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 W takim przypadku `myBrush` nadal zachowują `myRectangle` aktywność i będą wywoływać z powrotem do niej, gdy wyzwala <xref:System.Windows.Freezable.Changed> zdarzenie. Należy pamiętać, że przypisanie `myBrush` do właściwości <xref:System.Windows.Shapes.Shape.Fill%2A> nowej <xref:System.Windows.Shapes.Rectangle> spowoduje po prostu dodanie do `myBrush`innego programu obsługi zdarzeń.  
  
 Zalecanym sposobem oczyszczenia tych typów obiektów jest usunięcie <xref:System.Windows.Media.Brush> z właściwości <xref:System.Windows.Shapes.Shape.Fill%2A>, która spowoduje usunięcie programu obsługi zdarzeń <xref:System.Windows.Freezable.Changed>.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Wirtualizacja interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] również zawiera odmianę elementu <xref:System.Windows.Controls.StackPanel>, który automatycznie "umożliwia wirtualizację zawartości podrzędnej powiązanej z danymi. W tym kontekście wyraz "Wirtualizacja" odnosi się do techniki, za pomocą której podzbiór obiektów jest generowany na podstawie większej liczby elementów danych w zależności od tego, które elementy są widoczne na ekranie. Jest to czasochłonne, zarówno w zakresie pamięci, jak i procesora, aby generować dużą liczbę elementów interfejsu użytkownika, gdy tylko kilka może znajdować się na ekranie w danym momencie. <xref:System.Windows.Controls.VirtualizingStackPanel> (za pośrednictwem funkcji zapewnianych przez <xref:System.Windows.Controls.VirtualizingPanel>) oblicza widoczne elementy i współpracuje z <xref:System.Windows.Controls.ItemContainerGenerator> z <xref:System.Windows.Controls.ItemsControl> (na przykład <xref:System.Windows.Controls.ListBox> lub <xref:System.Windows.Controls.ListView>) tylko do tworzenia elementów dla widocznych elementów.  
  
 W miarę optymalizacji wydajności, obiekty wizualne dla tych elementów są generowane lub utrzymywane w stanie aktywności, jeśli są widoczne na ekranie. Obiekty wizualne mogą zostać usunięte, gdy nie znajdują się już w obszarze widocznym formantu. Nie ma to pomylić z wirtualizacją danych, w której obiekty danych nie są obecne w lokalnej kolekcji — a nie są przesyłane strumieniowo w razie potrzeby.  
  
 W poniższej tabeli przedstawiono czas dodawania i renderowania 5000 <xref:System.Windows.Controls.TextBlock> elementów do <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.VirtualizingStackPanel>. W tym scenariuszu pomiary przedstawiają czas między dołączeniem ciągu tekstowego do właściwości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> obiektu <xref:System.Windows.Controls.ItemsControl> do czasu, gdy elementy panelu wyświetlają ciąg tekstowy.  
  
|**Panel hosta**|**Czas renderowania (MS)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Zobacz też

- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Wykorzystanie możliwości sprzętu](optimizing-performance-taking-advantage-of-hardware.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Grafika 2D i obrazowanie](optimizing-performance-2d-graphics-and-imaging.md)
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Tekst](optimizing-performance-text.md)
- [Powiązanie danych](optimizing-performance-data-binding.md)
- [Inne zalecenia dotyczące wydajności](optimizing-performance-other-recommendations.md)
