---
title: Rozmieszczanie formantów przy użyciu FlowLayoutPanel
description: Dowiedz się, jak za pomocą kontrolki FlowLayoutPanel i formantu TableLayoutPanel zapewnić intuicyjne sposoby rozmieszczenia formantów w projekcie Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: efcb38275be7b0cf94afb6b68aa139876f7cf5fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619289"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>Wskazówki: rozmieszczanie formantów w aplikacji formularzy systemu Windows za pomocą FlowLayoutPanel

Niektóre aplikacje wymagają formularza z układem, który zmienia się odpowiednio w miarę zmieniania rozmiaru formularza lub zmiany rozmiaru. Gdy potrzebujesz układu dynamicznego i nie chcesz obsłużyć <xref:System.Windows.Forms.Control.Layout> zdarzeń jawnie w kodzie, rozważ użycie panelu układu.

<xref:System.Windows.Forms.FlowLayoutPanel>Formant i <xref:System.Windows.Forms.TableLayoutPanel> formant zapewniają intuicyjne sposoby rozmieszczenia formantów w formularzu. Obie umożliwiają automatyczną, konfigurowalną możliwość sterowania względnymi położeniami formantów podrzędnych zawartych w nich, a oba umożliwiają dynamiczne funkcje układu w czasie wykonywania, dzięki czemu można zmieniać rozmiar i zmienić położenie formantów podrzędnych w miarę zmiany wymiarów formularza nadrzędnego. Panele układu mogą być zagnieżdżane w panelach układów, aby umożliwić realizację zaawansowanych interfejsów użytkownika.

<xref:System.Windows.Forms.TableLayoutPanel>Rozmieszcza swoją zawartość w siatce, dostarczając funkcje podobne do \<table> elementu HTML. Jego komórki są ułożone w wiersze i kolumny, które mogą mieć różne rozmiary. Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

<xref:System.Windows.Forms.FlowLayoutPanel>Rozmieszcza zawartość w określonym kierunku przepływu: w poziomie lub w pionie. Jego zawartość może być opakowana z jednego wiersza do następnego lub z jednej kolumny na następną. Alternatywnie jego zawartość może być przycinana zamiast opakowana. Zadania przedstawione w tym instruktażu obejmują:

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

## <a name="create-the-project"></a>Tworzenie projektu

1. W programie Visual Studio Utwórz projekt aplikacji oparty na systemie Windows o nazwie "FlowLayoutPanelExample" (**plik**  >  **New**  >  **Project**  >  **Visual C#** lub **Visual Basic**  >  **klasycznej**  >  **aplikacji Windows Forms**Desktop).

2. Wybierz formularz w **projektancie formularzy**.

## <a name="arranging-controls-horizontally-and-vertically"></a>Rozmieszczanie formantów w poziomie i w pionie
 <xref:System.Windows.Forms.FlowLayoutPanel>Kontrolka umożliwia umieszczanie kontrolek w wierszach lub kolumnach bez konieczności precyzyjnego określania pozycji poszczególnych kontrolek.

 <xref:System.Windows.Forms.FlowLayoutPanel>Kontrolka może zmieniać rozmiar lub przepływ swoich kontrolek podrzędnych w miarę zmiany wymiarów w formularzu nadrzędnym.

### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Aby rozmieścić kontrolki w poziomie i w pionie przy użyciu FlowLayoutPanel

1. Przeciągnij <xref:System.Windows.Forms.FlowLayoutPanel> kontrolkę z **przybornika** do formularza.

2. Przeciągnij <xref:System.Windows.Forms.Button> kontrolkę z **przybornika** do elementu <xref:System.Windows.Forms.FlowLayoutPanel> . Należy zauważyć, że jest on automatycznie przenoszony do lewego górnego rogu <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki.

3. Przeciągnij inny <xref:System.Windows.Forms.Button> formant z **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel> . Należy zauważyć, że <xref:System.Windows.Forms.Button> formant jest automatycznie przenoszony do pozycji obok pierwszej <xref:System.Windows.Forms.Button> kontrolki. Jeśli <xref:System.Windows.Forms.FlowLayoutPanel> wartość jest zbyt wąska, aby dopasować dwie kontrolki w tym samym wierszu, nowy <xref:System.Windows.Forms.Button> formant jest automatycznie przenoszony do następnego wiersza.

4. Przeciągnij kilka więcej <xref:System.Windows.Forms.Button> kontrolek z **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel> . Kontynuuj umieszczanie <xref:System.Windows.Forms.Button> kontrolek do momentu, gdy jeden przejdzie do następnego wiersza.

5. Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> właściwości kontrolki <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> na `false` . Należy zauważyć, że kontrolki podrzędne nie przepływają już do następnego wiersza. Zamiast tego są one przenoszone do pierwszego wiersza i obcinane.

6. Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> właściwości kontrolki <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> na `true` . Należy zauważyć, że formanty podrzędne są ponownie zawijane do następnego wiersza.

7. Zmniejsz szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki do momentu <xref:System.Windows.Forms.Button> przesunięcia wszystkich formantów do pierwszej kolumny.

8. Zwiększ szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki do momentu <xref:System.Windows.Forms.Button> przesunięcia wszystkich formantów do pierwszego wiersza. Może zajść potrzeba zmiany rozmiaru formularza w celu polepszenia szerokości.

## <a name="changing-flow-direction"></a>Zmiana kierunku przepływu
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>Właściwość pozwala zmienić kierunek rozmieszczenia kontrolek. Kontrolki podrzędne można rozmieścić od lewej do prawej, od prawej do lewej, od góry do dołu lub od dołu do góry.

### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>Aby zmienić kierunek przepływu w FlowLayoutPanel

1. Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> właściwości kontrolki <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.TopDown> . Należy zauważyć, że kontrolki podrzędne są zmieniane na co najmniej jedną kolumnę, w zależności od wysokości formantu.

2. Zmień rozmiar <xref:System.Windows.Forms.FlowLayoutPanel> tak, aby wysokość była krótsza niż kolumna <xref:System.Windows.Forms.Button> kontrolek. Należy zauważyć, że <xref:System.Windows.Forms.FlowLayoutPanel> Reorganizuje kontrolki podrzędne do przepływu w następnej kolumnie. Kontynuuj zmniejszanie wysokości i Zauważ, że kontrolki podrzędne przepływają do kolejnych kolumn. Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> właściwości kontrolki <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.RightToLeft> . Należy zauważyć, że pozycje formantów podrzędnych są odwrócone. Obserwuj układ, gdy zmienisz wartość <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwości na <xref:System.Windows.Forms.FlowDirection.BottomUp> .

## <a name="inserting-flow-breaks"></a>Wstawianie przerw w przepływie
 <xref:System.Windows.Forms.FlowLayoutPanel>Kontrolka udostępnia Właściwość FlowBreak do jej formantów podrzędnych. Ustawienie wartości właściwości FlowBreak `true` powoduje <xref:System.Windows.Forms.FlowLayoutPanel> zatrzymanie przez formant układu formantów w bieżącym kierunku przepływu i przewinięcie do następnego wiersza lub kolumny.

### <a name="to-insert-flow-breaks"></a>Aby wstawić przerwy przepływu

1. Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> właściwości kontrolki <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.TopDown> .

2. Wybierz jedną z <xref:System.Windows.Forms.Button> kontrolek w środku kolumny z lewej strony.

3. Ustaw wartość <xref:System.Windows.Forms.Button> właściwości FlowBreak kontrolki na `true` . Zwróć uwagę, że kolumna jest uszkodzona i kontrolki po wybranym <xref:System.Windows.Forms.Button> przepływie sterowania do następnej kolumny. Ustaw wartość <xref:System.Windows.Forms.Button> właściwości FlowBreak kontrolki na `false` , aby powrócić do oryginalnego zachowania.

## <a name="positioning-controls-using-docking-and-anchoring"></a>Kontrolki pozycjonowania przy użyciu dokowania i zakotwiczania
 Zachowanie dokowania i zakotwiczenie formantów podrzędnych różni się od zachowań w innych kontrolkach kontenera. Zarówno dokowanie, jak i kotwicę są względem największego formantu w kierunku przepływu.

### <a name="to-position-controls-using-docking-and-anchoring"></a>Aby ustawić kontrolki przy użyciu dokowania i zakotwiczania

1. Zwiększenie rozmiaru <xref:System.Windows.Forms.FlowLayoutPanel> do momentu, aż <xref:System.Windows.Forms.Button> wszystkie kontrolki są rozmieszczone w kolumnie.

2. Wybierz górną <xref:System.Windows.Forms.Button> kontrolkę. Zwiększ jej szerokość tak, aby była ona bardzo podwójnie taka sama jak w przypadku innych <xref:System.Windows.Forms.Button> kontrolek.

3. Wybierz drugą <xref:System.Windows.Forms.Button> kontrolkę. Zmień wartość <xref:System.Windows.Forms.Control.Anchor%2A> właściwości na <xref:System.Windows.Forms.AnchorStyles.Right> . Należy zauważyć, że jest ona przenoszona tak, aby jej prawą krawędY była wyrównana do <xref:System.Windows.Forms.Button> prawej krawędzi pierwszej kontrolki.

4. Zmień wartość <xref:System.Windows.Forms.Control.Anchor%2A> właściwości na <xref:System.Windows.Forms.AnchorStyles.Right> i <xref:System.Windows.Forms.AnchorStyles.Left> . Należy pamiętać, że ma ona taką samą szerokość jak pierwszy <xref:System.Windows.Forms.Button> formant.

5. Wybierz trzeci <xref:System.Windows.Forms.Button> formant. Zmień wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwości na <xref:System.Windows.Forms.DockStyle.Fill> . Należy pamiętać, że ma ona taką samą szerokość jak pierwszy <xref:System.Windows.Forms.Button> formant.

## <a name="arranging-controls-using-padding-and-margins"></a>Rozmieszczanie formantów przy użyciu dopełnień i marginesów
 Możesz również rozmieścić kontrolki w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce, zmieniając <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Margin%2A> właściwości i.

 <xref:System.Windows.Forms.Control.Padding%2A>Właściwość pozwala kontrolować rozmieszczenie kontrolek w <xref:System.Windows.Forms.FlowLayoutPanel> komórce kontrolki. Określa odstęp między kontrolkami podrzędnymi a <xref:System.Windows.Forms.FlowLayoutPanel> obramowaniem kontrolki.

 <xref:System.Windows.Forms.Control.Margin%2A>Właściwość pozwala kontrolować odstępy między kontrolkami.

### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Aby rozmieścić formanty przy użyciu właściwości wypełnienia i marginesu

1. Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> właściwości kontrolki <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill> . Jeśli formularz jest wystarczająco duży, <xref:System.Windows.Forms.Button> formanty zostaną przeniesione do pierwszej kolumny <xref:System.Windows.Forms.FlowLayoutPanel> formantu.

2. Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> właściwości kontrolki <xref:System.Windows.Forms.Control.Padding%2A> , rozszerzając <xref:System.Windows.Forms.Control.Padding%2A> wpis w oknie **Właściwości** i ustawiając <xref:System.Windows.Forms.Padding.All%2A> Właściwość na **20**. Aby uzyskać więcej informacji, zobacz [Przewodnik: układowanie formantów Windows Forms z uzupełnieniem, marginesami i właściwością AutoSize](windows-forms-controls-padding-autosize.md). Należy zauważyć, że formanty podrzędne są przenoszone do środka <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki. Zwiększona wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwości powoduje wypchnięcie formantów podrzędnych z <xref:System.Windows.Forms.FlowLayoutPanel> obramowania kontrolki.

3. Zaznacz wszystkie <xref:System.Windows.Forms.Button> kontrolki w <xref:System.Windows.Forms.FlowLayoutPanel> i ustaw wartość <xref:System.Windows.Forms.Control.Margin%2A> właściwości na **20**. Należy zauważyć, że odstępy między <xref:System.Windows.Forms.Button> kontrolkami rosną, więc są one dalej przenoszone. Może być konieczna zmiana rozmiaru <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki, aby wyświetlić wszystkie kontrolki podrzędne.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Wstawianie kontrolek przez dwukrotne kliknięcie ich w przyborniku
 Kontrolkę można wypełnić <xref:System.Windows.Forms.FlowLayoutPanel> przez dwukrotne kliknięcie formantów w **przyborniku**.

### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Aby wstawić kontrolki przez dwukrotne kliknięcie w przyborniku

1. Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę kontrolki w **przyborniku**. Zauważ, że <xref:System.Windows.Forms.Button> w kontrolce pojawia się Nowa kontrolka <xref:System.Windows.Forms.FlowLayoutPanel> .

2. Kliknij dwukrotnie kilka kontrolek w **przyborniku**. Należy zauważyć, że nowe kontrolki pojawiają się kolejno w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Wstawianie kontrolki przez rysowanie jej konspektu
 Można wstawić kontrolkę do <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki i określić jej rozmiar, rysując jej kontur w komórce.

### <a name="to-insert-a-control-by-drawing-its-outline"></a>Aby wstawić formant przez rysowanie jego konspektu

1. W **przyborniku**kliknij <xref:System.Windows.Forms.Button> ikonę kontrolki. Nie przeciągaj go na formularz.

2. Przesuń wskaźnik myszy nad <xref:System.Windows.Forms.FlowLayoutPanel> kontrolkę. Zwróć uwagę, że wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.Button> dołączoną ikoną kontrolki.

3. Kliknij i przytrzymaj przycisk myszy.

4. Przeciągnij wskaźnik myszy, aby narysować kontur <xref:System.Windows.Forms.Button> formantu. Gdy rozmiar jest zadowalający, zwolnij przycisk myszy. Należy zauważyć, że <xref:System.Windows.Forms.Button> formant jest tworzony w następnej otwartej lokalizacji <xref:System.Windows.Forms.FlowLayoutPanel> formantu.

## <a name="inserting-controls-using-the-insertion-bar"></a>Wstawianie kontrolek przy użyciu paska wstawiania
 Kontrolki można wstawiać w konkretnym miejscu <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki. Gdy przeciągasz formant do <xref:System.Windows.Forms.FlowLayoutPanel> obszaru klienckiego kontrolki, pojawi się pasek wstawiania wskazujący, gdzie formant zostanie wstawiony.

### <a name="to-insert-a-control-using-the-caret"></a>Aby wstawić kontrolkę przy użyciu karetki

1. Przeciągnij <xref:System.Windows.Forms.Button> kontrolkę z **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki i wskaż miejsce między dwoma <xref:System.Windows.Forms.Button> kontrolkami. Należy zauważyć, że pasek wstawiania jest rysowany, wskazując, gdzie <xref:System.Windows.Forms.Button> zostanie umieszczony po upuszczeniu do <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki. Przed porzuceniem nowej <xref:System.Windows.Forms.Button> kontrolki w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce przesuń wskaźnik myszy, aby obserwować, jak przesuwa się pasek wstawiania.

2. Upuść nową <xref:System.Windows.Forms.Button> kontrolkę do <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki. Należy zauważyć, że nowy <xref:System.Windows.Forms.Button> formant nie jest wyrównany do innych, ponieważ jego <xref:System.Windows.Forms.Control.Margin%2A> Właściwość ma inną wartość.

## <a name="reassigning-existing-controls-to-a-different-parent"></a>Ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego
 Kontrolki, które istnieją w formularzu, można przypisać do nowej <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki.

### <a name="to-reparent-existing-controls"></a>Aby zmienić nadrzędne kontrolki

1. Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz. Umieść je blisko siebie, ale pozostaw nie wyrównane.

2. W **przyborniku**kliknij <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki. Nie przeciągaj go na formularz.

3. Przesuń wskaźnik myszy blisko trzech <xref:System.Windows.Forms.Button> kontrolek. Zwróć uwagę, że wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> dołączoną ikoną kontrolki.

4. Kliknij i przytrzymaj przycisk myszy.

5. Przeciągnij wskaźnik myszy, aby narysować kontur <xref:System.Windows.Forms.FlowLayoutPanel> formantu. Narysuj kontur wokół trzech <xref:System.Windows.Forms.Button> kontrolek.

6. Zwolnij przycisk myszy. Należy zauważyć, że trzy <xref:System.Windows.Forms.Button> kontrolki są wstawiane do <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki.

## <a name="next-steps"></a>Następne kroki
 Układ złożony można osiągnąć przy użyciu kombinacji paneli i kontrolek układu. Sugestie dotyczące większej eksploracji obejmują:

- Zmień rozmiar jednego z <xref:System.Windows.Forms.Button> formantów na większy rozmiar i zanotuj wpływ na układ.

- Panele układu mogą zawierać inne panele układu. Eksperymentuj z porzuceniem <xref:System.Windows.Forms.TableLayoutPanel> kontrolki do istniejącej kontrolki.

- Zadokuj <xref:System.Windows.Forms.FlowLayoutPanel> formant do formularza nadrzędnego. Zmień rozmiar formularza i zanotuj wpływ na układ.

- Ustaw <xref:System.Windows.Forms.Control.Visible%2A> Właściwość jednej z kontrolek na `false` i zwróć uwagę na to, jak <xref:System.Windows.Forms.FlowLayoutPanel> przepływy w odpowiedzi.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Wskazówki: rozmieszczanie formantów w formularzach systemu Windows za pomocą linii przyciągania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [AutoSize — Przegląd właściwości](autosize-property-overview.md)
- [Instrukcje: dokowanie kontrolek na formularzach Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Instrukcje: kotwiczenie kontrolek na formularzach Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Wskazówki: tworzenie formantów formularzy systemu Windows z uzupełnieniem, marginesami oraz właściwościami AutoSize](windows-forms-controls-padding-autosize.md)
