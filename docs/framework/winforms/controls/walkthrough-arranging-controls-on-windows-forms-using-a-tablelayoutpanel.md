---
title: "Wskazówki: rozmieszczanie formantów w aplikacji formularzy systemu Windows za pomocą TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9636585fe9671b8822a6510d405eef5e6f23527e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Wskazówki: rozmieszczanie formantów w aplikacji formularzy systemu Windows za pomocą TableLayoutPanel
Niektóre aplikacje wymagają formularza z układem rozmieszcza się odpowiednio rozmiarów formularza lub jako zawartość zmienia rozmiar. Kiedy należy układ dynamiczny i nie chcesz obsługiwać <xref:System.Windows.Forms.Control.Layout> zdarzenia jawnie w kodzie, należy wziąć pod uwagę przy użyciu panelu układu.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Kontroli i <xref:System.Windows.Forms.TableLayoutPanel> kontroli Podaj intuicyjne rozmieszczanie formantów w formularzu. Podaj zarówno automatyczne, można skonfigurować możliwość kontrolowania względne położenie formantów podrzędnych zawarte w nich, a oba zapewniają funkcje układ dynamiczny w czasie wykonywania, aby zmienić rozmiar i zmienia położenie formantów podrzędnych jako wymiary formularza nadrzędnego Zmiana. Panele układu mogą być zagnieżdżane w panele układu, aby włączyć realizacji interfejsy użytkownika zaawansowane.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Rozmieszcza jego zawartość w kierunku przepływu określonych: pozioma lub pionowa. Jego zawartość można ich opakować z jednego wiersza do następnego lub jedną kolumnę do następnego. Alternatywnie jego zawartość może zostać obcięty zamiast opakowana. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów w Windows Forms za pomocą FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Rozmieszcza jego zawartość w siatce, zapewniając funkcjonalność podobną do HTML \<tabeli > elementu. <xref:System.Windows.Forms.TableLayoutPanel> Sterowanie umożliwia Umieść formanty w układzie siatki bez konieczności precyzyjnie określić położenie każdego pojedynczego formantu. Jej komórek są rozmieszczone w wiersze i kolumny, a te mają różne rozmiary. Komórki można scalić między wierszy i kolumn. Komórki mogą zawierać żadnych formularza może zawierać i działają w większości aspektach jako kontenery.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Sterowania są także proporcjonalne możliwość zmiany rozmiaru w czasie wykonywania, więc układu można zmieniać sprawnie zmieni się rozmiar formularza. Dzięki temu <xref:System.Windows.Forms.TableLayoutPanel> kontroli dobrze nadaje się do celów, takich jak zlokalizowanych aplikacji i formularzy wprowadzania danych. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych](http://msdn.microsoft.com/library/e193b4fc-912a-4917-b036-b76c7a6f58ab) i [wskazówki: Tworzenie formularza systemu Windows Lokalizowalny](http://msdn.microsoft.com/library/c5240b6e-aaca-4286-9bae-778a416edb9c).  
  
 Ogólnie rzecz biorąc, nie należy używać <xref:System.Windows.Forms.TableLayoutPanel> formant jako kontener dla całego układu. Użyj <xref:System.Windows.Forms.TableLayoutPanel> formantów proporcjonalne funkcji zmiany rozmiaru w celu części układu.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu formularzy systemu Windows  
  
-   Rozmieszczanie formantów w wierszy i kolumn  
  
-   Ustawienie wiersza i kolumny właściwości  
  
-   Obejmowanie wierszy i kolumn za pomocą formantu  
  
-   Automatyczną obsługę przepełnienia  
  
-   Wstawianie formantów poprzez dwukrotne kliknięcie w przyborniku  
  
-   Wstawianie formantu za pomocą rysowania konturu jej  
  
-   Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego  
  
 Gdy skończysz, konieczne będzie zrozumienia rolę odgrywaną przez te funkcje ważne układu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji systemu Windows o nazwie "TableLayoutPanelExample". Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Wybierz formularza w **Windows** **Projektant formularzy**.  
  
## <a name="arranging-controls-in-rows-and-columns"></a>Rozmieszczanie formantów w wierszy i kolumn  
 <xref:System.Windows.Forms.TableLayoutPanel> Sterowanie umożliwia łatwe rozmieszczanie formantów w wiersze i kolumny.  
  
#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Aby rozmieszczanie formantów w wiersze i kolumny za pomocą TableLayoutPanel  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolować z **przybornika** na formularzu. Należy zauważyć, że domyślnie <xref:System.Windows.Forms.TableLayoutPanel> formant ma cztery komórki.  
  
2.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> kontroli i upuść go w jednej z komórek. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontrolki jest tworzona w ramach wybrana komórka.  
  
3.  Przeciągnij trzy więcej <xref:System.Windows.Forms.Button> formantów **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> kontrolować, tak aby każda komórka zawiera przycisk.  
  
4.  Wystarczy pobrać uchwyt zmiany rozmiaru w pionie między dwiema kolumnami i przenieść ją do lewej strony. Należy pamiętać, że <xref:System.Windows.Forms.Button> zmieniany jest rozmiar mniejszy szerokość, podczas rozmiaru formantów w pierwszej kolumnie <xref:System.Windows.Forms.Button> formantów w drugiej kolumnie jest bez zmian.  
  
5.  Wystarczy pobrać uchwyt zmiany rozmiaru w pionie między dwiema kolumnami i umieści ją w prawo. Należy pamiętać, że <xref:System.Windows.Forms.Button> formantów w pierwszej kolumnie powrócić do jego oryginalny rozmiar podczas <xref:System.Windows.Forms.Button> formantów w drugiej kolumnie są przenoszone z prawej strony.  
  
6.  Uchwyt zmiany rozmiaru w poziomie w górę i w dół, aby zobaczyć wpływ na formanty w panelu.  
  
## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Pozycjonowanie formantów w komórkach przy użyciu zadokowane i Zakotwiczanie  
 Zachowanie kotwiące formantów podrzędnych w <xref:System.Windows.Forms.TableLayoutPanel> różni się od zachowania w innych kontrolek w kontenerze. Zachowanie dokowanie formantów podrzędnych jest taki sam jak inne formanty kontenera.  
  
#### <a name="positioning-controls-within-cells"></a>Pozycjonowanie formantów w komórkach  
  
1.  Wybierz pierwsze <xref:System.Windows.Forms.Button> formantu. Zmień wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli rozwijany do wypełnienia jej komórki.  
  
2.  Wybierz jeden z innych <xref:System.Windows.Forms.Button> kontrolki. Zmień wartość jego <xref:System.Windows.Forms.Control.Anchor%2A> właściwości <xref:System.Windows.Forms.AnchorStyles.Right>. Należy pamiętać, że jest przenoszony, aby jego prawa krawędź znajduje się w pobliżu prawej krawędzi komórki. Odległość między granicami to suma <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Margin%2A> właściwości i panelu <xref:System.Windows.Forms.Control.Padding%2A> właściwości.  
  
3.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości <xref:System.Windows.Forms.AnchorStyles.Right> i <xref:System.Windows.Forms.AnchorStyles.Left>. Należy pamiętać, że kontrolka jest dopasowywany do szerokość komórki, z <xref:System.Windows.Forms.Control.Margin%2A> i <xref:System.Windows.Forms.Control.Padding%2A> wartości brana pod uwagę.  
  
4.  Powtórz kroki 2 i 3 o <xref:System.Windows.Forms.AnchorStyles.Top> i <xref:System.Windows.Forms.AnchorStyles.Bottom> style.  
  
## <a name="setting-row-and-column-properties"></a>Ustawienie wiersza i kolumny właściwości  
 Można ustawić właściwości poszczególnych wierszy i kolumn przy użyciu <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> i <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcji.  
  
#### <a name="to-set-row-and-column-properties"></a>Aby ustawić właściwości wierszy i kolumn  
  
1.  Wybierz <xref:System.Windows.Forms.TableLayoutPanel> kontroli w **Projektant formularzy systemu Windows**.  
  
2.  W **właściwości** windows Otwórz <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcji, klikając przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisku obok pozycji **kolumn** wpisu.  
  
3.  Wybierz pierwszą kolumnę i zmień wartość jego <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwości <xref:System.Windows.Forms.SizeType.AutoSize>. Kliknij przycisk **OK** aby zaakceptować zmianę. Należy pamiętać, że szerokość pierwszej kolumny zostanie zmniejszona do <xref:System.Windows.Forms.Button> formantu. Należy również zauważyć, że szerokość kolumny nie jest zmieniana.  
  
4.  W **właściwości** okna, otwórz <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcji, a następnie wybierz pierwszą kolumnę. Zmień wartość jego <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwości <xref:System.Windows.Forms.SizeType.Percent>. Kliknij przycisk **OK** aby zaakceptować zmianę. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> do większą szerokość kontrolować i należy pamiętać, że rozszerza szerokość pierwszej kolumny. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontroli Zmniejsz szerokość i należy pamiętać, że do rozmiaru komórki mają rozmiar przycisków w pierwszej kolumnie. Należy również zauważyć, że szerokość kolumny jest zmieniana.  
  
5.  W **właściwości** okna, otwórz <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekcji, a następnie wybierz wyświetlanych kolumn. Ustaw wartość każdego <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwości <xref:System.Windows.Forms.SizeType.Percent>. Kliknij przycisk **OK** aby zaakceptować zmianę. Powtarzania z <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> kolekcji.  
  
6.  Wystarczy pobrać jedną narożnika uchwyty do zmiany, a następnie zmień rozmiar szerokość i wysokość <xref:System.Windows.Forms.TableLayoutPanel> formantu. Należy pamiętać, że wiersze i kolumny zmieniany jest rozmiar jako <xref:System.Windows.Forms.TableLayoutPanel> zmiany rozmiaru formantu. Należy również zauważyć, że wiersze i kolumny są o zmiennych rozmiarach do poziomu i w pionie, uchwytów.  
  
## <a name="spanning-rows-and-columns-with-a-control"></a>Obejmowanie wierszy i kolumn za pomocą formantu  
 <xref:System.Windows.Forms.TableLayoutPanel> Kontroli dodaje kilka nowych właściwości do formantów w czasie projektowania. Dwa z tych właściwości są `RowSpan` i `ColumnSpan`. Aby zakres kontroli więcej niż jeden wiersz lub kolumnę, można użyć tych właściwości.  
  
#### <a name="to-span-rows-and-columns-with-a-control"></a>Aby obejmowanie rzędów i kolumn za pomocą formantu  
  
1.  Wybierz <xref:System.Windows.Forms.Button> formantu w pierwszym wierszu i pierwszej kolumny.  
  
2.  W **właściwości** systemu windows, zmień wartość `ColumnSpan` właściwości **2**. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli wypełnia kolumnie pierwszej i drugiej kolumny. Należy również zauważyć niż dodatkowy wiersz został dodany do uwzględnienia tej zmiany.  
  
3.  Powtórz kroki od 2 do `RowSpan` właściwości.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Wstawianie formantów poprzez dwukrotne kliknięcie w przyborniku  
 Można go wypełnić Twojej <xref:System.Windows.Forms.TableLayoutPanel> kontroli przez dwukrotne kliknięcie formantów w **przybornika**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Wstaw formanty przez dwukrotne kliknięcie w przyborniku  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolować z **przybornika** na formularzu.  
  
2.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę kontroli w **przybornika**. Należy pamiętać, że nową kontrolkę przycisku zostanie wyświetlone w <xref:System.Windows.Forms.TableLayoutPanel> pierwszej komórki formantu.  
  
3.  Kliknij dwukrotnie większej liczby opcji w **przybornika**. Należy pamiętać, że nowe formanty są wyświetlane w kolejno <xref:System.Windows.Forms.TableLayoutPanel> wolne komórki formantu. Należy również zauważyć, że <xref:System.Windows.Forms.TableLayoutPanel> kontroli zwiększa się odpowiednio nowe formanty, jeśli są dostępne nie Otwórz komórek.  
  
## <a name="automatic-handling-of-overflows"></a>Automatyczną obsługę przepełnienia  
 Gdy są wstawianie formantów do <xref:System.Windows.Forms.TableLayoutPanel> kontroli, możesz uruchamiać poza puste komórki nowe formanty. <xref:System.Windows.Forms.TableLayoutPanel> Kontroli obsługi tej sytuacji automatycznie przez odpowiednie zwiększenie liczby komórek.  
  
#### <a name="to-observe-automatic-handling-of-overflows"></a>Aby przyjrzeć się automatyczną obsługę przepełnienia  
  
1.  Jeśli występują nadal puste komórki w <xref:System.Windows.Forms.TableLayoutPanel> kontrolować, kontynuować wstawianie nowych <xref:System.Windows.Forms.Button> kontrolki do <xref:System.Windows.Forms.TableLayoutPanel> formant jest pełna.  
  
2.  Raz <xref:System.Windows.Forms.TableLayoutPanel> formant jest pełna, kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę w **przybornika** do wstawiania innego <xref:System.Windows.Forms.Button> formantu. Należy pamiętać, że <xref:System.Windows.Forms.TableLayoutPanel> kontroli tworzy nowych komórek w celu uwzględnienia nowego formantu. Wstawianie kontrolek więcej kilka i przyjrzeć się zachowaniu zmiany rozmiaru.  
  
3.  Zmień wartość <xref:System.Windows.Forms.TableLayoutPanel> formantu <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> właściwości <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę w **przybornika** do wstawienia <xref:System.Windows.Forms.Button> kontrolki do <xref:System.Windows.Forms.TableLayoutPanel> formant jest pełna. Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę w **przybornika** ponownie. Należy pamiętać, że pojawi się komunikat o błędzie z **Projektant formularzy systemu Windows** informujące o tym, że nie można utworzyć dodatkowych wierszy i kolumn.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Wstawianie formantu za pomocą rysowania konturu jej  
 Można wstawić do formantu <xref:System.Windows.Forms.TableLayoutPanel> kontroli oraz określić jego rozmiar za pomocą rysowania konturu jej w komórce.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Wstawianie formantu za Rysowanie konturu jej  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolować z **przybornika** na formularzu.  
  
2.  W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.Button> ikona formantu. Nie przeciągnij go na formularzu.  
  
3.  Przesuń wskaźnik myszy nad <xref:System.Windows.Forms.TableLayoutPanel> formantu. Należy pamiętać, że kursor zmienia się na krzyżyk z <xref:System.Windows.Forms.Button> ikona kontroli dołączony.  
  
4.  Kliknij i przytrzymaj przycisk myszy.  
  
5.  Przeciągnij wskaźnik myszy Rysowanie konturu <xref:System.Windows.Forms.Button> formantu. Po zakończeniu rozmiar zwolnij przycisk myszy. Należy pamiętać, że <xref:System.Windows.Forms.Button> formant jest tworzony w komórce, w którym zwrócił konspektu formantu.  
  
## <a name="multiple-controls-within-cells-are-not-permitted"></a>Wiele formantów w komórkach nie są dozwolone.  
 <xref:System.Windows.Forms.TableLayoutPanel> Formant może zawierać tylko jeden element podrzędny formant w komórce.  
  
#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Aby zademonstrować, że wiele formantów w komórkach nie są dozwolone  
  
-   Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> kontroli i upuść go w jednej z komórek zajęty. Należy pamiętać, że <xref:System.Windows.Forms.TableLayoutPanel> formantu nie pozwala na porzucić <xref:System.Windows.Forms.Button> formant w komórce zajęty.  
  
## <a name="swapping-controls"></a>Trwa zamienianie formantów  
 <xref:System.Windows.Forms.TableLayoutPanel> Kontroli umożliwia wymiany formanty zajmujące dwie różne komórki.  
  
#### <a name="to-swap-controls"></a>Można zamienić formantów  
  
-   Przeciągnij <xref:System.Windows.Forms.Button> formantów z komórki zajętych i upuszczanie do na inną komórkę zajęty. Należy pamiętać, że dwa formanty są przenoszone z jedną komórkę do drugiej.  
  
## <a name="next-steps"></a>Następne kroki  
 Można osiągnąć złożonego układu przy użyciu kombinacji panele układu i kontrolek. Sugestie dotyczące więcej eksploracji obejmują:  
  
-   Spróbuj zmiana rozmiaru jednego z <xref:System.Windows.Forms.Button> kontroli w celu większego rozmiaru i zanotuj wpływ na układ.  
  
-   Wklej zaznaczenie wielu formantów do <xref:System.Windows.Forms.TableLayoutPanel> kontroli i należy zwrócić uwagę, jak są wstawiane kontrolki.  
  
-   Panele układu może zawierać inne panele układu. Doświadczenia z usunięcie <xref:System.Windows.Forms.TableLayoutPanel> kontroli do istniejącego formantu.  
  
-   Dock <xref:System.Windows.Forms.TableLayoutPanel> sterowania do formularza nadrzędnego. Zmień rozmiar formularza i zanotuj wpływ na układ.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Środowisko użytkownika systemu Windows firmy Microsoft, oficjalnego wskazówki dla deweloperów interfejsu użytkownika i projektantów. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [Wskazówki: Tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych](http://msdn.microsoft.com/library/e193b4fc-912a-4917-b036-b76c7a6f58ab)  
 [Wskazówki: Tworzenie formularza zlokalizowania systemu Windows](http://msdn.microsoft.com/library/c5240b6e-aaca-4286-9bae-778a416edb9c)  
 [Najlepsze praktyki dotyczące kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 [AutoSize, właściwość — omówienie](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Instrukcje: dokowanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Instrukcje: kotwiczenie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
