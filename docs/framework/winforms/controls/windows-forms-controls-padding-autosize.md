---
title: "Wskazówki: tworzenie formantów formularzy systemu Windows z uzupełnieniem, marginesami oraz właściwościami AutoSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 797a432bb8cfd3af3b5f030be8f71c78a1a393e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a>Wskazówki: tworzenie formantów formularzy systemu Windows z uzupełnieniem, marginesami oraz właściwościami AutoSize
Rozmieszczenie kontrolek w formularzu jest wysoki priorytet dla wielu aplikacji. **Projektant formularzy systemu Windows** udostępnia wiele narzędzi układu, w tym celu. Trzy najważniejsze są <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, i <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości, które znajdują się na wszystkie formanty formularzy systemu Windows.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Właściwość definiuje obszar wokół formantu, czy przechowuje inne formanty w określonej odległości od obramowania formantu.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Właściwość definiuje miejsce wewnątrz kontrolkę, która zachowuje zawartość formantu (na przykład wartość jego <xref:System.Windows.Forms.Control.Text%2A> właściwości) w określonej odległości od obramowania formantu.  
  
 Na poniższej ilustracji pokazano <xref:System.Windows.Forms.Control.Padding%2A> i <xref:System.Windows.Forms.Control.Margin%2A> właściwości formantu.  
  
 ![Formanty formularzy dopełnienia i marginesów dla systemu Windows](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Właściwość nakazuje, aby automatycznie zmienia swój rozmiar do jego zawartości. Nie zmieni rozmiar samego może być mniejszy niż wartość jego oryginalnej <xref:System.Windows.Forms.Control.Size%2A> wartość uwzględnia właściwości, a jego <xref:System.Windows.Forms.Control.Padding%2A> właściwości.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu formularzy systemu Windows  
  
-   Ustawienie marginesów dla formantów  
  
-   Ustawienie wypełnienia dla formantów  
  
-   Automatycznie zmiany rozmiaru formantów  
  
 Gdy skończysz, konieczne będzie zrozumienia rolę odgrywaną przez te funkcje ważne układu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu potrzebne są:  
  
-   Wystarczających uprawnień, aby mieć możliwość tworzenia i uruchamiania projektów aplikacji formularzy systemu Windows na komputerze, którym jest zainstalowany program Visual Studio.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz **aplikacji systemu Windows** projektu o nazwie `LayoutExample`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Wybierz formularza w **Projektant formularzy systemu Windows**.  
  
## <a name="setting-margins-for-your-controls"></a>Ustawienie marginesów dla formantów  
 Można ustawić w domyślnej odległości między formantów przy użyciu <xref:System.Windows.Forms.Control.Margin%2A> właściwości. W przypadku przenoszenia formantu blisko inny formant, zostanie wyświetlone snapline —, pokazujący marginesów dwóch formantów. Formant, który przenosisz również spowoduje przyciąganie do odległość zdefiniowane przez marginesów.  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a>Aby rozmieszczanie formantów w formularzu przy użyciu właściwości margines  
  
1.  Przeciągnij dwa <xref:System.Windows.Forms.Button> formantów **przybornika** na formularzu.  
  
2.  Wybierz jedną z <xref:System.Windows.Forms.Button> steruje i przenieść blisko innych, dopóki nie są one prawie dotknięcie.  
  
     Obserwować snapline —, który pojawia się między nimi. Odległość jest sumą dwóch formantów <xref:System.Windows.Forms.Control.Margin%2A> wartości. Formant, który przenosisz przyciąganie do tej odległości. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów na formularzach systemu Windows przy użyciu linie przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
3.  Zmień <xref:System.Windows.Forms.Control.Margin%2A> właściwości formantów rozwijając <xref:System.Windows.Forms.Control.Margin%2A> wpis w **właściwości** okno i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości na 20.  
  
4.  Wybierz jedną z <xref:System.Windows.Forms.Button> formanty i przeniesienie go blisko innych.  
  
     Snapline — Definiowanie sumę wartości marginesu jest większa i formantu przyciąganie do większej odległości od innych formantu.  
  
5.  Zmień <xref:System.Windows.Forms.Control.Margin%2A> właściwości zaznaczonego formantu rozwijając <xref:System.Windows.Forms.Control.Margin%2A> wpis w **właściwości** okno i ustawienie <xref:System.Windows.Forms.Padding.Top%2A> właściwości na wartość 5.  
  
6.  Przenieś zaznaczony formant poniżej innych sterowania i sprawdź, czy snapline — jest krótszy. Przenieś wybraną kontrolkę w lewo innych sterowania i sprawdź, czy snapline — zachowuje wartość odczytaną w kroku 4.  
  
7.  Można ustawić każdy z aspektów <xref:System.Windows.Forms.Control.Margin%2A> właściwość <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, różne wartości, lub można ustawić je wszystkie do tej samej wartości z <xref:System.Windows.Forms.Padding.All%2A> właściwości.  
  
## <a name="setting-padding-for-your-controls"></a>Ustawienie wypełnienia dla formantów  
 Do uzyskania dokładnych układu wymagane dla aplikacji, formantów często będzie zawierać formantów podrzędnych. Aby określić bliskości obramowania formantu podrzędnego obramowania formantu nadrzędnego, należy użyć formantu nadrzędnego <xref:System.Windows.Forms.Control.Padding%2A> właściwość w połączeniu z formant podrzędny <xref:System.Windows.Forms.Control.Margin%2A> właściwości. <xref:System.Windows.Forms.Control.Padding%2A> Jest również używana do kontrolowania zbliżeniowe zawartości formantu (na przykład <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Text%2A> właściwości) do jego granic.  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a>Aby rozmieszczanie formantów w formularzu za pomocą wypełnienia  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularzu.  
  
2.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości `true`.  
  
3.  Zmień <xref:System.Windows.Forms.Control.Padding%2A> właściwości rozwijając <xref:System.Windows.Forms.Control.Padding%2A> wpis w **właściwości** okno i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości na wartość 5.  
  
     Aby zapewnić miejsce dla nowych uzupełnienie rozszerza się formantu.  
  
4.  Przeciągnij <xref:System.Windows.Forms.GroupBox> kontrolować z **przybornika** na formularzu. Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do <xref:System.Windows.Forms.GroupBox> formantu. Pozycja <xref:System.Windows.Forms.Button> kontrolować, dlatego jest wyrównana prawym dolnym rogu <xref:System.Windows.Forms.GroupBox> formantu.  
  
     Obserwować linie przyciągania, który pojawia się jako <xref:System.Windows.Forms.Button> kontroli zbliża się do dolnej i prawej obramowanie <xref:System.Windows.Forms.GroupBox> formantu. Te linie przyciągania odpowiadają <xref:System.Windows.Forms.Control.Margin%2A> właściwość <xref:System.Windows.Forms.Button>.  
  
5.  Zmień <xref:System.Windows.Forms.GroupBox> formantu <xref:System.Windows.Forms.Control.Padding%2A> właściwości rozwijając <xref:System.Windows.Forms.Control.Padding%2A> wpis w **właściwości** okno i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości na 20.  
  
6.  Wybierz <xref:System.Windows.Forms.Button> kontroli w ramach <xref:System.Windows.Forms.GroupBox> kontroli i przenieś ją do środka <xref:System.Windows.Forms.GroupBox>.  
  
     Linie przyciągania pojawiają się w większej odległości od obramowania <xref:System.Windows.Forms.GroupBox> formantu. Odległość to suma <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Margin%2A> właściwości i <xref:System.Windows.Forms.GroupBox> formantu <xref:System.Windows.Forms.Control.Padding%2A> właściwości.  
  
## <a name="automatically-sizing-your-controls"></a>Automatycznie zmiany rozmiaru formantów  
 W niektórych aplikacjach rozmiaru formantu nie będzie taka sama w czasie wykonywania jakim znajdował się w czasie projektowania. Tekst <xref:System.Windows.Forms.Button> kontrolki, na przykład może być pobranych z bazy danych, a jej długość nie będzie znane z wyprzedzeniem.  
  
 Gdy <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość jest ustawiona na `true`, formantu zmieni się rozmiar do jego zawartości. Aby uzyskać więcej informacji, zobacz [AutoSize — Przegląd właściwości](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a>Aby rozmieszczanie formantów w formularzu za pomocą AutoSize właściwość  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularzu.  
  
2.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości `true`.  
  
3.  Zmień <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Text%2A> dla właściwości "**ten przycisk jest długi ciąg dla właściwości Text**."  
  
     Po zatwierdzeniu zmian, <xref:System.Windows.Forms.Button> zmienia rozmiar kontrolki dopasuje nowego tekstu.  
  
4.  Przeciągnij kolejny <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularzu.  
  
5.  Zmień <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Text%2A> dla właściwości "**ten przycisk jest długi ciąg dla właściwości Text.**"  
  
     Po zatwierdzeniu zmian, <xref:System.Windows.Forms.Button> formantu nie zmieniany i zostanie obcięta przez prawą krawędzią formantu.  
  
6.  Zmień <xref:System.Windows.Forms.Control.Padding%2A> właściwości rozwijając <xref:System.Windows.Forms.Control.Padding%2A> wpis w **właściwości** okno i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości na wartość 5.  
  
     Wszystkie cztery strony jest przycinany tekst wewnątrz formantu.  
  
7.  Zmień <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości `true`.  
  
     <xref:System.Windows.Forms.Button> Kontroli samodzielnie zmienia rozmiar obejmujące cały ciąg. Ponadto dodano wypełnienia wokół tekstu, co powoduje <xref:System.Windows.Forms.Button> formantu, aby rozwinąć we wszystkich czterech kierunkach.  
  
8.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularzu. Umieść go w pobliżu prawym dolnym rogu formularza.  
  
9. Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości `true`.  
  
10. Ustaw <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.  
  
11. Zmień <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Text%2A> dla właściwości "**ten przycisk jest długi ciąg dla właściwości Text.**"  
  
     Po zatwierdzeniu zmian, <xref:System.Windows.Forms.Button> kontroli samodzielnie zmienia rozmiar w lewo. Ogólnie rzecz biorąc, automatycznej zmiany rozmiaru spowoduje zwiększenie rozmiaru formantu w przeciwnym kierunku jej <xref:System.Windows.Forms.Control.Anchor%2A> ustawienie właściwości.  
  
## <a name="autosize-and-autosizemode-properties"></a>AutoSize i właściwości AutoSizeMode  
 Niektóre formanty obsługują `AutoSizeMode` właściwość, która zapewnia bardziej precyzyjną kontrolę nad zachowanie automatycznej zmiany rozmiaru formantu.  
  
#### <a name="to-use-the-autosizemode-property"></a>Aby użyć AutoSizeMode właściwość  
  
1.  Przeciągnij <xref:System.Windows.Forms.Panel> kontrolować z **przybornika** na formularzu.  
  
2.  Ustaw wartość <xref:System.Windows.Forms.Panel> formantu <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości `true`.  
  
3.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do <xref:System.Windows.Forms.Panel> formantu.  
  
4.  Miejsce <xref:System.Windows.Forms.Button> formantu prawym dolnym rogu <xref:System.Windows.Forms.Panel> formantu.  
  
5.  Wybierz <xref:System.Windows.Forms.Panel> kontroli i przechwycić uchwyt zmiany rozmiaru w prawym dolnym. Zmień rozmiar <xref:System.Windows.Forms.Panel> formantu większych i mniejszych.  
  
    > [!NOTE]
    >  Za darmo można zmienić rozmiar <xref:System.Windows.Forms.Panel> sterowania, ale nie jego rozmiaru mniejszy niż pozycja <xref:System.Windows.Forms.Button> formantu prawym dolnym rogu. To zachowanie jest określony przez wartość domyślną `AutoSizeMode` właściwość, która jest <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.  
  
6.  Ustaw wartość <xref:System.Windows.Forms.Panel> formantu `AutoSizeMode` właściwości <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.  
  
     <xref:System.Windows.Forms.Panel> Kontroli rozmiary sam otaczającego <xref:System.Windows.Forms.Button> formantu. Nie można zmienić rozmiaru <xref:System.Windows.Forms.Panel> formantu.  
  
7.  Przeciągnij <xref:System.Windows.Forms.Button> kontroli kierunku lewego górnego rogu <xref:System.Windows.Forms.Panel> formantu.  
  
     <xref:System.Windows.Forms.Panel> Do zmienia rozmiar kontrolki <xref:System.Windows.Forms.Button> nowego położenia kontrolki.  
  
## <a name="next-steps"></a>Następne kroki  
 Istnieje wiele innych funkcji układu dla rozmieszczanie formantów w aplikacjach formularzy systemu Windows. Poniżej przedstawiono niektóre kombinacje, które może podjąć:  
  
-   Tworzenie formularza za pomocą <xref:System.Windows.Forms.TableLayoutPanel> formantu. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów w Windows Forms za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Spróbuj zmienić wartości <xref:System.Windows.Forms.TableLayoutPanel> formantu <xref:System.Windows.Forms.Control.Padding%2A> właściwości, oraz z <xref:System.Windows.Forms.Control.Margin%2A> właściwości na jej kontrolkach podrzędnych.  
  
-   Użyj tego samego eksperymentu <xref:System.Windows.Forms.FlowLayoutPanel> formantu. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów w Windows Forms za pomocą FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
-   Doświadczenia z dokowanie formantów podrzędnych w <xref:System.Windows.Forms.Panel> formantu. <xref:System.Windows.Forms.Control.Padding%2A> Właściwość jest bardziej ogólne realizacji <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> właściwości oraz spełnia samodzielnie czy jest to poprzez umieszczenie kontrolki podrzędnej <xref:System.Windows.Forms.Panel> kontroli i ustawienie formant podrzędny <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>. Ustaw <xref:System.Windows.Forms.Panel> formantu <xref:System.Windows.Forms.Control.Padding%2A> właściwości do różnych wartości i Uwaga efekt.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 [AutoSize, właściwość — omówienie](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
