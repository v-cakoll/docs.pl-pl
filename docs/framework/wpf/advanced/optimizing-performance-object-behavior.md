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
ms.openlocfilehash: 67184db7fc1459e83ac7b1e6ff09ef56e43f0ca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187075"
---
# <a name="optimizing-performance-object-behavior"></a>Optymalizacja wydajności: zachowanie obiektu
Zrozumienie wewnętrznego zachowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów pomoże Ci dokonać odpowiednich kompromisów między funkcjonalnością a wydajnością.  

<a name="Not_Removing_Event_Handlers"></a>
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Nieusuwanie programów obsługi zdarzeń w obiektach może utrzymać obiekty przy życiu  
 Pełnomocnik, który obiekt przekazuje do jego zdarzenia jest skutecznie odwołanie do tego obiektu. W związku z tym programy obsługi zdarzeń może utrzymać obiekty przy życiu dłużej niż oczekiwano. Podczas wykonywania oczyszczania obiektu, który został zarejestrowany do nasłuchiwania zdarzenia obiektu, istotne jest usunięcie tego delegata przed zwolnieniem obiektu. Utrzymywanie niepotrzebnych obiektów przy życiu zwiększa użycie pamięci aplikacji. Jest to szczególnie ważne, gdy obiekt jest katalogiem głównym drzewa logicznego lub drzewa wizualnego.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wprowadza wzorzec odbiornika słabych zdarzeń dla zdarzeń, które mogą być przydatne w sytuacjach, gdy relacje okresu istnienia obiektu między źródłem a odbiornikiem są trudne do śledzenia. Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] istniejące zdarzenia używają tego wzorca. Jeśli implementujesz obiekty ze zdarzeniami niestandardowymi, ten wzorzec może być dla Ciebie używany. Aby uzyskać szczegółowe informacje, zobacz [Słabe wzorce zdarzeń](weak-event-patterns.md).  
  
 Istnieje kilka narzędzi, takich jak profiler CLR i przeglądarka zestawów roboczych, które mogą dostarczać informacji na temat użycia pamięci określonego procesu. Program CLR Profiler zawiera szereg bardzo przydatnych widoków profilu alokacji, w tym histogram przydzielonych typów, wykresy alokacji i wywołań, wiersz czasu przedstawiający wyrzucanie elementów bezużytecznych z różnych pokoleń i wynikowy stan zarządzanego stosu po tych kolekcji i drzewa wywołań pokazujący alokacje dla metod i obciążenia zestawu. Aby uzyskać więcej informacji, zobacz [Wydajność](https://docs.microsoft.com/previous-versions/aa497289(v=msdn.10)).  
  
<a name="DPs_and_Objects"></a>
## <a name="dependency-properties-and-objects"></a>Właściwości zależności i obiekty  
 Ogólnie rzecz biorąc dostęp do właściwości <xref:System.Windows.DependencyObject> zależności a nie jest wolniejszy niż uzyskiwanie dostępu do właściwości CLR. Chociaż istnieje małe obciążenie wydajności dla ustawiania wartości właściwości, uzyskanie wartości jest tak szybko, jak uzyskanie wartości z właściwości CLR. Kompensowanie małych narzutów wydajności jest fakt, że właściwości zależności obsługują niezawodne funkcje, takie jak powiązanie danych, animacja, dziedziczenie i stylizacji. Aby uzyskać więcej informacji, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Optymalizacje właściwości zależności  
 Właściwości zależności w aplikacji należy bardzo dokładnie zdefiniować. Jeśli <xref:System.Windows.DependencyProperty> wpływa tylko na opcje metadanych typu renderowania, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>a nie inne opcje metadanych, takie jak , należy oznaczyć jako takie, zastępując jego metadane. Aby uzyskać więcej informacji na temat zastępowania lub uzyskiwania metadanych właściwości, zobacz [Metadane właściwości zależności](dependency-property-metadata.md).  
  
 Może być bardziej wydajne, aby program obsługi zmiany właściwości unieważnić miarę, rozmieścić i renderować przechodzi ręcznie, jeśli nie wszystkie zmiany właściwości rzeczywiście wpływają na miarę, rozmieszczenia i renderowania. Na przykład można zdecydować się na ponowne renderowanie tła tylko wtedy, gdy wartość jest większa niż ustawiony limit. W takim przypadku program obsługi zmiany właściwości będzie unieważniać renderowanie tylko wtedy, gdy wartość przekracza ustawiony limit.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Dokonywanie DependencyProperty inheritable nie jest wolny  
 Domyślnie zarejestrowane właściwości zależności są nie dziedziczne. Jednak można jawnie dokonać dowolnej właściwości dziedziczne. Chociaż jest to przydatna funkcja, konwersja właściwości do dziedzicznego wpływu wydajności przez zwiększenie czasu unieważnienia właściwości.  
  
### <a name="use-registerclasshandler-carefully"></a>Używaj funkcji RegisterClassHandler  
 Podczas <xref:System.Windows.EventManager.RegisterClassHandler%2A> wywoływania umożliwia zapisanie stanu wystąpienia, ważne jest, aby pamiętać, że program obsługi jest wywoływany w każdym wystąpieniu, co może powodować problemy z wydajnością. Użyj <xref:System.Windows.EventManager.RegisterClassHandler%2A> tylko wtedy, gdy aplikacja wymaga zapisania stanu wystąpienia.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Ustawianie wartości domyślnej właściwości zależności podczas rejestracji  
 Podczas tworzenia <xref:System.Windows.DependencyProperty> wartości domyślnej należy ustawić wartość przy użyciu domyślnych metadanych przekazanych jako parametr do <xref:System.Windows.DependencyProperty.Register%2A> metody <xref:System.Windows.DependencyProperty>programu . Użyj tej techniki, a nie ustawienie wartości właściwości w konstruktorze lub na każdym wystąpieniu elementu.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Ustawianie wartości PropertyMetadata przy użyciu funkcji Register  
 Podczas tworzenia <xref:System.Windows.DependencyProperty>programu , masz możliwość <xref:System.Windows.PropertyMetadata> ustawienia przy <xref:System.Windows.DependencyProperty.Register%2A> użyciu <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> albo metody. Chociaż obiekt może mieć konstruktora <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>statycznego do wywołania, nie jest to optymalne rozwiązanie i wpłynie na wydajność. Aby uzyskać najlepszą <xref:System.Windows.PropertyMetadata> wydajność, <xref:System.Windows.DependencyProperty.Register%2A>ustaw podczas połączenia na .  
  
<a name="Freezable_Objects"></a>
## <a name="freezable-objects"></a>Freezable obiektów  
 A <xref:System.Windows.Freezable> jest specjalnym typem obiektu, który ma dwa stany: niezamrożone i zamrożone. Zamrażanie obiektów, gdy jest to możliwe, zwiększa wydajność aplikacji i zmniejsza jej zestaw roboczy. Aby uzyskać więcej informacji, zobacz [Omówienie obiektów freezable](freezable-objects-overview.md).  
  
 Każdy <xref:System.Windows.Freezable> ma <xref:System.Windows.Freezable.Changed> zdarzenie, które jest wywoływane, gdy się zmieni. Jednak powiadomienia o zmianach są kosztowne pod względem wydajności aplikacji.  
  
 Rozważmy następujący przykład, <xref:System.Windows.Shapes.Rectangle> w którym <xref:System.Windows.Media.Brush> każdy używa tego samego obiektu:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia program obsługi <xref:System.Windows.Media.SolidColorBrush> zdarzeń dla <xref:System.Windows.Freezable.Changed> zdarzenia obiektu w <xref:System.Windows.Shapes.Rectangle> celu unieważnienia <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości obiektu. W takim przypadku za <xref:System.Windows.Media.SolidColorBrush> każdym razem, gdy ma do ognia jego <xref:System.Windows.Freezable.Changed> zdarzenia <xref:System.Windows.Shapes.Rectangle>jest wymagane do wywołania funkcji wywołania zwrotnego dla każdego — akumulacja tych wywołań funkcji wywołania wywołania zwrotnego nakłada znaczną karę wydajności. Ponadto jest bardzo dużej wydajności, aby dodać i usunąć programy obsługi w tym momencie, ponieważ aplikacja musiałaby przechodzić przez całą listę, aby to zrobić. Jeśli scenariusz aplikacji nigdy <xref:System.Windows.Media.SolidColorBrush>nie zmienia , będzie płacić <xref:System.Windows.Freezable.Changed> koszt utrzymania obsługi zdarzeń niepotrzebnie.  
  
 Zamrożenie <xref:System.Windows.Freezable> może poprawić jego wydajność, ponieważ nie musi już wydawać zasobów na utrzymanie powiadomień o zmianach. Poniższa tabela przedstawia rozmiar <xref:System.Windows.Media.SolidColorBrush> prostego, gdy jego <xref:System.Windows.Freezable.IsFrozen%2A> właściwość jest ustawiona na `true`, w porównaniu do, gdy nie jest. Zakłada się stosowanie jednego pędzla <xref:System.Windows.Shapes.Shape.Fill%2A> do <xref:System.Windows.Shapes.Rectangle> właściwości dziesięciu obiektów.  
  
|**Stan**|**Rozmiar**|  
|---------------|--------------|  
|Mrożone<xref:System.Windows.Media.SolidColorBrush>|212 bajtów|  
|Niemrozione<xref:System.Windows.Media.SolidColorBrush>|972 bajty|  
  
 Poniższy przykład kodu demonstruje tę koncepcję:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Zmieniono programy obsługi na Unfrozen Freezables może utrzymać obiekty przy życiu  
 Pełnomocnik, który obiekt przekazuje <xref:System.Windows.Freezable> do <xref:System.Windows.Freezable.Changed> zdarzenia obiektu jest skutecznie odwołanie do tego obiektu. W związku <xref:System.Windows.Freezable.Changed> z tym programy obsługi zdarzeń może utrzymać obiekty przy życiu dłużej niż oczekiwano. Podczas wykonywania oczyszczania obiektu, który został <xref:System.Windows.Freezable> zarejestrowany do <xref:System.Windows.Freezable.Changed> nasłuchiwania zdarzenia obiektu, istotne jest usunięcie tego delegata przed zwolnieniem obiektu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]również łączy <xref:System.Windows.Freezable.Changed> się z wydarzeniami wewnętrznie. Na przykład wszystkie właściwości zależności, <xref:System.Windows.Freezable> które przyjmują <xref:System.Windows.Freezable.Changed> jako wartość będzie nasłuchiwać zdarzeń automatycznie. Właściwość, <xref:System.Windows.Shapes.Shape.Fill%2A> która <xref:System.Windows.Media.Brush>przyjmuje , ilustruje tę koncepcję.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Przy przypisywaniu `myBrush` `myRectangle.Fill`do , delegat wskazujący <xref:System.Windows.Shapes.Rectangle> z powrotem <xref:System.Windows.Media.SolidColorBrush> do obiektu <xref:System.Windows.Freezable.Changed> zostaną dodane do zdarzenia obiektu. Oznacza to, że poniższy `myRect` kod faktycznie nie kwalifikuje się do wyrzucania elementów bezużytecznych:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 W tym `myBrush` przypadku `myRectangle` jest nadal przy życiu i będzie <xref:System.Windows.Freezable.Changed> oddzwonić do niego, gdy uruchamia jego zdarzenia. Należy zauważyć, `myBrush` że <xref:System.Windows.Shapes.Shape.Fill%2A> przypisanie <xref:System.Windows.Shapes.Rectangle> do właściwości nowego po `myBrush`prostu dodać inny program obsługi zdarzeń do .  
  
 Zalecanym sposobem oczyszczenia tych typów obiektów <xref:System.Windows.Media.Brush> jest <xref:System.Windows.Shapes.Shape.Fill%2A> usunięcie z właściwości, co <xref:System.Windows.Freezable.Changed> z kolei spowoduje usunięcie programu obsługi zdarzeń.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>
## <a name="user-interface-virtualization"></a>Wirtualizacja interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]również udostępnia odmianę <xref:System.Windows.Controls.StackPanel> elementu, który automatycznie "wirtualizuje" zawartość podrzędną związaną z danymi. W tym kontekście słowo wirtualizacja odnosi się do techniki, za pomocą której podzbiór obiektów jest generowany z większej liczby elementów danych, na podstawie których elementy są widoczne na ekranie. Jest intensywny, zarówno pod względem pamięci i procesora, aby wygenerować dużą liczbę elementów interfejsu użytkownika, gdy tylko kilka może być na ekranie w danym czasie. <xref:System.Windows.Controls.VirtualizingStackPanel>(za pomocą funkcji <xref:System.Windows.Controls.VirtualizingPanel>dostarczonych przez ) oblicza <xref:System.Windows.Controls.ItemContainerGenerator> widoczne <xref:System.Windows.Controls.ItemsControl> elementy <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ListView>współpracuje z z (takich jak lub ) do tworzenia tylko elementów dla widocznych elementów.  
  
 Jako optymalizacja wydajności obiekty wizualne dla tych elementów są generowane lub utrzymywane przy życiu tylko wtedy, gdy są widoczne na ekranie. Gdy nie znajdują się już w widocznym obszarze formantu, obiekty wizualne mogą zostać usunięte. Nie należy tego mylić z wirtualizacji danych, gdzie obiekty danych nie są obecne w kolekcji lokalnej, a przesyłane strumieniowo w razie potrzeby.  
  
 W poniższej tabeli przedstawiono czas, który upłynął, <xref:System.Windows.Controls.TextBlock> dodając <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.VirtualizingStackPanel>renderując 5000 elementów do a i a . W tym scenariuszu pomiary reprezentują czas między dołączaniem <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ciągu <xref:System.Windows.Controls.ItemsControl> tekstowego do właściwości obiektu do czasu, gdy elementy panelu wyświetlają ciąg tekstowy.  
  
|**Panel Hosta**|**Czas renderowania (ms)**|  
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
