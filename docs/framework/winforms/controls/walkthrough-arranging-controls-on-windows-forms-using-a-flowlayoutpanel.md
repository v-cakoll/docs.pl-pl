---
title: 'Wskazówki: rozmieszczanie formantów w aplikacji formularzy systemu Windows za pomocą FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: 5c1f4ec53831662bd25f1f15dc1973440067b32c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079847"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>Wskazówki: rozmieszczanie formantów w aplikacji formularzy systemu Windows za pomocą FlowLayoutPanel
Niektóre aplikacje wymagają układ, który organizuje sam odpowiednio podczas zmiany rozmiaru formularza lub zawartość zmienia rozmiar formularza. Kiedy należy układ dynamiczny i nie chcesz obsługiwać <xref:System.Windows.Forms.Control.Layout> zdarzenia jawnie w kodzie, należy wziąć pod uwagę przy użyciu panelu układu.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Kontroli i <xref:System.Windows.Forms.TableLayoutPanel> kontroli zapewnia intuicyjne, aby rozmieścić formanty w formularzu. Obie umożliwiają automatyczne, można skonfigurować do kontrolowania względne położenie formantów podrzędnych w nich zawarte i obie zapewniają funkcje układ dynamiczny w czasie wykonywania, dzięki czemu mogą zmienić rozmiar i zmienić położenie formantów podrzędnych jako wymiary formularza nadrzędnego Zmiana. Panele układów może być zagnieżdżona w panele układów, umożliwiające realizacji interfejsów użytkowników zaawansowanych.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Rozmieszcza jego zawartość w siatce, zapewniając funkcjonalność podobną do HTML \<tabeli > element. Jej komórek są rozmieszczone w wiersze i kolumny, a te może mieć różne rozmiary. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów Windows Forms za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Rozmieszcza jego zawartość w kierunku określonego przepływu: pozioma lub pionowa. Jego zawartość może zostać zawinięty, jeden wiersz do następnego lub z jednej kolumny do następnego. Alternatywnie jego zawartość może zostać obcięty zamiast opakowana. Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie projektu Windows Forms  
  
-   Rozmieszczanie formantów w pionie i poziomie  
  
-   Zmiana kierunku przepływu  
  
-   Wstawianie podziałów przepływu  
  
-   Rozmieszczanie kontrolek przy użyciu dopełnienia i marginesów  
  
-   Wstawianie formantów, klikając je dwukrotnie w przyborniku  
  
-   Wstawianie kontrolki za pomocą rysowania konturu jej  
  
-   Wstawianie formantów, używając symbolu grota  
  
-   Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego  
  
 Gdy skończysz, masz zrozumienia rolę odgrywaną przez te funkcje ważne układu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest tworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji systemu Windows o nazwie "FlowLayoutPanelExample" (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).  
  
2.  Wybierz formularz w **projektanta formularzy**.  
  
## <a name="arranging-controls-horizontally-and-vertically"></a>Rozmieszczanie formantów w pionie i poziomie  
 <xref:System.Windows.Forms.FlowLayoutPanel> Sterowanie umożliwia umieszczenie kontrolki wzdłuż wierszy lub kolumn bez konieczności dokładnie określać położenie każdego pojedynczego formantu.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Kontrolki można zmienić rozmiar lub przepełnieniem jego formantów podrzędnych jako wymiary zmiany elementu nadrzędnego w formularzu.  
  
#### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Aby rozmieścić formanty w poziomie i w pionie za pomocą FlowLayoutPanel  
  
1.  Przeciągnij <xref:System.Windows.Forms.FlowLayoutPanel> z kontrolować **przybornika** do formularza.  
  
2.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel>. Należy pamiętać, że jest automatycznie przeniesiona do lewego górnego rogu <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
3.  Przeciągnij kolejny <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel>. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli jest automatycznie przeniesiona obok pierwszego <xref:System.Windows.Forms.Button> kontroli. Jeśli Twoje <xref:System.Windows.Forms.FlowLayoutPanel> jest zbyt wąska, aby dopasować dwóch kontrolek na tym samym wierszu nowego <xref:System.Windows.Forms.Button> kontroli są automatycznie przenoszone do następnego wiersza.  
  
4.  Przeciągnij kilka dalszych <xref:System.Windows.Forms.Button> kontrolki z **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel>. Kontynuuj, umieszczając <xref:System.Windows.Forms.Button> kontroluje, dopóki jeden, jest zawijany do następnego wiersza.  
  
5.  Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> właściwość `false`. Należy pamiętać, element podrzędny określa już przepływ do następnego wiersza. Zamiast tego są przenoszone do pierwszego wiersza i przycięte.  
  
6.  Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> właściwość `true`. Należy pamiętać, element podrzędny określa ponownie zawijane do następnego wiersza.  
  
7.  Zmniejsz szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontroli, aż wszystkie <xref:System.Windows.Forms.Button> formanty są przenoszone do pierwszej kolumny.  
  
8.  Zwiększ szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontroli, aż wszystkie <xref:System.Windows.Forms.Button> formanty są przenoszone do pierwszego wiersza. Może trzeba zmienić rozmiar formularza większa szerokości.  
  
## <a name="changing-flow-direction"></a>Zmiana kierunku przepływu  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Właściwości umożliwia zmianę kierunku, w którym są rozmieszczone kontrolki. Można rozmieścić formanty podrzędne od lewej do prawej, z, od prawej do lewej, od góry do dołu lub od dołu do góry.  
  
#### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>Aby zmienić kierunek przepływu w FlowLayoutPanel  
  
1.  Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwość <xref:System.Windows.Forms.FlowDirection.TopDown>. Należy pamiętać, że są nieco inaczej rozmieszczone formantów podrzędnych w co najmniej jedną kolumnę, w zależności od tego, wysokość formantu.  
  
2.  Zmień rozmiar <xref:System.Windows.Forms.FlowLayoutPanel> , wysokość jest krótszy niż kolumna <xref:System.Windows.Forms.Button> kontrolki. Należy pamiętać, że <xref:System.Windows.Forms.FlowLayoutPanel> Reorganizuje formantów podrzędnych, które będą przepływać do następnej kolumny. Kontynuuj, zmniejszyć wysokość i należy pamiętać, że elementem podrzędnym kontroluje przepływu w kolejnych kolumnach. Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwość <xref:System.Windows.Forms.FlowDirection.RightToLeft>. Należy pamiętać, że położenie kontrolki podrzędne zostały cofnięte. Sprawdź układ po zmianie wartości <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwość <xref:System.Windows.Forms.FlowDirection.BottomUp>.  
  
## <a name="inserting-flow-breaks"></a>Wstawianie podziałów przepływu  
 <xref:System.Windows.Forms.FlowLayoutPanel> Control oferuje właściwości FlowBreak do jego formantów podrzędnych. Ustawienie wartości właściwości FlowBreak `true` powoduje, że <xref:System.Windows.Forms.FlowLayoutPanel> formantu, aby zatrzymać układu kontrolek w bieżącym kierunek przepływu i zawijania do następnego wiersza lub kolumny.  
  
#### <a name="to-insert-flow-breaks"></a>Aby wstawić podziały przepływu  
  
1.  Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwość <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
2.  Wybierz jedną z <xref:System.Windows.Forms.Button> kontrolek w trakcie skrajnej lewej kolumnie.  
  
3.  Ustaw wartość <xref:System.Windows.Forms.Button> FlowBreak właściwości kontrolki `true`. Należy pamiętać, że kolumna jest uszkodzona i kontrolki, zgodnie z wybranym <xref:System.Windows.Forms.Button> sterowania przepływem do następnej kolumny. Ustaw wartość <xref:System.Windows.Forms.Button> FlowBreak właściwości kontrolki `false` Aby przywrócić oryginalne zachowanie.  
  
## <a name="positioning-controls-using-docking-and-anchoring"></a>Pozycjonowanie formantów przy użyciu dokowanie i Zakotwiczanie  
 Zadokowane i zachowania formantów podrzędnych Zakotwiczanie różnią się od zachowania w innych kontrolek w kontenerze. Zakotwiczanie i dokowanie są względem największych kontroli w kierunku przepływu.  
  
#### <a name="to-position-controls-using-docking-and-anchoring"></a>Aby umieścić kontrolek z wykorzystaniem dokowanie i Zakotwiczanie  
  
1.  Zwiększ rozmiar <xref:System.Windows.Forms.FlowLayoutPanel> aż <xref:System.Windows.Forms.Button> formanty są rozmieszczone w kolumnie.  
  
2.  Wybierz najwyższy <xref:System.Windows.Forms.Button> kontroli. Zwiększenie jego szerokość, więc, że chodzi o dwa razy szerszy co inne <xref:System.Windows.Forms.Button> kontrolki.  
  
3.  Wybierz drugą <xref:System.Windows.Forms.Button> kontroli. Zmień wartość jego <xref:System.Windows.Forms.Control.Anchor%2A> właściwość <xref:System.Windows.Forms.AnchorStyles.Right>. Należy pamiętać, że są one przenoszone tak, aby jego prawej krawędzi jest wyrównany z pierwszym <xref:System.Windows.Forms.Button> prawej krawędzi formantu.  
  
4.  Zmień wartość jego <xref:System.Windows.Forms.Control.Anchor%2A> właściwości <xref:System.Windows.Forms.AnchorStyles.Right> i <xref:System.Windows.Forms.AnchorStyles.Left>. Należy pamiętać, jest o rozmiarze do tej samej szerokości, jak pierwszy <xref:System.Windows.Forms.Button> kontroli.  
  
5.  Wybierz trzecie <xref:System.Windows.Forms.Button> kontroli. Zmień wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>. Należy pamiętać, jest o rozmiarze do tej samej szerokości, jak pierwszy <xref:System.Windows.Forms.Button> kontroli.  
  
## <a name="arranging-controls-using-padding-and-margins"></a>Rozmieszczanie kontrolek przy użyciu dopełnienia i marginesów  
 Można także porządkować kontrolek w Twojej <xref:System.Windows.Forms.FlowLayoutPanel> kontroli, zmieniając <xref:System.Windows.Forms.Control.Padding%2A> i <xref:System.Windows.Forms.Control.Margin%2A> właściwości.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Właściwość pozwala kontrolować rozmieszczenie kontrolek w obrębie <xref:System.Windows.Forms.FlowLayoutPanel> komórce formantu. Określa odstępy między kontrolek podrzędnych i <xref:System.Windows.Forms.FlowLayoutPanel> obramowania formantu.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Właściwość pozwala na kontrolowanie odstępów między formantami.  
  
#### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Aby rozmieścić formanty za pomocą właściwości dopełnienia i marginesów  
  
1.  Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>. Jeśli formularz jest wystarczający, <xref:System.Windows.Forms.Button> kontrolki zostanie przeniesiony do pierwszej kolumny <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
2.  Zmień wartość właściwości <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki <xref:System.Windows.Forms.Control.Padding%2A> właściwości, rozwijając <xref:System.Windows.Forms.Control.Padding%2A> wpis **właściwości** okna i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości **20**. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie się Windows formantów formularzy przy użyciu dopełnienie, marginesy oraz właściwościami AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md). Należy pamiętać, że formanty podrzędne są przenoszone w kierunku środka <xref:System.Windows.Forms.FlowLayoutPanel> kontroli. Zwiększona wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwość wypycha formantów podrzędnych opuszczenie <xref:System.Windows.Forms.FlowLayoutPanel> obramowania formantu.  
  
3.  Zaznacz wszystkie <xref:System.Windows.Forms.Button> kontrolki w <xref:System.Windows.Forms.FlowLayoutPanel> i ustaw wartość <xref:System.Windows.Forms.Control.Margin%2A> właściwości **20**. Należy pamiętać, że odstępy między <xref:System.Windows.Forms.Button> kontroluje rośnie, dzięki czemu są one przenoszone dalsze od siebie. Konieczne może być zmiana rozmiaru <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki będą większe w celu wyświetlenia wszystkich kontrolek podrzędnych.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Wstawianie formantów, klikając je dwukrotnie w przyborniku  
 Możesz wypełnić swoje <xref:System.Windows.Forms.FlowLayoutPanel> kontroli przez dwukrotne kliknięcie kontrolek w **przybornika**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Aby wstawić formanty przez dwukrotne kliknięcie w przyborniku  
  
1.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę kontrolki w **przybornika**. Należy pamiętać, że nowy <xref:System.Windows.Forms.Button> formant jest widoczny w <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
2.  Kliknij dwukrotnie większej liczby opcji w **przybornika**. Należy pamiętać, że nowe formanty są wyświetlane kolejno w <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Wstawianie kontrolki za pomocą rysowania konturu jej  
 Możesz wstawić kontroli do <xref:System.Windows.Forms.FlowLayoutPanel> kontroli i określ jej rozmiar za pomocą rysowania konturu jej w komórce.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Aby wstawić formantu za pomocą rysowania konturu jej  
  
1.  W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.Button> ikonę kontrolki. Nie przeciągnij go na formularzu.  
  
2.  Przesuń wskaźnik myszy nad <xref:System.Windows.Forms.FlowLayoutPanel> kontroli. Należy zauważyć, że wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.Button> ikonę kontrolki dołączone.  
  
3.  Kliknij i przytrzymaj przycisk myszy.  
  
4.  Przeciągnij kursor do rysowania konturu <xref:System.Windows.Forms.Button> kontroli. Gdy jesteś zadowolony z rozmiarem, zwolnij przycisk myszy. Należy pamiętać, że <xref:System.Windows.Forms.Button> formant zostanie utworzony w następnym Otwórz lokalizację <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
## <a name="inserting-controls-using-the-insertion-bar"></a>Wstawianie kontrolek przy użyciu paska wstawiania  
 Możesz wstawić formanty na określonej pozycji w <xref:System.Windows.Forms.FlowLayoutPanel> kontroli. Przeciągnięcie formantu do <xref:System.Windows.Forms.FlowLayoutPanel> obszaru klienckiego kontrolki, aby wskazać, gdzie zostanie wstawiony formantu pojawia się pasek wstawiania.  
  
#### <a name="to-insert-a-control-using-the-caret"></a>Aby wstawić formant, używając symbolu grota  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel> sterowania, a następnie wskaż miejsce między dwoma <xref:System.Windows.Forms.Button> kontrolki. Należy pamiętać, że pasek wstawiania jest pobierana, wskazując, skąd <xref:System.Windows.Forms.Button> zostaną umieszczone po upuszczeniu go do <xref:System.Windows.Forms.FlowLayoutPanel> kontroli. Przed porzuceniem nowy <xref:System.Windows.Forms.Button> sterowania do <xref:System.Windows.Forms.FlowLayoutPanel> kontrolować, przenieś wskaźnik myszy około obserwuj, jak Przenosi pasek wstawiania.  
  
2.  Upuść nowy <xref:System.Windows.Forms.Button> sterowania do <xref:System.Windows.Forms.FlowLayoutPanel> kontroli. Należy pamiętać, że nowy <xref:System.Windows.Forms.Button> kontrolki jest wyrównany z innymi osobami, ponieważ jego <xref:System.Windows.Forms.Control.Margin%2A> właściwość ma inną wartość.  
  
## <a name="reassigning-existing-controls-to-a-different-parent"></a>Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego  
 Możesz przypisać formantów, które istnieją w formularzu na nowe <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
#### <a name="to-reparent-existing-controls"></a>Aby zmienić elementu nadrzędnego istniejących formantów  
  
1.  Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz. Umieść je blisko siebie, ale pozostawić je niewyrównanych.  
  
2.  W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki. Nie przeciągnij go na formularzu.  
  
3.  Przesuń wskaźnik myszy w pobliżu trzy <xref:System.Windows.Forms.Button> kontrolki. Należy zauważyć, że wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki dołączone.  
  
4.  Kliknij i przytrzymaj przycisk myszy.  
  
5.  Przeciągnij kursor do rysowania konturu <xref:System.Windows.Forms.FlowLayoutPanel> kontroli. Rysuj obramowania wokół trzech <xref:System.Windows.Forms.Button> kontrolki.  
  
6.  Zwolnij przycisk myszy. Należy pamiętać, że trzy <xref:System.Windows.Forms.Button> formanty są wstawiane do <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
## <a name="next-steps"></a>Następne kroki  
 Układ złożony przy użyciu kombinacji panele układów i formanty można osiągnąć. Sugestie dotyczące więcej eksploracji obejmują:  
  
-   Zmień rozmiar jednego z <xref:System.Windows.Forms.Button> kontrolki o większym rozmiarze i zwróć uwagę, wpływ na układ.  
  
-   Panele układów może zawierać innych paneli układów. Eksperymentuj z usuwanie <xref:System.Windows.Forms.TableLayoutPanel> kontroli do istniejącej kontrolki.  
  
-   Zadokuj <xref:System.Windows.Forms.FlowLayoutPanel> formantu do formularza nadrzędnego. Zmień rozmiar formularza i zanotuj wpływa na układ.  
  
-   Ustaw <xref:System.Windows.Forms.Control.Visible%2A> właściwości kontrolki do `false` i zwróć uwagę, jak <xref:System.Windows.Forms.FlowLayoutPanel> przepływu w odpowiedzi.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Środowisko użytkownika Microsoft Windows, oficjalnych wytycznych dotyczących projektanci i deweloperzy interfejsu użytkownika. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [AutoSize, właściwość — omówienie](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Instrukcje: dokowanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Instrukcje: kotwiczenie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
