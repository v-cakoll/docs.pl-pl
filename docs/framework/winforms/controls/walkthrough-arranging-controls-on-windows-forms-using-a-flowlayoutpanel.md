---
title: Rozmieszczanie formantów przy użyciu FlowLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: 6df0a910ee346f319fbee835e5e632808630a99e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745402"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>Wskazówki: rozmieszczanie formantów w aplikacji formularzy systemu Windows za pomocą FlowLayoutPanel

Niektóre aplikacje wymagają formularza z układem, który zmienia się odpowiednio w miarę zmieniania rozmiaru formularza lub zmiany rozmiaru. Gdy potrzebujesz układu dynamicznego i nie chcesz obsłużyć <xref:System.Windows.Forms.Control.Layout> zdarzeń jawnie w kodzie, rozważ użycie panelu układu.

Kontrolka <xref:System.Windows.Forms.FlowLayoutPanel> i kontrolka <xref:System.Windows.Forms.TableLayoutPanel> umożliwiają intuicyjne sposoby rozmieszczenia formantów w formularzu. Obie umożliwiają automatyczną, konfigurowalną możliwość sterowania względnymi położeniami formantów podrzędnych zawartych w nich, a oba umożliwiają dynamiczne funkcje układu w czasie wykonywania, dzięki czemu można zmieniać rozmiar i zmienić położenie formantów podrzędnych jako wymiary formularza nadrzędnego. stąp. Panele układu mogą być zagnieżdżane w panelach układów, aby umożliwić realizację zaawansowanych interfejsów użytkownika.

<xref:System.Windows.Forms.TableLayoutPanel> rozmieszcza swoją zawartość w siatce, zapewniając funkcjonalność podobną do tabeli \<HTML > elementu. Jego komórki są ułożone w wiersze i kolumny, które mogą mieć różne rozmiary. Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

<xref:System.Windows.Forms.FlowLayoutPanel> rozmieszcza swoją zawartość w określonym kierunku przepływu: w poziomie lub w pionie. Jego zawartość może być opakowana z jednego wiersza do następnego lub z jednej kolumny na następną. Alternatywnie jego zawartość może być przycinana zamiast opakowana. Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie projektu Windows Forms

- Rozmieszczanie formantów w poziomie i w pionie

- Zmiana kierunku przepływu

- Wstawianie przerw w przepływie

- Rozmieszczanie formantów przy użyciu dopełnień i marginesów

- Wstawianie kontrolek przez dwukrotne kliknięcie ich w przyborniku

- Wstawianie kontrolki przez rysowanie jej konspektu

- Wstawianie kontrolek przy użyciu karetki

- Ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego

Po zakończeniu będzie można zrozumieć rolę odgrywaną przez te ważne funkcje układu.

## <a name="create-the-project"></a>Utwórz projekt

1. W programie Visual Studio Utwórz projekt aplikacji oparty na systemie Windows o nazwie "FlowLayoutPanelExample" **(plik** > **Nowy** > **Project** > **wizualizacji C#**  i **Visual Basic** > **klasycznego pulpitu** > Windows Forms **aplikacji**).

2. Wybierz formularz w **projektancie formularzy**.

## <a name="arranging-controls-horizontally-and-vertically"></a>Rozmieszczanie formantów w poziomie i w pionie
 Formant <xref:System.Windows.Forms.FlowLayoutPanel> umożliwia umieszczenie kontrolek w wierszach lub kolumnach bez konieczności precyzyjnego określania pozycji poszczególnych kontrolek.

 Formant <xref:System.Windows.Forms.FlowLayoutPanel> może zmieniać rozmiar lub przepływ swoich kontrolek podrzędnych w miarę zmiany wymiarów w formularzu nadrzędnym.

### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Aby rozmieścić kontrolki w poziomie i w pionie przy użyciu FlowLayoutPanel

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.FlowLayoutPanel> z **przybornika** na formularz.

2. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel>. Należy zauważyć, że jest on automatycznie przenoszony do lewego górnego rogu kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.

3. Przeciągnij inną kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel>. Należy zauważyć, że formant <xref:System.Windows.Forms.Button> jest automatycznie przenoszony do pozycji obok pierwszej kontrolki <xref:System.Windows.Forms.Button>. Jeśli <xref:System.Windows.Forms.FlowLayoutPanel> jest zbyt wąska, aby dopasować dwie kontrolki w tym samym wierszu, nowy formant <xref:System.Windows.Forms.Button> jest automatycznie przenoszony do następnego wiersza.

4. Przeciągnij kilka <xref:System.Windows.Forms.Button> kontrolek z **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel>. Kontynuuj umieszczanie <xref:System.Windows.Forms.Button> kontrolek do momentu, aż jeden przejdzie do następnego wiersza.

5. Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> na `false`. Należy zauważyć, że kontrolki podrzędne nie przepływają już do następnego wiersza. Zamiast tego są one przenoszone do pierwszego wiersza i obcinane.

6. Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> na `true`. Należy zauważyć, że formanty podrzędne są ponownie zawijane do następnego wiersza.

7. Zmniejsz szerokość kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> do momentu, aż wszystkie kontrolki <xref:System.Windows.Forms.Button> zostaną przeniesione do pierwszej kolumny.

8. Zwiększ szerokość kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> do momentu, aż wszystkie kontrolki <xref:System.Windows.Forms.Button> zostaną przeniesione do pierwszego wiersza. Może zajść potrzeba zmiany rozmiaru formularza w celu polepszenia szerokości.

## <a name="changing-flow-direction"></a>Zmiana kierunku przepływu
 Właściwość <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> pozwala zmienić kierunek rozmieszczenia formantów. Kontrolki podrzędne można rozmieścić od lewej do prawej, od prawej do lewej, od góry do dołu lub od dołu do góry.

### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>Aby zmienić kierunek przepływu w FlowLayoutPanel

1. Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> na <xref:System.Windows.Forms.FlowDirection.TopDown>. Należy zauważyć, że kontrolki podrzędne są zmieniane na co najmniej jedną kolumnę, w zależności od wysokości formantu.

2. Zmień rozmiar <xref:System.Windows.Forms.FlowLayoutPanel>, tak aby jego wysokość była krótsza niż kolumna formantów <xref:System.Windows.Forms.Button>. Należy zauważyć, że <xref:System.Windows.Forms.FlowLayoutPanel> zmienia rozmieszczenie formantów podrzędnych, aby przepływać do następnej kolumny. Kontynuuj zmniejszanie wysokości i Zauważ, że kontrolki podrzędne przepływają do kolejnych kolumn. Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> na <xref:System.Windows.Forms.FlowDirection.RightToLeft>. Należy zauważyć, że pozycje formantów podrzędnych są odwrócone. Obserwuj układ po zmianie wartości właściwości <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.BottomUp>.

## <a name="inserting-flow-breaks"></a>Wstawianie przerw w przepływie
 Formant <xref:System.Windows.Forms.FlowLayoutPanel> udostępnia Właściwość FlowBreak do jej formantów podrzędnych. Ustawienie wartości `true` właściwości FlowBreak powoduje zatrzymanie sterowania <xref:System.Windows.Forms.FlowLayoutPanel> formantu w bieżącym kierunku przepływu i przewinięcie do następnego wiersza lub kolumny.

### <a name="to-insert-flow-breaks"></a>Aby wstawić przerwy przepływu

1. Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> na <xref:System.Windows.Forms.FlowDirection.TopDown>.

2. Wybierz jedną z formantów <xref:System.Windows.Forms.Button> w środku kolumny z lewej strony.

3. Ustaw wartość właściwości FlowBreak formantu <xref:System.Windows.Forms.Button> na `true`. Zwróć uwagę, że kolumna jest uszkodzona i kontrolki po wybranym przepływie sterowania <xref:System.Windows.Forms.Button> do następnej kolumny. Ustaw wartość właściwości FlowBreak formantu <xref:System.Windows.Forms.Button> na `false`, aby powrócić do oryginalnego zachowania.

## <a name="positioning-controls-using-docking-and-anchoring"></a>Kontrolki pozycjonowania przy użyciu dokowania i zakotwiczania
 Zachowanie dokowania i zakotwiczenie formantów podrzędnych różni się od zachowań w innych kontrolkach kontenera. Zarówno dokowanie, jak i kotwicę są względem największego formantu w kierunku przepływu.

### <a name="to-position-controls-using-docking-and-anchoring"></a>Aby ustawić kontrolki przy użyciu dokowania i zakotwiczania

1. Zwiększ rozmiar <xref:System.Windows.Forms.FlowLayoutPanel> do momentu, aż kontrolki <xref:System.Windows.Forms.Button> są ułożone w kolumnie.

2. Wybierz górną kontrolkę <xref:System.Windows.Forms.Button>. Zwiększ jej szerokość tak, aby była ona znacznie tak szeroka jak inne kontrolki <xref:System.Windows.Forms.Button>.

3. Wybierz drugą kontrolkę <xref:System.Windows.Forms.Button>. Zmień wartość właściwości <xref:System.Windows.Forms.Control.Anchor%2A> na <xref:System.Windows.Forms.AnchorStyles.Right>. Należy zauważyć, że jest ona przenoszona tak, aby jej prawą krawędY była wyrównana do pierwszej krawędzi kontrolki <xref:System.Windows.Forms.Button>.

4. Zmień wartość właściwości <xref:System.Windows.Forms.Control.Anchor%2A> na <xref:System.Windows.Forms.AnchorStyles.Right> i <xref:System.Windows.Forms.AnchorStyles.Left>. Należy zauważyć, że rozmiar jest taki sam jak szerokość pierwszej kontrolki <xref:System.Windows.Forms.Button>.

5. Wybierz trzecią kontrolkę <xref:System.Windows.Forms.Button>. Zmień wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>. Należy zauważyć, że rozmiar jest taki sam jak szerokość pierwszej kontrolki <xref:System.Windows.Forms.Button>.

## <a name="arranging-controls-using-padding-and-margins"></a>Rozmieszczanie formantów przy użyciu dopełnień i marginesów
 Możesz również rozmieścić kontrolki w kontrolce <xref:System.Windows.Forms.FlowLayoutPanel>, zmieniając właściwości <xref:System.Windows.Forms.Control.Padding%2A> i <xref:System.Windows.Forms.Control.Margin%2A>.

 Właściwość <xref:System.Windows.Forms.Control.Padding%2A> pozwala kontrolować rozmieszczenie kontrolek w komórce kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>. Określa odstęp między kontrolkami podrzędnymi a obramowaniem <xref:System.Windows.Forms.FlowLayoutPanel> formantu.

 Właściwość <xref:System.Windows.Forms.Control.Margin%2A> pozwala kontrolować odstępy między kontrolkami.

### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Aby rozmieścić formanty przy użyciu właściwości wypełnienia i marginesu

1. Zmień wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> na <xref:System.Windows.Forms.DockStyle.Fill>. Jeśli formularz jest wystarczająco duży, formanty <xref:System.Windows.Forms.Button> zostaną przeniesione do pierwszej kolumny kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.

2. Zmień wartość właściwości <xref:System.Windows.Forms.Control.Padding%2A> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>, rozszerzając wpis <xref:System.Windows.Forms.Control.Padding%2A> w oknie **Właściwości** i ustawiając właściwość <xref:System.Windows.Forms.Padding.All%2A> na **20**. Aby uzyskać więcej informacji, zobacz [Przewodnik: układowanie formantów Windows Forms z uzupełnieniem, marginesami i właściwością AutoSize](windows-forms-controls-padding-autosize.md). Należy zauważyć, że kontrolki podrzędne są przenoszone do środka kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>. Zwiększona wartość właściwości <xref:System.Windows.Forms.Control.Padding%2A> powoduje wypchnięcie formantów podrzędnych z krawędzi kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.

3. Zaznacz wszystkie kontrolki <xref:System.Windows.Forms.Button> w <xref:System.Windows.Forms.FlowLayoutPanel> i ustaw wartość właściwości <xref:System.Windows.Forms.Control.Margin%2A> na **20**. Należy zauważyć, że odstępy między kontrolkami <xref:System.Windows.Forms.Button> są zwiększane, dzięki czemu są one przenoszone poza siebie. Może zajść potrzeba zmiany rozmiaru kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>, aby była większa, aby zobaczyć wszystkie kontrolki podrzędne.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Wstawianie kontrolek przez dwukrotne kliknięcie ich w przyborniku
 Aby wypełnić formant <xref:System.Windows.Forms.FlowLayoutPanel>, kliknij dwukrotnie pozycję kontrolki w **przyborniku**.

### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Aby wstawić kontrolki przez dwukrotne kliknięcie w przyborniku

1. Kliknij dwukrotnie ikonę kontrolki <xref:System.Windows.Forms.Button> w **przyborniku**. Należy zauważyć, że w kontrolce <xref:System.Windows.Forms.FlowLayoutPanel> pojawia się Nowa kontrolka <xref:System.Windows.Forms.Button>.

2. Kliknij dwukrotnie kilka kontrolek w **przyborniku**. Należy zauważyć, że nowe kontrolki pojawiają się kolejno w kontrolce <xref:System.Windows.Forms.FlowLayoutPanel>.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Wstawianie kontrolki przez rysowanie jej konspektu
 Można wstawić formant do kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> i określić jej rozmiar, rysując kontur w komórce.

### <a name="to-insert-a-control-by-drawing-its-outline"></a>Aby wstawić formant przez rysowanie jego konspektu

1. W **przyborniku**kliknij ikonę kontrolki <xref:System.Windows.Forms.Button>. Nie przeciągaj go na formularz.

2. Przesuń wskaźnik myszy nad formant <xref:System.Windows.Forms.FlowLayoutPanel>. Należy zauważyć, że wskaźnik zmieni się na krzyżyk z dołączoną ikoną <xref:System.Windows.Forms.Button>.

3. Kliknij i przytrzymaj przycisk myszy.

4. Przeciągnij wskaźnik myszy, aby narysować kontur kontrolki <xref:System.Windows.Forms.Button>. Gdy rozmiar jest zadowalający, zwolnij przycisk myszy. Należy zauważyć, że formant <xref:System.Windows.Forms.Button> jest tworzony w następnej otwartej lokalizacji kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.

## <a name="inserting-controls-using-the-insertion-bar"></a>Wstawianie kontrolek przy użyciu paska wstawiania
 Kontrolki można wstawiać w określonym położeniu w kontrolce <xref:System.Windows.Forms.FlowLayoutPanel>. Po przeciągnięciu kontrolki do obszaru klienckiego kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> zostanie wyświetlony pasek wstawiania wskazujący, gdzie kontrolka zostanie wstawiona.

### <a name="to-insert-a-control-using-the-caret"></a>Aby wstawić kontrolkę przy użyciu karetki

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** do kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> i wskaż odstęp między dwoma kontrolkami <xref:System.Windows.Forms.Button>. Należy zauważyć, że pasek wstawiania jest rysowany, wskazując, gdzie <xref:System.Windows.Forms.Button> zostanie umieszczony po upuszczeniu do kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>. Przed porzuceniem nowej kontrolki <xref:System.Windows.Forms.Button> w kontrolce <xref:System.Windows.Forms.FlowLayoutPanel> przesuń wskaźnik myszy, aby obserwować, jak przesuwa się pasek wstawiania.

2. Porzuć nową kontrolkę <xref:System.Windows.Forms.Button> w kontrolce <xref:System.Windows.Forms.FlowLayoutPanel>. Należy zauważyć, że nowy formant <xref:System.Windows.Forms.Button> nie jest wyrównany do innych, ponieważ jego właściwość <xref:System.Windows.Forms.Control.Margin%2A> ma inną wartość.

## <a name="reassigning-existing-controls-to-a-different-parent"></a>Ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego
 Do nowej kontrolki <xref:System.Windows.Forms.FlowLayoutPanel> można przypisać kontrolki, które istnieją w formularzu.

### <a name="to-reparent-existing-controls"></a>Aby zmienić nadrzędne kontrolki

1. Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz. Umieść je blisko siebie, ale pozostaw nie wyrównane.

2. W **przyborniku**kliknij ikonę kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>. Nie przeciągaj go na formularz.

3. Przesuń wskaźnik myszy blisko trzech formantów <xref:System.Windows.Forms.Button>. Należy zauważyć, że wskaźnik zmieni się na krzyżyk z dołączoną ikoną <xref:System.Windows.Forms.FlowLayoutPanel>.

4. Kliknij i przytrzymaj przycisk myszy.

5. Przeciągnij wskaźnik myszy, aby narysować kontur kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>. Narysuj kontur wokół trzech formantów <xref:System.Windows.Forms.Button>.

6. Zwolnij przycisk myszy. Należy zauważyć, że trzy kontrolki <xref:System.Windows.Forms.Button> są wstawiane do kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.

## <a name="next-steps"></a>Następne kroki
 Układ złożony można osiągnąć przy użyciu kombinacji paneli i kontrolek układu. Sugestie dotyczące większej eksploracji obejmują:

- Zmień rozmiar jednego z formantów <xref:System.Windows.Forms.Button> na większy rozmiar i zanotuj wpływ na układ.

- Panele układu mogą zawierać inne panele układu. Eksperymentuj z porzuceniem kontrolki <xref:System.Windows.Forms.TableLayoutPanel> do istniejącej kontrolki.

- Zadokuj formant <xref:System.Windows.Forms.FlowLayoutPanel> do formularza nadrzędnego. Zmień rozmiar formularza i zanotuj wpływ na układ.

- Ustaw właściwość <xref:System.Windows.Forms.Control.Visible%2A> jednej z kontrolek, aby `false` i zwrócić uwagę, jak <xref:System.Windows.Forms.FlowLayoutPanel> przepływy w odpowiedzi.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
- [Instrukcje: dokowanie kontrolek na formularzach Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Instrukcje: kotwiczenie kontrolek na formularzach Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize](windows-forms-controls-padding-autosize.md)
