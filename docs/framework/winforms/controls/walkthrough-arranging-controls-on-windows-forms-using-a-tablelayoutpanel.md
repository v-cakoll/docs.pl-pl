---
title: 'Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: f337164043014ed14d42e219f26ee2ec8be06662
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305847"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel
Niektóre aplikacje wymagają układ, który organizuje sam odpowiednio podczas zmiany rozmiaru formularza lub zawartość zmienia rozmiar formularza. Kiedy należy układ dynamiczny i nie chcesz obsługiwać <xref:System.Windows.Forms.Control.Layout> zdarzenia jawnie w kodzie, należy wziąć pod uwagę przy użyciu panelu układu.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Kontroli i <xref:System.Windows.Forms.TableLayoutPanel> kontroli zapewnia intuicyjne, aby rozmieścić formanty w formularzu. Obie umożliwiają automatyczne, można skonfigurować do kontrolowania względne położenie formantów podrzędnych w nich zawarte i obie zapewniają funkcje układ dynamiczny w czasie wykonywania, dzięki czemu mogą zmienić rozmiar i zmienić położenie formantów podrzędnych jako wymiary formularza nadrzędnego Zmiana. Panele układów może być zagnieżdżona w panele układów, umożliwiające realizacji interfejsów użytkowników zaawansowanych.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Rozmieszcza jego zawartość w kierunku określonego przepływu: pozioma lub pionowa. Jego zawartość może zostać zawinięty, jeden wiersz do następnego lub z jednej kolumny do następnego. Alternatywnie jego zawartość może zostać obcięty zamiast opakowana. Aby uzyskać więcej informacji, zobacz [instruktażu: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Rozmieszcza jego zawartość w siatce, zapewniając funkcjonalność podobną do HTML \<tabeli > element. <xref:System.Windows.Forms.TableLayoutPanel> Sterowanie umożliwia Umieść formanty w przypadku układu tabelarycznego bez konieczności dokładnie określać położenie każdego pojedynczego formantu. Jej komórek są rozmieszczone w wiersze i kolumny, a te może mieć różne rozmiary. Komórki mogą zostać scalone między wierszami i kolumnami. Komórki mogą zawierać żadnych formularza może zawierać i zachowują się w większości innych aspektach jako kontenery.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Kontroli także proporcjonalna możliwość zmiany rozmiaru w czasie wykonywania, dzięki czemu układu można zmienić bez problemów ze zmienionym rozmiarem formularza. To sprawia, że <xref:System.Windows.Forms.TableLayoutPanel> kontroli dobrze nadaje się do celów takich jak formularze wprowadzanie danych i aplikacji zlokalizowanych. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) i [instruktażu: Tworzenie formularza Windows Lokalizowalny](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).  
  
 Ogólnie rzecz biorąc, nie należy używać <xref:System.Windows.Forms.TableLayoutPanel> kontroli jako kontener dla całego układu. Użyj <xref:System.Windows.Forms.TableLayoutPanel> formantów, aby zapewnić możliwości zmiany rozmiaru proporcjonalne części układu.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie projektu Windows Forms  
  
-   Rozmieszczanie formantów w wiersze i kolumny  
  
-   Ustawienie wierszy i kolumn właściwości  
  
-   Obejmowanie wierszy i kolumn z kontrolką  
  
-   Automatyczną obsługę przepełnienia  
  
-   Wstawianie formantów, klikając je dwukrotnie w przyborniku  
  
-   Wstawianie kontrolki za pomocą rysowania konturu jej  
  
-   Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego  
  
 Gdy skończysz, masz zrozumienia rolę odgrywaną przez te funkcje ważne układu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest tworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji Windows o nazwie "TableLayoutPanelExample". Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) .  
  
2.  Wybierz formularz w **Windows** **projektanta formularzy**.  
  
## <a name="arranging-controls-in-rows-and-columns"></a>Rozmieszczanie formantów w wiersze i kolumny  
 <xref:System.Windows.Forms.TableLayoutPanel> Sterowanie umożliwia łatwe rozmieścić formanty w wiersze i kolumny.  
  
#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Aby rozmieścić formanty w wiersze i kolumny za pomocą TableLayoutPanel  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza. Należy zauważyć, że domyślnie <xref:System.Windows.Forms.TableLayoutPanel> kontrolka ma cztery komórki.  
  
2.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> kontroli i upuść go w jednej z komórek. Należy pamiętać, że <xref:System.Windows.Forms.Button> formant zostanie utworzony w ramach wybrana komórka.  
  
3.  Przeciągnij trzech <xref:System.Windows.Forms.Button> kontrolki z **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> kontrolować, tak aby każda komórka zawiera przycisk.  
  
4.  Chwyć uchwyt zmiany rozmiaru w pionie między dwiema kolumnami, a następnie przesuń w lewo. Należy pamiętać, że <xref:System.Windows.Forms.Button> zmieniany jest rozmiar Zmniejsz szerokość podczas rozmiaru formantów w pierwszej kolumnie <xref:System.Windows.Forms.Button> kontrolek w drugiej kolumnie pozostaje niezmieniony.  
  
5.  Chwyć uchwyt zmiany rozmiaru w pionie między dwiema kolumnami, a następnie przesuń w prawo. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontrolek w pierwszej kolumnie powrót do ich oryginalnego rozmiaru, podczas gdy <xref:System.Windows.Forms.Button> kontrolek w drugiej kolumnie są przenoszone z prawej strony.  
  
6.  Uchwyt zmiany rozmiaru w poziomie górę i w dół, aby zobaczyć wpływ na kontrolki w panelu.  
  
## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Pozycjonowanie formantów w komórkach przy użyciu dokowanie i Zakotwiczanie  
 Zachowanie kotwiące formantów podrzędnych w <xref:System.Windows.Forms.TableLayoutPanel> różni się od zachowania w innych kontrolek w kontenerze. Zachowanie dokowania formantów podrzędnych jest taka sama, jak inne kontrolki kontenera.  
  
#### <a name="positioning-controls-within-cells"></a>Pozycjonowanie formantów w komórkach  
  
1.  Zaznacz pierwszą pozycję <xref:System.Windows.Forms.Button> kontroli. Zmień wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli jest rozszerzany, aby wypełnić komórkę.  
  
2.  Wybierz jedną z innych <xref:System.Windows.Forms.Button> kontrolki. Zmień wartość jego <xref:System.Windows.Forms.Control.Anchor%2A> właściwość <xref:System.Windows.Forms.AnchorStyles.Right>. Należy pamiętać, że są one przenoszone tak, aby jego prawa krawędź w pobliżu prawej krawędzi komórki. Odległość między obramowania jest sumą <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Margin%2A> właściwości i stronie panelu <xref:System.Windows.Forms.Control.Padding%2A> właściwości.  
  
3.  Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwości <xref:System.Windows.Forms.AnchorStyles.Right> i <xref:System.Windows.Forms.AnchorStyles.Left>. Należy zauważyć, że kontrolka ma rozmiar do szerokości komórki, za pomocą <xref:System.Windows.Forms.Control.Margin%2A> i <xref:System.Windows.Forms.Control.Padding%2A> brana pod uwagę wartości.  
  
4.  Powtórz kroki 2 i 3 z <xref:System.Windows.Forms.AnchorStyles.Top> i <xref:System.Windows.Forms.AnchorStyles.Bottom> style.  
  
## <a name="setting-row-and-column-properties"></a>Ustawienie wierszy i kolumn właściwości  
 Można ustawić właściwości poszczególnych wierszy i kolumn, używając <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> i <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcji.  
  
#### <a name="to-set-row-and-column-properties"></a>Aby ustawić właściwości wierszy i kolumn  
  
1.  Wybierz <xref:System.Windows.Forms.TableLayoutPanel> w kontrolce **Windows Forms Designer**.  
  
2.  W **właściwości** systemu windows, otwórz <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcji, klikając przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisku obok pozycji **kolumn** wpisu.  
  
3.  Wybierz pierwszą kolumnę, a następnie zmień wartość jego <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość <xref:System.Windows.Forms.SizeType.AutoSize>. Kliknij przycisk **OK** aby zaakceptować zmianę. Należy pamiętać, że szerokość pierwszej kolumny jest ograniczona do dopasowania <xref:System.Windows.Forms.Button> kontroli. Należy również zauważyć, że szerokość kolumny nie jest o zmiennym rozmiarze.  
  
4.  W **właściwości** otwarte okno <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcji, a następnie wybierz pierwszą kolumnę. Zmień wartość jego <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość <xref:System.Windows.Forms.SizeType.Percent>. Kliknij przycisk **OK** aby zaakceptować zmianę. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolę większą szerokość i należy pamiętać, że rozwija szerokość pierwszej kolumny. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontroli Zmniejsz szerokość i należy pamiętać, że przyciski w pierwszej kolumnie mają rozmiar do rozmiaru komórki. Należy również zauważyć, że szerokości kolumny jest o zmiennym rozmiarze.  
  
5.  W **właściwości** otwarte okno <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcji, a następnie wybierz wyświetlanych kolumn. Ustaw wartość każdego <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość <xref:System.Windows.Forms.SizeType.Percent>. Kliknij przycisk **OK** aby zaakceptować zmianę. Powtórz tę procedurę przy użyciu <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> kolekcji.  
  
6.  Pobierz jeden z rogów uchwyty do zmiany i zmienianie rozmiaru, szerokość i wysokość <xref:System.Windows.Forms.TableLayoutPanel> kontroli. Należy zauważyć, że wiersze i kolumny zmieniany jest rozmiar jako <xref:System.Windows.Forms.TableLayoutPanel> zmiany rozmiaru formantu. Należy również zauważyć, że wiersze i kolumny są o zmiennych rozmiarach do poziomu i w pionie, uchwytów zmiany rozmiaru.  
  
## <a name="spanning-rows-and-columns-with-a-control"></a>Obejmowanie wierszy i kolumn z kontrolką  
 <xref:System.Windows.Forms.TableLayoutPanel> Kontroli dodaje kilka nowych właściwości do formantów w czasie projektowania. Dwa z tych właściwości są `RowSpan` i `ColumnSpan`. Zapewnienie kontroli zakresu więcej niż jeden wiersz lub kolumnę, można użyć tych właściwości.  
  
#### <a name="to-span-rows-and-columns-with-a-control"></a>Aby obejmowanie rzędów i kolumn z kontrolką  
  
1.  Wybierz <xref:System.Windows.Forms.Button> formantu w pierwszym wierszu i pierwszą kolumnę.  
  
2.  W **właściwości** systemu windows, zmień wartość właściwości `ColumnSpan` właściwości **2**. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli wypełnia kolumnie pierwszej i drugiej kolumny. Należy również zauważyć, niż jest dodatkowy wiersz został dodany do uwzględnienia tej zmiany.  
  
3.  Powtórz krok 2 dla `RowSpan` właściwości.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Wstawianie formantów, klikając je dwukrotnie w przyborniku  
 Możesz wypełnić swoje <xref:System.Windows.Forms.TableLayoutPanel> kontroli przez dwukrotne kliknięcie kontrolek w **przybornika**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Aby wstawić formanty przez dwukrotne kliknięcie w przyborniku  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.  
  
2.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę kontrolki w **przybornika**. Należy zauważyć, że nowy formant przycisku, który pojawia się w <xref:System.Windows.Forms.TableLayoutPanel> kontrolki pierwszej komórki.  
  
3.  Kliknij dwukrotnie większej liczby opcji w **przybornika**. Należy pamiętać, że nowe formanty są wyświetlane kolejno w <xref:System.Windows.Forms.TableLayoutPanel> wolnych komórkach formantu. Należy również zauważyć, że <xref:System.Windows.Forms.TableLayoutPanel> kontroli jest rozszerzany, aby uwzględnić nowe formanty, jeśli nie otwartego komórki są dostępne.  
  
## <a name="automatic-handling-of-overflows"></a>Automatyczną obsługę przepełnienia  
 Gdy wstawiasz formanty do <xref:System.Windows.Forms.TableLayoutPanel> kontrolki, możesz uruchamiać poza pustych komórek nowych formantów. <xref:System.Windows.Forms.TableLayoutPanel> Kontroli tej sytuacji automatycznie obsługiwane przez odpowiednie zwiększenie liczby komórek.  
  
#### <a name="to-observe-automatic-handling-of-overflows"></a>Aby obserwować automatyczną obsługę przepełnienia  
  
1.  Jeśli nadal puste komórki w <xref:System.Windows.Forms.TableLayoutPanel> i kontynuować wstawianie nowych <xref:System.Windows.Forms.Button> kontroluje aż do <xref:System.Windows.Forms.TableLayoutPanel> kontroli jest pełny.  
  
2.  Raz <xref:System.Windows.Forms.TableLayoutPanel> kontroli jest pełny, kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę **przybornika** do wstawiania innego <xref:System.Windows.Forms.Button> kontroli. Należy pamiętać, że <xref:System.Windows.Forms.TableLayoutPanel> kontroli tworzy nowe komórki w celu uwzględnienia nowej kontrolki. Wstaw kilka więcej kontrolek i przyjrzeć się zachowaniu zmiany rozmiaru.  
  
3.  Zmień wartość właściwości <xref:System.Windows.Forms.TableLayoutPanel> kontrolki <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> właściwość <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę **przybornika** do wstawienia <xref:System.Windows.Forms.Button> kontroluje aż do <xref:System.Windows.Forms.TableLayoutPanel> kontroli jest pełny. Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę **przybornika** ponownie. Należy pamiętać, że otrzymasz komunikat o błędzie z **Windows Forms Designer** informujące o tym, że nie można utworzyć dodatkowe wiersze i kolumny.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Wstawianie kontrolki za pomocą rysowania konturu jej  
 Możesz wstawić kontroli do <xref:System.Windows.Forms.TableLayoutPanel> kontroli i określ jej rozmiar za pomocą rysowania konturu jej w komórce.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Aby wstawić formantu za pomocą rysowania konturu jej  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.  
  
2.  W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.Button> ikonę kontrolki. Nie przeciągnij go na formularzu.  
  
3.  Przesuń wskaźnik myszy nad <xref:System.Windows.Forms.TableLayoutPanel> kontroli. Należy zauważyć, że wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.Button> ikonę kontrolki dołączone.  
  
4.  Kliknij i przytrzymaj przycisk myszy.  
  
5.  Przeciągnij kursor do rysowania konturu <xref:System.Windows.Forms.Button> kontroli. Gdy jesteś zadowolony z rozmiarem, zwolnij przycisk myszy. Należy pamiętać, że <xref:System.Windows.Forms.Button> formant zostanie utworzony w komórce, w którym zostało narysowane konspektu formantu.  
  
## <a name="multiple-controls-within-cells-are-not-permitted"></a>Wiele kontrolek w komórkach nie są dozwolone.  
 <xref:System.Windows.Forms.TableLayoutPanel> Formant może zawierać tylko jeden element podrzędny formant w komórce.  
  
#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Aby zademonstrować, że wielu formantów w komórkach nie są dozwolone  
  
-   Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> kontroli i upuść go w jednej z komórek zajęty. Należy pamiętać, że <xref:System.Windows.Forms.TableLayoutPanel> kontroli nie pozwalają na upuszczanie <xref:System.Windows.Forms.Button> formant w komórce zajęty.  
  
## <a name="swapping-controls"></a>Trwa zamienianie formantów  
 <xref:System.Windows.Forms.TableLayoutPanel> Kontroli umożliwia przełączanie kontrolek zajmuje dwie różne komórki.  
  
#### <a name="to-swap-controls"></a>Można zamienić formantów  
  
-   Przeciągnij jeden z <xref:System.Windows.Forms.Button> formantów z zajętych komórkę i upuść do na innej komórce zajęty. Należy pamiętać, że dwie kontrolki są przenoszone z jedną komórkę do drugiej.  
  
## <a name="next-steps"></a>Następne kroki  
 Układ złożony przy użyciu kombinacji panele układów i formanty można osiągnąć. Sugestie dotyczące więcej eksploracji obejmują:  
  
-   Spróbuj zmienić rozmiar poszczególnych <xref:System.Windows.Forms.Button> kontrolki o większym rozmiarze i zwróć uwagę, wpływ na układ.  
  
-   Wklej zaznaczenie wielu formantów do <xref:System.Windows.Forms.TableLayoutPanel> kontroli i należy pamiętać, jak są wstawiane kontrolki.  
  
-   Panele układów może zawierać innych paneli układów. Eksperymentuj z usuwanie <xref:System.Windows.Forms.TableLayoutPanel> kontroli do istniejącej kontrolki.  
  
-   Zadokuj <xref:System.Windows.Forms.TableLayoutPanel> formantu do formularza nadrzędnego. Zmień rozmiar formularza i zanotuj wpływa na układ.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Środowisko użytkownika Microsoft Windows, oficjalnych wytycznych dotyczących projektanci i deweloperzy interfejsu użytkownika. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [Przewodnik: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [Przewodnik: Tworzenie formularza Windows Lokalizowalny](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [Najlepsze praktyki dotyczące kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize, właściwość — omówienie](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
- [Instrukcje: Dokowanie formantów na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)
- [Instrukcje: Zakotwiczenia formantów na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
- [Przewodnik: Układania Windows formantów formularzy przy użyciu dopełnienie, marginesy oraz właściwościami AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
