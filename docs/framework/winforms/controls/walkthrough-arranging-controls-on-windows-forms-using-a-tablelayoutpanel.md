---
title: Rozmieszczanie formantów przy użyciu TableLayoutPanel
description: Dowiedz się, jak rozmieścić kontrolki na Windows Forms przy użyciu kontrolki FlowLayoutPanel i formantu TableLayoutPanel.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 6dfc6dbdef38d635dc94877f79a8e3659295bd98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622799"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Wskazówki: rozmieszczanie formantów w aplikacji formularzy systemu Windows za pomocą TableLayoutPanel

Niektóre aplikacje wymagają formularza z układem, który zmienia się odpowiednio w miarę zmieniania rozmiaru formularza lub zmiany rozmiaru. Gdy potrzebujesz układu dynamicznego i nie chcesz obsłużyć <xref:System.Windows.Forms.Control.Layout> zdarzeń jawnie w kodzie, rozważ użycie panelu układu.

<xref:System.Windows.Forms.FlowLayoutPanel>Formant i <xref:System.Windows.Forms.TableLayoutPanel> formant zapewniają intuicyjne sposoby rozmieszczenia formantów w formularzu. Obie umożliwiają automatyczną, konfigurowalną możliwość sterowania względnymi położeniami formantów podrzędnych zawartych w nich, a oba umożliwiają dynamiczne funkcje układu w czasie wykonywania, dzięki czemu można zmieniać rozmiar i zmienić położenie formantów podrzędnych w miarę zmiany wymiarów formularza nadrzędnego. Panele układu mogą być zagnieżdżane w panelach układów, aby umożliwić realizację zaawansowanych interfejsów użytkownika.

<xref:System.Windows.Forms.FlowLayoutPanel>Rozmieszcza zawartość w określonym kierunku przepływu: w poziomie lub w pionie. Jego zawartość może być opakowana z jednego wiersza do następnego lub z jednej kolumny na następną. Alternatywnie jego zawartość może być przycinana zamiast opakowana. Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

<xref:System.Windows.Forms.TableLayoutPanel>Rozmieszcza swoją zawartość w siatce, dostarczając funkcje podobne do \<table> elementu HTML. <xref:System.Windows.Forms.TableLayoutPanel>Kontrolka umożliwia umieszczenie kontrolek w układzie siatki bez konieczności precyzyjnego określania pozycji poszczególnych kontrolek. Jego komórki są ułożone w wiersze i kolumny, które mogą mieć różne rozmiary. Komórki można scalać między wierszami i kolumnami. Komórki mogą zawierać wszystko, co może zawierać i obsłużyć formularz w większości innych kwestii jako kontenerów.

<xref:System.Windows.Forms.TableLayoutPanel>Kontrolka zapewnia także proporcjonalną zmianę rozmiaru w czasie wykonywania, dzięki czemu układ może być bezproblemowo zmieniany w miarę zmiany rozmiaru formularza. Sprawia to, że <xref:System.Windows.Forms.TableLayoutPanel> formant jest dobrze dostosowany do celów, takich jak formularze wprowadzania danych i zlokalizowane aplikacje. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze na potrzeby wprowadzania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) i [przewodnika: Tworzenie Lokalizowalnego formularza systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).

Ogólnie rzecz biorąc nie należy używać <xref:System.Windows.Forms.TableLayoutPanel> kontrolki jako kontenera dla całego układu. Użyj <xref:System.Windows.Forms.TableLayoutPanel> kontrolek, aby zapewnić proporcjonalne zmiany rozmiarów dla części układu.

Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie projektu Windows Forms

- Rozmieszczanie formantów w wierszach i kolumnach

- Ustawianie właściwości wiersza i kolumny

- Łączenie wierszy i kolumn z kontrolką

- Automatyczna obsługa przepełnień

- Wstawianie kontrolek przez dwukrotne kliknięcie ich w przyborniku

- Wstawianie kontrolki przez rysowanie jej konspektu

- Ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego

Po zakończeniu będzie można zrozumieć rolę odgrywaną przez te ważne funkcje układu.

## <a name="creating-the-project"></a>Tworzenie projektu

Pierwszym krokiem jest utworzenie projektu i skonfigurowanie formularza.

#### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. Utwórz projekt aplikacji systemu Windows o nazwie "TableLayoutPanelExample". Aby uzyskać więcej informacji, zobacz [How to: Create a Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) .

2. Wybierz formularz w **projektancie formularzy** **systemu Windows** .

## <a name="arranging-controls-in-rows-and-columns"></a>Rozmieszczanie formantów w wierszach i kolumnach

<xref:System.Windows.Forms.TableLayoutPanel>Kontrolka umożliwia łatwe rozmieszczanie kontrolek w wierszach i kolumnach.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Aby rozmieścić kontrolki w wierszach i kolumnach przy użyciu TableLayoutPanel

1. Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę z **przybornika** do formularza. Należy pamiętać, że domyślnie <xref:System.Windows.Forms.TableLayoutPanel> kontrolka ma cztery komórki.

2. Przeciągnij <xref:System.Windows.Forms.Button> kontrolkę z **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> kontrolki i upuść ją na jedną z komórek. Należy zauważyć, że <xref:System.Windows.Forms.Button> formant jest tworzony w wybranej komórce.

3. Przeciągnij trzy inne <xref:System.Windows.Forms.Button> kontrolki z **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> kontrolki, aby każda komórka zawierała przycisk.

4. Należy pomieścić pionowy uchwyt zmiany rozmiarów między dwiema kolumnami i przenieść go w lewo. Należy zauważyć, że <xref:System.Windows.Forms.Button> zmiany rozmiaru kontrolek w pierwszej kolumnie są zmieniane na mniejszą szerokość, podczas gdy rozmiar <xref:System.Windows.Forms.Button> formantów w drugiej kolumnie jest niezmieniony.

5. Pochwyć pionowy uchwyt zmiany rozmiarów między dwiema kolumnami i przenieś go w prawo. Należy zauważyć, że <xref:System.Windows.Forms.Button> kontrolki w pierwszej kolumnie zwracają do ich oryginalnego rozmiaru, podczas gdy <xref:System.Windows.Forms.Button> kontrolki w drugiej kolumnie są przenoszone z prawej strony.

6. Przesuń poziom obsługi skalowania w górę i w dół, aby zobaczyć efekt na kontrolkach w panelu.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Pozycjonowanie kontrolek w komórkach przy użyciu dokowania i Zakotwiczanie

Zachowanie zakotwiczone w kontrolkach podrzędnych w <xref:System.Windows.Forms.TableLayoutPanel> innym zakresie niż zachowanie w innych kontrolkach kontenera. Zachowanie dokowania formantów podrzędnych jest takie samo jak w przypadku innych kontrolek kontenera.

#### <a name="positioning-controls-within-cells"></a>Kontrolki pozycjonowania w komórkach

1. Wybierz pierwszy <xref:System.Windows.Forms.Button> formant. Zmień wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwości na <xref:System.Windows.Forms.DockStyle.Fill> . Zauważ, że <xref:System.Windows.Forms.Button> formant rozwija się, aby wypełnić jego komórkę.

2. Wybierz jedną z innych <xref:System.Windows.Forms.Button> kontrolek. Zmień wartość <xref:System.Windows.Forms.Control.Anchor%2A> właściwości na <xref:System.Windows.Forms.AnchorStyles.Right> . Należy zauważyć, że jest ona przenoszona tak, aby jej prawa krawędź była blisko prawej krawędzi komórki. Odległość między obramowaniami jest sumą <xref:System.Windows.Forms.Button> właściwości kontrolki <xref:System.Windows.Forms.Control.Margin%2A> i <xref:System.Windows.Forms.Control.Padding%2A> Właściwości panelu.

3. Zmień wartość <xref:System.Windows.Forms.Button> właściwości kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> na <xref:System.Windows.Forms.AnchorStyles.Right> i <xref:System.Windows.Forms.AnchorStyles.Left> . Należy zauważyć, że rozmiar kontrolki jest zmieniany na szerokość komórki, z uwzględnieniem <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Control.Padding%2A> wartości i.

4. Powtórz kroki od 2 do 3 ze <xref:System.Windows.Forms.AnchorStyles.Top> <xref:System.Windows.Forms.AnchorStyles.Bottom> stylami i.

## <a name="setting-row-and-column-properties"></a>Ustawianie właściwości wiersza i kolumny

Można ustawić poszczególne właściwości wierszy i kolumn za pomocą <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcji i.

#### <a name="to-set-row-and-column-properties"></a>Aby ustawić właściwości wiersza i kolumny

1. Zaznacz <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę w **Projektant formularzy systemu Windows**.

2. W oknach **Właściwości** , Otwórz kolekcję, <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> klikając wielokropek ( ![ przycisk wielokropka (...) w okno właściwości w programie Visual Studio. ](./media/visual-studio-ellipsis-button.png) ) obok pozycji **kolumny** .

3. Wybierz pierwszą kolumnę i zmień wartość jej <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwości na <xref:System.Windows.Forms.SizeType.AutoSize> . Kliknij przycisk **OK** , aby zaakceptować zmianę. Należy zauważyć, że szerokość pierwszej kolumny jest zmniejszana, aby dopasować ją do <xref:System.Windows.Forms.Button> kontrolki. Należy również zauważyć, że szerokość kolumny nie jest zmieniana.

4. W oknie **Właściwości** Otwórz <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcję i wybierz pierwszą kolumnę. Zmień wartość <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwości na <xref:System.Windows.Forms.SizeType.Percent> . Kliknij przycisk **OK** , aby zaakceptować zmianę. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki na większą szerokość i pamiętaj, że szerokość pierwszej kolumny zostanie rozwinięta. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki na mniejszą szerokość i Zauważ, że przyciski w pierwszej kolumnie mają rozmiar dopasowany do komórki. Należy również zauważyć, że szerokość kolumny jest zmieniana.

5. W oknie **Właściwości** Otwórz <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcję i zaznacz wszystkie kolumny z listy. Ustaw wartość każdej <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwości na <xref:System.Windows.Forms.SizeType.Percent> . Kliknij przycisk **OK** , aby zaakceptować zmianę. Powtórz tę <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> kolekcję.

6. Przechwyć jeden z narożnych uchwytów zmiany rozmiaru i zmień szerokość i wysokość <xref:System.Windows.Forms.TableLayoutPanel> formantu. Należy zauważyć, że rozmiar wierszy i kolumn jest <xref:System.Windows.Forms.TableLayoutPanel> zmieniany w miarę zmiany rozmiaru formantu. Należy również zauważyć, że rozmiary wierszy i kolumn są zmiennymi, a uchwyty rozmiaru w poziomie i w pionie.

## <a name="spanning-rows-and-columns-with-a-control"></a>Łączenie wierszy i kolumn z kontrolką

<xref:System.Windows.Forms.TableLayoutPanel>Kontrolka dodaje kilka nowych właściwości do kontrolek w czasie projektowania. Dwie z tych właściwości są `RowSpan` i `ColumnSpan` . Tych właściwości można użyć, aby kontrolka obejmowała więcej niż jeden wiersz lub kolumnę.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Aby rozłączyć wiersze i kolumny z kontrolką

1. Zaznacz <xref:System.Windows.Forms.Button> kontrolkę w pierwszym wierszu i w pierwszej kolumnie.

2. W oknach **Właściwości** , Zmień wartość `ColumnSpan` właściwości na **2**. Należy zauważyć, że <xref:System.Windows.Forms.Button> kontrolka wypełnia pierwszą kolumnę i drugą kolumnę. Należy również zwrócić uwagę na to, że dodatkowy wiersz został dodany w celu uwzględnienia tej zmiany.

3. Powtórz krok 2 dla `RowSpan` właściwości.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Wstawianie kontrolek przez dwukrotne kliknięcie ich w przyborniku

Kontrolkę można wypełnić <xref:System.Windows.Forms.TableLayoutPanel> przez dwukrotne kliknięcie formantów w **przyborniku**.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Aby wstawić kontrolki przez dwukrotne kliknięcie w przyborniku

1. Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę z **przybornika** do formularza.

2. Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę kontrolki w **przyborniku**. Należy zauważyć, że w <xref:System.Windows.Forms.TableLayoutPanel> pierwszej komórce kontrolki pojawia się nowa Kontrolka przycisku.

3. Kliknij dwukrotnie kilka kontrolek w **przyborniku**. Należy zauważyć, że nowe kontrolki pojawiają się kolejno w <xref:System.Windows.Forms.TableLayoutPanel> niezajętych komórkach kontrolki. Należy również zauważyć, że <xref:System.Windows.Forms.TableLayoutPanel> formant rozszerza się, aby uwzględnić nowe kontrolki, jeśli nie są dostępne żadne otwarte komórki.

## <a name="automatic-handling-of-overflows"></a>Automatyczna obsługa przepełnień

Gdy wstawiasz kontrolki do <xref:System.Windows.Forms.TableLayoutPanel> kontrolki, możesz napotkać puste komórki dla nowych kontrolek. <xref:System.Windows.Forms.TableLayoutPanel>Formant automatycznie obsługuje tę sytuację przez zwiększenie liczby komórek.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Aby obserwować automatyczne obsługiwanie przepełnień

1. Jeśli w kontrolce nadal znajdują się puste komórki <xref:System.Windows.Forms.TableLayoutPanel> , Kontynuuj wstawianie nowych <xref:System.Windows.Forms.Button> kontrolek do momentu <xref:System.Windows.Forms.TableLayoutPanel> zapełnienia formantu.

2. Gdy <xref:System.Windows.Forms.TableLayoutPanel> kontrolka jest pełna, kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę w **przyborniku** , aby wstawić inną <xref:System.Windows.Forms.Button> kontrolkę. Należy zauważyć, że <xref:System.Windows.Forms.TableLayoutPanel> formant tworzy nowe komórki, aby pomieścić nową kontrolkę. Wstaw jeszcze kilka kontrolek i obserwuj zachowanie zmiany rozmiarów.

3. Zmień wartość <xref:System.Windows.Forms.TableLayoutPanel> właściwości kontrolki <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> na <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize> . Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę w **przyborniku** , aby wstawić <xref:System.Windows.Forms.Button> kontrolki do momentu <xref:System.Windows.Forms.TableLayoutPanel> zapełnienia formantu. Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę w **przyborniku** . Należy zauważyć, że zostanie wyświetlony komunikat o błędzie z **Projektant formularzy systemu Windows** informujący o tym, że nie można utworzyć dodatkowych wierszy i kolumn.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Wstawianie kontrolki przez rysowanie jej konspektu

Można wstawić kontrolkę do <xref:System.Windows.Forms.TableLayoutPanel> kontrolki i określić jej rozmiar, rysując jej kontur w komórce.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Aby wstawić formant przez rysowanie jego konspektu

1. Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę z **przybornika** do formularza.

2. W **przyborniku**kliknij <xref:System.Windows.Forms.Button> ikonę kontrolki. Nie przeciągaj go na formularz.

3. Przesuń wskaźnik myszy nad <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę. Zwróć uwagę, że wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.Button> dołączoną ikoną kontrolki.

4. Kliknij i przytrzymaj przycisk myszy.

5. Przeciągnij wskaźnik myszy, aby narysować kontur <xref:System.Windows.Forms.Button> formantu. Gdy rozmiar jest zadowalający, zwolnij przycisk myszy. Należy zauważyć, że <xref:System.Windows.Forms.Button> formant jest tworzony w komórce, w której narysowany został konspekt formantu.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Wiele kontrolek w komórkach jest niedozwolonych

<xref:System.Windows.Forms.TableLayoutPanel>Kontrolka może zawierać tylko jedną kontrolkę podrzędną na komórkę.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Aby udowodnić, że wiele kontrolek w komórkach jest niedozwolonych

- Przeciągnij <xref:System.Windows.Forms.Button> kontrolkę z **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> kontrolki i upuść ją na jedną z zajmowanych komórek. Należy zauważyć, że <xref:System.Windows.Forms.TableLayoutPanel> formant nie zezwala na porzucenie <xref:System.Windows.Forms.Button> kontrolki w komórce zajmowanej.

## <a name="swapping-controls"></a>Zamiana formantów

<xref:System.Windows.Forms.TableLayoutPanel>Kontrolka pozwala na zamianę formantów, które zajmują dwie różne komórki.

#### <a name="to-swap-controls"></a>Aby zamienić kontrolki

- Przeciągnij jedną z <xref:System.Windows.Forms.Button> kontrolek z zajętej komórki i upuść ją na inną zajmowaną komórkę. Należy zauważyć, że dwie kontrolki są przenoszone z jednej komórki do drugiej.

## <a name="next-steps"></a>Następne kroki

Układ złożony można osiągnąć przy użyciu kombinacji paneli i kontrolek układu. Sugestie dotyczące większej eksploracji obejmują:

- Spróbuj zmienić rozmiar jednego z <xref:System.Windows.Forms.Button> formantów na większy i zanotuj wpływ na układ.

- Wklej zaznaczenie wielu formantów do <xref:System.Windows.Forms.TableLayoutPanel> kontrolki i zanotuj, jak są wstawiane formanty.

- Panele układu mogą zawierać inne panele układu. Eksperymentuj z porzuceniem <xref:System.Windows.Forms.TableLayoutPanel> kontrolki do istniejącej kontrolki.

- Zadokuj <xref:System.Windows.Forms.TableLayoutPanel> formant do formularza nadrzędnego. Zmień rozmiar formularza i zanotuj wpływ na układ.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Wskazówki: rozmieszczanie formantów w formularzach systemu Windows za pomocą linii przyciągania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze na potrzeby wprowadzania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [Przewodnik: Tworzenie Lokalizowalnego formularza systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [Najlepsze praktyki dotyczące formantu TableLayoutPanel](best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize — Przegląd właściwości](autosize-property-overview.md)
- [Instrukcje: dokowanie kontrolek na formularzach Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Instrukcje: kotwiczenie kontrolek na formularzach Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Wskazówki: tworzenie formantów formularzy systemu Windows z uzupełnieniem, marginesami oraz właściwościami AutoSize](windows-forms-controls-padding-autosize.md)
