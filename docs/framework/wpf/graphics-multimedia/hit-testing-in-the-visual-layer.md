---
title: Test trafienia w warstwie Visual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit testing functionality [WPF]
- visual layer [WPF], hit testing functionality
ms.assetid: b1a64b61-14be-4d75-b89a-5c67bebb2c7b
ms.openlocfilehash: 60da11af51722e86a61c5e3298fafba2221f000b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558112"
---
# <a name="hit-testing-in-the-visual-layer"></a>Test trafienia w warstwie Visual
Ten temat zawiera omówienie trafień testowania funkcje udostępniane przez warstwę visual. Obsługa testowania trafień pozwala określić, czy wartość geometry, czy punkt znajduje się w renderowanej zawartości <xref:System.Windows.Media.Visual>, co umożliwia wdrożenie zachowania interfejsu użytkownika, takie jak prostokąta zaznaczenia, aby zaznaczyć wiele obiektów.  
  
 
  
<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>Scenariusze testowania trafień  
 <xref:System.Windows.UIElement> Klasa udostępnia <xref:System.Windows.UIElement.InputHitTest%2A> metodę, która służy do testowania względem elementu za pomocą podanej wartości współrzędnych trafienia. W wielu przypadkach <xref:System.Windows.UIElement.InputHitTest%2A> metoda zapewnia informacji dotyczących odpowiednich funkcji dla wykonania trafień testowania elementów. Istnieje jednak kilka scenariuszy, w których może być konieczne wdrożenie testowania trafień w warstwie visual.  
  
-   Trafienia testowanie inną niż<xref:System.Windows.UIElement> obiektów: ma to zastosowanie, jeśli są osiągane testowania z systemem innym niż<xref:System.Windows.UIElement> obiekty, takie jak <xref:System.Windows.Media.DrawingVisual> lub obiektów graficznych.  
  
-   Testowanie przy użyciu geometrię trafień: ma to zastosowanie, jeśli musisz za pomocą obiektu geometrii, a nie wartość współrzędnych punktu testowania trafienia.  
  
-   Testowanie wielu obiektów trafień: ma to zastosowanie, gdy trzeba trafień badanie wiele obiektów, takich jak nakładających się obiektów. Aby uzyskać wyniki dla wszystkich elementów wizualnych przecinające się geometrycznych lub punkt, nie tylko pierwsza z nich.  
  
-   Ignorowanie <xref:System.Windows.UIElement> trafień testowania zasad: ma to zastosowanie, gdy należy zignorować <xref:System.Windows.UIElement> trafień testowania zasad, które uwzględnia takie czynniki jak określa, czy element jest wyłączone i niewidoczne.  
  
> [!NOTE]
>  Dla ilustrujące przykładowe kompletny kod testowania trafień w warstwie visual, zobacz [trafień przy użyciu DrawingVisuals próbki](http://go.microsoft.com/fwlink/?LinkID=159994) i [trafień testu z przykładowych współdziałanie Win32](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>Obsługa testowania trafień  
 Celem <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metod w <xref:System.Windows.Media.VisualTreeHelper> klasa ma na celu określenie, czy wartość współrzędnych geometrii lub punkt znajduje się w renderowanej zawartości danego obiektu, takich jak kontrola lub elementu graficznego. Można na przykład użyć testowania trafień ustalenie, czy kliknięcie myszki w prostokątem obiektu mieści się w geometrii okręgu. Można również zastąpić domyślną implementację trafień testy w celu wykonywania obliczeń niestandardowych testu trafienia.  
  
 Na poniższej ilustracji przedstawiono relację między regionu nieregularnych obiekt i jego prostokątem.  
  
 ![Diagram regionu prawidłowy testu trafienia](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagram prawidłowy testu trafienia regionu  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>Testowanie trafień i porządek osi z  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Warstwy visual obsługuje testowania trafień względem wszystkich obiektów w ramach punktu lub geometry, nie tylko z obiektem umieszczony najwyżej. Wyniki są zwracane w porządku osi z. Jednak visual obiekt, który można przekazać jako parametru <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> Metoda określa, które części z drzewa wizualnego nastąpi trafienie testu. Naciśnij klawisz badanie całego drzewa wizualnego lub jakiejkolwiek jego części.  
  
 Na poniższej ilustracji obiektu okręgu znajduje się na szczycie kwadrat i trójkąt obiektów. Jeśli interesuje Cię tylko trafień testowania visual obiektu, którego wartość kolejności jest najwyżej, można ustawić wyliczenia visual testu trafienia do zwrócenia <xref:System.Windows.Media.HitTestResultBehavior.Stop> z <xref:System.Windows.Media.HitTestResultCallback> można zatrzymać testu trafienia przechodzenie od pierwszego elementu.  
  
 ![Diagram z&#45;kolejność drzewa wizualnego](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagram porządek osi z drzewa wizualnego  
  
 Aby wyliczyć wszystkie obiekty visual pod określony punkt lub geometrii wrócić <xref:System.Windows.Media.HitTestResultBehavior.Continue> z <xref:System.Windows.Media.HitTestResultCallback>. Oznacza to, że można trafień testu visual obiektów, które są pod innymi obiektami, nawet wtedy, gdy są one całkowicie zasłonięty. Zobacz przykładowy kod w sekcji "Przy użyciu trafień testu wyniki wywołania zwrotnego" Aby uzyskać więcej informacji.  
  
> [!NOTE]
>  Visual obiekt, który jest niewidoczny również mogą zakończyć testowanie.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Testowanie trafień przy użyciu domyślnego  
 Można określić, czy punkt znajduje się w geometrii obiektu visual przy użyciu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodę, aby określić obiekt wizualny, a punkt koordynować wartość do przetestowania. Parametr obiektu visual identyfikuje punkt początkowy w drzewie wizualnym wyszukiwania testu trafienia. Jeśli obiekt wizualny znajduje się w drzewie wizualnym, których geometrii zawiera współrzędne, jest równa <xref:System.Windows.Media.HitTestResult.VisualHit%2A> właściwość <xref:System.Windows.Media.HitTestResult> obiektu. <xref:System.Windows.Media.HitTestResult> Jest następnie zwracany z <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody. Jeśli punkt nie znajduje się z drzewa wizualnego podrzędne są osiągane testowania, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> zwraca `null`.  
  
> [!NOTE]
>  Trafień domyślnego badania zawsze zwraca obiekt najwyższy w porządku osi z. Aby zidentyfikować wszystkie obiekty visual, nawet te, które może być częściowo lub całkowicie zasłonięty, użyj wywołania zwrotnego wynik testu trafienia.  
  
 Wartość współrzędnych jako parametr punktu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda ma względem współrzędnych są osiągane testowanie obiektu visual. Na przykład, jeśli można zagnieżdżać zdefiniowanych obiektów visual na (100, 100) w przestrzeni współrzędnych elementu nadrzędnego, następnie testowania trafień element wizualny podrzędnych w (0, 0) jest odpowiednikiem trafień testowanie (100, 100) w przestrzeni współrzędnych obiektu nadrzędnego.  
  
 Poniższy kod przedstawia sposób konfigurowania obsługi zdarzeń myszy <xref:System.Windows.UIElement> obiekt, który służy do rejestrowania zdarzenia używane na potrzeby testowania trafień.  
  
 [!code-csharp[HitTestingOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Testowanie trafień wpływ drzewa wizualnego  
 Punkt początkowy w drzewie wizualnym określa obiekty, które są zwracane podczas wyliczania testu trafienia obiektów. Jeśli masz wiele obiektów, które chcesz testowania trafienia visual obiekt używany jako punkt początkowy w drzewie wizualnym musi być wspólnego elementu nadrzędnego wszystkich obiektów zainteresowań. Na przykład jeśli planuje się trafień testowania button element i rysowanie visual na poniższym diagramie, trzeba ustawić punkt początkowy w drzewie wizualnym do wspólnego elementu nadrzędnego w obu. W tym przypadku canvas element jest wspólnego elementu nadrzędnego button element i rysowania visual.  
  
 ![Diagram hierarchii w drzewie wizualnym](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagram hierarchii w drzewie wizualnym  
  
> [!NOTE]
>  <xref:System.Windows.UIElement.IsHitTestVisible%2A> Właściwości pobiera lub ustawia wartość, która deklaruje czy <xref:System.Windows.UIElement>-pochodnej obiekt może być zwrócony jako wynik testu trafienia z niektórych części zrenderowanej zawartości. Dzięki temu można selektywnie alter drzewa wizualnego, aby określić visual obiekty, które są zaangażowane w testu trafienia.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Używa wywołania zwrotnego wynik testu trafienia  
 Można wyliczyć wszystkich obiektów visual w drzewie wizualnym, których geometrii zawiera określoną wartość współrzędnych. Dzięki temu można zidentyfikować wszystkie obiekty visual, nawet tych, które może być częściowo lub całkowicie zasłonięty przez inne obiekty visual. Do wyliczenia obiektów visual używany drzewa wizualnego <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody za pomocą funkcji wywołania zwrotnego testu trafienia. Funkcja wywołania zwrotnego testu trafienia jest wywoływane przez system, gdy współrzędnych podaną wartość jest zawarta w obiektu visual.  
  
 Podczas trafień test wyliczenie wyniki, nie należy wykonywać żadnej operacji, które modyfikuje drzewa wizualnego. Dodawanie lub usuwanie obiektu z drzewa wizualnego, gdy jest on przechodzić może spowodować nieprzewidywalne zachowanie. Można bezpiecznie zmodyfikować drzewa wizualnego po <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> zwraca metody. Chcesz zapewnić struktury danych, takich jak <xref:System.Collections.ArrayList>, aby zapisać wartości podczas wyliczania wyników testu trafienia.  
  
 [!code-csharp[HitTestingOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 Metoda wywołania zwrotnego testu trafienia definiuje akcje, które należy wykonać podczas testu trafienia określono dla określonego obiektu visual w drzewie wizualnym. Po wykonaniu akcji zwracają <xref:System.Windows.Media.HitTestResultBehavior> wartość, która określa, czy kontynuować wyliczenie innego obiektu visual lub nie.  
  
 [!code-csharp[HitTestingOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
>  Kolejności wyliczenie obiektów visual trafień jest porządek osi z. Obiekt wizualny na poziomie najwyżej porządek jest pierwszy obiekt wyliczone. Inne obiekty visual wyliczyć są w trakcie obniżania poziomu porządek osi z. To Zamówienie Wyliczenie odpowiada kolejności renderowanie elementów wizualnych.  
  
 Wyliczenie obiektów visual w funkcji wywołania zwrotnego testu trafienia w dowolnym momencie można zatrzymać zwracając <xref:System.Windows.Media.HitTestResultBehavior.Stop>.  
  
 [!code-csharp[HitTestingOverview#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Przy użyciu zwrotnym filtra testu trafienia  
 Aby ograniczyć obiekty, które są przekazywane do wyników testu trafienia, można użyć filtru opcjonalne testu trafienia. Dzięki temu można zignorować części drzewa wizualnego, że nie jesteś zainteresowany przetwarzania w wynikach testu trafienia. Aby zastosować filtr testu trafienia, zdefiniować funkcję wywołania zwrotnego filtru testu trafienia i przekaż go jako wartości parametru, podczas wywoływania <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.  
  
 [!code-csharp[HitTestingOverview#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Jeśli nie chcesz podać funkcja wywołania zwrotnego testu trafienia opcjonalny filtr, Przekaż `null` wartość jako jego parametr <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.  
  
 [!code-csharp[HitTestingOverview#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Oczyszczanie drzewa wizualnego przy użyciu filtru testu trafienia](../../../../docs/framework/wpf/graphics-multimedia/media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Oczyszczanie drzewa wizualnego  
  
 Funkcja wywołania zwrotnego filtru testu trafienia umożliwia wyliczyć wszystkich elementów wizualnych którego renderowanej zawartości zawiera współrzędne, które określisz. Możesz jednak zignorować niektórych gałęziach drzewa wizualnego, że nie jesteś zainteresowany przetwarzania w funkcji wywołania zwrotnego wyników testu trafienia. Wartość zwracana funkcji wywołania zwrotnego filtru testu trafienia Określa, jakiego typu akcji wyliczenie obiektów visual powinno zająć. Na przykład, jeśli zwróci wartość <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, można usunąć bieżącego obiektu visual i jej funkcji podrzędnych z wyliczenia wyników testu trafienia. Oznacza to, że funkcja wywołania zwrotnego wyników testu trafienia nie zostaną wyświetlone te obiekty w wyliczeniu, jego. Oczyszczeniem drzewa wizualnego obiektów zmniejsza ilość przetwarzanych danych w trakcie przebiegu wyliczenie wyników testu trafienia. W poniższym przykładzie kodu filtr pomija etykiety i ich elementy podrzędne i trafień testów wszystkich innych urządzeń.  
  
 [!code-csharp[HitTestingOverview#106](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
>  Wywołanie zwrotne filtru testu trafienia czasami zostanie wywołana w przypadkach, w którym nie wywołano wywołanie zwrotne wyników testu trafienia.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Zastępowanie domyślnego testy trafienia  
 Można zastąpić trafień domyślny obiekt wizualny testowania pomocy technicznej przez zastąpienie <xref:System.Windows.Media.Visual.HitTestCore%2A> metody. Oznacza to, że po wywołaniu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda, implementacji przesłoniętych <xref:System.Windows.Media.Visual.HitTestCore%2A> jest wywoływana. Przesłoniętą metodę wywoływaną, gdy testu trafienia mieści się w prostokątem obiektu visual nawet jeśli Współrzędna wypada poza renderowanej zawartości obiektu visual.  
  
 [!code-csharp[HitTestingOverview#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Może to być razy, kiedy zachodzi potrzeba trafień badanie zarówno prostokątem i renderowanej zawartości obiektu visual. Za pomocą `PointHitTestParameters` wartość parametru w Twojej przesłoniętych <xref:System.Windows.Media.Visual.HitTestCore%2A> metody jako parametr do metody podstawowej <xref:System.Windows.Media.Visual.HitTestCore%2A>, można wykonać akcji w oparciu o trafienie prostokątem obiektu visual, a następnie wykonaj drugiego testu trafienia przed renderowania zawartości obiektu visual.  
  
 [!code-csharp[HitTestingOverview#108](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 <xref:System.Windows.Media.HitTestResult>  
 <xref:System.Windows.Media.HitTestResultCallback>  
 <xref:System.Windows.Media.HitTestFilterCallback>  
 <xref:System.Windows.UIElement.IsHitTestVisible%2A>  
 [Kliknij przycisk Test przy użyciu DrawingVisuals — przykład](http://go.microsoft.com/fwlink/?LinkID=159994)  
 [Kliknij przycisk Test z przykładowych współdziałanie Win32](http://go.microsoft.com/fwlink/?LinkID=159995)  
 [Przeprowadzanie testu trafienia geometrii w wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)  
 [Przeprowadzanie testu trafienia za pomocą kontenera hosta Win32](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-a-win32-host-container.md)
