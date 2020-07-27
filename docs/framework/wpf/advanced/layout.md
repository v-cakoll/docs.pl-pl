---
title: Układ
description: Dowiedz się, jak i kiedy mają być wykonywane obliczenia układu w systemie Windows Presentation Foundation układu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: 0db3f2a6cbabc610362435d64de3fc970f01a73c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164771"
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

Gdy zastanawiasz się nad układem w WPF, ważne jest, aby zrozumieć pole ograniczenia otaczające wszystkie elementy. Każdy <xref:System.Windows.FrameworkElement> zużyty przez system układu może być uważany za prostokąt, który jest wbudowany w układ. <xref:System.Windows.Controls.Primitives.LayoutInformation>Klasa zwraca granice alokacji układu elementu lub gniazda. Rozmiar prostokąta jest określany przez obliczenie dostępnego miejsca na ekranie, rozmiaru wszelkich ograniczeń, właściwości specyficznych dla układu (takich jak margines i uzupełnienie) oraz indywidualnego zachowania <xref:System.Windows.Controls.Panel> elementu nadrzędnego. Przetwarzanie tych danych, system układu może obliczyć położenie wszystkich elementów podrzędnych określonego <xref:System.Windows.Controls.Panel> . Należy pamiętać, że cechy ustalania rozmiarów zdefiniowane w elemencie nadrzędnym, takie jak <xref:System.Windows.Controls.Border> , wpływają na jego elementy podrzędne.

Na poniższej ilustracji przedstawiono prosty układ.

![Zrzut ekranu pokazujący typową siatkę, bez nakładania się pól powiązanych.](./media/layout/grid-no-bounding-box-superimpose.png)

Ten układ można osiągnąć przy użyciu następującego polecenia [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

[!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]

Pojedynczy <xref:System.Windows.Controls.TextBlock> element jest hostowany w obrębie elementu <xref:System.Windows.Controls.Grid> . Gdy tekst wypełnia tylko lewy górny róg pierwszej kolumny, przydzieloną przestrzeń dla <xref:System.Windows.Controls.TextBlock> jest w rzeczywistości znacznie większa. Obwiednię dowolnego elementu <xref:System.Windows.FrameworkElement> można pobrać przy użyciu <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metody. Na poniższej ilustracji przedstawiono obwiednię <xref:System.Windows.Controls.TextBlock> elementu.

![Zrzut ekranu pokazujący, że pole powiązania TextBlock jest teraz widoczne.](./media/layout/visible-textblock-bounding-box.png)

Jak pokazano przez żółty prostokąt, przydzielone miejsce dla <xref:System.Windows.Controls.TextBlock> elementu jest w rzeczywistości znacznie większe od jego rozmiaru. Gdy dodatkowe elementy są dodawane do <xref:System.Windows.Controls.Grid> , ta Alokacja może zostać pomniejszana lub rozwinięta, w zależności od typu i rozmiaru dodawanych elementów.

Miejsce układu <xref:System.Windows.Controls.TextBlock> jest tłumaczone na obiekt przy <xref:System.Windows.Shapes.Path> użyciu <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metody. Ta technika może być przydatna do wyświetlania pola ograniczenia elementu.

[!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
[!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]

<a name="LayoutSystem_Overview"></a>

## <a name="the-layout-system"></a>Układ układu

W najprostszej układzie jest to system cykliczny, który prowadzi do elementu, który ma rozmiar, pozycjonowane i rysowane. Dokładniej mówiąc, układ opisuje proces mierzenia i rozmieszczania elementów członkowskich <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Panel.Children%2A> kolekcji elementu. Układ to czasochłonny proces. Im większa <xref:System.Windows.Controls.Panel.Children%2A> kolekcja, tym większa liczba obliczeń, które muszą zostać wykonane. Złożoność można także wprowadzić na podstawie zachowania układu zdefiniowanego przez <xref:System.Windows.Controls.Panel> element, który jest właścicielem kolekcji. Stosunkowo prosta <xref:System.Windows.Controls.Panel> , taka jak <xref:System.Windows.Controls.Canvas> , może znacznie zwiększyć wydajność niż bardziej skomplikowany, na przykład <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Grid> .

Za każdym razem, gdy element podrzędny <xref:System.Windows.UIElement> zmienia swoją pozycję, ma możliwość wyzwalania nowego przebiegu przez system układu. W związku z tym ważne jest, aby zrozumieć zdarzenia, które mogą wywołać system układu, ponieważ niepotrzebne wywołanie może prowadzić do słabej wydajności aplikacji. Poniżej opisano proces, który występuje podczas wywoływania systemu układu.

1. Element podrzędny <xref:System.Windows.UIElement> rozpoczyna proces układu po pierwszym zamierzeniu jego właściwości podstawowych.

2. Właściwości ustalania rozmiarów zdefiniowane na <xref:System.Windows.FrameworkElement> są oceniane, takie jak <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.FrameworkElement.Height%2A> , i <xref:System.Windows.FrameworkElement.Margin%2A> .

3. <xref:System.Windows.Controls.Panel>stosowana jest logika specyficzna, na przykład <xref:System.Windows.Controls.Dock> kierunek lub stos <xref:System.Windows.Controls.StackPanel.Orientation%2A> .

4. Zawartość jest uporządkowana po przejściu wszystkich elementów podrzędnych.

5. <xref:System.Windows.Controls.Panel.Children%2A>Kolekcja jest rysowana na ekranie.

6. Proces jest wywoływany ponownie w przypadku <xref:System.Windows.Controls.Panel.Children%2A> dodania dodatkowych do kolekcji, <xref:System.Windows.FrameworkElement.LayoutTransform%2A> zostanie zastosowany lub <xref:System.Windows.UIElement.UpdateLayout%2A> Metoda jest wywoływana.

Ten proces i sposób jego wywoływania są zdefiniowane bardziej szczegółowo w poniższych sekcjach.

<a name="LayoutSystem_Measure_Arrange"></a>

## <a name="measuring-and-arranging-children"></a>Mierzenie i rozmieszczanie elementów podrzędnych

System układu wykonuje dwa przebiegi dla każdego elementu członkowskiego <xref:System.Windows.Controls.Panel.Children%2A> kolekcji, przebieg mierzy i przebieg uporządkowany. Każdy element podrzędny <xref:System.Windows.Controls.Panel> zapewnia własne <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody w celu osiągnięcia własnego zachowania określonego układu.

Podczas przebiegu miary są oceniane wszystkie składowe <xref:System.Windows.Controls.Panel.Children%2A> kolekcji. Proces rozpoczyna się od wywołania <xref:System.Windows.UIElement.Measure%2A> metody. Ta metoda jest wywoływana w ramach implementacji <xref:System.Windows.Controls.Panel> elementu nadrzędnego i nie musi być jawnie wywoływana do układu.

Najpierw są oceniane właściwości rozmiaru natywnego <xref:System.Windows.UIElement> , takie jak <xref:System.Windows.UIElement.Clip%2A> i <xref:System.Windows.UIElement.Visibility%2A> . Spowoduje to wygenerowanie wartości o nazwie `constraintSize` , która jest przenoszona do <xref:System.Windows.FrameworkElement.MeasureCore%2A> .

Na <xref:System.Windows.FrameworkElement> koniec przetwarzane są właściwości Framework, które mają wpływ na wartość `constraintSize` . Te właściwości zazwyczaj opisują charakterystykę wielkości bazowego, na przykład,,, <xref:System.Windows.UIElement> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Margin%2A> i <xref:System.Windows.FrameworkElement.Style%2A> . Każda z tych właściwości może zmienić miejsce, które jest niezbędne do wyświetlenia elementu. <xref:System.Windows.FrameworkElement.MeasureOverride%2A>jest następnie wywoływana za pomocą `constraintSize` jako parametru.

> [!NOTE]
> Istnieje różnica między właściwościami <xref:System.Windows.FrameworkElement.Height%2A> i i <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> <xref:System.Windows.FrameworkElement.ActualWidth%2A> . Na przykład <xref:System.Windows.FrameworkElement.ActualHeight%2A> Właściwość jest wartością obliczaną na podstawie innych danych wejściowych wysokości i systemu układu. Wartość jest ustawiana przez system układu w oparciu o rzeczywiste przebieg renderingu i dlatego może być nieco opóźnione za ustawioną wartością właściwości, na przykład <xref:System.Windows.FrameworkElement.Height%2A> , które są podstawą zmiany danych wejściowych.
>
> Ponieważ <xref:System.Windows.FrameworkElement.ActualHeight%2A> jest wartością obliczaną, należy pamiętać, że może być wiele lub przyrostowo raportowane zmiany w tym wyniku różne operacje wykonywane przez system układu. System układu może obliczać wymaganą przestrzeń miary dla elementów podrzędnych, ograniczeń przez element nadrzędny i tak dalej.

Ostatecznym celem osiągnięcia miary jest określenie <xref:System.Windows.UIElement.DesiredSize%2A> , które występuje w trakcie <xref:System.Windows.FrameworkElement.MeasureCore%2A> wywołania. <xref:System.Windows.UIElement.DesiredSize%2A>Wartość jest przechowywana przez <xref:System.Windows.UIElement.Measure%2A> program do użycia podczas przebiegu rozmieszczania zawartości.

Przebieg porządkowania rozpoczyna się od wywołania <xref:System.Windows.UIElement.Arrange%2A> metody. W trakcie przebiegu porządkowania element nadrzędny <xref:System.Windows.Controls.Panel> generuje prostokąt, który reprezentuje granice elementu podrzędnego. Ta wartość jest przenoszona do <xref:System.Windows.FrameworkElement.ArrangeCore%2A> metody do przetwarzania.

<xref:System.Windows.FrameworkElement.ArrangeCore%2A>Metoda oblicza wartość <xref:System.Windows.UIElement.DesiredSize%2A> podrzędną i oblicza wszystkie dodatkowe marginesy, które mogą wpływać na wyrenderowany rozmiar elementu. <xref:System.Windows.FrameworkElement.ArrangeCore%2A>generuje `arrangeSize` , który jest przesyłany do <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody <xref:System.Windows.Controls.Panel> jako parametr. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>generuje `finalSize` element podrzędny. Na koniec <xref:System.Windows.FrameworkElement.ArrangeCore%2A> Metoda wykonuje ostateczną ocenę właściwości przesunięcia, takich jak margines i wyrównanie, i umieszcza element podrzędny w obrębie swojego gniazda układu. Element podrzędny nie musi być (i często nie) wypełniać całego przydzielonych miejsc. Następnie formant jest zwracany do elementu nadrzędnego <xref:System.Windows.Controls.Panel> , a proces układu jest zakończony.

<a name="LayoutSystem_PanelsCustom"></a>

## <a name="panel-elements-and-custom-layout-behaviors"></a>Elementy panelu i niestandardowe zachowania układu

WPF obejmuje grupę elementów pochodzących od <xref:System.Windows.Controls.Panel> . Te <xref:System.Windows.Controls.Panel> elementy umożliwiają włączenie wielu złożonych układów. Na przykład elementy stosujące można łatwo osiągnąć przy użyciu <xref:System.Windows.Controls.StackPanel> elementu, a bardziej skomplikowane i swobodne układy przepływów są możliwe przy użyciu <xref:System.Windows.Controls.Canvas> .

Poniższa tabela zawiera podsumowanie dostępnych elementów układu <xref:System.Windows.Controls.Panel> .

|Nazwa panelu|Opis|
|----------------|-----------------|
|<xref:System.Windows.Controls.Canvas>|Definiuje obszar, w obrębie którego możesz jawnie pozycjonować elementy podrzędne według współrzędnych względem <xref:System.Windows.Controls.Canvas> obszaru.|
|<xref:System.Windows.Controls.DockPanel>|Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub w pionie względem siebie.|
|<xref:System.Windows.Controls.Grid>|Definiuje elastyczny obszar siatki składający się z kolumn i wierszy.|
|<xref:System.Windows.Controls.StackPanel>|Rozmieszcza elementy podrzędne w pojedynczym wierszu, który może być zorientowany w poziomie lub w pionie.|
|<xref:System.Windows.Controls.VirtualizingPanel>|Zapewnia strukturę dla <xref:System.Windows.Controls.Panel> elementów, które współużytkują ich podrzędną kolekcję danych. Jest to Klasa abstrakcyjna.|
|<xref:System.Windows.Controls.WrapPanel>|Położenie elementów podrzędnych w kolejności od lewej do prawej, przerwanie zawartości do następnego wiersza na krawędzi pola zawierającego. Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej, w zależności od wartości <xref:System.Windows.Controls.WrapPanel.Orientation%2A> właściwości.|

W przypadku aplikacji, które wymagają układu, który nie jest możliwy przy użyciu żadnego ze wstępnie zdefiniowanych <xref:System.Windows.Controls.Panel> elementów, niestandardowe zachowania układu można osiągnąć przez dziedziczenie z <xref:System.Windows.Controls.Panel> i zastępowanie <xref:System.Windows.FrameworkElement.MeasureOverride%2A> <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metod i.

<a name="LayoutSystem_Performance"></a>

## <a name="layout-performance-considerations"></a>Zagadnienia dotyczące wydajności układu

Układ jest procesem cyklicznym. Każdy element podrzędny w <xref:System.Windows.Controls.Panel.Children%2A> kolekcji jest przetwarzany podczas każdego wywołania systemu układu. W związku z tym należy unikać uruchamiania systemu układu, gdy nie jest to konieczne. Poniższe zagadnienia mogą pomóc osiągnąć lepszą wydajność.

- Należy pamiętać, że zmiany wartości właściwości spowodują wymuszenie aktualizacji cyklicznej przez system układu.

  Właściwości zależności, których wartości mogą spowodować zainicjowanie systemu układu, są oznaczone flagami publicznymi. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>i <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> Podaj przydatne wskazówki dotyczące tego, które zmiany wartości właściwości spowodują wymuszenie aktualizacji cyklicznej przez system układu. Ogólnie rzecz biorąc, Każda właściwość, która może wpływać na rozmiar pola ograniczenia elementu, powinna mieć <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> flagę ustawioną na wartość true. Aby uzyskać więcej informacji, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).

- Gdy to możliwe, użyj <xref:System.Windows.UIElement.RenderTransform%2A> zamiast <xref:System.Windows.FrameworkElement.LayoutTransform%2A> .

  <xref:System.Windows.FrameworkElement.LayoutTransform%2A>Może być bardzo użyteczny sposób, aby mieć wpływ na zawartość [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . Jeśli jednak efekt przekształcenia nie ma wpływu na położenie innych elementów, najlepiej jest użyć <xref:System.Windows.UIElement.RenderTransform%2A> zamiast tego, ponieważ nie <xref:System.Windows.UIElement.RenderTransform%2A> wywołuje systemu układu. <xref:System.Windows.FrameworkElement.LayoutTransform%2A>stosuje jego transformację i wymusza cykliczną aktualizację układu w celu uwzględnienia nowej pozycji elementu, którego dotyczy.

- Unikaj niepotrzebnych wywołań do programu <xref:System.Windows.UIElement.UpdateLayout%2A> .

  <xref:System.Windows.UIElement.UpdateLayout%2A>Metoda wymusza cykliczną aktualizację układu i często nie jest konieczna. Jeśli nie masz pewności, że wymagana jest pełna aktualizacja, polegaj na systemie układu do wywołania tej metody.

- Podczas pracy z dużą <xref:System.Windows.Controls.Panel.Children%2A> kolekcją warto rozważyć użycie <xref:System.Windows.Controls.VirtualizingStackPanel> zamiast regularnego <xref:System.Windows.Controls.StackPanel> .

  Dzięki wirtualizacji kolekcji podrzędnej program <xref:System.Windows.Controls.VirtualizingStackPanel> zachowuje tylko obiekty w pamięci, które znajdują się obecnie w okienku ekranu elementu nadrzędnego. W związku z tym wydajność jest znacznie ulepszona w większości scenariuszy.

<a name="LayoutSystem_LayoutRounding"></a>

## <a name="sub-pixel-rendering-and-layout-rounding"></a>Renderowanie w pikselach i zaokrąglenie układu

System grafiki WPF używa jednostek niezależnych od urządzenia, aby umożliwić Rozwiązywanie problemów i niezależność urządzeń. Każdy niezależny piksel urządzenia automatycznie skaluje się przy użyciu systemu kropek na cal (dpi). Zapewnia to aplikacjom WPF odpowiednie skalowanie dla różnych ustawień DPI i sprawia, że aplikacja automatycznie rozpoznaje wartość dpi.

Jednak ta niezależna wartość DPI może tworzyć nieregularne renderowanie krawędzi z powodu wygładzania. Te artefakty, zazwyczaj widziane jako rozmyte lub częściowo przezroczyste, mogą wystąpić, gdy lokalizacja krawędzi znajduje się w środku piksela urządzenia, a nie między pikselami urządzeń. Układ układu umożliwia dostosowanie tego elementu przy użyciu zaokrąglania układu. Zaokrąglanie układu polega na tym, że system układu zaokrągla wszystkie wartości niecałkowitych pikseli podczas przebiegu układu.

Zaokrąglanie układu jest domyślnie wyłączone. Aby włączyć zaokrąglenie układu, należy ustawić <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> Właściwość `true` na wartość on <xref:System.Windows.FrameworkElement> . Ponieważ jest to właściwość zależności, wartość zostanie przepropagowana do wszystkich elementów podrzędnych w drzewie wizualnym. Aby włączyć zaokrąglenie układu dla całego interfejsu użytkownika, ustaw <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> wartość `true` na w kontenerze głównym. Aby zapoznać się z przykładem, zobacz <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> .

<a name="LayoutSystem_whatsnext"></a>

## <a name="whats-next"></a>Co dalej?

Zrozumienie sposobu mierzenia i rozmieszczania elementów jest pierwszym krokiem w zrozumieniu układu. Aby uzyskać więcej informacji na temat dostępnych <xref:System.Windows.Controls.Panel> elementów, zobacz [Omówienie paneli](../controls/panels-overview.md). Aby lepiej zrozumieć różne właściwości pozycjonowania, które mogą mieć wpływ na układ, zobacz [wyrównanie, marginesy i dopełnienie](alignment-margins-and-padding-overview.md). Gdy wszystko jest gotowe do umieszczenia w lekkiej aplikacji, zobacz [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [Przegląd Panele](../controls/panels-overview.md)
- [Przegląd Wyrównanie, marginesy i wypełnienia](alignment-margins-and-padding-overview.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
