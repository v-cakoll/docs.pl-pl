---
title: 'Przewodnik: rozmieszczanie kontrolek w aplikacji formularzy systemu Windows za pomocą TableLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 7566f19282ffd5a3cac86693a64899f25ce37b9f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040278"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Przewodnik: rozmieszczanie kontrolek w aplikacji formularzy systemu Windows za pomocą TableLayoutPanel

Niektóre aplikacje wymagają formularza z układem, który zmienia się odpowiednio w miarę zmieniania rozmiaru formularza lub zmiany rozmiaru. Gdy potrzebujesz układu dynamicznego i nie chcesz obsłużyć <xref:System.Windows.Forms.Control.Layout> zdarzeń jawnie w kodzie, rozważ użycie panelu układu.

<xref:System.Windows.Forms.FlowLayoutPanel> Formant<xref:System.Windows.Forms.TableLayoutPanel> i formant zapewniają intuicyjne sposoby rozmieszczenia formantów w formularzu. Obie umożliwiają automatyczną, konfigurowalną możliwość sterowania względnymi położeniami formantów podrzędnych zawartych w nich, a oba umożliwiają dynamiczne funkcje układu w czasie wykonywania, dzięki czemu można zmieniać rozmiar i zmienić położenie formantów podrzędnych jako wymiary formularza nadrzędnego. stąp. Panele układu mogą być zagnieżdżane w panelach układów, aby umożliwić realizację zaawansowanych interfejsów użytkownika.

<xref:System.Windows.Forms.FlowLayoutPanel> Rozmieszcza zawartość w określonym kierunku przepływu: w poziomie lub w pionie. Jego zawartość może być opakowana z jednego wiersza do następnego lub z jednej kolumny na następną. Alternatywnie jego zawartość może być przycinana zamiast opakowana. Aby uzyskać więcej informacji, [zobacz Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)użyciu FlowLayoutPanel.

Rozmieszcza zawartość w siatce, dostarczając funkcje podobne do tabeli HTML \<> elementu. <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> Kontrolka umożliwia umieszczenie kontrolek w układzie siatki bez konieczności precyzyjnego określania pozycji poszczególnych kontrolek. Jego komórki są ułożone w wiersze i kolumny, które mogą mieć różne rozmiary. Komórki można scalać między wierszami i kolumnami. Komórki mogą zawierać wszystko, co może zawierać i obsłużyć formularz w większości innych kwestii jako kontenerów.

<xref:System.Windows.Forms.TableLayoutPanel> Kontrolka zapewnia także proporcjonalną zmianę rozmiaru w czasie wykonywania, dzięki czemu układ może być bezproblemowo zmieniany w miarę zmiany rozmiaru formularza. Sprawia to, <xref:System.Windows.Forms.TableLayoutPanel> że formant jest dobrze dostosowany do celów, takich jak formularze wprowadzania danych i zlokalizowane aplikacje. Aby uzyskać więcej informacji, [zobacz Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze na](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) potrzeby [wprowadzania danych i przewodnika: Tworzenie Lokalizowalnego formularza](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))systemu Windows.

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

1. Utwórz projekt aplikacji systemu Windows o nazwie "TableLayoutPanelExample". Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms.

2. Wybierz formularz w **projektancie formularzy** **systemu Windows** .

## <a name="arranging-controls-in-rows-and-columns"></a>Rozmieszczanie formantów w wierszach i kolumnach

<xref:System.Windows.Forms.TableLayoutPanel> Kontrolka umożliwia łatwe rozmieszczanie kontrolek w wierszach i kolumnach.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Aby rozmieścić kontrolki w wierszach i kolumnach przy użyciu TableLayoutPanel

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TableLayoutPanel> Należy pamiętać, że domyślnie <xref:System.Windows.Forms.TableLayoutPanel> kontrolka ma cztery komórki.

2. Przeciągnij kontrolkę z <xref:System.Windows.Forms.TableLayoutPanel> przybornika do kontrolki i upuść ją na jedną z komórek. <xref:System.Windows.Forms.Button> Należy zauważyć, <xref:System.Windows.Forms.Button> że formant jest tworzony w wybranej komórce.

3. Przeciągnij trzy inne <xref:System.Windows.Forms.Button> kontrolki z <xref:System.Windows.Forms.TableLayoutPanel> przybornika do kontrolki, aby każda komórka zawierała przycisk.

4. Należy pomieścić pionowy uchwyt zmiany rozmiarów między dwiema kolumnami i przenieść go w lewo. Należy zauważyć, <xref:System.Windows.Forms.Button> że zmiany rozmiaru kontrolek w pierwszej kolumnie są zmieniane na mniejszą szerokość, podczas gdy rozmiar <xref:System.Windows.Forms.Button> formantów w drugiej kolumnie jest niezmieniony.

5. Pochwyć pionowy uchwyt zmiany rozmiarów między dwiema kolumnami i przenieś go w prawo. Należy zauważyć, <xref:System.Windows.Forms.Button> że kontrolki w pierwszej kolumnie zwracają do ich oryginalnego rozmiaru, <xref:System.Windows.Forms.Button> podczas gdy kontrolki w drugiej kolumnie są przenoszone z prawej strony.

6. Przesuń poziom obsługi skalowania w górę i w dół, aby zobaczyć efekt na kontrolkach w panelu.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Pozycjonowanie kontrolek w komórkach przy użyciu dokowania i Zakotwiczanie

Zachowanie zakotwiczone w kontrolkach podrzędnych w <xref:System.Windows.Forms.TableLayoutPanel> innym zakresie niż zachowanie w innych kontrolkach kontenera. Zachowanie dokowania formantów podrzędnych jest takie samo jak w przypadku innych kontrolek kontenera.

#### <a name="positioning-controls-within-cells"></a>Kontrolki pozycjonowania w komórkach

1. Wybierz pierwszy <xref:System.Windows.Forms.Button> formant. Zmień wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwości na <xref:System.Windows.Forms.DockStyle.Fill>. Zauważ, że <xref:System.Windows.Forms.Button> formant rozwija się, aby wypełnić jego komórkę.

2. Wybierz jedną z innych <xref:System.Windows.Forms.Button> kontrolek. Zmień wartość <xref:System.Windows.Forms.Control.Anchor%2A> właściwości na <xref:System.Windows.Forms.AnchorStyles.Right>. Należy zauważyć, że jest ona przenoszona tak, aby jej prawa krawędź była blisko prawej krawędzi komórki. Odległość między obramowaniami jest sumą <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Control.Padding%2A> właściwości kontrolki i właściwości panelu.

3. <xref:System.Windows.Forms.Button> Zmień wartość <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na <xref:System.Windows.Forms.AnchorStyles.Right> i <xref:System.Windows.Forms.AnchorStyles.Left>. Należy zauważyć, że rozmiar kontrolki jest zmieniany na szerokość komórki, z <xref:System.Windows.Forms.Control.Margin%2A> uwzględnieniem wartości i <xref:System.Windows.Forms.Control.Padding%2A> .

4. Powtórz kroki <xref:System.Windows.Forms.AnchorStyles.Top> od 2 do 3 ze stylami i <xref:System.Windows.Forms.AnchorStyles.Bottom> .

## <a name="setting-row-and-column-properties"></a>Ustawianie właściwości wiersza i kolumny

Można ustawić poszczególne właściwości wierszy i kolumn za pomocą <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> kolekcji i. <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>

#### <a name="to-set-row-and-column-properties"></a>Aby ustawić właściwości wiersza i kolumny

1. Zaznacz kontrolkę w **Projektant formularzy systemu Windows.** <xref:System.Windows.Forms.TableLayoutPanel>

2. W oknach **Właściwości** , Otwórz <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcję, klikając wielokropek (![przycisk wielokropka (...) w okno właściwości w programie Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok pozycji **kolumny** .

3. Wybierz pierwszą kolumnę i zmień wartość jej <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwości na. <xref:System.Windows.Forms.SizeType.AutoSize> Kliknij przycisk **OK** , aby zaakceptować zmianę. Należy zauważyć, że szerokość pierwszej kolumny jest zmniejszana, aby dopasować <xref:System.Windows.Forms.Button> ją do kontrolki. Należy również zauważyć, że szerokość kolumny nie jest zmieniana.

4. W oknie **Właściwości** Otwórz <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcję i wybierz pierwszą kolumnę. Zmień wartość <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwości na <xref:System.Windows.Forms.SizeType.Percent>. Kliknij przycisk **OK** , aby zaakceptować zmianę. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki na większą szerokość i pamiętaj, że szerokość pierwszej kolumny zostanie rozwinięta. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki na mniejszą szerokość i Zauważ, że przyciski w pierwszej kolumnie mają rozmiar dopasowany do komórki. Należy również zauważyć, że szerokość kolumny jest zmieniana.

5. W oknie **Właściwości** Otwórz <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcję i zaznacz wszystkie kolumny z listy. Ustaw wartość każdej <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwości na <xref:System.Windows.Forms.SizeType.Percent>. Kliknij przycisk **OK** , aby zaakceptować zmianę. Powtórz tę kolekcję <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> .

6. Przechwyć jeden z narożnych uchwytów zmiany rozmiaru i zmień szerokość i wysokość <xref:System.Windows.Forms.TableLayoutPanel> formantu. Należy zauważyć, że rozmiar wierszy i kolumn jest zmieniany w <xref:System.Windows.Forms.TableLayoutPanel> miarę zmiany rozmiaru formantu. Należy również zauważyć, że rozmiary wierszy i kolumn są zmiennymi, a uchwyty rozmiaru w poziomie i w pionie.

## <a name="spanning-rows-and-columns-with-a-control"></a>Łączenie wierszy i kolumn z kontrolką

<xref:System.Windows.Forms.TableLayoutPanel> Kontrolka dodaje kilka nowych właściwości do kontrolek w czasie projektowania. Dwie z tych właściwości są `RowSpan` i `ColumnSpan`. Tych właściwości można użyć, aby kontrolka obejmowała więcej niż jeden wiersz lub kolumnę.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Aby rozłączyć wiersze i kolumny z kontrolką

1. <xref:System.Windows.Forms.Button> Zaznacz kontrolkę w pierwszym wierszu i w pierwszej kolumnie.

2. W oknach **Właściwości** , Zmień wartość `ColumnSpan` właściwości na **2**. Należy zauważyć, <xref:System.Windows.Forms.Button> że kontrolka wypełnia pierwszą kolumnę i drugą kolumnę. Należy również zwrócić uwagę na to, że dodatkowy wiersz został dodany w celu uwzględnienia tej zmiany.

3. Powtórz krok 2 dla `RowSpan` właściwości.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Wstawianie kontrolek przez dwukrotne kliknięcie ich w przyborniku

<xref:System.Windows.Forms.TableLayoutPanel> Kontrolkę można wypełnić przez dwukrotne kliknięcie formantów w **przyborniku**.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Aby wstawić kontrolki przez dwukrotne kliknięcie w przyborniku

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TableLayoutPanel>

2. Kliknij dwukrotnie ikonę kontrolkiwprzyborniku<xref:System.Windows.Forms.Button> . Należy zauważyć, że w <xref:System.Windows.Forms.TableLayoutPanel> pierwszej komórce kontrolki pojawia się nowa Kontrolka przycisku.

3. Kliknij dwukrotnie kilka kontrolek w przyborniku. Należy zauważyć, że nowe kontrolki pojawiają <xref:System.Windows.Forms.TableLayoutPanel> się kolejno w niezajętych komórkach kontrolki. Należy również zauważyć, <xref:System.Windows.Forms.TableLayoutPanel> że formant rozszerza się, aby uwzględnić nowe kontrolki, jeśli nie są dostępne żadne otwarte komórki.

## <a name="automatic-handling-of-overflows"></a>Automatyczna obsługa przepełnień

Gdy wstawiasz kontrolki do <xref:System.Windows.Forms.TableLayoutPanel> kontrolki, możesz napotkać puste komórki dla nowych kontrolek. <xref:System.Windows.Forms.TableLayoutPanel> Formant automatycznie obsługuje tę sytuację przez zwiększenie liczby komórek.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Aby obserwować automatyczne obsługiwanie przepełnień

1. Jeśli w <xref:System.Windows.Forms.TableLayoutPanel> kontrolce nadal znajdują się puste komórki, Kontynuuj Wstawianie <xref:System.Windows.Forms.Button> nowych kontrolek <xref:System.Windows.Forms.TableLayoutPanel> do momentu zapełnienia formantu.

2. Gdy kontrolka jest pełna, <xref:System.Windows.Forms.Button> kliknij dwukrotnie ikonę w przyborniku, aby wstawić inną <xref:System.Windows.Forms.Button> kontrolkę. <xref:System.Windows.Forms.TableLayoutPanel> Należy zauważyć, <xref:System.Windows.Forms.TableLayoutPanel> że formant tworzy nowe komórki, aby pomieścić nową kontrolkę. Wstaw jeszcze kilka kontrolek i obserwuj zachowanie zmiany rozmiarów.

3. Zmień wartość <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> właściwości kontrolki na <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Kliknij dwukrotnie <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.TableLayoutPanel> ikonę w przyborniku, aby wstawić kontrolki do momentu zapełnienia formantu. <xref:System.Windows.Forms.Button> Kliknij <xref:System.Windows.Forms.Button> dwukrotnie ikonę w przyborniku. Należy zauważyć, że zostanie wyświetlony komunikat o błędzie z **Projektant formularzy systemu Windows** informujący o tym, że nie można utworzyć dodatkowych wierszy i kolumn.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Wstawianie kontrolki przez rysowanie jej konspektu

Można wstawić kontrolkę do <xref:System.Windows.Forms.TableLayoutPanel> kontrolki i określić jej rozmiar, rysując jej kontur w komórce.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Aby wstawić formant przez rysowanie jego konspektu

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TableLayoutPanel>

2. W **przyborniku**kliknij <xref:System.Windows.Forms.Button> ikonę kontrolki. Nie przeciągaj go na formularz.

3. Przesuń wskaźnik myszy nad <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę. Zwróć uwagę, że wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.Button> dołączoną ikoną kontrolki.

4. Kliknij i przytrzymaj przycisk myszy.

5. Przeciągnij wskaźnik myszy, aby narysować kontur <xref:System.Windows.Forms.Button> formantu. Gdy rozmiar jest zadowalający, zwolnij przycisk myszy. Należy zauważyć, <xref:System.Windows.Forms.Button> że formant jest tworzony w komórce, w której narysowany został konspekt formantu.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Wiele kontrolek w komórkach jest niedozwolonych

<xref:System.Windows.Forms.TableLayoutPanel> Kontrolka może zawierać tylko jedną kontrolkę podrzędną na komórkę.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Aby udowodnić, że wiele kontrolek w komórkach jest niedozwolonych

- Przeciągnij kontrolkę z <xref:System.Windows.Forms.TableLayoutPanel> przybornika do kontrolki i upuść ją na jedną z zajmowanych komórek. <xref:System.Windows.Forms.Button> Należy zauważyć, <xref:System.Windows.Forms.TableLayoutPanel> że formant nie zezwala na <xref:System.Windows.Forms.Button> porzucenie kontrolki w komórce zajmowanej.

## <a name="swapping-controls"></a>Zamiana formantów

<xref:System.Windows.Forms.TableLayoutPanel> Kontrolka pozwala na zamianę formantów, które zajmują dwie różne komórki.

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
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu linii wyrównania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Środowisko użytkownika systemu Microsoft Windows, oficjalne wytyczne dla deweloperów interfejsu użytkownika i projektantów. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze na potrzeby wprowadzania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [Przewodnik: Tworzenie Lokalizowalnego formularza systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [Najlepsze praktyki dotyczące kontrolki TableLayoutPanel](best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
- [Instrukcje: Zadokuj kontrolki na Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Instrukcje: Kontrolki kotwicowe na Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Przewodnik: Określanie układu formantów Windows Forms z dopełnieniem, marginesami i właściwością AutoSize](windows-forms-controls-padding-autosize.md)
