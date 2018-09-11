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
ms.openlocfilehash: fe54578407e881ec7d6782ec21100b29eded07a3
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365984"
---
# <a name="hit-testing-in-the-visual-layer"></a>Test trafienia w warstwie Visual
Ten temat zawiera omówienie funkcji testowania trafień, dostarczone przez warstwy visual. Obsługa testowania trafień pozwala określić, czy wartość geometrii lub punkt mieści się w renderowanym zawartość <xref:System.Windows.Media.Visual>, dzięki czemu można zaimplementować zachowania interfejsu użytkownika, takie jak prostokąta zaznaczenia na wybranie wielu obiektów.  
  
 
  
<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>Trafienia scenariuszy testowania  
 <xref:System.Windows.UIElement> Klasa udostępnia <xref:System.Windows.UIElement.InputHitTest%2A> metody, która pozwala na trafień Testuj pod względem elementu za pomocą podanej wartości współrzędnych. W wielu przypadkach <xref:System.Windows.UIElement.InputHitTest%2A> metoda zapewnia odpowiednich funkcji do testowania elementów wykonawczych trafień. Istnieje jednak kilka scenariuszy, w których użytkownik może być konieczne wdrożenie testowania trafień w warstwie visual.  
  
-   Test przed non - trafienia<xref:System.Windows.UIElement> obiektów: ma to zastosowanie, jeśli napotkasz testowania non -<xref:System.Windows.UIElement> obiekty, takie jak <xref:System.Windows.Media.DrawingVisual> lub obiektów graficznych.  
  
-   Test przy użyciu geometrii trafienia: ma to zastosowanie, jeśli potrzebujesz test trafienia przy użyciu obiektów geometrii, a nie wartość współrzędnych punktu.  
  
-   Test względem wielu obiektów trafienia: ma to zastosowanie, gdy trzeba trafień Testuj pod względem wielu obiektów, takich jak nakładających się obiektów. Aby uzyskać wyniki dla wszystkich wizualizacji przecinające się geometrię lub punktu, nie tylko pierwszy z nich.  
  
-   Ignorowanie <xref:System.Windows.UIElement> zasady testowania trafień: ma to zastosowanie, gdy należy zignorować <xref:System.Windows.UIElement> trafień testowania zasad, które uwzględnia takie czynniki jak tego, czy element jest wyłączony lub niewidoczne.  
  
> [!NOTE]
>  Aby uzyskać kompletny kod przykładowy pokazujący test trafienia w warstwie wizualizacji, zobacz [trafień za pomocą DrawingVisuals próbkę](https://go.microsoft.com/fwlink/?LinkID=159994) i [trafień testu z Win32 — współdziałanie](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>Obsługa testowania trafień  
 Celem <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody <xref:System.Windows.Media.VisualTreeHelper> klasy ma na celu określenie, czy wartość współrzędnych geometrii lub punkt znajduje się w renderowanej zawartości danego obiektu, takiego jak kontrolka lub element graficzny. Na przykład można użyć testowania trafień do określenia, czy kliknięcia w ramach prostokąt otaczający obiektu mieści się w geometrii okrąg. Można także Przesłoń domyślną implementację elementu testowania trafień do wykonywania obliczeń test trafień niestandardowy.  
  
 Poniższa ilustracja przedstawia relację między regionów innych niż prostokątne obiekt i jego prostokąt otaczający.  
  
 ![Diagram region prawidłowe testu trafienia](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagram przedstawiający region prawidłowe testu trafienia  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>Testowanie trafień i porządek osi z  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Warstwy visual obsługuje testowania trafień względem wszystkich obiektów w ramach punktu lub geometrii, nie tylko najważniejsze obiekty. Wyniki są zwracane w porządku osi z. Jednak obiekt wizualny, który jest przekazywany jako parametr do <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> Metoda określa, które części drzewa wizualnego, który będzie wskazywać testu. Testuj pod względem całego drzewa wizualnego lub jakiejkolwiek jego części jest osiągalny.  
  
 Na poniższej ilustracji obiekt circle znajduje się na szczycie kwadratu i trójkąt obiektów. Jeśli interesuje Cię tylko obiekt wizualny, którego wartość porządku osi jest umieszczony najwyżej testowania trafień, możesz ustawić wyliczenie visual testu trafienia do zwrócenia <xref:System.Windows.Media.HitTestResultBehavior.Stop> z <xref:System.Windows.Media.HitTestResultCallback> przestanie przechodzenie testu trafienia po pierwszym elementem.  
  
 ![Diagram z&#45;kolejność drzewa wizualnego](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagram przedstawiający porządek drzewo wizualne  
  
 Aby wyliczyć wszystkich obiektów wizualnych pod określony punkt lub geometrii wrócić <xref:System.Windows.Media.HitTestResultBehavior.Continue> z <xref:System.Windows.Media.HitTestResultCallback>. Oznacza to, że mogą trafić testu dla obiektów wizualnych, które są pod innymi obiektami, nawet wtedy, gdy są one całkowicie zasłonięte. Zobacz przykładowy kod w sekcji "Przy użyciu trafień testu wyniki wywołania zwrotnego", aby uzyskać więcej informacji.  
  
> [!NOTE]
>  Wizualne obiekt, który jest przezroczysty również mogą trafić testu.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Test trafienia przy użyciu domyślnego  
 Można zidentyfikować, czy punkt znajduje się w geometrię obiektu visual przy użyciu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodę, aby określić obiekt wizualny i punkt koordynować wartości na potrzeby testowania wstępnego. Parametr obiekt wizualny identyfikuje punkt początkowy w drzewie wizualnym wyszukiwania testu trafienia. Jeśli obiekt wizualny znajduje się w drzewie wizualnym, w których geometrii zawiera współrzędne, jest równa <xref:System.Windows.Media.HitTestResult.VisualHit%2A> właściwość <xref:System.Windows.Media.HitTestResult> obiektu. <xref:System.Windows.Media.HitTestResult> Jest następnie zwracany z <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody. Jeśli punkt nie znajduje się za pomocą podrzędne drzewa wizualnego, testowania, są trafień <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> zwraca `null`.  
  
> [!NOTE]
>  Trafień domyślnego badania zawsze zwraca najważniejsze obiekty w porządku osi z. Aby zidentyfikować wszystkie obiekty wizualne, nawet te, które mogą być całkowicie lub częściowo zasłonięte, należy użyć wywołania zwrotnego wynik testu trafienia.  
  
 Wartość współrzędnych jako parametr punktu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda ma względem współrzędnych obiekt wizualny trafisz testowanie. Na przykład, jeśli można zagnieżdżać zdefiniowanych obiektów wizualnych na (100, 100) przestrzeni współrzędnych obiektu nadrzędnego, kliknij przycisk testowania wizualizacji podrzędnych w (0, 0) jest odpowiednikiem trafień, testowanie w firmie (100, 100) w przestrzeni współrzędnych obiektu nadrzędnego.  
  
 Poniższy kod przedstawia sposób konfigurowania obsługi zdarzeń myszy <xref:System.Windows.UIElement> obiekt, który służy do przechwytywania zdarzeń używane do testowania trafień.  
  
 [!code-csharp[HitTestingOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Test trafienia wpływ drzewo wizualne  
 Począwszy od punktu w drzewie wizualnym określa obiekty, które są zwracane podczas wyliczania testu trafienia obiektów. W przypadku wielu obiektów, które mają być przeprowadzanie testu trafienia visual obiekt używany jako punktu wyjścia w drzewie wizualnym musi być nadrzędnej wspólnej dla wszystkich obiektów zainteresowania. Na przykład jeśli interesują Cię trafień testowania button element i rysowania visual na poniższym diagramie, trzeba ustawić punkt początkowy w drzewie wizualnym nadrzędnej wspólnej dla obu tych elementów. W tym przypadku element roboczy jest nadrzędnej wspólnej dla zarówno button element, jak i rysowania wizualizacji.  
  
 ![Diagram hierarchii drzewa wizualnego](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagram hierarchii drzewa wizualnego  
  
> [!NOTE]
>  <xref:System.Windows.UIElement.IsHitTestVisible%2A> Właściwości pobiera lub ustawia wartość deklarującą, czy <xref:System.Windows.UIElement>-pochodnego obiektu może być zwrócony jako wynik testu trafienia z niektórych części zrenderowanej zawartości. Dzięki temu można selektywnie zmieniać drzewa wizualnego, aby określić obiekty wizualne, które są zaangażowane w hit test.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Za pomocą wywołania zwrotnego wynik testu trafienia  
 Można wyliczyć wszystkich obiektów wizualnych w drzewie wizualnym, w których geometrii zawiera określoną wartość współrzędnych. Dzięki temu można zidentyfikować wszystkie obiekty wizualne, nawet tych, które mogą być całkowicie lub częściowo zasłonięte przez inne obiekty visual. Do wyliczenia obiektów wizualnych w użyciu drzewa wizualnego <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody za pomocą funkcji wywołania zwrotnego testu trafienia. Funkcja wywołania zwrotnego test trafień jest wywoływane przez system, gdy współrzędnych podaną wartość jest zawarta w obiekt wizualny.  
  
 Podczas trafień badania wyliczenie wyników, nie należy wykonywać żadnych operacji, która modyfikuje drzewo wizualne. Dodawanie lub usuwanie obiektu z drzewa wizualnego, podczas gdy jej linia może spowodować nieprzewidywalne zachowanie. Można bezpiecznie modyfikować drzewa wizualnego po <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda zwraca. Możesz chcieć zapewnić struktury danych, takich jak <xref:System.Collections.ArrayList>, aby przechowywać wartości podczas wyliczania wyników testu trafienia.  
  
 [!code-csharp[HitTestingOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 Metody wywołania zwrotnego test trafień Określa akcje, które wykonujesz w chwili zidentyfikowania hit test dla określonego obiektu visual w drzewie wizualnym. Po wykonaniu akcji, zwraca <xref:System.Windows.Media.HitTestResultBehavior> wartość, która określa, czy należy kontynuować wyliczania innych obiektów wizualnych, czy nie.  
  
 [!code-csharp[HitTestingOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
>  Kolejność wyliczania obiektów wizualnych trafień jest według porządku osi z. Obiekt wizualny na poziomie najbardziej na wierzchu porządek jest pierwszy obiekt wyliczenia. Innych obiektów wizualnych wyliczany znajdują się w zmniejsza poziomu porządku osi z. Kolejność wyliczania odnosi się do renderowania kolejność elementów wizualnych.  
  
 Wyliczanie obiektów wizualnych w funkcji wywołania zwrotnego testu trafienia w dowolnym momencie można zatrzymać, zwracając <xref:System.Windows.Media.HitTestResultBehavior.Stop>.  
  
 [!code-csharp[HitTestingOverview#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Za pomocą zwrotnym filtra Hit Test  
 Filtr opcjonalne testu trafienia można użyć do ograniczenia obiektów, które są przekazywane do wyników testu trafienia. Dzięki temu można zignorować części drzewa wizualnego, że nie jesteś zainteresowany przetwarzania w wynikach testu trafienia. Aby zaimplementować filtr test trafień, definiowanie funkcji wywołania zwrotnego filtru test trafień i przekazać go jako wartość parametru, gdy wywołujesz <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.  
  
 [!code-csharp[HitTestingOverview#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Jeśli nie chcesz podać funkcji wywołania zwrotnego filtru opcjonalne test trafień, przekazać `null` wartość jako parametr dla <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.  
  
 [!code-csharp[HitTestingOverview#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Oczyszczanie drzewa wizualnego, za pomocą filtru testów trafienia](../../../../docs/framework/wpf/graphics-multimedia/media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Oczyszczanie drzewa wizualnego  
  
 Funkcja wywołania zwrotnego testu trafienia filtru można wyliczyć wszystkie wizualizacje renderowanych zawierającym współrzędne, które określisz. Jednakże można zignorować niektórych gałęzi drzewa wizualnego, że nie jesteś zainteresowany przetwarzania w funkcji wywołania zwrotnego wyników testu trafienia. Wartość zwracana funkcji wywołania zwrotnego filtr test trafień Określa, jakiego rodzaju akcji wyliczenie obiektów wizualnych powinno zająć. Na przykład, jeśli zwróci wartość <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, możesz usunąć bieżący obiekt wizualny i jego elementy podrzędne z wyliczenia wyników testu trafienia. Oznacza to, czy funkcja wywołania zwrotnego wyników testu trafienia nie będą widzieć tych obiektów w wyliczeniu, jego. Widok drzewa obiektów czyszczenia zmniejsza ilość przetwarzania podczas wyliczania wyników testu trafienia — dostęp próbny. W poniższym przykładzie kodu filtr pomija etykiety i jego elementy podrzędne i naciśnij klawisz analiz, wszystkie inne elementy.  
  
 [!code-csharp[HitTestingOverview#106](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
>  Wywołanie zwrotne filtr testu trafienia czasami zostanie wywołana w przypadkach, gdy wywołanie zwrotne wyników testu trafienia nie zostanie wywołana.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Zastępowanie domyślnego testowania trafień  
 Można zastąpić trafień domyślny obiekt wizualny obsługę testów poprzez zastąpienie <xref:System.Windows.Media.Visual.HitTestCore%2A> metody. Oznacza to, że po wywołaniu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody, implementacja zgodnym z przesłoniętą <xref:System.Windows.Media.Visual.HitTestCore%2A> jest wywoływana. Zastąpione metoda jest wywoływana, gdy hit test mieści się w prostokąt otaczający obiekt wizualny nawet wtedy, gdy współrzędnych znajduje się poza renderowanej zawartości obiekt wizualny.  
  
 [!code-csharp[HitTestingOverview#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Mogą wystąpić sytuacje, gdy zachodzi potrzeba trafień Testuj pod względem prostokąt otaczający i renderowanej zawartości obiekt wizualny. Za pomocą `PointHitTestParameters` wartość parametru w swojej zastąpione <xref:System.Windows.Media.Visual.HitTestCore%2A> metoda jako parametr do metody podstawowej <xref:System.Windows.Media.Visual.HitTestCore%2A>, można wykonywać działania dotyczące trafienie prostokąt otaczający obiekt wizualny, a następnie wykonaj drugi test trafień dla renderowania zawartości obiekt wizualny.  
  
 [!code-csharp[HitTestingOverview#108](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 <xref:System.Windows.Media.HitTestResult>  
 <xref:System.Windows.Media.HitTestResultCallback>  
 <xref:System.Windows.Media.HitTestFilterCallback>  
 <xref:System.Windows.UIElement.IsHitTestVisible%2A>  
 [Test trafienia przy użyciu przykładowych DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994)  
 [Hit Test przykład współdziałanie Win32](https://go.microsoft.com/fwlink/?LinkID=159995)  
 [Przeprowadzanie testu trafienia geometrii w wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)  
 [Przeprowadzanie testu trafienia za pomocą kontenera hosta Win32](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-a-win32-host-container.md)
