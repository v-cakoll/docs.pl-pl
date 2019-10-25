---
title: 'Wskazówki: rozmieszczanie formantów w aplikacji formularzy systemu Windows za pomocą TableLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 7b7380690d8668f46b98272e1d42640f23679b19
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799113"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Wskazówki: rozmieszczanie formantów w aplikacji formularzy systemu Windows za pomocą TableLayoutPanel

Niektóre aplikacje wymagają formularza z układem, który zmienia się odpowiednio w miarę zmieniania rozmiaru formularza lub zmiany rozmiaru. Gdy potrzebujesz układu dynamicznego i nie chcesz obsłużyć <xref:System.Windows.Forms.Control.Layout> zdarzeń jawnie w kodzie, rozważ użycie panelu układu.

Kontrolka <xref:System.Windows.Forms.FlowLayoutPanel> i kontrolka <xref:System.Windows.Forms.TableLayoutPanel> umożliwiają intuicyjne sposoby rozmieszczenia formantów w formularzu. Obie umożliwiają automatyczną, konfigurowalną możliwość sterowania względnymi położeniami formantów podrzędnych zawartych w nich, a oba umożliwiają dynamiczne funkcje układu w czasie wykonywania, dzięki czemu można zmieniać rozmiar i zmienić położenie formantów podrzędnych jako wymiary formularza nadrzędnego. stąp. Panele układu mogą być zagnieżdżane w panelach układów, aby umożliwić realizację zaawansowanych interfejsów użytkownika.

<xref:System.Windows.Forms.FlowLayoutPanel> rozmieszcza swoją zawartość w określonym kierunku przepływu: w poziomie lub w pionie. Jego zawartość może być opakowana z jednego wiersza do następnego lub z jednej kolumny na następną. Alternatywnie jego zawartość może być przycinana zamiast opakowana. Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

<xref:System.Windows.Forms.TableLayoutPanel> rozmieszcza swoją zawartość w siatce, zapewniając funkcjonalność podobną do tabeli \<HTML > elementu. Formant <xref:System.Windows.Forms.TableLayoutPanel> umożliwia umieszczenie kontrolek w układzie siatki bez konieczności precyzyjnego określania pozycji poszczególnych kontrolek. Jego komórki są ułożone w wiersze i kolumny, które mogą mieć różne rozmiary. Komórki można scalać między wierszami i kolumnami. Komórki mogą zawierać wszystko, co może zawierać i obsłużyć formularz w większości innych kwestii jako kontenerów.

Formant <xref:System.Windows.Forms.TableLayoutPanel> zapewnia także proporcjonalną zmianę rozmiaru w czasie wykonywania, dzięki czemu układ może być bezproblemowo zmieniany w miarę zmiany rozmiaru formularza. Dzięki temu formant <xref:System.Windows.Forms.TableLayoutPanel> jest dobrze dostosowany do celów takich jak formularze wprowadzania danych i zlokalizowane aplikacje. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze na potrzeby wprowadzania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) i [przewodnika: Tworzenie Lokalizowalnego formularza systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).

Ogólnie rzecz biorąc nie należy używać kontrolki <xref:System.Windows.Forms.TableLayoutPanel> jako kontenera dla całego układu. Użyj kontrolek <xref:System.Windows.Forms.TableLayoutPanel>, aby zapewnić proporcjonalne zmiany rozmiarów dla części układu.

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

Formant <xref:System.Windows.Forms.TableLayoutPanel> umożliwia łatwe rozmieszczanie kontrolek w wierszach i kolumnach.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Aby rozmieścić kontrolki w wierszach i kolumnach przy użyciu TableLayoutPanel

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z **przybornika** na formularz. Należy pamiętać, że domyślnie formant <xref:System.Windows.Forms.TableLayoutPanel> ma cztery komórki.

2. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** do kontrolki <xref:System.Windows.Forms.TableLayoutPanel> i upuść ją na jedną z komórek. Należy zauważyć, że formant <xref:System.Windows.Forms.Button> jest tworzony w wybranej komórce.

3. Przeciągnij trzy więcej formantów <xref:System.Windows.Forms.Button> z **przybornika** do kontrolki <xref:System.Windows.Forms.TableLayoutPanel>, tak aby każda komórka zawierała przycisk.

4. Należy pomieścić pionowy uchwyt zmiany rozmiarów między dwiema kolumnami i przenieść go w lewo. Należy pamiętać, że zmiany rozmiaru formantów <xref:System.Windows.Forms.Button> w pierwszej kolumnie są zmieniane na mniejszą szerokość, podczas gdy rozmiar kontrolek <xref:System.Windows.Forms.Button> w drugiej kolumnie jest niezmieniony.

5. Pochwyć pionowy uchwyt zmiany rozmiarów między dwiema kolumnami i przenieś go w prawo. Należy zauważyć, że kontrolki <xref:System.Windows.Forms.Button> w pierwszej kolumnie zwracają do ich oryginalnego rozmiaru, podczas gdy kontrolki <xref:System.Windows.Forms.Button> w drugiej kolumnie są przenoszone z prawej strony.

6. Przesuń poziom obsługi skalowania w górę i w dół, aby zobaczyć efekt na kontrolkach w panelu.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Pozycjonowanie kontrolek w komórkach przy użyciu dokowania i Zakotwiczanie

Zachowanie zakotwiczone w kontrolkach podrzędnych w <xref:System.Windows.Forms.TableLayoutPanel> różni się od zachowania w innych kontrolkach kontenera. Zachowanie dokowania formantów podrzędnych jest takie samo jak w przypadku innych kontrolek kontenera.

#### <a name="positioning-controls-within-cells"></a>Kontrolki pozycjonowania w komórkach

1. Wybierz pierwszą kontrolkę <xref:System.Windows.Forms.Button>. Zmień wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>. Należy zauważyć, że formant <xref:System.Windows.Forms.Button> rozszerza się, aby wypełnić jego komórkę.

2. Wybierz jedną z innych kontrolek <xref:System.Windows.Forms.Button>. Zmień wartość właściwości <xref:System.Windows.Forms.Control.Anchor%2A> na <xref:System.Windows.Forms.AnchorStyles.Right>. Należy zauważyć, że jest ona przenoszona tak, aby jej prawa krawędź była blisko prawej krawędzi komórki. Odległość między obramowaniami to suma właściwości <xref:System.Windows.Forms.Control.Margin%2A> kontrolki <xref:System.Windows.Forms.Button> i właściwości <xref:System.Windows.Forms.Control.Padding%2A> panelu.

3. Zmień wartość właściwości <xref:System.Windows.Forms.Control.Anchor%2A> kontrolki <xref:System.Windows.Forms.Button> na <xref:System.Windows.Forms.AnchorStyles.Right> i <xref:System.Windows.Forms.AnchorStyles.Left>. Należy zauważyć, że rozmiar kontrolki jest zmieniany na szerokość komórki, z uwzględnieniem wartości <xref:System.Windows.Forms.Control.Margin%2A> i <xref:System.Windows.Forms.Control.Padding%2A>.

4. Powtórz kroki 2 i 3 za pomocą stylów <xref:System.Windows.Forms.AnchorStyles.Top> i <xref:System.Windows.Forms.AnchorStyles.Bottom>.

## <a name="setting-row-and-column-properties"></a>Ustawianie właściwości wiersza i kolumny

Można ustawić poszczególne właściwości wierszy i kolumn przy użyciu kolekcji <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> i <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>.

#### <a name="to-set-row-and-column-properties"></a>Aby ustawić właściwości wiersza i kolumny

1. Wybierz kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> w **Projektant formularzy systemu Windows**.

2. W oknach **Właściwości** , otwórz kolekcję <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>, klikając przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok pozycji **kolumny** .

3. Wybierz pierwszą kolumnę i zmień wartość jej właściwości <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> na <xref:System.Windows.Forms.SizeType.AutoSize>. Kliknij przycisk **OK** , aby zaakceptować zmianę. Należy zauważyć, że szerokość pierwszej kolumny jest zmniejszana, aby dopasować ją do formantu <xref:System.Windows.Forms.Button>. Należy również zauważyć, że szerokość kolumny nie jest zmieniana.

4. W oknie **Właściwości** otwórz kolekcję <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> i wybierz pierwszą kolumnę. Zmień wartość właściwości <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> na <xref:System.Windows.Forms.SizeType.Percent>. Kliknij przycisk **OK** , aby zaakceptować zmianę. Zmień rozmiar kontrolki <xref:System.Windows.Forms.TableLayoutPanel> na większą szerokość i Zauważ, że szerokość pierwszej kolumny zostanie rozwinięta. Zmień rozmiar kontrolki <xref:System.Windows.Forms.TableLayoutPanel> na mniejszą szerokość i Zauważ, że przyciski w pierwszej kolumnie mają rozmiar dopasowany do komórki. Należy również zauważyć, że szerokość kolumny jest zmieniana.

5. W oknie **Właściwości** otwórz kolekcję <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> i zaznacz wszystkie kolumny z listy. Ustaw wartość każdej właściwości <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> na <xref:System.Windows.Forms.SizeType.Percent>. Kliknij przycisk **OK** , aby zaakceptować zmianę. Powtórz te czynności za pomocą kolekcji <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>.

6. Przechwyć jeden z narożnych uchwytów zmiany rozmiaru i zmień szerokość i wysokość kontrolki <xref:System.Windows.Forms.TableLayoutPanel>. Należy zauważyć, że rozmiar wierszy i kolumn jest zmieniany w miarę zmiany rozmiaru kontrolki <xref:System.Windows.Forms.TableLayoutPanel>. Należy również zauważyć, że rozmiary wierszy i kolumn są zmiennymi, a uchwyty rozmiaru w poziomie i w pionie.

## <a name="spanning-rows-and-columns-with-a-control"></a>Łączenie wierszy i kolumn z kontrolką

Kontrolka <xref:System.Windows.Forms.TableLayoutPanel> dodaje kilka nowych właściwości do kontrolek w czasie projektowania. Dwie z tych właściwości są `RowSpan` i `ColumnSpan`. Tych właściwości można użyć, aby kontrolka obejmowała więcej niż jeden wiersz lub kolumnę.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Aby rozłączyć wiersze i kolumny z kontrolką

1. Wybierz kontrolkę <xref:System.Windows.Forms.Button> w pierwszym wierszu i w pierwszej kolumnie.

2. W oknach **Właściwości** Zmień wartość właściwości `ColumnSpan` na **2**. Należy zauważyć, że formant <xref:System.Windows.Forms.Button> wypełnia pierwszą kolumnę i drugą kolumnę. Należy również zwrócić uwagę na to, że dodatkowy wiersz został dodany w celu uwzględnienia tej zmiany.

3. Powtórz krok 2 dla właściwości `RowSpan`.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Wstawianie kontrolek przez dwukrotne kliknięcie ich w przyborniku

Aby wypełnić formant <xref:System.Windows.Forms.TableLayoutPanel>, kliknij dwukrotnie pozycję kontrolki w **przyborniku**.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Aby wstawić kontrolki przez dwukrotne kliknięcie w przyborniku

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z **przybornika** na formularz.

2. Kliknij dwukrotnie ikonę kontrolki <xref:System.Windows.Forms.Button> w **przyborniku**. Należy zauważyć, że w pierwszej komórce kontrolki <xref:System.Windows.Forms.TableLayoutPanel> jest wyświetlana Nowa kontrolka przycisku.

3. Kliknij dwukrotnie kilka kontrolek w **przyborniku**. Należy zauważyć, że nowe kontrolki pojawiają się kolejno w niezajętych komórkach formantu <xref:System.Windows.Forms.TableLayoutPanel>. Należy również zauważyć, że formant <xref:System.Windows.Forms.TableLayoutPanel> rozszerza się, aby pomieścić nowe kontrolki, jeśli nie są dostępne żadne otwarte komórki.

## <a name="automatic-handling-of-overflows"></a>Automatyczna obsługa przepełnień

Gdy wstawiasz kontrolki do kontrolki <xref:System.Windows.Forms.TableLayoutPanel>, możesz napotkać puste komórki dla nowych kontrolek. Formant <xref:System.Windows.Forms.TableLayoutPanel> automatycznie obsługuje tę sytuację przez zwiększenie liczby komórek.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Aby obserwować automatyczne obsługiwanie przepełnień

1. Jeśli w kontrolce <xref:System.Windows.Forms.TableLayoutPanel> nadal znajdują się puste komórki, Kontynuuj wstawianie nowych <xref:System.Windows.Forms.Button> formantów do momentu zapełnienia kontrolki <xref:System.Windows.Forms.TableLayoutPanel>.

2. Po zapełnieniu kontrolki <xref:System.Windows.Forms.TableLayoutPanel> kliknij dwukrotnie ikonę <xref:System.Windows.Forms.Button> w **przyborniku** , aby wstawić kolejną kontrolkę <xref:System.Windows.Forms.Button>. Należy zauważyć, że formant <xref:System.Windows.Forms.TableLayoutPanel> tworzy nowe komórki, aby pomieścić nową kontrolkę. Wstaw jeszcze kilka kontrolek i obserwuj zachowanie zmiany rozmiarów.

3. Zmień wartość właściwości <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> kontrolki <xref:System.Windows.Forms.TableLayoutPanel> na <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Kliknij dwukrotnie ikonę <xref:System.Windows.Forms.Button> w **przyborniku** , aby wstawić kontrolki <xref:System.Windows.Forms.Button> do momentu zapełnienia kontrolki <xref:System.Windows.Forms.TableLayoutPanel>. Kliknij dwukrotnie ikonę <xref:System.Windows.Forms.Button> w **przyborniku** . Należy zauważyć, że zostanie wyświetlony komunikat o błędzie z **Projektant formularzy systemu Windows** informujący o tym, że nie można utworzyć dodatkowych wierszy i kolumn.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Wstawianie kontrolki przez rysowanie jej konspektu

Można wstawić formant do kontrolki <xref:System.Windows.Forms.TableLayoutPanel> i określić jej rozmiar, rysując kontur w komórce.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Aby wstawić formant przez rysowanie jego konspektu

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z **przybornika** na formularz.

2. W **przyborniku**kliknij ikonę kontrolki <xref:System.Windows.Forms.Button>. Nie przeciągaj go na formularz.

3. Przesuń wskaźnik myszy nad formant <xref:System.Windows.Forms.TableLayoutPanel>. Należy zauważyć, że wskaźnik zmieni się na krzyżyk z dołączoną ikoną <xref:System.Windows.Forms.Button>.

4. Kliknij i przytrzymaj przycisk myszy.

5. Przeciągnij wskaźnik myszy, aby narysować kontur kontrolki <xref:System.Windows.Forms.Button>. Gdy rozmiar jest zadowalający, zwolnij przycisk myszy. Należy zauważyć, że formant <xref:System.Windows.Forms.Button> jest tworzony w komórce, w której narysowany został konspekt formantu.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Wiele kontrolek w komórkach jest niedozwolonych

Kontrolka <xref:System.Windows.Forms.TableLayoutPanel> może zawierać tylko jedną kontrolkę podrzędną na komórkę.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Aby udowodnić, że wiele kontrolek w komórkach jest niedozwolonych

- Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** do kontrolki <xref:System.Windows.Forms.TableLayoutPanel> i upuść ją na jedną z zajmowanych komórek. Należy zauważyć, że formant <xref:System.Windows.Forms.TableLayoutPanel> nie zezwala na porzucenie kontrolki <xref:System.Windows.Forms.Button> w komórce zajęte.

## <a name="swapping-controls"></a>Zamiana formantów

Kontrolka <xref:System.Windows.Forms.TableLayoutPanel> pozwala na zamianę kontrolek zajmują dwie różne komórki.

#### <a name="to-swap-controls"></a>Aby zamienić kontrolki

- Przeciągnij jedną z formantów <xref:System.Windows.Forms.Button> z zajętej komórki i upuść ją na inną zajmowaną komórkę. Należy zauważyć, że dwie kontrolki są przenoszone z jednej komórki do drugiej.

## <a name="next-steps"></a>Następne kroki

Układ złożony można osiągnąć przy użyciu kombinacji paneli i kontrolek układu. Sugestie dotyczące większej eksploracji obejmują:

- Spróbuj zmienić rozmiar jednego z formantów <xref:System.Windows.Forms.Button> na większy i zanotuj wpływ na układ.

- Wklej zaznaczenie wielu formantów do kontrolki <xref:System.Windows.Forms.TableLayoutPanel> i zanotuj, jak są wstawiane formanty.

- Panele układu mogą zawierać inne panele układu. Eksperymentuj z porzuceniem kontrolki <xref:System.Windows.Forms.TableLayoutPanel> do istniejącej kontrolki.

- Zadokuj formant <xref:System.Windows.Forms.TableLayoutPanel> do formularza nadrzędnego. Zmień rozmiar formularza i zanotuj wpływ na układ.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze na potrzeby wprowadzania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [Przewodnik: Tworzenie Lokalizowalnego formularza systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [Najlepsze praktyki dotyczące kontrolki TableLayoutPanel](best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
- [Instrukcje: dokowanie kontrolek na formularzach Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Instrukcje: kotwiczenie kontrolek na formularzach Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize](windows-forms-controls-padding-autosize.md)
