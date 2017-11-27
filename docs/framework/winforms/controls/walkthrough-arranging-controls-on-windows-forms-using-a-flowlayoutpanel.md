---
title: "Wskazówki: rozmieszczanie formantów w aplikacji formularzy systemu Windows za pomocą FlowLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 84b909f0c638bf0fb7c19ecc3a86c7c32bab2adb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>Wskazówki: rozmieszczanie formantów w aplikacji formularzy systemu Windows za pomocą FlowLayoutPanel
Niektóre aplikacje wymagają formularza z układem rozmieszcza się odpowiednio rozmiarów formularza lub jako zawartość zmienia rozmiar. Kiedy należy układ dynamiczny i nie chcesz obsługiwać <xref:System.Windows.Forms.Control.Layout> zdarzenia jawnie w kodzie, należy wziąć pod uwagę przy użyciu panelu układu.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Kontroli i <xref:System.Windows.Forms.TableLayoutPanel> kontroli Podaj intuicyjne rozmieszczanie formantów w formularzu. Podaj zarówno automatyczne, można skonfigurować możliwość kontrolowania względne położenie formantów podrzędnych zawarte w nich, a oba zapewniają funkcje układ dynamiczny w czasie wykonywania, aby zmienić rozmiar i zmienia położenie formantów podrzędnych jako wymiary formularza nadrzędnego Zmiana. Panele układu mogą być zagnieżdżane w panele układu, aby włączyć realizacji interfejsy użytkownika zaawansowane.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Rozmieszcza jego zawartość w siatce, zapewniając funkcjonalność podobną do HTML \<tabeli > elementu. Jej komórek są rozmieszczone w wiersze i kolumny, a te mają różne rozmiary. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów w Windows Forms za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Rozmieszcza jego zawartość w kierunku przepływu określonych: pozioma lub pionowa. Jego zawartość można ich opakować z jednego wiersza do następnego lub jedną kolumnę do następnego. Alternatywnie jego zawartość może zostać obcięty zamiast opakowana. Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu formularzy systemu Windows  
  
-   Rozmieszczanie formantów w poziomie i w pionie  
  
-   Zmiana kierunek przepływu  
  
-   Wstawianie podziałów przepływu  
  
-   Rozmieszczanie formantów za pomocą wypełnienia i marginesy  
  
-   Wstawianie formantów poprzez dwukrotne kliknięcie w przyborniku  
  
-   Wstawianie formantu za pomocą rysowania konturu jej  
  
-   Wstawianie formantów przy użyciu karetkę  
  
-   Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego  
  
 Gdy skończysz, konieczne będzie zrozumienia rolę odgrywaną przez te funkcje ważne układu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji systemu Windows o nazwie "FlowLayoutPanelExample". Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Wybierz formularza w **Projektant formularzy**.  
  
## <a name="arranging-controls-horizontally-and-vertically"></a>Rozmieszczanie formantów w poziomie i w pionie  
 <xref:System.Windows.Forms.FlowLayoutPanel> Sterowanie umożliwia Umieść formanty wzdłuż wierszy lub kolumn bez konieczności precyzyjnie określić położenie każdego pojedynczego formantu.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Formantu można zmienić rozmiar lub ułożenia formantów podrzędnych jako wymiary zmiany formularza nadrzędnego.  
  
#### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Aby zorganizować formantów poziomie i w pionie za pomocą FlowLayoutPanel  
  
1.  Przeciągnij <xref:System.Windows.Forms.FlowLayoutPanel> kontrolować z **przybornika** na formularzu.  
  
2.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel>. Należy pamiętać, że zostanie automatycznie przeniesiona do lewego górnego rogu <xref:System.Windows.Forms.FlowLayoutPanel> formantu.  
  
3.  Przeciągnij kolejny <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel>. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli jest automatycznie przeniesiona obok pierwszy <xref:System.Windows.Forms.Button> formantu. Jeśli Twoje <xref:System.Windows.Forms.FlowLayoutPanel> jest zbyt ograniczone, aby dopasować dwóch formantów w tym samym wierszu nowego <xref:System.Windows.Forms.Button> kontroli jest automatycznie przenoszona do następnego wiersza.  
  
4.  Przeciągnij kilka innych <xref:System.Windows.Forms.Button> formantów **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel>. Kontynuować umieszczenie <xref:System.Windows.Forms.Button> kontrolki, dopóki jeden zawijany do następnego wiersza.  
  
5.  Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> formantu <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> właściwości `false`. Należy pamiętać, podrzędne kontrolki już przepływu do następnego wiersza. Zamiast tego są przenoszone do pierwszego wiersza i przycięta.  
  
6.  Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> formantu <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> właściwości `true`. Należy pamiętać, podrzędne kontrolki ponownie zawijania do następnego wiersza.  
  
7.  Zmniejsz szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontroli, aż wszystkie <xref:System.Windows.Forms.Button> formanty zostaną przeniesione do pierwszej kolumny.  
  
8.  Zwiększ rozmiar <xref:System.Windows.Forms.FlowLayoutPanel> kontroli, aż wszystkie <xref:System.Windows.Forms.Button> formanty zostaną przeniesione do pierwszego wiersza. Może być konieczne zmienianie rozmiaru formularza większa szerokości.  
  
## <a name="changing-flow-direction"></a>Zmiana kierunek przepływu  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Właściwości umożliwia zmianę kierunku, w którym są rozmieszczone formanty. Można rozmieścić formantów podrzędnych od lewej do prawej, od prawej do lewej, od góry do dołu lub od dołu do góry.  
  
#### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>Aby zmienić kierunek przepływu FlowLayoutPanel  
  
1.  Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> formantu <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwości <xref:System.Windows.Forms.FlowDirection.TopDown>. Należy pamiętać, że w co najmniej jedną kolumnę, w zależności od wysokość formantu są przestawiać formantów podrzędnych.  
  
2.  Zmień rozmiar <xref:System.Windows.Forms.FlowLayoutPanel> , jego wysokość jest krótszy niż kolumna <xref:System.Windows.Forms.Button> kontrolki. Należy pamiętać, że <xref:System.Windows.Forms.FlowLayoutPanel> Reorganizuje formantów podrzędnych do następnej kolumnie. Kontynuuj, zmniejszyć wysokość i należy pamiętać, że podrzędne kontroluje przepływu na kolejnych kolumny. Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> formantu <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwości <xref:System.Windows.Forms.FlowDirection.RightToLeft>. Należy pamiętać, że są wycofywane pozycji formantów podrzędnych. Sprawdź układ po zmianie wartości <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwości <xref:System.Windows.Forms.FlowDirection.BottomUp>.  
  
## <a name="inserting-flow-breaks"></a>Wstawianie podziałów przepływu  
 <xref:System.Windows.Forms.FlowLayoutPanel> Kontrola zapewnia właściwości FlowBreak w celu jej kontrolkach podrzędnych. Ustawienie wartości dla właściwości FlowBreak `true` powoduje, że <xref:System.Windows.Forms.FlowLayoutPanel> formant przestanie układania formantów w bieżącym kierunek przepływu i zawijania do następnego wiersza lub kolumny.  
  
#### <a name="to-insert-flow-breaks"></a>Aby wstawić podziały przepływu  
  
1.  Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> formantu <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwości <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
2.  Wybierz jedną z <xref:System.Windows.Forms.Button> formantów pośrodku kolumny z lewej strony.  
  
3.  Ustaw wartość <xref:System.Windows.Forms.Button> FlowBreak właściwości formantu `true`. Należy pamiętać, że kolumna jest uszkodzony i formanty po wybranym <xref:System.Windows.Forms.Button> sterowania przepływem w następnej kolumnie. Ustaw wartość <xref:System.Windows.Forms.Button> FlowBreak właściwości formantu `false` Aby przywrócić oryginalne zachowanie.  
  
## <a name="positioning-controls-using-docking-and-anchoring"></a>Pozycjonowanie formantów za pomocą zadokowane i Zakotwiczanie  
 Zadokowane i Zakotwiczanie zachowania formantów podrzędnych różnią się od zachowania w innych kontrolek w kontenerze. Zarówno zadokowane i Zakotwiczanie są względem największy formantu w kierunku przepływu.  
  
#### <a name="to-position-controls-using-docking-and-anchoring"></a>Aby umieścić kontrolek z wykorzystaniem zadokowane i Zakotwiczanie  
  
1.  Zwiększ rozmiar <xref:System.Windows.Forms.FlowLayoutPanel> do momentu <xref:System.Windows.Forms.Button> formanty są rozmieszczone w kolumnie.  
  
2.  Wybierz najwyższy <xref:System.Windows.Forms.Button> formantu. Zwiększyć tak, aby o dwa razy szerszy co inne <xref:System.Windows.Forms.Button> kontrolki.  
  
3.  Wybierz drugą <xref:System.Windows.Forms.Button> formantu. Zmień wartość jego <xref:System.Windows.Forms.Control.Anchor%2A> właściwości <xref:System.Windows.Forms.AnchorStyles.Right>. Należy pamiętać, że jest przenoszony, aby jego prawej krawędzi jest wyrównany z pierwszym <xref:System.Windows.Forms.Button> prawej granicy formantu.  
  
4.  Zmień wartość jego <xref:System.Windows.Forms.Control.Anchor%2A> właściwości <xref:System.Windows.Forms.AnchorStyles.Right> i <xref:System.Windows.Forms.AnchorStyles.Left>. Należy pamiętać, jest o rozmiarze do tej samej szerokości jako pierwszy <xref:System.Windows.Forms.Button> formantu.  
  
5.  Wybierz trzecie <xref:System.Windows.Forms.Button> formantu. Zmień wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>. Należy pamiętać, jest o rozmiarze do tej samej szerokości jako pierwszy <xref:System.Windows.Forms.Button> formantu.  
  
## <a name="arranging-controls-using-padding-and-margins"></a>Rozmieszczanie formantów za pomocą wypełnienia i marginesy  
 Można także porządkować formantów w Twojej <xref:System.Windows.Forms.FlowLayoutPanel> formantu, zmieniając <xref:System.Windows.Forms.Control.Padding%2A> i <xref:System.Windows.Forms.Control.Margin%2A> właściwości.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Właściwość służy do kontrolowania umieszczania formantów w <xref:System.Windows.Forms.FlowLayoutPanel> komórki formantu. Określa odstępy między formantów podrzędnych i <xref:System.Windows.Forms.FlowLayoutPanel> obramowania formantu.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Właściwość umożliwia określenie odstępów między formantami.  
  
#### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Aby zorganizować formantów za pomocą właściwości dopełnienia i marginesów  
  
1.  Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>. Jeśli formularz jest mały, <xref:System.Windows.Forms.Button> formanty zostaną przeniesione do pierwszej kolumny <xref:System.Windows.Forms.FlowLayoutPanel> formantu.  
  
2.  Zmień wartość <xref:System.Windows.Forms.FlowLayoutPanel> formantu <xref:System.Windows.Forms.Control.Padding%2A> właściwości rozwijając <xref:System.Windows.Forms.Control.Padding%2A> wpis w **właściwości** okno i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości **20**. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie limit formantów formularzy systemu Windows z dopełnienie, marginesami oraz właściwościami AutoSize właściwość](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md). Nadany formantów podrzędnych w kierunku środka <xref:System.Windows.Forms.FlowLayoutPanel> formantu. Zwiększona wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwości wypchnięcia formantów podrzędnych od <xref:System.Windows.Forms.FlowLayoutPanel> obramowania formantu.  
  
3.  Wybierz wszystkie <xref:System.Windows.Forms.Button> formantów w <xref:System.Windows.Forms.FlowLayoutPanel> i ustaw wartość <xref:System.Windows.Forms.Control.Margin%2A> właściwości **20**. Należy pamiętać, że odstępy między <xref:System.Windows.Forms.Button> steruje rosną, dlatego są one przenoszone dalsze od siebie. Trzeba zmienić rozmiar <xref:System.Windows.Forms.FlowLayoutPanel> formant będzie większy, aby wyświetlić wszystkie formantów podrzędnych.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Wstawianie formantów poprzez dwukrotne kliknięcie w przyborniku  
 Można go wypełnić Twojej <xref:System.Windows.Forms.FlowLayoutPanel> kontroli przez dwukrotne kliknięcie formantów w **przybornika**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Wstaw formanty przez dwukrotne kliknięcie w przyborniku  
  
1.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę kontroli w **przybornika**. Należy pamiętać, że nowy <xref:System.Windows.Forms.Button> formant jest widoczny w <xref:System.Windows.Forms.FlowLayoutPanel> formantu.  
  
2.  Kliknij dwukrotnie większej liczby opcji w **przybornika**. Należy pamiętać, że nowe formanty są wyświetlane w kolejno <xref:System.Windows.Forms.FlowLayoutPanel> formantu.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Wstawianie formantu za pomocą rysowania konturu jej  
 Można wstawić do formantu <xref:System.Windows.Forms.FlowLayoutPanel> kontroli oraz określić jego rozmiar za pomocą rysowania konturu jej w komórce.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Wstawianie formantu za Rysowanie konturu jej  
  
1.  W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.Button> ikona formantu. Nie przeciągnij go na formularzu.  
  
2.  Przesuń wskaźnik myszy nad <xref:System.Windows.Forms.FlowLayoutPanel> formantu. Należy pamiętać, że kursor zmienia się na krzyżyk z <xref:System.Windows.Forms.Button> ikona kontroli dołączony.  
  
3.  Kliknij i przytrzymaj przycisk myszy.  
  
4.  Przeciągnij wskaźnik myszy Rysowanie konturu <xref:System.Windows.Forms.Button> formantu. Po zakończeniu rozmiar zwolnij przycisk myszy. Należy pamiętać, że <xref:System.Windows.Forms.Button> formant jest tworzony w następnej lokalizacji Otwórz <xref:System.Windows.Forms.FlowLayoutPanel> formantu.  
  
## <a name="inserting-controls-using-the-insertion-bar"></a>Wstawianie formantów za pomocą paska wstawiania  
 Formanty można wstawiać na określonej pozycji w <xref:System.Windows.Forms.FlowLayoutPanel> formantu. Przeciągnięcie kontroli do <xref:System.Windows.Forms.FlowLayoutPanel> obszaru klienckiego formantu, wskaż, gdy formant zostanie wstawiony zostanie wyświetlony pasek wstawiania.  
  
#### <a name="to-insert-a-control-using-the-caret"></a>Aby wstawić formantu przy użyciu karetkę  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do <xref:System.Windows.Forms.FlowLayoutPanel> kontroli, a następnie wskaż miejsce między dwiema <xref:System.Windows.Forms.Button> kontrolki. Należy pamiętać, że pasek wstawiania jest pobierana, wskazująca, gdzie <xref:System.Windows.Forms.Button> zostaną umieszczone po upuszczeniu go do <xref:System.Windows.Forms.FlowLayoutPanel> formantu. Przed musisz porzucić nowe <xref:System.Windows.Forms.Button> sterowania do <xref:System.Windows.Forms.FlowLayoutPanel> kontrolować, przenieś wskaźnik myszy około, aby sprawdzić, jak Przenosi pasek wstawiania.  
  
2.  Upuść nowy <xref:System.Windows.Forms.Button> sterowania do <xref:System.Windows.Forms.FlowLayoutPanel> formantu. Należy pamiętać, że nowe <xref:System.Windows.Forms.Button> formantu nie jest wyrównana z innych, ponieważ jego <xref:System.Windows.Forms.Control.Margin%2A> właściwość ma inną wartość.  
  
## <a name="reassigning-existing-controls-to-a-different-parent"></a>Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego  
 Można przypisać formantów, które istnieją w formularzu na nowy <xref:System.Windows.Forms.FlowLayoutPanel> formantu.  
  
#### <a name="to-reparent-existing-controls"></a>Aby zmienić elementu nadrzędnego istniejących formantów  
  
1.  Przeciągnij trzy <xref:System.Windows.Forms.Button> formantów **przybornika** na formularzu. Umieść je się w pobliżu siebie, ale pozostaw je niewyrównany.  
  
2.  W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.FlowLayoutPanel> ikona formantu. Nie przeciągnij go na formularzu.  
  
3.  Przenieś wskaźnik myszy w pobliżu trzech <xref:System.Windows.Forms.Button> kontrolki. Należy pamiętać, że kursor zmienia się na krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> ikona kontroli dołączony.  
  
4.  Kliknij i przytrzymaj przycisk myszy.  
  
5.  Przeciągnij wskaźnik myszy Rysowanie konturu <xref:System.Windows.Forms.FlowLayoutPanel> formantu. Rysuj obramowania wokół trzech <xref:System.Windows.Forms.Button> kontrolki.  
  
6.  Zwolnij przycisk myszy. Należy pamiętać, że trzech <xref:System.Windows.Forms.Button> formanty są wstawiane do <xref:System.Windows.Forms.FlowLayoutPanel> formantu.  
  
## <a name="next-steps"></a>Następne kroki  
 Można osiągnąć złożonego układu przy użyciu kombinacji panele układu i kontrolek. Sugestie dotyczące więcej eksploracji obejmują:  
  
-   Zmień rozmiar jednego z <xref:System.Windows.Forms.Button> kontroli w celu większego rozmiaru i zanotuj wpływ na układ.  
  
-   Panele układu może zawierać inne panele układu. Doświadczenia z usunięcie <xref:System.Windows.Forms.TableLayoutPanel> kontroli do istniejącego formantu.  
  
-   Dock <xref:System.Windows.Forms.FlowLayoutPanel> sterowania do formularza nadrzędnego. Zmień rozmiar formularza i zanotuj wpływ na układ.  
  
-   Ustaw <xref:System.Windows.Forms.Control.Visible%2A> właściwość formanty `false` i zanotuj, jak <xref:System.Windows.Forms.FlowLayoutPanel> przepływu w odpowiedzi.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Środowisko użytkownika systemu Windows firmy Microsoft, oficjalnego wskazówki dla deweloperów interfejsu użytkownika i projektantów. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [AutoSize — Przegląd właściwości](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Porady: dokowanie formantów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Porady: kotwiczenie formantów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [Wskazówki: Tworzenie Windows formantów formularzy dopełnienie, marginesami oraz właściwościami AutoSize właściwość](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
