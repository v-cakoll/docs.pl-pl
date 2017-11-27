---
title: "Optymalizacja wydajności: zachowanie obiektu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e929ec927bc0eb7494d8865fc5452cfc6910169
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-object-behavior"></a>Optymalizacja wydajności: zachowanie obiektu
Opis zachowania wewnętrznych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów pomoże Ci kompromisy prawo między funkcjonalność i wydajność.  
  

  
<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Nie usuwanie programów obsługi zdarzeń w obiektach może Keep Alive obiektów  
 Delegat, obiekt przekazywany do jego zdarzenia skutecznie jest odwołanie do tego obiektu. W związku z tym obsługi zdarzeń może podtrzymywania obiektów dłużej niż oczekiwano. Wykonywanie czyszczenia obiekt, który został zarejestrowany do nasłuchiwania zdarzeń obiektu, jest ważne, aby usunąć ten delegat przed zwolnieniem obiektu. Utrzymywanie aktywności niepotrzebnych obiektów zwiększa wykorzystanie pamięci aplikacji. Jest to szczególnie istotne, gdy obiekt jest głównym drzewa logicznego lub wizualnego drzewa.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wprowadza wzorzec odbiornika słabe zdarzeń dla zdarzenia, które mogą być przydatne w sytuacjach, w którym są trudne do śledzenia relacje okres istnienia obiektów między źródłem i odbiornika. Niektóre istniejące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia użycia tego wzorca. W przypadku wdrażania obiektów niestandardowych zdarzeń, ten wzorzec mogą być uwzględnione dla Ciebie. Aby uzyskać więcej informacji, zobacz [słabe wzorce zdarzeń](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
 Istnieje kilka narzędzi, takich jak CLR Profiler i pracy Set Viewer, można zawierający informacje o użyciu pamięci przez określony proces. CLR Profiler zawiera szereg widoki przydatne profil alokacji, w tym histogram przydzielone typy wykresów alokacji i wywołanie, przedstawiający wyrzucania różnych generacji i wynikowy stanu sterty zarządzanej po osi czasu te kolekcje, a drzewo wywołań przedstawiający-metoda alokacji i załadowań zestawów. Aby uzyskać więcej informacji, zobacz [Centrum deweloperów .NET Framework](http://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Właściwości zależności i obiekty  
 Ogólnie rzecz biorąc, uzyskiwanie dostępu do właściwości zależności <xref:System.Windows.DependencyObject> nie jest mniejsza niż podczas uzyskiwania dostępu do [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości. W trakcie małej wydajności w czasie ustawiania wartości właściwości pobierania wartości jest tak szybko, jak pobieranie wartości z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości. Przesunięcie małe obciążenie jest fakt, że właściwości zależności obsługuje niezawodne funkcje, takie jak powiązania danych, animacji dziedziczenia i stylów. Aby uzyskać więcej informacji, zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Optymalizacje DependencyProperty  
 Należy zdefiniować dokładnie właściwości zależności w aplikacji. Jeśli Twoje <xref:System.Windows.DependencyProperty> wpływa na renderować obraz tylko typ metadanych opcje, a nie inne opcje metadanych takich jak <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, należy oznaczyć go jako takie przez zastąpienie jej metadane. Aby uzyskać więcej informacji na temat zastępowanie i uzyskiwanie metadanych właściwości, zobacz [metadanych właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
 Może być bardziej efektywne ma obsługi zmiany właściwości unieważnienie miary, rozmieszczanie i ręcznie renderowania przekazuje Jeśli nie wszystkie zmiany właściwości rzeczywiście wpływa na miarę, rozmieszczanie i renderowania. Na przykład możesz ponownie renderowania tło tylko wtedy, gdy wartość jest większa niż ustawiony limit. W takim przypadku programu obsługi zmiany właściwości tylko spowoduje unieważnienie renderowania, jeśli wartość przekracza ustawiony limit.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Tworzenie dziedziczne DependencyProperty jest nie  
 Domyślnie zależności zarejestrowanych właściwości są dziedziczone z systemem innym niż. Jednak możesz jawnie wprowadzić dowolną właściwość dziedziczonych. Jest to przydatna funkcja, konwertowanie właściwość, która ma być dziedziczona wpływa na wydajność, zwiększając czas dla unieważniania właściwości.  
  
### <a name="use-registerclasshandler-carefully"></a>Ostrożnie korzystaj z RegisterClassHandler  
 Podczas wywoływania <xref:System.Windows.EventManager.RegisterClassHandler%2A> można zapisywać Twoje stan wystąpienia jest należy pamiętać, że program obsługi jest wywoływana na każde wystąpienie, co może spowodować problemy z wydajnością. Należy używać tylko <xref:System.Windows.EventManager.RegisterClassHandler%2A> gdy aplikacja wymaga, aby zapisać swój stan wystąpienia.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Ustaw wartość domyślną parametru DependencyProperty podczas rejestracji  
 Podczas tworzenia <xref:System.Windows.DependencyProperty> która wymaga wartości domyślnej, należy ustawić wartość przy użyciu metadanych domyślne przekazany jako parametr <xref:System.Windows.DependencyProperty.Register%2A> metody <xref:System.Windows.DependencyProperty>. Użyj tej metody nie ustawiania wartości właściwości w konstruktorze lub w każdym wystąpieniu elementu.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Ustaw wartość obiekt PropertyMetadata za pomocą rejestru  
 Podczas tworzenia <xref:System.Windows.DependencyProperty>, istnieje możliwość ustawienia <xref:System.Windows.PropertyMetadata> za pomocą <xref:System.Windows.DependencyProperty.Register%2A> lub <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metody. Mimo że obiekt może mieć Konstruktor statyczny do wywołania <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, to nie jest optymalnym rozwiązaniem i będzie mieć wpływ na wydajność. Aby uzyskać najlepszą wydajność, <xref:System.Windows.PropertyMetadata> podczas wywołania <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Obiektu freezable obiektów  
 A <xref:System.Windows.Freezable> to specjalny typ obiektu, który ma dwa stany: odblokowana i jest zablokowana. Zamrażanie obiekty możliwe poprawia wydajność aplikacji i zmniejsza jej zestawu roboczego. Aby uzyskać więcej informacji, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Każdy <xref:System.Windows.Freezable> ma <xref:System.Windows.Freezable.Changed> zdarzenie jest zgłaszane, gdy zmieni się. Jednak kosztowna pod względem wydajności aplikacji są powiadomienia o zmianie.  
  
 Należy wziąć pod uwagę w poniższym przykładzie, w którym każdy <xref:System.Windows.Shapes.Rectangle> wykorzystuje takie same <xref:System.Windows.Media.Brush> obiektu:  
  
 [!code-csharp[Performance#PerformanceSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia program obsługi zdarzeń dla <xref:System.Windows.Media.SolidColorBrush> obiektu <xref:System.Windows.Freezable.Changed> zdarzeń w celu unieważnienia <xref:System.Windows.Shapes.Rectangle> obiektu <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości. W takim przypadku po każdej aktualizacji <xref:System.Windows.Media.SolidColorBrush> ma uruchomienie jej <xref:System.Windows.Freezable.Changed> zdarzenia jest wymagana do wywołania funkcji wywołania zwrotnego dla każdego <xref:System.Windows.Shapes.Rectangle>— zmniejszenie wydajności znaczących nałożyć akumulacji tych wywołań funkcji wywołania zwrotnego. Ponadto jest bardzo wydajności znacznym do dodawania i usuwania programów obsługi na tym etapie, ponieważ aplikacja będzie musiał przejść przez całą listę, aby to zrobić. Jeśli scenariusz aplikacji nie ulega zmianie <xref:System.Windows.Media.SolidColorBrush>, będzie płatności kosztów obsługi <xref:System.Windows.Freezable.Changed> procedury obsługi zdarzeń niepotrzebnie.  
  
 Zamrażanie <xref:System.Windows.Freezable> może zwiększyć jej wydajność, ponieważ nie jest już konieczne rozwiń zasobów na utrzymanie powiadomienia o zmianie. W poniższej tabeli przedstawiono rozmiar prostą <xref:System.Windows.Media.SolidColorBrush> po jego <xref:System.Windows.Freezable.IsFrozen%2A> właściwość jest ustawiona na `true`, w porównaniu do kiedy nie jest. Przyjęto założenie, że jeden pędzla do stosowania <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości dziesięciu <xref:System.Windows.Shapes.Rectangle> obiektów.  
  
|**Stan**|**Rozmiar**|  
|---------------|--------------|  
|Zablokowane<xref:System.Windows.Media.SolidColorBrush>|212 bajtów|  
|Zablokowane na inne niż<xref:System.Windows.Media.SolidColorBrush>|972 bajtów|  
  
 Poniższy przykładowy kod przedstawia tę koncepcję:  
  
 [!code-csharp[Performance#PerformanceSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Zmienione programów obsługi na odblokowanej obiektów Freezable może Keep Alive obiektów  
 Delegat, który przekazuje obiekt <xref:System.Windows.Freezable> obiektu <xref:System.Windows.Freezable.Changed> zdarzeń jest odwołanie do tego obiektu. W związku z tym <xref:System.Windows.Freezable.Changed> procedury obsługi zdarzeń może podtrzymywania obiektów dłużej niż oczekiwano. Podczas wykonywania oczyszczania obiektu, który został zarejestrowany do nasłuchiwania na <xref:System.Windows.Freezable> obiektu <xref:System.Windows.Freezable.Changed> zdarzeń, ważne jest, aby usunąć ten delegat przed zwolnieniem obiektu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Przechwytuje również <xref:System.Windows.Freezable.Changed> zdarzenia wewnętrznie. Na przykład wszystkie właściwości zależności, które biorą <xref:System.Windows.Freezable> jako wartość będzie nasłuchiwać <xref:System.Windows.Freezable.Changed> zdarzeń automatycznie. <xref:System.Windows.Shapes.Shape.Fill%2A> Właściwość, która przyjmuje <xref:System.Windows.Media.Brush>, ilustruje tę koncepcję.  
  
 [!code-csharp[Performance#PerformanceSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Na przypisanie `myBrush` do `myRectangle.Fill`, wskazujące do delegata <xref:System.Windows.Shapes.Rectangle> obiekt zostanie dodany do <xref:System.Windows.Media.SolidColorBrush> obiektu <xref:System.Windows.Freezable.Changed> zdarzeń. W efekcie następujący kod nie powoduje faktycznie `myRect` wyczyszczeniu:  
  
 [!code-csharp[Performance#PerformanceSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 W takim przypadku `myBrush` jest zachowując `myRectangle` aktywności i spowoduje wywołanie zwrotne do niego po jego jego <xref:System.Windows.Freezable.Changed> zdarzeń. Należy pamiętać, że przypisywanie `myBrush` do <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości nowej <xref:System.Windows.Shapes.Rectangle> po prostu doda inny program obsługi zdarzeń do `myBrush`.  
  
 Zalecany sposób, aby wyczyścić te typy obiektów, należy usunąć <xref:System.Windows.Media.Brush> z <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość, która z kolei spowoduje usunięcie <xref:System.Windows.Freezable.Changed> obsługi zdarzeń.  
  
 [!code-csharp[Performance#PerformanceSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Wirtualizacja interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dostępne są także odmianą <xref:System.Windows.Controls.StackPanel> element, który automatycznie "Wirtualizuje" zawartość elementu podrzędnego powiązane z danymi. W tym kontekście wirtualizacji wyraz odwołuje się do technika, przez którą podzbiór obiektów są generowane na podstawie większą liczbę elementów danych oparte na elementy, które są widoczne na ekranie. Jest znacznym zarówno pod względem pamięci i procesora, aby generować dużą liczbę elementów interfejsu użytkownika, gdy tylko kilka może znajdować się na ekranie w danym momencie. <xref:System.Windows.Controls.VirtualizingStackPanel>(za pośrednictwem funkcji udostępnianych przez usługę <xref:System.Windows.Controls.VirtualizingPanel>) oblicza widocznych elementów i współdziała z <xref:System.Windows.Controls.ItemContainerGenerator> z <xref:System.Windows.Controls.ItemsControl> (takich jak <xref:System.Windows.Controls.ListBox> lub <xref:System.Windows.Controls.ListView>) można tworzyć tylko elementy dla widocznych elementów.  
  
 Jak zoptymalizować wydajność obiektów visual dla tych elementów są tylko wygenerowany lub utrzymywane, jeśli są one widoczne na ekranie. Gdy nie są już w widocznym obszarze formantu visual obiektów mogą zostać usunięte. To nie należy mylić z wirtualizacją danych, gdy obiekty danych nie występują wszystkie w lokalnym kolekcji-raczej strumieniowo zgodnie z potrzebami.  
  
 W poniższej tabeli przedstawiono czas Dodawanie i renderowania 5000 <xref:System.Windows.Controls.TextBlock> elementy <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.VirtualizingStackPanel>. W tym scenariuszu pomiarów odpowiadają za czas między dołączanie ciąg tekstowy do <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ItemsControl> obiektu do momentu, gdy elementy panelu wyświetlić ciąg tekstowy.  
  
|**Panel hosta**|**Renderowanie czas (ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planowanie wydajności aplikacji](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Dzięki funkcji sprzętu](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Grafika 2W i utworzenia obrazu](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Zasoby aplikacji](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Inne zalecenia dotyczące wydajności](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
