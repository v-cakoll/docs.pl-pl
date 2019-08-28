---
title: Układ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: d4ea8d105b2d956323566a42108c7db3bfc4936d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046339"
---
# <a name="layout"></a>Układ

W tym temacie opisano system układu Windows Presentation Foundation (WPF). Zrozumienie, w jaki sposób i kiedy nastąpi Obliczanie układu, jest niezbędne do tworzenia interfejsów użytkownika w WPF.

Ten temat zawiera następujące sekcje:

- [Pola związane z elementem](#LayoutSystem_BoundingBox)

- [Układ układu](#LayoutSystem_Overview)

- [Mierzenie i rozmieszczanie elementów podrzędnych](#LayoutSystem_Measure_Arrange)

- [Elementy panelu i niestandardowe zachowania układu](#LayoutSystem_PanelsCustom)

- [Zagadnienia dotyczące wydajności układu](#LayoutSystem_Performance)

- [Renderowanie w pikselach i zaokrąglenie układu](#LayoutSystem_LayoutRounding)

- [Co dalej](#LayoutSystem_whatsnext)

<a name="LayoutSystem_BoundingBox"></a>

## <a name="element-bounding-boxes"></a>Pola związane z elementem

Gdy zastanawiasz się nad układem w WPF, ważne jest, aby zrozumieć pole ograniczenia otaczające wszystkie elementy. Każdy <xref:System.Windows.FrameworkElement> zużyty przez system układu może być uważany za prostokąt, który jest wbudowany w układ. <xref:System.Windows.Controls.Primitives.LayoutInformation> Klasa zwraca granice alokacji układu elementu lub gniazda. Rozmiar prostokąta jest określany przez obliczenie dostępnego miejsca na ekranie, rozmiaru wszelkich ograniczeń, właściwości specyficznych dla układu (takich jak margines i uzupełnienie) oraz indywidualnego zachowania elementu nadrzędnego <xref:System.Windows.Controls.Panel> . Przetwarzanie tych danych, system układu może obliczyć położenie wszystkich elementów podrzędnych określonego <xref:System.Windows.Controls.Panel>. Należy pamiętać, że cechy ustalania rozmiarów zdefiniowane w elemencie nadrzędnym, takie jak <xref:System.Windows.Controls.Border>, wpływają na jego elementy podrzędne.

Na poniższej ilustracji przedstawiono prosty układ.

![Zrzut ekranu pokazujący typową siatkę, bez nakładania się pól powiązanych.](./media/layout/grid-no-bounding-box-superimpose.png)

Ten układ można osiągnąć przy użyciu następującego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]polecenia.

[!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]

Pojedynczy <xref:System.Windows.Controls.TextBlock> element jest hostowany w obrębie elementu <xref:System.Windows.Controls.Grid>. Gdy tekst wypełnia tylko lewy górny róg pierwszej kolumny, przydzieloną przestrzeń dla <xref:System.Windows.Controls.TextBlock> jest w rzeczywistości znacznie większa. Obwiednię dowolnego <xref:System.Windows.FrameworkElement> elementu można pobrać przy <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> użyciu metody. Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.TextBlock> obwiednię elementu.

![Zrzut ekranu pokazujący, że pole powiązania TextBlock jest teraz widoczne.](./media/layout/visible-textblock-bounding-box.png)

Jak pokazano przez żółty prostokąt, przydzielone miejsce dla <xref:System.Windows.Controls.TextBlock> elementu jest w rzeczywistości znacznie większe od jego rozmiaru. Gdy dodatkowe elementy są dodawane do <xref:System.Windows.Controls.Grid>, ta Alokacja może zostać pomniejszana lub rozwinięta, w zależności od typu i rozmiaru dodawanych elementów.

Miejsce <xref:System.Windows.Controls.TextBlock> układu jest tłumaczone na obiekt <xref:System.Windows.Shapes.Path> przy użyciu <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metody. Ta technika może być przydatna do wyświetlania pola ograniczenia elementu.

[!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
[!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]

<a name="LayoutSystem_Overview"></a>

## <a name="the-layout-system"></a>Układ układu

W najprostszej układzie jest to system cykliczny, który prowadzi do elementu, który ma rozmiar, pozycjonowane i rysowane. Dokładniej mówiąc, układ opisuje proces mierzenia i rozmieszczania elementów członkowskich <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Panel.Children%2A> kolekcji elementu. Układ to czasochłonny proces. Im <xref:System.Windows.Controls.Panel.Children%2A> większa kolekcja, tym większa liczba obliczeń, które muszą zostać wykonane. Złożoność można także wprowadzić na podstawie zachowania układu zdefiniowanego przez <xref:System.Windows.Controls.Panel> element, który jest właścicielem kolekcji. Stosunkowo prosta <xref:System.Windows.Controls.Panel>, taka jak <xref:System.Windows.Controls.Canvas>, może znacznie zwiększyć wydajność niż <xref:System.Windows.Controls.Grid>bardziej skomplikowany <xref:System.Windows.Controls.Panel>, na przykład.

Za każdym razem, gdy <xref:System.Windows.UIElement> element podrzędny zmienia swoją pozycję, ma możliwość wyzwalania nowego przebiegu przez system układu. W związku z tym ważne jest, aby zrozumieć zdarzenia, które mogą wywołać system układu, ponieważ niepotrzebne wywołanie może prowadzić do słabej wydajności aplikacji. Poniżej opisano proces, który występuje podczas wywoływania systemu układu.

1. Element podrzędny <xref:System.Windows.UIElement> rozpoczyna proces układu po pierwszym zamierzeniu jego właściwości podstawowych.

2. Właściwości ustalania rozmiarów <xref:System.Windows.FrameworkElement> zdefiniowane na są oceniane, <xref:System.Windows.FrameworkElement.Width%2A>takie <xref:System.Windows.FrameworkElement.Height%2A>jak, <xref:System.Windows.FrameworkElement.Margin%2A>, i.

3. <xref:System.Windows.Controls.Panel>stosowana jest logika specyficzna, na <xref:System.Windows.Controls.Dock> przykład kierunek lub <xref:System.Windows.Controls.StackPanel.Orientation%2A>stos.

4. Zawartość jest uporządkowana po przejściu wszystkich elementów podrzędnych.

5. <xref:System.Windows.Controls.Panel.Children%2A> Kolekcja jest rysowana na ekranie.

6. Proces jest wywoływany ponownie w przypadku <xref:System.Windows.Controls.Panel.Children%2A> dodania dodatkowych do kolekcji <xref:System.Windows.FrameworkElement.LayoutTransform%2A> , <xref:System.Windows.UIElement.UpdateLayout%2A> zostanie zastosowany lub metoda jest wywoływana.

Ten proces i sposób jego wywoływania są zdefiniowane bardziej szczegółowo w poniższych sekcjach.

<a name="LayoutSystem_Measure_Arrange"></a>

## <a name="measuring-and-arranging-children"></a>Mierzenie i rozmieszczanie elementów podrzędnych

System układu wykonuje dwa przebiegi dla każdego elementu członkowskiego <xref:System.Windows.Controls.Panel.Children%2A> kolekcji, przebieg mierzy i przebieg uporządkowany. Każdy element <xref:System.Windows.Controls.Panel> podrzędny zapewnia własne <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody w celu osiągnięcia własnego zachowania określonego układu.

Podczas przebiegu miary są oceniane wszystkie składowe <xref:System.Windows.Controls.Panel.Children%2A> kolekcji. Proces rozpoczyna się od wywołania <xref:System.Windows.UIElement.Measure%2A> metody. Ta metoda jest wywoływana w ramach implementacji elementu nadrzędnego <xref:System.Windows.Controls.Panel> i nie musi być jawnie wywoływana do układu.

Najpierw <xref:System.Windows.UIElement> są oceniane właściwości rozmiaru natywnego, takie jak <xref:System.Windows.UIElement.Clip%2A> i <xref:System.Windows.UIElement.Visibility%2A>. Spowoduje to wygenerowanie wartości `constraintSize` o nazwie, która <xref:System.Windows.FrameworkElement.MeasureCore%2A>jest przenoszona do.

Na <xref:System.Windows.FrameworkElement> koniec`constraintSize`przetwarzane są właściwości Framework, które mają wpływ na wartość. Te właściwości zazwyczaj opisują charakterystykę wielkości bazowego <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement.Height%2A>na przykład, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Margin%2A>,, i <xref:System.Windows.FrameworkElement.Style%2A>. Każda z tych właściwości może zmienić miejsce, które jest niezbędne do wyświetlenia elementu. <xref:System.Windows.FrameworkElement.MeasureOverride%2A>jest następnie wywoływana za `constraintSize` pomocą jako parametru.

> [!NOTE]
> Istnieje różnica między <xref:System.Windows.FrameworkElement.Height%2A> właściwościami <xref:System.Windows.FrameworkElement.ActualHeight%2A> i <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.ActualWidth%2A>i. Na przykład <xref:System.Windows.FrameworkElement.ActualHeight%2A> właściwość jest wartością obliczaną na podstawie innych danych wejściowych wysokości i systemu układu. Wartość jest ustawiana przez system układu w oparciu o rzeczywiste przebieg renderingu i dlatego może być nieco opóźnione za ustawioną wartością właściwości, <xref:System.Windows.FrameworkElement.Height%2A>na przykład, które są podstawą zmiany danych wejściowych.
>
> Ponieważ <xref:System.Windows.FrameworkElement.ActualHeight%2A> jest wartością obliczaną, należy pamiętać, że może być wiele lub przyrostowo raportowane zmiany w tym wyniku różne operacje wykonywane przez system układu. System układu może obliczać wymaganą przestrzeń miary dla elementów podrzędnych, ograniczeń przez element nadrzędny i tak dalej.

Ostatecznym celem osiągnięcia miary jest określenie <xref:System.Windows.UIElement.DesiredSize%2A>, które występuje w <xref:System.Windows.FrameworkElement.MeasureCore%2A> trakcie wywołania. Wartość jest przechowywana przez <xref:System.Windows.UIElement.Measure%2A> program do użycia podczas przebiegu rozmieszczania zawartości. <xref:System.Windows.UIElement.DesiredSize%2A>

Przebieg porządkowania rozpoczyna się od wywołania <xref:System.Windows.UIElement.Arrange%2A> metody. W trakcie przebiegu porządkowania element nadrzędny <xref:System.Windows.Controls.Panel> generuje prostokąt, który reprezentuje granice elementu podrzędnego. Ta wartość jest przenoszona do <xref:System.Windows.FrameworkElement.ArrangeCore%2A> metody do przetwarzania.

<xref:System.Windows.FrameworkElement.ArrangeCore%2A> Metoda oblicza<xref:System.Windows.UIElement.DesiredSize%2A> wartość podrzędną i oblicza wszystkie dodatkowe marginesy, które mogą wpływać na wyrenderowany rozmiar elementu. <xref:System.Windows.FrameworkElement.ArrangeCore%2A>generuje, który jest przesyłany <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> do metody <xref:System.Windows.Controls.Panel> jako parametr. `arrangeSize` <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>`finalSize` generuje element podrzędny. Na <xref:System.Windows.FrameworkElement.ArrangeCore%2A> koniec Metoda wykonuje ostateczną ocenę właściwości przesunięcia, takich jak margines i wyrównanie, i umieszcza element podrzędny w obrębie swojego gniazda układu. Element podrzędny nie musi być (i często nie) wypełniać całego przydzielonych miejsc. Następnie formant jest zwracany do elementu nadrzędnego <xref:System.Windows.Controls.Panel> , a proces układu jest zakończony.

<a name="LayoutSystem_PanelsCustom"></a>

## <a name="panel-elements-and-custom-layout-behaviors"></a>Elementy panelu i niestandardowe zachowania układu

WPF obejmuje grupę elementów pochodzących od <xref:System.Windows.Controls.Panel>. Te <xref:System.Windows.Controls.Panel> elementy umożliwiają włączenie wielu złożonych układów. Na przykład elementy stosujące można łatwo osiągnąć przy użyciu <xref:System.Windows.Controls.StackPanel> elementu, a bardziej skomplikowane i swobodne układy przepływów są możliwe przy <xref:System.Windows.Controls.Canvas>użyciu.

Poniższa tabela zawiera podsumowanie dostępnych elementów układu <xref:System.Windows.Controls.Panel> .

|Nazwa panelu|Opis|
|----------------|-----------------|
|<xref:System.Windows.Controls.Canvas>|Definiuje obszar, w obrębie którego możesz jawnie pozycjonować elementy podrzędne według współrzędnych <xref:System.Windows.Controls.Canvas> względem obszaru.|
|<xref:System.Windows.Controls.DockPanel>|Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub w pionie względem siebie.|
|<xref:System.Windows.Controls.Grid>|Definiuje elastyczny obszar siatki składający się z kolumn i wierszy.|
|<xref:System.Windows.Controls.StackPanel>|Rozmieszcza elementy podrzędne w pojedynczym wierszu, który może być zorientowany w poziomie lub w pionie.|
|<xref:System.Windows.Controls.VirtualizingPanel>|Zapewnia strukturę dla elementów <xref:System.Windows.Controls.Panel> , które współużytkują ich podrzędną kolekcję danych. Jest to Klasa abstrakcyjna.|
|<xref:System.Windows.Controls.WrapPanel>|Położenie elementów podrzędnych w kolejności od lewej do prawej, przerwanie zawartości do następnego wiersza na krawędzi pola zawierającego. Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej, w zależności od wartości <xref:System.Windows.Controls.WrapPanel.Orientation%2A> właściwości.|

W przypadku aplikacji, które wymagają układu, który nie jest możliwy przy użyciu żadnego ze <xref:System.Windows.Controls.Panel> wstępnie zdefiniowanych elementów, niestandardowe zachowania układu można osiągnąć przez dziedziczenie <xref:System.Windows.Controls.Panel> z i zastępowanie <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metod i.

<a name="LayoutSystem_Performance"></a>

## <a name="layout-performance-considerations"></a>Zagadnienia dotyczące wydajności układu

Układ jest procesem cyklicznym. Każdy element podrzędny w kolekcji <xref:System.Windows.Controls.Panel.Children%2A> jest przetwarzany podczas każdego wywołania systemu układu. W związku z tym należy unikać uruchamiania systemu układu, gdy nie jest to konieczne. Poniższe zagadnienia mogą pomóc osiągnąć lepszą wydajność.

- Należy pamiętać, że zmiany wartości właściwości spowodują wymuszenie aktualizacji cyklicznej przez system układu.

  Właściwości zależności, których wartości mogą spowodować zainicjowanie systemu układu, są oznaczone flagami publicznymi. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>i <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> Podaj przydatne wskazówki dotyczące tego, które zmiany wartości właściwości spowodują wymuszenie aktualizacji cyklicznej przez system układu. Ogólnie rzecz biorąc, Każda właściwość, która może wpływać na rozmiar pola ograniczenia elementu, powinna mieć <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> flagę ustawioną na wartość true. Aby uzyskać więcej informacji, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).

- Gdy to możliwe, użyj <xref:System.Windows.UIElement.RenderTransform%2A> zamiast. <xref:System.Windows.FrameworkElement.LayoutTransform%2A>

  Może być bardzo użyteczny sposób, aby mieć wpływ na zawartość [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> Jeśli jednak efekt przekształcenia nie ma wpływu na położenie innych elementów, najlepiej jest użyć <xref:System.Windows.UIElement.RenderTransform%2A> zamiast tego, ponieważ <xref:System.Windows.UIElement.RenderTransform%2A> nie wywołuje systemu układu. <xref:System.Windows.FrameworkElement.LayoutTransform%2A>stosuje jego transformację i wymusza cykliczną aktualizację układu w celu uwzględnienia nowej pozycji elementu, którego dotyczy.

- Unikaj niepotrzebnych wywołań do programu <xref:System.Windows.UIElement.UpdateLayout%2A>.

  <xref:System.Windows.UIElement.UpdateLayout%2A> Metoda wymusza cykliczną aktualizację układu i często nie jest konieczna. Jeśli nie masz pewności, że wymagana jest pełna aktualizacja, polegaj na systemie układu do wywołania tej metody.

- Podczas pracy z dużą <xref:System.Windows.Controls.Panel.Children%2A> kolekcją warto rozważyć <xref:System.Windows.Controls.VirtualizingStackPanel> użycie zamiast regularnego <xref:System.Windows.Controls.StackPanel>.

  Dzięki wirtualizacji kolekcji podrzędnej program <xref:System.Windows.Controls.VirtualizingStackPanel> zachowuje tylko obiekty w pamięci, które znajdują się obecnie w okienku ekranu elementu nadrzędnego. W związku z tym wydajność jest znacznie ulepszona w większości scenariuszy.

<a name="LayoutSystem_LayoutRounding"></a>

## <a name="sub-pixel-rendering-and-layout-rounding"></a>Renderowanie w pikselach i zaokrąglenie układu

System grafiki WPF używa jednostek niezależnych od urządzenia, aby umożliwić Rozwiązywanie problemów i niezależność urządzeń. Każdy niezależny piksel urządzenia automatycznie skaluje się przy użyciu systemu kropek na cal (dpi). Zapewnia to aplikacjom WPF odpowiednie skalowanie dla różnych ustawień DPI i sprawia, że aplikacja automatycznie rozpoznaje wartość dpi.

Jednak ta niezależna wartość DPI może tworzyć nieregularne renderowanie krawędzi z powodu wygładzania. Te artefakty, zazwyczaj widziane jako rozmyte lub częściowo przezroczyste, mogą wystąpić, gdy lokalizacja krawędzi znajduje się w środku piksela urządzenia, a nie między pikselami urządzeń. Układ układu umożliwia dostosowanie tego elementu przy użyciu zaokrąglania układu. Zaokrąglanie układu polega na tym, że system układu zaokrągla wszystkie wartości niecałkowitych pikseli podczas przebiegu układu.

Zaokrąglanie układu jest domyślnie wyłączone. Aby włączyć zaokrąglenie układu, należy ustawić <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> `true` właściwość na wartość on <xref:System.Windows.FrameworkElement>. Ponieważ jest to właściwość zależności, wartość zostanie przepropagowana do wszystkich elementów podrzędnych w drzewie wizualnym. Aby włączyć zaokrąglenie układu dla całego interfejsu użytkownika, ustaw <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> wartość `true` na w kontenerze głównym. Aby zapoznać się z przykładem, zobacz <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>.

<a name="LayoutSystem_whatsnext"></a>

## <a name="whats-next"></a>Co dalej

Zrozumienie sposobu mierzenia i rozmieszczania elementów jest pierwszym krokiem w zrozumieniu układu. Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.Panel> dostępnych elementów, zobacz [Omówienie paneli](../controls/panels-overview.md). Aby lepiej zrozumieć różne właściwości pozycjonowania, które mogą mieć wpływ na układ, zobacz [wyrównanie, marginesy i](alignment-margins-and-padding-overview.md)dopełnienie. Gdy wszystko będzie gotowe do umieszczenia wszystkich w lekkiej aplikacji, zobacz [Przewodnik: Moja pierwsza aplikacja](../getting-started/walkthrough-my-first-wpf-desktop-application.md)klasyczna WPF.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [Panele — omówienie](../controls/panels-overview.md)
- [Przegląd wyrównania, marginesów i wypełnień](alignment-margins-and-padding-overview.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
