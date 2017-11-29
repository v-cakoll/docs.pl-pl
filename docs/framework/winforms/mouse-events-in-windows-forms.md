---
title: Zdarzenia myszy w formularzach systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 803f2daab5b8f6e216effe4a9ae9f34752d24e70
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="mouse-events-in-windows-forms"></a>Zdarzenia myszy w formularzach systemu Windows
Podczas obsługi myszy w danych wejściowych, zwykle zapoznać się położenie myszy wskaźnik i stan przycisku myszy. Ten temat zawiera szczegółowe informacje dotyczące sposobu uzyskania tych informacji ze zdarzeń myszy i wyjaśniono kolejności, w których kliknięcie zdarzenia są generowane w formantach formularzy systemu Windows. Aby uzyskać listę i opis wszystkich zdarzeń myszy, zobacz [sposób działania wejście myszy w formularzach systemu Windows](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  Zobacz też [Przegląd obsługi zdarzeń (formularze systemu Windows)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [Przegląd zdarzeń (formularze systemu Windows)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))  
  
## <a name="mouse-information"></a>Informacje o myszy  
 A <xref:System.Windows.Forms.MouseEventArgs> są wysyłane do obsługi zdarzeń myszy związanych z kliknięcie przycisku myszy i śledzenie ruchów myszy. <xref:System.Windows.Forms.MouseEventArgs>zawiera informacje o bieżącym stanie mysz, takich jak lokalizacja wskaźnika myszy we współrzędnych klienta, które naciśnięciu przycisku myszy, i czy ma być przewijane kółka myszy. Kilka razy zdarzeń, takich jak te, które po prostu powiadomić podczas obliczania wskaźnika myszy wprowadzona lub granice formantu w lewo, wysyłanie <xref:System.EventArgs> obsługi zdarzeń z dalsze informacje.  
  
 Jeśli chcesz wiedzieć, bieżący stan przycisku myszy lub położenia wskaźnika myszy, a chce się uniknąć obsługi zdarzeń myszy, można również użyć <xref:System.Windows.Forms.Control.MouseButtons%2A> i <xref:System.Windows.Forms.Control.MousePosition%2A> właściwości <xref:System.Windows.Forms.Control> klasy. <xref:System.Windows.Forms.Control.MouseButtons%2A>Zwraca informacje o tym, które są aktualnie naciśnięcia przycisku myszy. <xref:System.Windows.Forms.Control.MousePosition%2A> Zwraca współrzędne ekranu wskaźnika myszy i jest odpowiednikiem wartości zwróconej przez <xref:System.Windows.Forms.Cursor.Position%2A>.  
  
## <a name="converting-between-screen-and-client-coordinates"></a>Konwertowanie pomiędzy ekranu i klienta koordynuje  
 Ponieważ niektóre informacje o lokalizacji myszy współrzędne klienta i niektóre jest we współrzędnych ekranu, konieczne może być przekonwertować punkt z jednego systemu współrzędnych. Łatwo to zrobić, za pomocą <xref:System.Windows.Forms.Control.PointToClient%2A> i <xref:System.Windows.Forms.Control.PointToScreen%2A> metod na <xref:System.Windows.Forms.Control> klasy.  
  
## <a name="standard-click-event-behavior"></a>Standard kliknij zachowania zdarzenia  
 Jeśli chcesz obsługiwać zdarzenia w prawidłowej kolejności kliknięcia myszą, należy znać kolejności, w których kliknij zdarzenia są generowane w formantach formularzy systemu Windows. Po przycisk myszy jest wciśnięty i wydane (niezależnie od tego, który przycisk myszy), chyba że zaznaczono inaczej na poniższej liście dla pojedynczych formantów, wszystkich formularzy systemu Windows, które kontrolki podnieść kliknij zdarzenia w tej samej kolejności. Na poniższej liście przedstawiono kolejność zdarzeń zgłaszanych Click pojedynczego przycisku myszy:  
  
1.  <xref:System.Windows.Forms.Control.MouseDown>zdarzenie.  
  
2.  <xref:System.Windows.Forms.Control.Click>zdarzenie.  
  
3.  <xref:System.Windows.Forms.Control.MouseClick>zdarzenie.  
  
4.  <xref:System.Windows.Forms.Control.MouseUp>zdarzenie.  
  
 Poniżej przedstawiono kolejność zdarzeń dla kliknij dwa razy przycisk myszy.  
  
1.  <xref:System.Windows.Forms.Control.MouseDown>zdarzenie.  
  
2.  <xref:System.Windows.Forms.Control.Click>zdarzenie.  
  
3.  <xref:System.Windows.Forms.Control.MouseClick>zdarzenie.  
  
4.  <xref:System.Windows.Forms.Control.MouseUp>zdarzenie.  
  
5.  <xref:System.Windows.Forms.Control.MouseDown>zdarzenie.  
  
6.  <xref:System.Windows.Forms.Control.DoubleClick>zdarzenie. (To może się różnić w zależności od tego, czy w formancie ma <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> bitu stylu do `true`. Aby uzyskać więcej informacji na temat sposobu ustawiania <xref:System.Windows.Forms.ControlStyles> bit, zobacz <xref:System.Windows.Forms.Control.SetStyle%2A> metody.)  
  
7.  <xref:System.Windows.Forms.Control.MouseDoubleClick>zdarzenie.  
  
8.  <xref:System.Windows.Forms.Control.MouseUp>zdarzenie.  
  
 Na przykład kod, który demonstruje kolejność myszy zdarzenia kliknięcia, zobacz [porady: Obsługa zdarzeń danych wejściowych użytkownika w formantach formularzy systemu Windows](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md).  
  
### <a name="individual-controls"></a>Pojedynczych formantów  
 Następujące formanty nie są zgodne ze standardowej myszki kliknij zachowania zdarzenia:  
  
-   <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, i <xref:System.Windows.Forms.RadioButton> formantów  
  
    > [!NOTE]
    >  Aby uzyskać <xref:System.Windows.Forms.ComboBox> kontroli zachowania zdarzenia szczegółowe później występuje, gdy użytkownik kliknie w polu edycji, po kliknięciu przycisku lub element na liście.  
  
    -   Lewy przycisk: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Kliknij prawym przyciskiem myszy: Brak zdarzeń kliknij wywoływane  
  
    -   Po lewej stronie kliknij dwukrotnie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Kliknij dwukrotnie ikonę prawym: żadne zdarzenia kliknij wywoływane  
  
-   <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, i <xref:System.Windows.Forms.CheckedListBox> formantów  
  
    > [!NOTE]
    >  Zachowanie zdarzeń szczegółowe później występuje, gdy użytkownik kliknie w dowolnym miejscu w ramach tych kontrolek.  
  
    -   Lewy przycisk: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Kliknij prawym przyciskiem myszy: Brak zdarzeń kliknij wywoływane  
  
    -   Po lewej stronie kliknij dwukrotnie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Kliknij dwukrotnie ikonę prawym: żadne zdarzenia kliknij wywoływane  
  
-   <xref:System.Windows.Forms.ListView>Formant  
  
    > [!NOTE]
    >  Zachowanie zdarzeń szczegółowe później występuje tylko po kliknięciu przez użytkownika dla elementów w <xref:System.Windows.Forms.ListView> formantu. Żadne zdarzenia nie są zgłaszane dla kliknięć miejscach w formancie. Oprócz zdarzenia w dalszej części, istnieją <xref:System.Windows.Forms.ListView.BeforeLabelEdit> i <xref:System.Windows.Forms.ListView.AfterLabelEdit> zdarzenia, które mogą być przydatne, jeśli chcesz używać weryfikacji z <xref:System.Windows.Forms.ListView> formantu.  
  
    -   Lewy przycisk: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Po lewej stronie kliknij dwukrotnie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Kliknij dwukrotnie ikonę prawym: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
-   <xref:System.Windows.Forms.TreeView>Formant  
  
    > [!NOTE]
    >  Zachowanie zdarzeń szczegółowe później występuje tylko po kliknięciu przez użytkownika na elementach, samodzielnie lub w prawo elementów w <xref:System.Windows.Forms.TreeView> formantu. Żadne zdarzenia nie są zgłaszane dla kliknięć miejscach w formancie. Oprócz tych w dalszej części, istnieją <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, i <xref:System.Windows.Forms.TreeView.AfterLabelEdit> zdarzenia, które mogą być przydatne, jeśli chcesz używać weryfikacji z <xref:System.Windows.Forms.TreeView> formantu .  
  
    -   Lewy przycisk: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Po lewej stronie kliknij dwukrotnie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Kliknij dwukrotnie ikonę prawym: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
### <a name="painting-behavior-of-toggle-controls"></a>Malowanie zachowanie przełączania formantów  
 Przełącz formanty, takie jak formanty wynikających z <xref:System.Windows.Forms.ButtonBase> klasa, ma następujące zachowanie charakterystyczne malowania w połączeniu z myszy zdarzenia kliknięcia:  
  
1.  Użytkownik naciśnie przycisk myszy.  
  
2.  W stan naciśnięcia umożliwia malowanie formantu.  
  
3.  <xref:System.Windows.Forms.Control.MouseDown> Zdarzenia.  
  
4.  Użytkownik zwolni przycisk myszy.  
  
5.  W stanie zgłoszono umożliwia malowanie formantu.  
  
6.  <xref:System.Windows.Forms.Control.Click> Zdarzenia.  
  
7.  <xref:System.Windows.Forms.Control.MouseClick> Zdarzenia.  
  
8.  <xref:System.Windows.Forms.Control.MouseUp> Zdarzenia.  
  
    > [!NOTE]
    >  Jeśli użytkownik przesuwa wskaźnik poza formantu przełącznika, gdy przycisk myszy jest wciśnięty (takie jak przesuwanie wskaźnika myszy <xref:System.Windows.Forms.Button> kontrolować naciśniętym zostanie), Przełącz sterowanie namaluje w zgłoszono stanu i to tylko <xref:System.Windows.Forms.Control.MouseUp> zdarzenie. <xref:System.Windows.Forms.Control.Click> Lub <xref:System.Windows.Forms.Control.MouseClick> w takiej sytuacji nie nastąpi zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Wejście myszy w systemie Windows formularzy aplikacji](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
