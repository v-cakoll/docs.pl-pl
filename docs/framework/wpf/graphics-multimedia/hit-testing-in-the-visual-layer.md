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
ms.openlocfilehash: d4d304353e91147c57297dcc4525759ff1474b4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186404"
---
# <a name="hit-testing-in-the-visual-layer"></a>Test trafienia w warstwie Visual
W tym temacie przedstawiono omówienie funkcji testowania trafień udostępnianych przez warstwę wizualną. Obsługa testowania trafień umożliwia określenie, czy geometria lub wartość <xref:System.Windows.Media.Visual>punktu mieści się w renderowanej zawartości programu , co pozwala na zaimplementowanie zachowania interfejsu użytkownika, takiego jak prostokąt zaznaczenia, aby zaznaczyć wiele obiektów.  

<a name="hit_testing_scenarios"></a>
## <a name="hit-testing-scenarios"></a>Scenariusze testowania trafień  
 Klasa <xref:System.Windows.UIElement> zapewnia <xref:System.Windows.UIElement.InputHitTest%2A> metodę, która umożliwia trafienie test u elementu przy użyciu danej wartości współrzędnych. W wielu przypadkach <xref:System.Windows.UIElement.InputHitTest%2A> metoda zapewnia żądaną funkcjonalność do implementowania testowania trafień elementów. Istnieje jednak kilka scenariuszy, w których może być konieczne zaimplementowanie testowania trafień w warstwie wizualnej.  
  
- Testowanie trafień<xref:System.Windows.UIElement> przeciwko obiektom niebędącym obiektami:<xref:System.Windows.UIElement> ma to <xref:System.Windows.Media.DrawingVisual> zastosowanie w przypadku trafienia podczas testowania obiektów niebędących obiektami, takimi jak obiekty graficzne.  
  
- Testowanie trafień przy użyciu geometrii: Ma to zastosowanie, jeśli konieczne jest trafienie testu przy użyciu obiektu geometrii, a nie wartości współrzędnych punktu.  
  
- Testowanie trafień względem wielu obiektów: ma to zastosowanie, gdy trzeba trafić test na wiele obiektów, takich jak nakładające się obiekty. Można uzyskać wyniki dla wszystkich wizualizacji przecinających geometrię lub punkt, a nie tylko dla pierwszego.  
  
- Ignorowanie <xref:System.Windows.UIElement> zasad testowania trafień: ma to <xref:System.Windows.UIElement> zastosowanie, gdy trzeba zignorować zasady testowania trafień, która uwzględnia takie czynniki, jak to, czy element jest wyłączony, czy niewidoczny.  
  
> [!NOTE]
> Aby uzyskać pełny przykładowy kod ilustrujący testowanie trafień w warstwie wizualnej, zobacz [Hit Test using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual) and Hit Test with [Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).  
  
<a name="hit_testing_support"></a>
## <a name="hit-testing-support"></a>Pomoc techniczna w testowaniu trafień  
 Celem <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metod w <xref:System.Windows.Media.VisualTreeHelper> klasie jest określenie, czy wartość geometrii lub współrzędnych punktowych znajduje się w renderowanych zawartości danego obiektu, takich jak formant lub element graficzny. Na przykład można użyć testowania trafień, aby ustalić, czy kliknięcie myszą w obrębie prostokąta ograniczającego obiektu mieści się w geometrii okręgu. Można również zastąpić domyślną implementację testowania trafień, aby wykonać własne niestandardowe obliczenia testu trafień.  
  
 Na poniższej ilustracji przedstawiono relację między regionem obiektu niekularnego a jego prostokątnym prostokątem.  
  
 ![Diagram prawidłowego regionu testu trafień](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagram prawidłowego regionu testu trafień  
  
<a name="hit_testing_and_z-order"></a>
## <a name="hit-testing-and-z-order"></a>Testowanie trafień i zamówienie Z  
 Warstwa wizualna [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsługuje testowanie trafień względem wszystkich obiektów znajdujących się pod punktem lub geometrią, a nie tylko obiektów najwyższej klasy. Wyniki są zwracane w kolejności z. Jednak obiekt wizualny, który przekazujesz <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> jako parametr do metody określa, która część drzewa wizualnego, która zostanie trafiona test. Możesz trafić test na całe drzewo wizualne lub dowolną jego część.  
  
 Na poniższej ilustracji obiekt okręgu znajduje się zarówno na wierzchu obiektów kwadratowych, jak i trójkątnych. Jeśli jesteś zainteresowany tylko trafienie testowania obiektu wizualnego, którego wartość z-order jest najwyższa, <xref:System.Windows.Media.HitTestResultBehavior.Stop> można <xref:System.Windows.Media.HitTestResultCallback> ustawić wizualne wyliczenie testu trafienia, aby powrócić z, aby zatrzymać przechodzenie testu trafień po pierwszym elemencie.  
  
 ![Diagram kolejności&#45;z drzewa wizualnego](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagram kolejności z drzewa wizualnego  
  
 Jeśli chcesz wyliczyć wszystkie obiekty wizualne pod określonym <xref:System.Windows.Media.HitTestResultBehavior.Continue> punktem <xref:System.Windows.Media.HitTestResultCallback>lub geometrią, wróć z pliku . Oznacza to, że można trafić test dla obiektów wizualnych, które znajdują się pod innymi obiektami, nawet jeśli są one całkowicie zasłonięte. Zobacz przykładowy kod w sekcji "Korzystanie z wywołania zwrotnego wyników testu trafień", aby uzyskać więcej informacji.  
  
> [!NOTE]
> Obiekt wizualny, który jest przezroczysty może być również test trafienia.  
  
<a name="using_default_hit_testing"></a>
## <a name="using-default-hit-testing"></a>Korzystanie z domyślnego testowania trafień  
 Można określić, czy punkt znajduje się w geometrii <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> obiektu wizualnego, za pomocą metody, aby określić obiekt wizualny i wartość współrzędnych punktu do przetestowania. Parametr obiektu wizualnego identyfikuje punkt początkowy w drzewie wizualnym dla wyszukiwania testu trafień. Jeśli obiekt wizualny zostanie znaleziony w drzewie wizualnym, którego <xref:System.Windows.Media.HitTestResult.VisualHit%2A> geometria <xref:System.Windows.Media.HitTestResult> zawiera współrzędną, jest on ustawiony na właściwość obiektu. Następnie <xref:System.Windows.Media.HitTestResult> jest zwracany <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> z metody. Jeśli punkt nie jest zawarty w wizualnym poddrzewie, które trafisz, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> zwraca wartość `null`.  
  
> [!NOTE]
> Domyślne testowanie trafień zawsze zwraca najbardziej najlepszy obiekt w kolejności z. Aby zidentyfikować wszystkie obiekty wizualne, nawet te, które mogą być częściowo lub całkowicie zasłonięte, użyj wywołania zwrotnego wyniku testu trafień.  
  
 Wartość współrzędnych, którą <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> przekazujesz jako parametr punktowy dla metody, musi być względem przestrzeni współrzędnych obiektu wizualnego, przeciwko której trafisz test. Na przykład jeśli masz zagnieżdżone obiekty wizualne zdefiniowane w (100, 100) w przestrzeni współrzędnych nadrzędnego, a następnie trafienie testowania wizualizacji podrzędnej w (0, 0) jest równoznaczne z testowaniem trafień (100, 100) w przestrzeni współrzędnych rodzica.  
  
 Poniższy kod pokazuje, jak skonfigurować programy <xref:System.Windows.UIElement> obsługi zdarzeń myszy dla obiektu, który jest używany do przechwytywania zdarzeń używanych do testowania trafień.  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Jak drzewo wizualne wpływa na testowanie trafień  
 Punkt początkowy w drzewie wizualnym określa, które obiekty są zwracane podczas wyliczania obiektów testu trafień. Jeśli masz wiele obiektów, które chcesz trafić test, obiekt wizualny używany jako punkt początkowy w drzewie wizualnym musi być wspólnym elementem nadrzędnym wszystkich interesujących obiektów. Na przykład jeśli chcesz trafić testowania zarówno elementu przycisku i rysunku wizualnego na poniższym diagramie, trzeba ustawić punkt początkowy w drzewie wizualnym do wspólnego elementu nadrzędnego obu. W takim przypadku element płótna jest wspólnym elementem nadrzędnym zarówno elementu przycisku, jak i wizualizacji rysunku.  
  
 ![Diagram hierarchii drzewa wizualnego](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagram hierarchii drzewa wizualnego  
  
> [!NOTE]
> Właściwość <xref:System.Windows.UIElement.IsHitTestVisible%2A> pobiera lub ustawia wartość, <xref:System.Windows.UIElement>która deklaruje, czy obiekt pochodny może być ewentualnie zwrócony jako wynik testu trafień z pewnej części jego renderowanej zawartości. Dzięki temu można selektywnie zmienić drzewa wizualnego, aby określić, które obiekty wizualne są zaangażowane w test trafień.  
  
<a name="using_a_hit_test_result_callback"></a>
## <a name="using-a-hit-test-result-callback"></a>Korzystanie z wywołania zwrotnego wyniku testu trafień  
 Można wyliczyć wszystkie obiekty wizualne w drzewie wizualnym, którego geometria zawiera określoną wartość współrzędnych. Pozwala to zidentyfikować wszystkie obiekty wizualne, nawet te, które mogą być częściowo lub całkowicie zasłonięte przez inne obiekty wizualne. Aby wyliczyć obiekty wizualne w <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> drzewie wizualnym należy użyć metody z funkcją wywołania zwrotnego testu trafień. Funkcja wywołania zwrotnego testu trafień jest wywoływana przez system, gdy określona wartość współrzędnych znajduje się w obiekcie wizualnym.  
  
 Podczas wyliczania wyników testu trafienia nie należy wykonywać żadnej operacji, która modyfikuje drzewo wizualne. Dodawanie lub usuwanie obiektu z drzewa wizualnego podczas przechodzenia może spowodować nieprzewidywalne zachowanie. Można bezpiecznie zmodyfikować drzewa <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> wizualnego po zwraca metodę. Można podać strukturę danych, takich <xref:System.Collections.ArrayList>jak , do przechowywania wartości podczas wyliczenia wyników testu trafienia.  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 Metoda wywołania zwrotnego testu trafień definiuje akcje wykonywane po zidentyfikowaniu testu trafień na określonym obiekcie wizualnym w drzewie wizualnym. Po wykonaniu akcji zwracasz <xref:System.Windows.Media.HitTestResultBehavior> wartość, która określa, czy kontynuować wyliczanie innych obiektów wizualnych, czy nie.  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> Kolejność wyliczania trafień obiektów wizualnych jest według kolejności z. Obiekt wizualny na najwyższym poziomie z-order jest pierwszym obiektem wyliczonym. Wszystkie inne obiekty wizualne wyliczone są na malejącym poziomie z-order. Ta kolejność wyliczenia odpowiada kolejności renderowania wizualizacji.  
  
 Wyliczenie obiektów wizualnych można zatrzymać w dowolnym momencie w funkcji <xref:System.Windows.Media.HitTestResultBehavior.Stop>wywołania zwrotnego testu trafień, zwracając program .  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>
## <a name="using-a-hit-test-filter-callback"></a>Korzystanie z wywołania zwrotnego filtru testu trafień  
 Można użyć opcjonalnego filtru testu trafień, aby ograniczyć obiekty, które są przekazywane do wyników testu trafień. Dzięki temu można zignorować części drzewa wizualnego, które nie są zainteresowane przetwarzania w wynikach testu trafienia. Aby zaimplementować filtr testu trafień, należy zdefiniować funkcję wywołania zwrotnego filtru testu trafień i przekazać ją jako wartość parametru podczas wywoływania <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Jeśli nie chcesz podać opcjonalnefilmowanie filtru testu `null` trafienia wywołania <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> zwrotnego, przekazać wartość jako jego parametr dla metody.  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Przycinanie drzewa wizualnego przy użyciu filtru testu trafień](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Przycinanie drzewa wizualnego  
  
 Funkcja wywołania zwrotnego filtru testu trafień umożliwia wyliczenie wszystkich wizualizacji, których renderowana zawartość zawiera określone współrzędne. Jednak można zignorować niektóre gałęzie drzewa wizualnego, które nie są zainteresowane przetwarzaniem w wynikach trafień funkcji wywołania zwrotnego wyników. Zwracana wartość funkcji wywołania zwrotnego filtru testu trafień określa, jaki typ akcji należy podjąć wyliczanie obiektów wizualnych. Na przykład, jeśli zwrócisz <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>wartość, można usunąć bieżący obiekt wizualny i jego elementy podrzędne z wyliczenia wyników testu trafienia. Oznacza to, że wyniki testu trafienia wywołanie zwrotne funkcji nie zobaczy tych obiektów w jego wyliczenia. Przycinanie drzewa wizualnego obiektów zmniejsza ilość przetwarzania podczas przebiegu wyliczenia wyników testu trafień. W poniższym przykładzie kodu filtr pomija etykiety i ich elementy podrzędne i trafienia testuje wszystko inne.  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> Wywołanie zwrotne filtru testu trafień będzie czasami wywoływane w przypadkach, gdy wywołanie wywołania zwrotnego wyników testu trafień nie jest wywoływane.  
  
<a name="overriding_default_hit_testing"></a>
## <a name="overriding-default-hit-testing"></a>Zastępowanie domyślnego testowania trafień  
 Można zastąpić domyślną obsługę testowania trafień obiektu wizualnego, zastępując <xref:System.Windows.Media.Visual.HitTestCore%2A> metodę. Oznacza to, że podczas <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> wywoływania metody, implementacja zastąpiona <xref:System.Windows.Media.Visual.HitTestCore%2A> jest wywoływana. Zastąpiona metoda jest wywoływana, gdy test trafień mieści się w prostokątze ograniczającym obiektu wizualnego, nawet jeśli współrzędna wykracza poza renderowanej zawartości obiektu wizualnego.  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Może się okazać, że chcesz trafić test zarówno względem prostokąta ograniczającego, jak i renderowanej zawartości obiektu wizualnego. Za pomocą `PointHitTestParameters` wartości parametru w <xref:System.Windows.Media.Visual.HitTestCore%2A> zastąpiona metoda jako <xref:System.Windows.Media.Visual.HitTestCore%2A>parametr do metody podstawowej , można wykonać akcje na podstawie trafienia prostokąta ograniczającego obiektu wizualnego, a następnie wykonać drugi test trafień względem renderowanej zawartości obiektu wizualnego.  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [Test trafień przy użyciu przykładu DrawingVisuals](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)
- [Test trafień z próbką interoperacyjności Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [Przeprowadź test trafienia geometrii w Visual](how-to-hit-test-geometry-in-a-visual.md)
- [Przeprowadzanie testu trafienia za pomocą kontenera hosta Win32](how-to-hit-test-using-a-win32-host-container.md)
