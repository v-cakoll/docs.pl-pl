---
title: 'Optymalizacja wydajności: Zachowanie obiektu'
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
ms.openlocfilehash: 025c8691eb1aaf9483a222530a5590670ede486b
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400470"
---
# <a name="optimizing-performance-object-behavior"></a>Optymalizacja wydajności: Zachowanie obiektu
Zrozumienie wewnętrznych zachowań [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów pomoże zapewnić odpowiednie kompromisy między funkcjonalnością i wydajnością.  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Nie można usunąć programów obsługi zdarzeń na obiektach, które mogą utrzymać aktywność obiektów  
 Delegat, który obiekt przekazuje do jego zdarzenia, efektywnie jest odwołaniem do tego obiektu. W związku z tym programy obsługi zdarzeń mogą utrzymać aktywność obiektów dłużej niż oczekiwano. Podczas czyszczenia obiektu, który został zarejestrowany w celu nasłuchiwania zdarzenia obiektu, należy usunąć tego delegata przed zwolnieniem obiektu. Utrzymywanie niepotrzebnych obiektów zwiększa użycie pamięci przez aplikację. Jest to szczególnie prawdziwe, gdy obiekt jest elementem głównym drzewa logicznego lub drzewa wizualnego.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wprowadza słaby wzorzec odbiornika zdarzeń dla zdarzeń, które mogą być przydatne w sytuacjach, w których relacje czasu istnienia obiektu między źródłem a odbiornikiem są trudne do śledzenia. Niektóre istniejące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia używają tego wzorca. W przypadku implementowania obiektów ze zdarzeniami niestandardowymi ten wzorzec może być używany przez użytkownika. Aby uzyskać szczegółowe informacje, zobacz [słabe wzorce zdarzeń](weak-event-patterns.md).  
  
 Istnieje kilka narzędzi, takich jak Profiler CLR i przeglądarka zestawu roboczego, które mogą dostarczać informacje dotyczące użycia pamięci przez określony proces. Profiler CLR zawiera wiele przydatnych widoków profilu alokacji, w tym histogramu przydzielone typy, alokacje i wykresy wywołań, wiersz czasu przedstawiający wyrzucanie elementów bezużytecznych różnych generacji i stan wynikający z zarządzanego sterty po Kolekcje te i drzewo wywołań pokazujące alokacje poszczególnych metod i obciążenia zestawu. Aby uzyskać więcej informacji, zobacz [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Właściwości zależności i obiekty  
 Ogólnie rzecz biorąc, uzyskanie dostępu do właściwości zależności <xref:System.Windows.DependencyObject> elementu nie jest wolniejsze niż dostęp do właściwości CLR. W przypadku niewielkich obciążeń związanych z wydajnością ustawiania wartości właściwości, pobieranie wartości jest tak szybkie jak pobieranie wartości z właściwości CLR. Zmniejszenie kosztów związanych z małą wydajnością jest faktem, że właściwości zależności obsługują niezawodne funkcje, takie jak powiązanie danych, animacja, dziedziczenie i style. Aby uzyskać więcej informacji, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Optymalizacje DependencyProperty  
 Należy uważnie definiować właściwości zależności w aplikacji. Jeśli ma to wpływ tylko na opcje metadanych typu renderowania, a nie inne opcje metadanych <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, takie jak, należy oznaczyć ją jako taką, zastępując jej metadane. <xref:System.Windows.DependencyProperty> Aby uzyskać więcej informacji na temat przesłaniania lub uzyskiwania metadanych właściwości, zobacz [metadane właściwości zależności](dependency-property-metadata.md).  
  
 Może być bardziej wydajne, aby program obsługi zmian właściwości unieważnił miarę, rozmieszczać i renderować przebiegi ręcznie, jeśli nie wszystkie zmiany właściwości faktycznie wpływają na miary, Rozmieść i renderowane. Na przykład możesz zdecydować się na ponowne renderowanie tła tylko wtedy, gdy wartość jest większa niż ustalony limit. W takim przypadku program obsługi zmian właściwości tylko unieważnia Render, gdy wartość przekroczy ustawiony limit.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Dziedziczenie klasy DependencyProperty jest niewolne  
 Domyślnie zarejestrowane właściwości zależności nie są dziedziczenia. Można jednak jawnie wprowadzać każdą właściwość dziedziczenia. Chociaż jest to przydatna funkcja, konwertowanie właściwości na dziedziczenie wpływa na wydajność przez zwiększenie czasu ważności właściwości.  
  
### <a name="use-registerclasshandler-carefully"></a>Używaj RegisterClassHandler uważnie  
 Podczas gdy <xref:System.Windows.EventManager.RegisterClassHandler%2A> wywoływanie umożliwia zapisanie stanu wystąpienia, należy pamiętać, że program obsługi jest wywoływany dla każdego wystąpienia, co może spowodować problemy z wydajnością. Należy używać <xref:System.Windows.EventManager.RegisterClassHandler%2A> tylko wtedy, gdy aplikacja wymaga zapisania stanu wystąpienia.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Ustaw wartość domyślną dla DependencyProperty podczas rejestracji  
 Podczas tworzenia <xref:System.Windows.DependencyProperty> , który wymaga wartości domyślnej, należy ustawić wartość przy użyciu domyślnych metadanych przekazaną jako parametr <xref:System.Windows.DependencyProperty.Register%2A> do metody <xref:System.Windows.DependencyProperty>. Użyj tej techniki zamiast ustawiania wartości właściwości w konstruktorze lub w każdym wystąpieniu elementu.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Ustaw wartość metodę PropertyMetadata przy użyciu rejestru  
 Podczas tworzenia programu <xref:System.Windows.DependencyProperty>dostępna jest opcja <xref:System.Windows.PropertyMetadata> ustawiania przy użyciu <xref:System.Windows.DependencyProperty.Register%2A> albo <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metod. Chociaż obiekt może mieć statyczny Konstruktor do wywołania <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, nie jest to optymalne rozwiązanie i będzie miało wpływ na wydajność. Aby uzyskać najlepszą wydajność, należy <xref:System.Windows.PropertyMetadata> ustawić podczas <xref:System.Windows.DependencyProperty.Register%2A>wywołania.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable — obiekty  
 A <xref:System.Windows.Freezable> jest specjalnym typem obiektu, który ma dwa stany: Niezamrożone i zamrożone. Zamrażanie obiektów zawsze, gdy jest to możliwe, zwiększa wydajność aplikacji i zmniejsza jej zestaw roboczy. Aby uzyskać więcej informacji, zobacz [Freezable obiektów — Omówienie](freezable-objects-overview.md).  
  
 Każdy <xref:System.Windows.Freezable> z<xref:System.Windows.Freezable.Changed> nich ma zdarzenie, które jest zgłaszane przy każdej zmianie. Powiadomienia o zmianach są jednak kosztowne pod względem wydajności aplikacji.  
  
 Rozważmy następujący przykład, w którym <xref:System.Windows.Shapes.Rectangle> każdy używa tego <xref:System.Windows.Media.Brush> samego obiektu:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] program zapewnia obsługę zdarzeń dla <xref:System.Windows.Freezable.Changed> zdarzenia obiektu, <xref:System.Windows.Media.SolidColorBrush> aby unieważnić <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość obiektu. W takim przypadku, za każdym razem <xref:System.Windows.Media.SolidColorBrush> , gdy musi <xref:System.Windows.Freezable.Changed> uruchomić zdarzenie wywołania zwrotnego dla każdego <xref:System.Windows.Shapes.Rectangle>z nich — kumulacja wywołań funkcji wywołania zwrotnego narzuca znaczący spadek wydajności. Ponadto bardzo intensywna wydajność pozwala dodawać i usuwać programy obsługi w tym momencie, ponieważ aplikacja musiałaby przechodzenie przez całą listę. Jeśli scenariusz aplikacji nigdy nie ulegnie zmianie <xref:System.Windows.Media.SolidColorBrush>, nastąpi zwrócenie kosztów <xref:System.Windows.Freezable.Changed> obsługi zdarzeń.  
  
 Zamrażanie <xref:System.Windows.Freezable> a może poprawić wydajność, ponieważ nie jest już potrzebne do obsługi powiadomień o zmianach. W poniższej tabeli przedstawiono rozmiar prosty <xref:System.Windows.Media.SolidColorBrush> , gdy jego <xref:System.Windows.Freezable.IsFrozen%2A> właściwość jest ustawiona na `true`, w porównaniu do, gdy nie jest. Przyjmuje się, <xref:System.Windows.Shapes.Shape.Fill%2A> że zastosowano jeden Pędzel do właściwości <xref:System.Windows.Shapes.Rectangle> dziesięciu obiektów.  
  
|**State**|**Zmienia**|  
|---------------|--------------|  
|Zamrożone<xref:System.Windows.Media.SolidColorBrush>|212 bajtów|  
|Zamrożone<xref:System.Windows.Media.SolidColorBrush>|972 bajtów|  
  
 Poniższy przykład kodu demonstruje następujące koncepcje:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Zmiany obsługi dla niezamrożonych obiektów Freezable platformie mogą utrzymać aktywność obiektów  
 Delegat, który obiekt przekazuje do <xref:System.Windows.Freezable> <xref:System.Windows.Freezable.Changed> zdarzenia obiektu, jest efektywnie odwołaniem do tego obiektu. W związku <xref:System.Windows.Freezable.Changed> z tym programy obsługi zdarzeń mogą utrzymać aktywność obiektów dłużej niż oczekiwano. Podczas czyszczenia obiektu, który został zarejestrowany w celu nasłuchiwania <xref:System.Windows.Freezable> <xref:System.Windows.Freezable.Changed> zdarzenia obiektu, należy usunąć tego delegata przed zwolnieniem obiektu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]również łączy <xref:System.Windows.Freezable.Changed> zdarzenia wewnętrznie. Na przykład wszystkie właściwości zależności, które przyjmują <xref:System.Windows.Freezable> jako wartość, będą <xref:System.Windows.Freezable.Changed> nasłuchiwać zdarzeń automatycznie. Właściwość, która <xref:System.Windows.Media.Brush>przyjmuje, ilustruje tę koncepcję. <xref:System.Windows.Shapes.Shape.Fill%2A>  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 `myBrush` W przypisaniu <xref:System.Windows.Freezable.Changed> do `myRectangle.Fill`, <xref:System.Windows.Shapes.Rectangle> delegat wskazujący z powrotem do obiektu zostanie dodany do <xref:System.Windows.Media.SolidColorBrush> zdarzenia obiektu. Oznacza to, że następujący kod nie `myRect` kwalifikuje się w rzeczywistości do wyrzucania elementów bezużytecznych:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 W takim przypadku `myBrush` `myRectangle` nadal trwa utrzymywanie aktywności i nastąpi wywołanie zwrotne, gdy <xref:System.Windows.Freezable.Changed> wyzwala zdarzenie. Należy pamiętać, `myBrush` że przypisanie <xref:System.Windows.Shapes.Shape.Fill%2A> do właściwości nowego <xref:System.Windows.Shapes.Rectangle> programu spowoduje po prostu dodanie kolejnej procedury `myBrush`obsługi zdarzeń do.  
  
 Zalecanym sposobem oczyszczenia tych typów obiektów jest usunięcie <xref:System.Windows.Media.Brush> <xref:System.Windows.Shapes.Shape.Fill%2A> z właściwości, która <xref:System.Windows.Freezable.Changed> spowoduje usunięcie programu obsługi zdarzeń.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Wirtualizacja interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera również odmianę <xref:System.Windows.Controls.StackPanel> elementu, który automatycznie "umożliwia wirtualizację zawartości podrzędnej powiązanej z danymi. W tym kontekście wyraz "Wirtualizacja" odnosi się do techniki, za pomocą której podzbiór obiektów jest generowany na podstawie większej liczby elementów danych w zależności od tego, które elementy są widoczne na ekranie. Jest to czasochłonne, zarówno w zakresie pamięci, jak i procesora, aby generować dużą liczbę elementów interfejsu użytkownika, gdy tylko kilka może znajdować się na ekranie w danym momencie. <xref:System.Windows.Controls.VirtualizingStackPanel>(za pośrednictwem funkcji <xref:System.Windows.Controls.VirtualizingPanel>zapewnianych przez program) oblicza widoczne elementy <xref:System.Windows.Controls.ItemContainerGenerator> i współpracuje <xref:System.Windows.Controls.ItemsControl> z obiektem <xref:System.Windows.Controls.ListBox> od <xref:System.Windows.Controls.ListView>a (na przykład lub) do tworzenia tylko elementów dla widocznych elementów.  
  
 W miarę optymalizacji wydajności, obiekty wizualne dla tych elementów są generowane lub utrzymywane w stanie aktywności, jeśli są widoczne na ekranie. Obiekty wizualne mogą zostać usunięte, gdy nie znajdują się już w obszarze widocznym formantu. Nie ma to pomylić z wirtualizacją danych, w której obiekty danych nie są obecne w lokalnej kolekcji — a nie są przesyłane strumieniowo w razie potrzeby.  
  
 W poniższej tabeli przedstawiono czas dodawania i renderowania elementów 5000 <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.StackPanel> do i <xref:System.Windows.Controls.VirtualizingStackPanel>. W tym scenariuszu pomiary przedstawiają czas między dołączeniem ciągu tekstowego do <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości <xref:System.Windows.Controls.ItemsControl> obiektu do czasu, gdy elementy panelu wyświetlają ciąg tekstowy.  
  
|**Panel hosta**|**Czas renderowania (MS)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Zobacz także

- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Wykorzystanie możliwości sprzętu](optimizing-performance-taking-advantage-of-hardware.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Grafika 2D i obrazowanie](optimizing-performance-2d-graphics-and-imaging.md)
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Tekst](optimizing-performance-text.md)
- [Powiązanie danych](optimizing-performance-data-binding.md)
- [Inne zalecenia dotyczące wydajności](optimizing-performance-other-recommendations.md)
