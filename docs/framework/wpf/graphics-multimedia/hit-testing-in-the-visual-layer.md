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
ms.openlocfilehash: 92b7e8ffab001af4dba6c571fd06c64f2865b1e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962119"
---
# <a name="hit-testing-in-the-visual-layer"></a>Test trafienia w warstwie Visual
Ten temat zawiera omówienie funkcji testowania trafień zapewnianych przez warstwę wizualizacji. Obsługa testowania trafień pozwala określić, czy wartość geometrii lub punkt znajduje się w renderowanej zawartości a <xref:System.Windows.Media.Visual>, co pozwala na wdrożenie zachowań interfejsu użytkownika, takich jak prostokąt wyboru w celu zaznaczenia wielu obiektów.  

<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>Scenariusze testowania trafień  
 <xref:System.Windows.UIElement> Klasa<xref:System.Windows.UIElement.InputHitTest%2A> udostępnia metodę, która umożliwia trafienie testu względem elementu przy użyciu danej wartości współrzędnych. W wielu przypadkach <xref:System.Windows.UIElement.InputHitTest%2A> Metoda zapewnia odpowiednie funkcje do implementowania testowania trafień elementów. Istnieje jednak kilka scenariuszy, w których może być konieczne zaimplementowanie testowania trafień w warstwie wizualnej.  
  
- Testowanie trafień względem obiektów<xref:System.Windows.UIElement> nienależących do: Ma to zastosowanie, gdy trafisz test niebędący<xref:System.Windows.UIElement> obiektami, takimi jak <xref:System.Windows.Media.DrawingVisual> lub obiektami graficznymi.  
  
- Testowanie trafień przy użyciu geometrii: Ma to zastosowanie w przypadku konieczności testowania przy użyciu obiektu geometrycznego, a nie wartości współrzędnych punktu.  
  
- Testowanie trafień dla wielu obiektów: Ma to zastosowanie, gdy konieczne jest przetestowanie na wielu obiektach, takich jak nakładające się obiekty. Możesz uzyskać wyniki dla wszystkich wizualizacji przecinających geometrię lub punkt, a nie tylko pierwszej.  
  
- Ignorowanie zasad testowania trafień: <xref:System.Windows.UIElement> Ma to zastosowanie, gdy zachodzi potrzeba <xref:System.Windows.UIElement> ignorowania zasad testowania trafień, które uwzględniają takie czynniki jak to, czy element jest wyłączony czy niewidoczny.  
  
> [!NOTE]
> Aby uzyskać kompletny przykładowy kod ilustrujący testowanie trafień na warstwie wizualizacji, zobacz [test trafień przy użyciu przykładu DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994) i [test trafień z funkcją międzyoperacyjności Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>Obsługa testowania trafień  
 Celem <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metod<xref:System.Windows.Media.VisualTreeHelper> w klasie jest określenie, czy wartość współrzędnej geometrii lub punktu znajduje się w wyrenderowanej zawartości danego obiektu, takiej jak kontrolka lub element graficzny. Na przykład można użyć testowania trafień, aby określić, czy kliknięcie myszy w granicach prostokąta obiektu znajduje się w geometrii okręgu. Możesz również zastąpić domyślną implementację testowania trafień, aby wykonać własne niestandardowe obliczenia testów trafień.  
  
 Poniższa ilustracja przedstawia relację między regionem obiektu nieprostokątnego a jego prostokątem związanym.  
  
 ![Diagram prawidłowego regionu testu trafień](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagram prawidłowego regionu testu trafień  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>Testowanie trafień i porządek osi Z  
 Warstwa [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] wizualizacji obsługuje testowanie trafień dla wszystkich obiektów w ramach punktu lub geometrii, a nie tylko z najwyższego obiektu. Wyniki są zwracane w kolejności z. Jednak obiekt wizualizacji, który jest przekazywany jako parametr do <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody Określa, która część drzewa wizualnego ma zostać przetestowana. Test można trafić do całego drzewa wizualnego lub dowolnej jego części.  
  
 Na poniższej ilustracji obiekt Circle znajduje się na górze obydwu obiektów. Jeśli interesuje Cię tylko testowanie z trafieniem obiektu wizualizacji, którego wartość Order z jest największa, można ustawić Wyliczenie testów trafień wizualizacji, aby <xref:System.Windows.Media.HitTestResultBehavior.Stop> wrócić z <xref:System.Windows.Media.HitTestResultCallback> programu, aby zatrzymać przechodzenie testu trafień po pierwszym elemencie.  
  
 ![Diagram porządku osi z&#45;drzewa wizualnego](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagram porządku osi z drzewa wizualnego  
  
 Jeśli chcesz wyliczyć wszystkie obiekty wizualizacji w określonym punkcie lub geometrii, Wróć <xref:System.Windows.Media.HitTestResultBehavior.Continue> <xref:System.Windows.Media.HitTestResultCallback>z. Oznacza to, że można trafić test dla obiektów wizualnych, które znajdują się pod innymi obiektami, nawet jeśli są one całkowicie zasłonięte. Aby uzyskać więcej informacji, zobacz przykładowy kod w sekcji "Używanie Wyniki testów wywołania zwrotnego".  
  
> [!NOTE]
> Obiekt wizualny, który jest przezroczysty, może również być test trafień.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Używanie domyślnego testowania trafień  
 Można określić, czy punkt znajduje się w geometrii obiektu wizualizacji, przy użyciu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody, aby określić obiekt wizualizacji i wartość współrzędnych punktu do przetestowania. Parametr obiektu wizualnego identyfikuje punkt początkowy w drzewie wizualnym dla wyszukiwania testów trafień. Jeśli obiekt wizualny zostanie znaleziony w drzewie wizualnym, którego geometria zawiera współrzędną, jest ustawiona <xref:System.Windows.Media.HitTestResult.VisualHit%2A> na Właściwość <xref:System.Windows.Media.HitTestResult> obiektu. Następnie jest zwracany <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>zmetody. <xref:System.Windows.Media.HitTestResult> Jeśli punkt nie jest zawarty w poddrzewie wizualnym, które są testowane, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> zwraca. `null`  
  
> [!NOTE]
> Domyślne testowanie trafień zawsze zwraca najbardziej górny obiekt w kolejności z. Aby zidentyfikować wszystkie obiekty wizualizacji, nawet te, które mogą być częściowo lub w całości ukrywane, użyj wywołania zwrotnego wynik testu trafień.  
  
 Wartość współrzędnej, która jest przekazywany jako parametr punktu dla <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody, musi być względna względem przestrzeni współrzędnych obiektu wizualizacji, względem którego trafisz testowanie. Na przykład jeśli zagnieżdżonych obiektów wizualnych zdefiniowanych w (100, 100) w obszarze współrzędnych elementu nadrzędnego, trafij test wizualizacji podrzędnej (0, 0) jest odpowiednikiem testowania trafień (100, 100) w przestrzeni współrzędnych elementu nadrzędnego.  
  
 Poniższy kod pokazuje, jak skonfigurować programy obsługi zdarzeń myszy dla <xref:System.Windows.UIElement> obiektu, który jest używany do przechwytywania zdarzeń używanych do testowania trafień.  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Jak drzewo wizualne wpływa na testowanie trafień  
 Punkt początkowy w drzewie wizualnym określa, które obiekty są zwracane podczas wyliczania testów trafień. Jeśli masz wiele obiektów do przetestowania, obiekt wizualizacji używany jako punkt początkowy w drzewie wizualnym musi być wspólnym elementem nadrzędnym wszystkich interesujących Cię obiektów. Na przykład, jeśli interesują Cię trafienia w przypadku testowania elementu Button i wizualizacji na poniższym diagramie, należy ustawić punkt początkowy w drzewie wizualnym do wspólnego elementu nadrzędnego obu. W tym przypadku element kanwy jest wspólnym elementem nadrzędnym obu elementów Button i wizualizacji rysunku.  
  
 ![Diagram hierarchii drzewa wizualnego](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagram hierarchii drzewa wizualnego  
  
> [!NOTE]
> Właściwość pobiera lub ustawia wartość, która deklaruje, <xref:System.Windows.UIElement>czy obiekt pochodny może być zwracany jako wynik testu trafień z pewnej części zawartości renderowanej. <xref:System.Windows.UIElement.IsHitTestVisible%2A> Dzięki temu można wybiórczo zmienić drzewo wizualne, aby określić, które obiekty wizualne są uwzględnione w teście trafień.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Używanie wywołania zwrotnego wyniku testu trafień  
 Można wyliczyć wszystkie obiekty wizualizacji w drzewie wizualnym, których geometria zawiera określoną wartość współrzędnej. Pozwala to identyfikować wszystkie obiekty wizualizacji, nawet te, które mogą być częściowo lub w całości ukrywane przez inne obiekty wizualne. Aby wyliczyć obiekty wizualne w drzewie wizualnym, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> Użyj metody z funkcją wywołania zwrotnego testu trafień. Funkcja wywołania zwrotnego testu trafień jest wywoływana przez system, gdy określona wartość współrzędnej jest zawarta w obiekcie wizualnym.  
  
 Podczas wyliczania wyników testów trafień nie należy wykonywać żadnej operacji modyfikującej drzewo wizualne. Dodanie lub usunięcie obiektu z drzewa wizualnego podczas jego przechodzenia może spowodować nieprzewidywalne zachowanie. Można bezpiecznie modyfikować drzewo wizualne po <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> powrocie metody. Warto podać strukturę danych, taką jak <xref:System.Collections.ArrayList>,, aby przechowywać wartości podczas wyliczania wyników testu trafień.  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 Metoda wywołania zwrotnego testu trafień definiuje akcje wykonywane, gdy test trafień jest identyfikowany w określonym obiekcie wizualizacji w drzewie wizualnym. Po wykonaniu akcji zwracasz <xref:System.Windows.Media.HitTestResultBehavior> wartość określającą, czy kontynuować wyliczanie innych obiektów wizualnych, czy nie.  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> Kolejność wyliczania obiektów wizualnych trafień jest według kolejności z. Obiekt wizualizacji na poziomie najwyższego rzędu z jest pierwszym wyliczonym obiektem. Wszystkie inne obiekty wizualizacji są wyliczane na poziomie osi z. Ta kolejność wyliczania odpowiada kolejności renderowania wizualizacji.  
  
 Można zatrzymać Wyliczanie obiektów wizualnych w dowolnym momencie w funkcji wywołania zwrotnego testu trafień, <xref:System.Windows.Media.HitTestResultBehavior.Stop>zwracając wartość.  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Używanie wywołania zwrotnego filtru testów trafień  
 Można użyć opcjonalnego filtra testów trafień, aby ograniczyć obiekty, które są przesyłane do wyników testu trafień. Pozwala to na ignorowanie części drzewa wizualnego, które nie są zainteresowane przetwarzaniem w wynikach testu trafień. Aby zaimplementować filtr testów trafień, należy zdefiniować funkcję wywołania zwrotnego filtru testów trafień i przekazać ją jako wartość parametru podczas wywoływania <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Jeśli nie chcesz podawać opcjonalnej funkcji wywołania zwrotnego filtru testów trafień, Przekaż `null` wartość jako parametr <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Oczyszczanie drzewa wizualnego przy użyciu filtru testów trafień](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Oczyszczanie drzewa wizualnego  
  
 Funkcja wywołania zwrotnego filtru testów trafień umożliwia wyliczenie wszystkich wizualizacji, których renderowana zawartość zawiera określone współrzędne. Można jednak zignorować pewne gałęzie drzewa wizualnego, które nie są zainteresowane przetwarzaniem w funkcji wywołania zwrotnego wyników testu trafień. Wartość zwracana funkcji wywołania zwrotnego filtru testów trafień określa typ akcji, która ma być Wyliczenie obiektów wizualnych. Na przykład, jeśli zwracasz wartość, <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>możesz usunąć bieżący obiekt wizualny i jego elementy podrzędne z wyliczenia wyników testów trafień. Oznacza to, że funkcja wywołania zwrotnego wyników testów trafień nie będzie widziała tych obiektów w jego wyliczeniu. Oczyszczanie drzewa wizualnego obiektów zmniejsza ilość przetwarzania w czasie wykonywania wyliczenia wyników testu trafień. W poniższym przykładzie kodu filtr pomija etykiety i ich elementy podrzędne i trafi wszystkie pozostałe.  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> Wywołanie zwrotne filtru testów trafień będzie czasami wywoływane w przypadkach, gdy wywołanie zwrotne wyników testu trafień nie jest wywoływane.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Zastępowanie domyślnych testów trafień  
 Można zastąpić domyślną obsługę testowania trafień obiektu wizualnego, zastępując <xref:System.Windows.Media.Visual.HitTestCore%2A> metodę. Oznacza to, że po wywołaniu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody, zastąpiona <xref:System.Windows.Media.Visual.HitTestCore%2A> implementacja jest wywoływana. Zastąpiona metoda jest wywoływana, gdy test trafień znajduje się w granicach obiektu wizualizacji, nawet jeśli Współrzędna znajduje się poza renderowaną zawartością obiektu wizualnego.  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Mogą wystąpić sytuacje, w których chcesz trafić test względem prostokąta ograniczenia i renderowanej zawartości obiektu wizualnego. Używając `PointHitTestParameters` wartości parametru w zastąpionej <xref:System.Windows.Media.Visual.HitTestCore%2A> metodzie jako parametru do metody <xref:System.Windows.Media.Visual.HitTestCore%2A>bazowej, można wykonywać akcje na podstawie trafień prostokąta granicy obiektu wizualizacji, a następnie wykonać drugi test trafień względem renderowana zawartość obiektu wizualnego.  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [Test trafień za pomocą przykładu DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994)
- [Test trafień z próbką międzyoperacyjną Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Przeprowadzanie testu trafienia geometrii w wizualizacji](how-to-hit-test-geometry-in-a-visual.md)
- [Przeprowadzanie testu trafienia za pomocą kontenera hosta Win32](how-to-hit-test-using-a-win32-host-container.md)
