---
title: 'Wskazówki: tworzenie formantów formularzy systemu Windows z uzupełnieniem, marginesami oraz właściwościami AutoSize'
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
ms.openlocfilehash: 52bc75135e4f8cf5b9c1888b2ad9f5e278c1d6e2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209480"
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a>Wskazówki: tworzenie formantów formularzy systemu Windows z uzupełnieniem, marginesami oraz właściwościami AutoSize
Rozmieszczenie kontrolek w formularzu jest wysoki priorytet dla wielu aplikacji. **Windows Forms Designer** udostępnia wiele narzędzi układu, w tym celu. Są trzy najważniejsze <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, i <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości, które znajdują się na wszystkie kontrolki Windows Forms.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Właściwość definiuje miejsca wokół formantu, że przechowuje inne kontrolki w określonej odległości od obramowania formantu.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Właściwość definiuje miejsce wewnątrz kontrolki, która zachowuje zawartość formantu (na przykład, wartość jego <xref:System.Windows.Forms.Control.Text%2A> właściwości) w określonej odległości od obramowania formantu.  
  
 Poniższa ilustracja przedstawia <xref:System.Windows.Forms.Control.Padding%2A> i <xref:System.Windows.Forms.Control.Margin%2A> właściwości formantu.  
  
 ![Wypełnienie i margines Windows formantów formularzy](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Właściwość zawiera informacje dla formantu, który ma automatycznie rozmiar samego do jego zawartości. Nie będzie rozmiar samego może być mniejszy niż wartość jego oryginalnej <xref:System.Windows.Forms.Control.Size%2A> właściwość która będzie uwzględniać wartość jego <xref:System.Windows.Forms.Control.Padding%2A> właściwości.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie projektu Windows Forms  
  
-   Ustawienie marginesów dla formantów  
  
-   Ustawienie wypełnienia dla formantów  
  
-   Automatyczne ustalanie rozmiaru kontrolki  
  
 Gdy skończysz, masz zrozumienia rolę odgrywaną przez te funkcje ważne układu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
-   Wystarczające uprawnienia, aby można było utworzyć i uruchomić projekty aplikacji Windows Forms na komputerze, w którym jest zainstalowany program Visual Studio.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest tworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Tworzenie **aplikacji Windows** projekt o nazwie `LayoutExample`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Wybierz formularz w **Windows Forms Designer**.  
  
## <a name="setting-margins-for-your-controls"></a>Ustawienie marginesów dla formantów  
 Możesz ustawić domyślnej odległości między kontrolek przy użyciu <xref:System.Windows.Forms.Control.Margin%2A> właściwości. Po przeniesieniu formantu blisko inna kontrolka, zostanie wyświetlony snapline —, pokazujący marginesy dla dwóch kontrolek. Formant, który przenosisz zostaną przyciągania do odległości definicją marginesów.  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a>Aby rozmieścić formanty w formularzu za pomocą właściwości marginesów  
  
1.  Przeciągnij dwa <xref:System.Windows.Forms.Button> kontrolki z **przybornika** do formularza.  
  
2.  Wybierz jedną z <xref:System.Windows.Forms.Button> kontroluje i przenieść blisko innych, dopóki nie są one prawie dotknięcie.  
  
     Obserwuj snapline —, który pojawia się między nimi. To jest sumą dwóch kontrolek <xref:System.Windows.Forms.Control.Margin%2A> wartości. Formant, który chcesz przenieść przyciąganie do tego odległości. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
3.  Zmiana <xref:System.Windows.Forms.Control.Margin%2A> właściwości formantów, rozwijając <xref:System.Windows.Forms.Control.Margin%2A> wpisu w **właściwości** okna i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości na 20.  
  
4.  Wybierz jedną z <xref:System.Windows.Forms.Button> kontroluje i przenieś ją w pobliżu innych.  
  
     Snapline — Definiowanie sumę wartości marginesu jest większa, a kontrolka punkty przyciągania podczas większa odległość od innego formantu.  
  
5.  Zmiana <xref:System.Windows.Forms.Control.Margin%2A> właściwości wybranej kontrolki, rozwijając <xref:System.Windows.Forms.Control.Margin%2A> wpisu w **właściwości** okna i ustawienie <xref:System.Windows.Forms.Padding.Top%2A> właściwości do 5.  
  
6.  Przenieś zaznaczony formant poniżej innej kontrolki i sprawdź, czy snapline — jest krótszy. Przenieś zaznaczony formant w lewo inne kontrolki i sprawdź, czy snapline — przechowuje wartość w kroku 4.  
  
7.  Możesz ustawić każdy z aspektów <xref:System.Windows.Forms.Control.Margin%2A> właściwości <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, różne wartości, lub można ustawić je wszystkie do tej samej wartości z <xref:System.Windows.Forms.Padding.All%2A> właściwości.  
  
## <a name="setting-padding-for-your-controls"></a>Ustawienie wypełnienia dla formantów  
 Aby uzyskać dokładne układ wymaganej dla aplikacji, kontrolki często zawierają formantów podrzędnych. Aby określić bliskość obramowania kontrolki podrzędnej obramowania kontrolki nadrzędnej, należy użyć kontrolki nadrzędnej <xref:System.Windows.Forms.Control.Padding%2A> właściwość w połączeniu z kontrolki podrzędnej <xref:System.Windows.Forms.Control.Margin%2A> właściwości. <xref:System.Windows.Forms.Control.Padding%2A> Jest również używana do sterowania odległości między elementami zawartości formantu (na przykład <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Text%2A> właściwość) do jego obramowania.  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a>Aby rozmieścić formanty w formularzu za pomocą wypełnienia  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do formularza.  
  
2.  Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość `true`.  
  
3.  Zmiana <xref:System.Windows.Forms.Control.Padding%2A> właściwości, rozwijając <xref:System.Windows.Forms.Control.Padding%2A> wpisu w **właściwości** okna i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości do 5.  
  
     Kontrolka rozwija Podaj miejsce dla nowych dopełnienia.  
  
4.  Przeciągnij <xref:System.Windows.Forms.GroupBox> z kontrolować **przybornika** do formularza. Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do <xref:System.Windows.Forms.GroupBox> kontroli. Pozycja <xref:System.Windows.Forms.Button> kontrolować, więc w prawym dolnym rogu <xref:System.Windows.Forms.GroupBox> kontroli.  
  
     Obserwuj linii przyciągania, które są wyświetlane jako <xref:System.Windows.Forms.Button> kontroli zbliża się do dołu i prawe krawędzie <xref:System.Windows.Forms.GroupBox> kontroli. Te linii przyciągania odpowiadają <xref:System.Windows.Forms.Control.Margin%2A> właściwość <xref:System.Windows.Forms.Button>.  
  
5.  Zmiana <xref:System.Windows.Forms.GroupBox> kontrolki <xref:System.Windows.Forms.Control.Padding%2A> właściwości, rozwijając <xref:System.Windows.Forms.Control.Padding%2A> wpisu w **właściwości** okna i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości na 20.  
  
6.  Wybierz <xref:System.Windows.Forms.Button> kontrolki w <xref:System.Windows.Forms.GroupBox> kontroli i przenieś ją w kierunku środka <xref:System.Windows.Forms.GroupBox>.  
  
     Linii przyciągania pojawiają się w odległości większa od obramowania <xref:System.Windows.Forms.GroupBox> kontroli. To jest sumą <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Margin%2A> właściwości i <xref:System.Windows.Forms.GroupBox> kontrolki <xref:System.Windows.Forms.Control.Padding%2A> właściwości.  
  
## <a name="automatically-sizing-your-controls"></a>Automatyczne ustalanie rozmiaru kontrolki  
 W niektórych aplikacjach rozmiaru formantu nie będzie taka sama w czasie wykonywania jakim znajdował się w czasie projektowania. Tekst <xref:System.Windows.Forms.Button> kontrolki, na przykład mogą zostać podjęte z bazy danych, a jej długość nie będzie znane z wyprzedzeniem.  
  
 Gdy <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość jest ustawiona na `true`, kontrolka zostanie sam rozmiar do jego zawartości. Aby uzyskać więcej informacji, zobacz [AutoSize właściwość — omówienie](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a>Aby rozmieścić formanty w formularzu za pomocą właściwości AutoSize  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do formularza.  
  
2.  Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość `true`.  
  
3.  Zmiana <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Text%2A> właściwość "**ten przycisk ma długi ciąg dla właściwości Text**."  
  
     Podczas zatwierdzania zmian, <xref:System.Windows.Forms.Button> zmienia rozmiar formantu dopasuje nowego tekstu.  
  
4.  Przeciągnij kolejny <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do formularza.  
  
5.  Zmiana <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Text%2A> właściwość "**ten przycisk ma długi ciąg dla właściwości Text.**"  
  
     Podczas zatwierdzania zmian, <xref:System.Windows.Forms.Button> formantu nie zmieniał swój rozmiar i zostanie obcięta przez prawą krawędzią kontrolki.  
  
6.  Zmiana <xref:System.Windows.Forms.Control.Padding%2A> właściwości, rozwijając <xref:System.Windows.Forms.Control.Padding%2A> wpisu w **właściwości** okna i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości do 5.  
  
     Wszystkie cztery strony jest przycinany tekst wewnątrz formantu.  
  
7.  Zmiana <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość `true`.  
  
     <xref:System.Windows.Forms.Button> Kontroli zmienia rozmiar, aby obejmować cały ciąg. Ponadto dodano dopełnienie wokół tekstu, co powoduje <xref:System.Windows.Forms.Button> sterowania, aby rozwinąć we wszystkich czterech kierunkach.  
  
8.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do formularza. Umieść go w pobliżu prawego dolnego rogu formularza.  
  
9. Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość `true`.  
  
10. Ustaw <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwości <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.  
  
11. Zmiana <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Text%2A> właściwość "**ten przycisk ma długi ciąg dla właściwości Text.**"  
  
     Podczas zatwierdzania zmian, <xref:System.Windows.Forms.Button> kontroli rozmiaru w lewo. Ogólnie rzecz biorąc, automatycznej zmiany rozmiaru spowoduje zwiększenie rozmiaru kontrolki, w przeciwnym kierunku jego <xref:System.Windows.Forms.Control.Anchor%2A> ustawienie właściwości.  
  
## <a name="autosize-and-autosizemode-properties"></a>AutoSize i AutoSizeMode właściwości  
 Niektóre formanty obsługują `AutoSizeMode` właściwość, która zapewnia bardziej precyzyjną kontrolę nad zachowaniem automatycznej zmiany rozmiaru formantu.  
  
#### <a name="to-use-the-autosizemode-property"></a>Aby użyć AutoSizeMode właściwość  
  
1.  Przeciągnij <xref:System.Windows.Forms.Panel> z kontrolować **przybornika** do formularza.  
  
2.  Ustaw wartość <xref:System.Windows.Forms.Panel> kontrolki <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość `true`.  
  
3.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do <xref:System.Windows.Forms.Panel> kontroli.  
  
4.  Miejsce <xref:System.Windows.Forms.Button> formant w pobliżu prawego dolnego rogu <xref:System.Windows.Forms.Panel> kontroli.  
  
5.  Wybierz <xref:System.Windows.Forms.Panel> kontroli i Pobierz prawy dolny uchwyt. Zmień rozmiar <xref:System.Windows.Forms.Panel> do większych i mniejszych formant.  
  
    > [!NOTE]
    >  Możesz swobodnie zmieniać rozmiar <xref:System.Windows.Forms.Panel> kontroli, ale nie jego rozmiaru mniejszy niż pozycja <xref:System.Windows.Forms.Button> formantu prawym dolnym rogu. To zachowanie jest określony przez wartość domyślną `AutoSizeMode` właściwość, która jest <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.  
  
6.  Ustaw wartość <xref:System.Windows.Forms.Panel> kontrolki `AutoSizeMode` właściwość <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.  
  
     <xref:System.Windows.Forms.Panel> Kontroli rozciąga się Otocz <xref:System.Windows.Forms.Button> kontroli. Nie można zmienić rozmiaru <xref:System.Windows.Forms.Panel> kontroli.  
  
7.  Przeciągnij <xref:System.Windows.Forms.Button> kontroli kierunku lewego górnego rogu <xref:System.Windows.Forms.Panel> kontroli.  
  
     <xref:System.Windows.Forms.Panel> Kontroli dopasowuje się do <xref:System.Windows.Forms.Button> położenie nowej kontrolki.  
  
## <a name="next-steps"></a>Następne kroki  
 Istnieje wiele innych funkcji układu dla rozmieszczanie formantów w aplikacjach Windows Forms. Poniżej przedstawiono niektóre kombinacje, które może wypróbować:  
  
-   Tworzenie formularza przy użyciu <xref:System.Windows.Forms.TableLayoutPanel> kontroli. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów Windows Forms za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Spróbuj zmienić wartości <xref:System.Windows.Forms.TableLayoutPanel> kontrolki <xref:System.Windows.Forms.Control.Padding%2A> właściwości, jak również <xref:System.Windows.Forms.Control.Margin%2A> właściwość jego formantów podrzędnych.  
  
-   Wypróbuj, w tym samym eksperymentu przy użyciu <xref:System.Windows.Forms.FlowLayoutPanel> kontroli. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów Windows Forms za pomocą FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
-   Eksperymentuj z dokowanie formantów podrzędnych w <xref:System.Windows.Forms.Panel> kontroli. <xref:System.Windows.Forms.Control.Padding%2A> Właściwość jest bardziej ogólnych realizacji <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> właściwości, na które może spełnić samodzielnie, jest to poprzez umieszczenie kontrolki podrzędnej <xref:System.Windows.Forms.Panel> kontrolki i ustawiając kontrolę rodzicielską <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>. Ustaw <xref:System.Windows.Forms.Panel> kontrolki <xref:System.Windows.Forms.Control.Padding%2A> właściwości różnych wartości i zwróć uwagę, efekt.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 [AutoSize, właściwość — omówienie](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
