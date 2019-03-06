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
ms.openlocfilehash: 5548292480f07fa192985800931f9d0262f2b791
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352688"
---
# <a name="optimizing-performance-object-behavior"></a>Optymalizacja wydajności: Zachowanie obiektu
Opis zachowania wewnętrzne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów ułatwi Ci odpowiednie kompromis między funkcjonalność i wydajność.  
  

  
<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Nie usuwanie programów obsługi zdarzeń w obiektach może zachować aktywności obiektów  
 Delegat, który przekazuje obiekt, do jej zdarzenia jest skutecznym odniesieniem do tego obiektu. W związku z tym programy obsługi zdarzeń można przechowywać obiekty aktywności dłużej niż oczekiwano. Wykonywanie czyszczenia obiekt, który został zarejestrowany do nasłuchiwania zdarzeń obiektu, jest istotne, aby usunąć ten delegat przed zwolnieniem obiektu. Utrzymywanie zbędnych obiektów aktywności powoduje zwiększenie użycia pamięci aplikacji. Jest to szczególnie istotne w przypadku, gdy obiekt jest głównym drzewa logicznego lub drzewo wizualne.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wprowadza wzorzec odbiornika zdarzeń słabych dla zdarzenia, które mogą być przydatne w sytuacjach, w których trudno jest śledzić relacje okres istnienia obiektów między źródłem i odbiornika. Niektóre istniejące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia, użyj tego wzorca. W przypadku wdrażania obiektów zdarzeń niestandardowych, ten wzorzec może być użytkowania do Ciebie. Aby uzyskać więcej informacji, zobacz [słabe wzorce zdarzeń](weak-event-patterns.md).  
  
 Istnieje kilka narzędzi, takich jak Profiler CLR i Praca Ustaw przeglądarkę, który można zawiera informacje na temat użycia pamięci przez określony proces. Profiler CLR obejmuje pewną liczbę bardzo przydatne widoki profil alokacji, w tym histogram przydzielonych typów, alokacji i wywołanie wykresów, przedstawiający wyrzucania elementów bezużytecznych różnych generacji i wynikowego stanu sterty zarządzanej po osi czasu te kolekcje i drzewo wywołań alokacji na metody i załadowań zestawów. Aby uzyskać więcej informacji, zobacz [Centrum deweloperów .NET Framework](https://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Właściwości zależności i obiekty  
 Ogólnie rzecz biorąc, uzyskiwanie dostępu do właściwości zależności <xref:System.Windows.DependencyObject> nie jest wolniejsze niż dostęp do [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości. W trakcie małej wydajności w czasie ustawiania wartości właściwości wartość jest tak szybko, jak uzyskać korzyści z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości. Przesunięcie małe obciążenie jest fakt, że właściwości zależności obsługuje niezawodne funkcje, takie jak powiązania danych, animacji, dziedziczenie i stylów. Aby uzyskać więcej informacji, zobacz [Przegląd właściwości zależności](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Optymalizacje DependencyProperty  
 Należy dokładnie zdefiniować właściwości zależności w aplikacji. Jeśli Twoje <xref:System.Windows.DependencyProperty> wpływa na renderować obraz tylko opcje metadanych typu, a nie inne opcje metadanych takich jak <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, należy oznaczyć w związku z tym poprzez zastąpienie jej metadane. Aby uzyskać więcej informacji o zastępowanie i uzyskiwanie metadanych właściwości modelu, zobacz [metadane zależności właściwości](dependency-property-metadata.md).  
  
 Może być bardziej efektywne, gdy obsługi zmiany właściwości unieważnienie miary, rozmieszczanie i ręczne renderowanie przebiegów Jeśli nie wszystkie zmiany właściwości rzeczywiście wpływa na miarę, rozmieszczanie i renderowania. Na przykład można zdecydować, w celu ponownego renderowania w tle, tylko wtedy, gdy wartość jest większa niż limit zestawu. W tym przypadku procedury obsługi zmiany właściwości tylko spowoduje unieważnienie renderowania, gdy wartość przekracza ustalony limit.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Tworzenie dziedziczne DependencyProperty jest nie jest wolna  
 Właściwości zależności zarejestrowanych są domyślnie nie są dziedziczone. Jednak można jawnie tworzyć dowolnej właściwości dziedziczonych. Jest to przydatne, konwertowania właściwość, która ma być dziedziczona ma wpływ na wydajność, zwiększając czas dla unieważniania właściwości.  
  
### <a name="use-registerclasshandler-carefully"></a>Ostrożne korzystanie z RegisterClassHandler  
 Podczas wywoływania <xref:System.Windows.EventManager.RegisterClassHandler%2A> pozwala zapisać swoje wystąpienie przechodzi w stan, ważne jest, aby wiedzieć, że program obsługi jest wywoływana dla każdego wystąpienia, co może powodować problemy z wydajnością. Używaj tylko <xref:System.Windows.EventManager.RegisterClassHandler%2A> po aplikacja wymaga, aby zapisać swoje wystąpienie przechodzi w stan.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Ustaw wartość domyślną dla DependencyProperty podczas rejestracji  
 Podczas tworzenia <xref:System.Windows.DependencyProperty> wymagającym wartość domyślną, ustaw wartość przy użyciu metadanych domyślne przekazany jako parametr do <xref:System.Windows.DependencyProperty.Register%2A> metody <xref:System.Windows.DependencyProperty>. Użyj tej techniki, zamiast ustawiania wartości właściwości w konstruktorze lub na każdym wystąpieniu elementu.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Ustaw wartość PropertyMetadata przy użyciu rejestru  
 Podczas tworzenia <xref:System.Windows.DependencyProperty>, istnieje możliwość ustawienia <xref:System.Windows.PropertyMetadata> za pomocą <xref:System.Windows.DependencyProperty.Register%2A> lub <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metody. Chociaż obiekt może mieć Konstruktor statyczny do wywołania <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, to nie jest optymalne rozwiązanie i będzie mieć wpływ na wydajność. Aby uzyskać najlepszą wydajność, ustaw <xref:System.Windows.PropertyMetadata> podczas wywołania <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Obiekty freezable  
 A <xref:System.Windows.Freezable> to specjalny typ obiektu, który ma dwa stany: odblokowany i zablokowane. Blokowanie obiektów w miarę możliwości zwiększa wydajność aplikacji i zmniejsza jej zestawu roboczego. Aby uzyskać więcej informacji, zobacz [Przegląd obiektów Freezable](freezable-objects-overview.md).  
  
 Każdy <xref:System.Windows.Freezable> ma <xref:System.Windows.Freezable.Changed> zdarzenia, które jest wywoływane zawsze wtedy, gdy zmienia się. Powiadomienia o zmianach, są jednak kosztowna pod względem wydajności aplikacji.  
  
 Rozważmy następujący przykład, w których każdy <xref:System.Windows.Shapes.Rectangle> używa tych samych <xref:System.Windows.Media.Brush> obiektu:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera program obsługi zdarzeń dla <xref:System.Windows.Media.SolidColorBrush> obiektu <xref:System.Windows.Freezable.Changed> zdarzeń w celu unieważnienia <xref:System.Windows.Shapes.Rectangle> obiektu <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości. W tym przypadku każdym <xref:System.Windows.Media.SolidColorBrush> musi wyzwalać jego <xref:System.Windows.Freezable.Changed> zdarzenia jest wymagany do wywołania funkcji wywołania zwrotnego dla każdego <xref:System.Windows.Shapes.Rectangle>— gromadzenia te wywołania funkcji wywołania zwrotnego powodować spadek istotnie poprawiającą wydajność. Ponadto jest bardzo wydajności dużej ilości Dodawanie i usuwanie programów obsługi na tym etapie, ponieważ aplikacja musi przechodzić przez całą listę, aby to zrobić. Jeśli scenariusz aplikacji nigdy się nie zmienia <xref:System.Windows.Media.SolidColorBrush>, będzie ponoszenia kosztów utrzymywania <xref:System.Windows.Freezable.Changed> procedury obsługi zdarzeń niepotrzebnie.  
  
 Zamrażanie <xref:System.Windows.Freezable> może zwiększyć jej wydajność, ponieważ nie jest już musi używać zasobów przy zachowaniu powiadomienia o zmianach. W poniższej tabeli przedstawiono rozmiar prostego <xref:System.Windows.Media.SolidColorBrush> podczas jego <xref:System.Windows.Freezable.IsFrozen%2A> właściwość jest ustawiona na `true`, w porównaniu do kiedy nie jest. Założono, że stosowanie jednej pędzla do <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość dziesięciu <xref:System.Windows.Shapes.Rectangle> obiektów.  
  
|**State**|**Rozmiar**|  
|---------------|--------------|  
|Zamrożone <xref:System.Windows.Media.SolidColorBrush>|212 bajtów|  
|Zamrożone inne niż <xref:System.Windows.Media.SolidColorBrush>|972 bajtów|  
  
 Poniższy przykład kodu ilustruje tę koncepcję:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Zmiany programów obsługi na odblokowanej obiektów Freezable może zachować aktywności obiektów  
 Delegat, który przekazuje obiekt <xref:System.Windows.Freezable> obiektu <xref:System.Windows.Freezable.Changed> zdarzeń jest skutecznym odniesieniem do tego obiektu. W związku z tym <xref:System.Windows.Freezable.Changed> procedury obsługi zdarzeń można zachować obiektów aktywności dłużej niż oczekiwano. Podczas wykonywania oczyszczania obiektu, który został zarejestrowany do nasłuchiwania <xref:System.Windows.Freezable> obiektu <xref:System.Windows.Freezable.Changed> zdarzeń, ważne jest aby usunąć ten delegat przed zwolnieniem obiektu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] również przechwytuje <xref:System.Windows.Freezable.Changed> zdarzenia wewnętrznie. Na przykład, wszystkie właściwości zależności, które przejście <xref:System.Windows.Freezable> zgodnie z wartością będzie nasłuchiwać <xref:System.Windows.Freezable.Changed> zdarzeń automatycznie. <xref:System.Windows.Shapes.Shape.Fill%2A> Właściwość, która przyjmuje <xref:System.Windows.Media.Brush>, ilustruje tę koncepcję.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Na przypisanie `myBrush` do `myRectangle.Fill`, obiekt delegowany, wskazując powrót do <xref:System.Windows.Shapes.Rectangle> obiekt zostanie dodany do <xref:System.Windows.Media.SolidColorBrush> obiektu <xref:System.Windows.Freezable.Changed> zdarzeń. Oznacza to, poniższy kod faktycznie nie wprowadza `myRect` odśmiecaniu pamięci:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 W tym przypadku `myBrush` nadal może być utrzymywanie `myRectangle` aktywności i będzie wywołania zwrotnego do niego po jego jego <xref:System.Windows.Freezable.Changed> zdarzeń. Należy pamiętać, że przypisanie `myBrush` do <xref:System.Windows.Shapes.Shape.Fill%2A> nową właściwość <xref:System.Windows.Shapes.Rectangle> będzie po prostu dodać innego programu obsługi zdarzeń do `myBrush`.  
  
 Zalecany sposób, aby wyczyścić te typy obiektów, jest usunięcie <xref:System.Windows.Media.Brush> z <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość, która z kolei spowoduje usunięcie <xref:System.Windows.Freezable.Changed> programu obsługi zdarzeń.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Wirtualizacja interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia również odmianą <xref:System.Windows.Controls.StackPanel> element, który automatycznie "Wirtualizuje" zawartość elementu podrzędnego powiązanych z danymi. W tym kontekście słowo wirtualizacji dotyczy to technika, za pomocą której podzbiór obiektów są generowane na podstawie większej liczby elementów danych na podstawie elementy, które są widoczne na ekranie. Jest intensywna, zarówno pod względem pamięci i procesora, aby generować dużą liczbę elementów interfejsu użytkownika, gdy tylko kilka może znajdować się na ekranie w danym momencie. <xref:System.Windows.Controls.VirtualizingStackPanel> (za pośrednictwem funkcje udostępniane przez <xref:System.Windows.Controls.VirtualizingPanel>) oblicza widocznych elementów i projektów w programach <xref:System.Windows.Controls.ItemContainerGenerator> z <xref:System.Windows.Controls.ItemsControl> (takie jak <xref:System.Windows.Controls.ListBox> lub <xref:System.Windows.Controls.ListView>) można tworzyć tylko elementy widoczne elementy.  
  
 Jak zoptymalizować wydajność obiektów wizualnych dla tych elementów są generowane lub tylko życiu, jeśli są one widoczne na ekranie. Gdy nie są już obszar wyświetlany formantu, mogą zostać usunięte obiekty wizualne. To nie należy mylić z wirtualizacją danych, gdzie obiekty danych nie występują wszystkie lokalne kolekcji — zamiast strumieniowo zgodnie z potrzebami.  
  
 W poniższej tabeli przedstawiono czas dodawania i renderowanie 5000 <xref:System.Windows.Controls.TextBlock> elementów <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.VirtualizingStackPanel>. W tym scenariuszu pomiarów reprezentują czas między dołączanie ciąg tekstowy <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ItemsControl> obiektu do chwili, gdy elementy panelu wyświetlić ciąg tekstowy.  
  
|**Panel hosta**|**Renderowanie czas (ms)**|  
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
