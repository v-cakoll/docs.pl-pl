---
title: 'Wskazówki: rozmieszczanie formantów w formularzach systemu Windows za pomocą linii przyciągania'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: 170b79f03515ab371f7013c267b28ba85dafd0f5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180621"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>Wskazówki: rozmieszczanie formantów w formularzach systemu Windows za pomocą linii przyciągania
Rozmieszczenie kontrolek w formularzu jest wysoki priorytet dla wielu aplikacji. Windows Forms Designer udostępnia wiele narzędzi układu, w tym celu. Jednym z najważniejszych jest <xref:System.Windows.Forms.Design.Behavior.SnapLine> funkcji.  
  
 Linii przyciągania Pokaż dokładnie, gdzie wyrównać formanty z innymi formantami. Również pokazują zalecane odległości marginesy między kontrolkami, zgodnie z wytycznymi interfejsu użytkownika Windows. Aby uzyskać więcej informacji, zobacz [projektowania interfejsu użytkownika i rozwoju](https://go.microsoft.com/FWLink/?LinkId=83878).  
  
 Linii przyciągania ułatwiają wyrównywanie formantów na ostre, profesjonalnych wygląd i zachowanie (wygląd i działanie).  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie projektu Windows Forms  
  
-   Odstępy i wyrównywanie formantów, za pomocą linii przyciągania  
  
-   Dopasowanie do formularza i marginesów kontenera  
  
-   Wyrównywanie kontrolek zgrupowanych  
  
-   Za pomocą linii przyciągania, aby umieścić kontrolkę zwijanie jej rozmiaru  
  
-   Za pomocą linii przyciągania podczas przeciągania kontrolki z przybornika  
  
-   Zmiana rozmiaru formantów, za pomocą linii przyciągania  
  
-   Wyrównanie etykiety do formantu tekstu  
  
-   Za pomocą linii przyciągania z klawiatury  
  
-   Liniami przyciągania oraz panele układów  
  
-   Wyłączanie linii przyciągania  
  
 Gdy skończysz, masz zrozumienia układ roli za pomocą linii przyciągania funkcji.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest tworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji systemu Windows o nazwie "SnaplineExample" (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).  
  
2.  Wybierz formularz w projektancie formularzy.  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>Odstępy i wyrównywanie formantów, za pomocą linii przyciągania  
 Linii przyciągania umożliwiają dokładne i intuicyjny sposób wyrównywanie formantów na formularzu. Pojawiają się podczas przenoszenia wybranej kontrolki lub kontrolki obok pozycji, która będzie wyrównane z innego formantu lub zbiór kontrolek. Wybór będzie "przyciągana" sugerowane pozycji w trakcie przemieszczania upłynął innych kontrolek.  
  
#### <a name="to-arrange-controls-using-snaplines"></a>Aby rozmieścić formanty za pomocą linii przyciągania  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do formularza.  
  
2.  Przenieś <xref:System.Windows.Forms.Button> formantu do prawego dolnego rogu formularza. Uwaga linii przyciągania, które są wyświetlane jako <xref:System.Windows.Forms.Button> kontroli zbliża się do dołu i prawe krawędzie formularza. Te linii przyciągania wyświetlić zalecaną odległość między obramowania formantu formularza.  
  
3.  Przenieś <xref:System.Windows.Forms.Button> kontroli wokół obramowania formularza i zwróć uwagę, w których występują linii przyciągania. Po zakończeniu przenoszenia <xref:System.Windows.Forms.Button> kontrolki formularz na środku.  
  
4.  Przeciągnij kolejny <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do formularza.  
  
5.  Przenieś drugi <xref:System.Windows.Forms.Button> kontrolowanie momentu niemal poziomu, przy czym pierwsze. Zanotuj snapline —, wyświetlany w linii bazowej tekstu zarówno przycisków i należy pamiętać, że formant, który chcesz przenieść punkty przyciągania podczas położeniu dokładnie poziomu przy użyciu innej kontrolki.  
  
6.  Przenieś drugi <xref:System.Windows.Forms.Button> kontrolować, dopóki nie jest umieszczony bezpośrednio nad pierwszym. Należy pamiętać, linii przyciągania, są wyświetlane wzdłuż lewej i prawej krawędzi oba przyciski, a następnie należy zauważyć, że formant zostanie przenoszenie przyciąganie do pozycji, która jest dokładnie wyrównana z innej kontrolki.  
  
7.  Wybierz jedną z <xref:System.Windows.Forms.Button> kontroluje i przenieść blisko innych, dopóki nie są one prawie dotknięcie. Należy pamiętać, snapline —, który pojawia się między nimi. To jest to zalecane odległość między obramowania kontrolki. Należy również zauważyć, że formant, który chcesz przenieść przyciąganie do tej pozycji.  
  
8.  Przeciągnij dwa <xref:System.Windows.Forms.Panel> kontrolki z **przybornika** do formularza.  
  
9. Przenieść jeden z <xref:System.Windows.Forms.Panel> kontroluje, dopóki nie zostanie prawie poziomu, przy czym pierwsze. Należy pamiętać, linii przyciągania, są wyświetlane wzdłuż górnej i dolnej krawędzi obie kontrolki, która należy pamiętać, że formant, który chcesz przenieść punkty przyciągania podczas położeniu dokładnie poziomu przy użyciu innej kontrolki.  
  
## <a name="aligning-to-form-and-container-margins"></a>Dopasowanie do formularza i marginesów kontenera  
 Linii przyciągania ułatwiają wyrównywanie formantów do formularza i kontener marginesu w spójny sposób.  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a>Aby wyrównać formanty do formularza i kontener marginesów  
  
1.  Wybierz jedną z <xref:System.Windows.Forms.Button> kontroluje i przenieść blisko prawej krawędzi formularza, aż pojawi się snapline —. Snapline — odległości od prawej krawędzi jest sumą formantu <xref:System.Windows.Forms.Control.Margin%2A> właściwości i w formularzu <xref:System.Windows.Forms.Control.Padding%2A> wartości właściwości.  
  
> [!NOTE]
>  Jeśli formularz <xref:System.Windows.Forms.Control.Padding%2A> właściwość jest ustawiona na 0,0,0,0, Windows Forms Designer zapewnia formularza zasłonięte <xref:System.Windows.Forms.Control.Padding%2A> wartość 9,9,9,9. Aby zastąpić to zachowanie, należy przypisać wartość inna niż 0,0,0,0.  
  
1.  Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Margin%2A> właściwości, rozwijając <xref:System.Windows.Forms.Control.Margin%2A> wpis **właściwości** okna i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości na wartość 0. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie się Windows formantów formularzy przy użyciu dopełnienie, marginesy oraz właściwościami AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).  
  
2.  Przenieś <xref:System.Windows.Forms.Button> kontroli blisko prawej krawędzi formularza, aż pojawi się snapline —. Odległość tę teraz jest określony przez wartość w postaci <xref:System.Windows.Forms.Control.Padding%2A> właściwości.  
  
3.  Przeciągnij <xref:System.Windows.Forms.GroupBox> z kontrolować **przybornika** do formularza.  
  
4.  Zmień wartość właściwości <xref:System.Windows.Forms.GroupBox> kontrolki <xref:System.Windows.Forms.Control.Padding%2A> właściwości, rozwijając <xref:System.Windows.Forms.Control.Padding%2A> wpis **właściwości** okna i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości do 10.  
  
5.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do <xref:System.Windows.Forms.GroupBox> kontroli.  
  
6.  Przenieś <xref:System.Windows.Forms.Button> kontroli blisko prawej krawędzi <xref:System.Windows.Forms.GroupBox> kontrolować, aż pojawi się snapline —. Przenieś <xref:System.Windows.Forms.Button> kontrolki w <xref:System.Windows.Forms.GroupBox> kontroli i zwróć uwagę, w których występują linii przyciągania.  
  
## <a name="aligning-to-grouped-controls"></a>Wyrównywanie kontrolek zgrupowanych  
 Linii przyciągania umożliwia wyrównywanie kontrolki zgrupowane również jako kontrolki w ramach <xref:System.Windows.Forms.GroupBox> kontroli.  
  
#### <a name="to-align-to-grouped-controls"></a>Dostosowanie do kontrolki zgrupowane  
  
1.  Wybierz dwóch kontrolek w formularzu. Poruszanie się zaznaczenie i zwróć uwagę linii przyciągania, pojawiających się między wybraną i inne kontrolki.  
  
2.  Przeciągnij <xref:System.Windows.Forms.GroupBox> z kontrolować **przybornika** do formularza.  
  
3.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do <xref:System.Windows.Forms.GroupBox> kontroli.  
  
4.  Wybierz jedną z <xref:System.Windows.Forms.Button> kontroluje i poruszania się po <xref:System.Windows.Forms.GroupBox> kontroli. Uwaga linii przyciągania, które pojawiają się na krawędzi <xref:System.Windows.Forms.GroupBox> kontroli. Należy również zauważyć linii przyciągania, które pojawiają się na krawędzi <xref:System.Windows.Forms.Button> formant, który jest zawarty w <xref:System.Windows.Forms.GroupBox> kontroli. Formanty, które są elementami podrzędnymi kontrolki kontenera obsługują także linii przyciągania.  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Za pomocą linii przyciągania, aby umieścić kontrolkę zwijanie jej rozmiaru  
 Linii przyciągania ułatwiają wyrównywanie formantów, kiedy należy najpierw umieścić je w formularzu.  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Umieść formant zwijanie jej rozmiar za pomocą linii przyciągania  
  
1.  W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.Button> ikonę kontrolki. Nie przeciągnij go na formularzu.  
  
2.  Przesuń wskaźnik myszy nad powierzchnię projektową formularza. Należy zauważyć, że wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.Button> ikonę kontrolki dołączone. Należy również zauważyć linii przyciągania, wyświetlane proponować wyrównany pozycje <xref:System.Windows.Forms.Button> kontroli.  
  
3.  Kliknij i przytrzymaj przycisk myszy.  
  
4.  Przeciągnij wskaźnik myszy na formularzu. Należy pamiętać, że jest wstawiany konspektu, wskazującą położenie i rozmiar formantu.  
  
5.  Przeciągnij kursor do momentu powoduje wyrównanie z inną kontrolką w formularzu. Pamiętaj, że snapline — pojawia się w celu wskazania wyrównania.  
  
6.  Zwolnij przycisk myszy. Formant zostanie utworzony na położenie i rozmiar wskazywanym przez konspektu.  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Za pomocą linii przyciągania podczas przeciągania kontrolki z przybornika  
 Linii przyciągania ułatwiają wyrównywanie formantów podczas przeciągania z **przybornika** do formularza.  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Aby użyć linii przyciągania podczas przeciągania kontrolki z przybornika  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do formularza, ale nie zwolnij przycisk myszy.  
  
2.  Przesuń wskaźnik myszy nad powierzchnię projektową formularza. Należy pamiętać, że wskaźnik zmieni się na wskazują pozycję, w której nowy <xref:System.Windows.Forms.Button> formant zostanie utworzony.  
  
3.  Przeciągnij wskaźnik myszy na formularzu. Należy pamiętać, linii przyciągania, wyświetlane proponować wyrównany pozycje <xref:System.Windows.Forms.Button> kontroli. Znajdź pozycji, która jest powiązana z innymi kontrolkami.  
  
4.  Zwolnij przycisk myszy. Formant zostanie utworzony w miejscu wskazywanym przez linii przyciągania.  
  
## <a name="resizing-controls-using-snaplines"></a>Zmiana rozmiaru formantów, za pomocą linii przyciągania  
 Linii przyciągania ułatwiają wyrównywanie formantów, gdy zmieniasz rozmiar.  
  
#### <a name="to-resize-a-control-using-snaplines"></a>Aby zmienić rozmiar formantu za pomocą linii przyciągania  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do formularza.  
  
2.  Zmień rozmiar <xref:System.Windows.Forms.Button> kontroli przez Przechwytywanie jeden rogu uchwytów zmiany rozmiaru, a następnie przeciągając. Aby uzyskać więcej informacji, zobacz [porady: zmiana rozmiaru formantów na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).  
  
3.  Przeciągnij uchwyt zmiany rozmiaru, dopóki jeden z <xref:System.Windows.Forms.Button> obramowania kontrolki jest wyrównany z inną kontrolką. Pamiętaj, że snapline — zostanie wyświetlona. Należy również zauważyć, że uchwyt zmiany rozmiaru przyciąganie do pozycji snapline —.  
  
4.  Zmień rozmiar <xref:System.Windows.Forms.Button> kontroli w różnych kierunkach i dopasuj uchwyt zmiany rozmiaru, aby inne kontrolki. Należy pamiętać o tym, jak linii przyciągania są wyświetlane w różnych orientacje, aby wskazać wyrównania.  
  
## <a name="aligning-a-label-to-a-controls-text"></a>Wyrównanie etykiety do formantu tekstu  
 Niektóre kontrolki oferują snapline — wyrównywania inne formanty do wyświetlanego tekstu.  
  
#### <a name="to-align-a-label-to-a-controls-text"></a>Aby wyrównać etykietę do kontrolki tekstu  
  
1.  Przeciągnij <xref:System.Windows.Forms.TextBox> z kontrolować **przybornika** do formularza. Gdy usuniesz <xref:System.Windows.Forms.TextBox> sterowania do formularza, kliknij symbol tagu inteligentne i wybierz **Ustaw tekst na textBox1** opcji. Aby uzyskać więcej informacji, zobacz [przewodnik: wykonywanie typowych zadań przy użyciu tagów inteligentnych do kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).  
  
2.  Przeciągnij <xref:System.Windows.Forms.Label> z kontrolować **przybornika** do formularza.  
  
3.  Zmień wartość właściwości <xref:System.Windows.Forms.Label> kontrolki <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość `true`. Należy pamiętać, że obramowania formantu jest dopasowana do wyświetlania tekstu.  
  
4.  Przenieś <xref:System.Windows.Forms.Label> kontroli po lewej stronie <xref:System.Windows.Forms.TextBox> kontrolować, dzięki czemu jest wyrównane do dolnej krawędzi <xref:System.Windows.Forms.TextBox> kontroli. Należy pamiętać, snapline —, który pojawia się wzdłuż dolnej krawędzi dwóch kontrolek.  
  
5.  Przenieś <xref:System.Windows.Forms.Label> kontroli nieco tendencję do momentu <xref:System.Windows.Forms.Label> tekstu i <xref:System.Windows.Forms.TextBox> tekstu są wyrównane. Należy pamiętać, snapline — inaczej ze stylem, zostanie wyświetlone, wskazująca, kiedy są wyrównane pola tekstowego obie kontrolki.  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>Za pomocą linii przyciągania z klawiatury  
 Linii przyciągania ułatwiają wyrównywanie formantów, gdy są rozmieszczanie ich za pomocą klawiszy strzałek.  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a>Linii przyciągania za pomocą klawiatury  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do formularza. Umieść go w lewym górnym rogu formularza.  
  
2.  Naciśnij klawisze CTRL + Strzałka w dół. Pamiętaj, że kontrolka przenosi w dół formularza do pierwszej pozycji dostępnych wyrównanie w poziomie.  
  
3.  Naciśnij klawisze CTRL + Strzałka w dół, aż formant osiągnie dolnej części formularza. Należy pamiętać, pozycje, które zajmuje, kiedy przesuwa się on w dół do formularza.  
  
4.  Naciśnij klawisze CTRL + Strzałka w prawo. Pamiętaj, że kontrolka porusza się na formularzu do pierwszej pozycji dostępnych wyrównanie w pionie.  
  
5.  Naciśnij klawisze CTRL + Strzałka w prawo, aż formant osiągnie rogu formularza. Należy pamiętać, pozycje, które zajmuje, kiedy przesuwa się on w formularzu.  
  
6.  Przenieś formant na formularzu za pomocą kombinacji klawiszy strzałek. Należy pamiętać, pozycje, które zajmuje kontrolki i linii przyciągania, który towarzyszy im.  
  
7.  Naciśnij klawisze SHIFT + klawiszy strzałek, aby zmienić rozmiar <xref:System.Windows.Forms.Button> kontrola zwiększa o jeden piksel.  
  
8.  Naciśnij klawisze CTRL + SHIFT + klawiszy strzałek, aby zmienić rozmiar <xref:System.Windows.Forms.Button> kontroli w przyrostach snapline —.  
  
## <a name="snaplines-and-layout-panels"></a>Liniami przyciągania oraz panele układów  
 Linii przyciągania są wyłączone w ramach paneli układów.  
  
#### <a name="to-selectively-disable-snaplines"></a>Aby wyłączyć linii przyciągania  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.  
  
2.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę kontrolki w **przybornika**. Należy zauważyć, że nowy formant przycisku, który pojawia się w <xref:System.Windows.Forms.TableLayoutPanel> kontrolki pierwszej komórki.  
  
3.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę kontrolki w **przybornika** dwa razy więcej. Spowoduje to pozostawienie co pustą komórkę w <xref:System.Windows.Forms.TableLayoutPanel> kontroli.  
  
4.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do pustej komórki z <xref:System.Windows.Forms.TableLayoutPanel> kontroli. Pamiętaj, że są wyświetlane nie linii przyciągania.  
  
5.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować poza <xref:System.Windows.Forms.TableLayoutPanel> kontroli i poruszania się po <xref:System.Windows.Forms.TableLayoutPanel> kontroli. Pamiętaj, że linii przyciągania pojawiają się ponownie.  
  
## <a name="disabling-snaplines"></a>Wyłączanie linii przyciągania  
 Linii przyciągania są włączone domyślnie. Można wyłączyć linii przyciągania selektywnie lub można je wyłączyć w środowisku projektowym.  
  
#### <a name="to-selectively-disable-snaplines"></a>Aby wyłączyć linii przyciągania  
  
-   Naciśnij klawisz ALT i podczas przenoszenia kontrolki na formularzu.  
  
     Pamiętaj, że są wyświetlane nie linii przyciągania formantu nie przyciąganie do wszelkich potencjalnych pozycji wyrównania.  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a>Aby wyłączyć linii przyciągania w środowisku projektowania  
  
1.  Z **narzędzia** menu Otwórz **opcje** okno dialogowe. Otwórz okno dialogowe Windows Forms Designer. Aby uzyskać więcej informacji, zobacz [ogólne, Windows Forms Designer, okno dialogowe Opcje](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).  
  
2.  Wybierz **ogólne** węzła. W **tryb układu** sekcji, zmień zaznaczoną wartość z **linii przyciągania** do **SnapToGrid**.  
  
3.  Kliknij przycisk OK, aby zastosować ustawienia.  
  
4.  Wybierz kontrolkę w formularzu i poruszać innych kontrolek. Należy pamiętać, że zostały wyświetlone opcje linii przyciągania.  
  
## <a name="next-steps"></a>Następne kroki  
 Linii przyciągania oferują intuicyjne środki wyrównywanie formantów na formularzu. Sugestie dotyczące więcej eksploracji obejmują:  
  
-   Spróbuj zagnieżdżanie <xref:System.Windows.Forms.GroupBox> kontroli w ramach innego <xref:System.Windows.Forms.GroupBox> kontroli. Miejsce <xref:System.Windows.Forms.Button> kontrolki podrzędne <xref:System.Windows.Forms.GroupBox> kontroli, a druga nadrzędnym <xref:System.Windows.Forms.GroupBox> kontroli. Przenieś <xref:System.Windows.Forms.Button> około kontrolki i zobacz, jak linii przyciągania cross granice kontenera.  
  
-   Tworzenie kolumny <xref:System.Windows.Forms.TextBox> kontrolek i odpowiednią kolumnę <xref:System.Windows.Forms.Label> kontrolki. Ustaw wartość <xref:System.Windows.Forms.Label> kontrolek <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość `true`. Przenoszenie za pomocą linii przyciągania <xref:System.Windows.Forms.Label> kontroluje, dzięki czemu ich wyświetlany tekst będzie wyrównany z tekstem w <xref:System.Windows.Forms.TextBox> kontrolki.  
  
 Aby uzyskać informacji na temat projektowania interfejsu użytkownika Windows, zobacz książki *środowisko użytkownika systemu Microsoft Windows, oficjalne wskazówki dla deweloperów interfejsu użytkownika i projektantów* Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>  
 [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
