---
title: Zdarzenia myszy w formularzach systemu Windows
ms.date: 03/30/2017
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
ms.openlocfilehash: 6f457756d2266a84c4f241a1cea167af194d8b81
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43537162"
---
# <a name="mouse-events-in-windows-forms"></a>Zdarzenia myszy w formularzach systemu Windows
Podczas obsługi myszy w danych wejściowych, zwykle chcą wiedzieć lokalizacji kursora myszy wskaźnik i stan przycisku myszy. Ten temat zawiera szczegółowe informacje dotyczące sposobu uzyskania tych informacji ze zdarzeń myszy i wyjaśnia kolejność, w której kliknięcie myszą zdarzenia są wywoływane w kontrolkach formularzy Windows Forms. Aby uzyskać listę i opis wszystkich zdarzeń myszy, zobacz [sposób działania wejście myszy w formularzach Windows Forms](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  Zobacz też [Przegląd obsługi zdarzeń (Windows Forms)](https://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [Przegląd zdarzeń (systemu Windows Windows Forms)](https://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))  
  
## <a name="mouse-information"></a>Informacje o myszy  
 A <xref:System.Windows.Forms.MouseEventArgs> są wysyłane do obsługi zdarzeń myszy kliknięcie przycisku myszy i śledzenie ruchów myszy. <xref:System.Windows.Forms.MouseEventArgs> zawiera informacje o bieżącym stanie mysz, takich jak lokalizacja wskaźnika myszy we współrzędnych klienta, które są naciśnięte przyciski myszy oraz czy ma być przewijane kółka myszy. Mysz kilka zdarzeń, takich jak te, które po prostu powiadamia, kiedy wskaźnik myszy wprowadzone lub left granice formantu, wysyłanie <xref:System.EventArgs> do narzędzia obsługi zdarzeń bez dalszych informacji.  
  
 Jeśli chcesz znać bieżący stan przycisku myszy lub lokalizacji kursora myszy i chcesz uniknąć obsługi zdarzenia myszy, można również użyć <xref:System.Windows.Forms.Control.MouseButtons%2A> i <xref:System.Windows.Forms.Control.MousePosition%2A> właściwości <xref:System.Windows.Forms.Control> klasy. <xref:System.Windows.Forms.Control.MouseButtons%2A> Zwraca informacje o tym, które obecnie są naciśnięte przyciski myszy. <xref:System.Windows.Forms.Control.MousePosition%2A> Zwraca współrzędne ekranu wskaźnika myszy, a następnie jest odpowiednikiem wartości zwracanej przez <xref:System.Windows.Forms.Cursor.Position%2A>.  
  
## <a name="converting-between-screen-and-client-coordinates"></a>Konwertowanie pomiędzy ekranu i klienta służy do koordynowania  
 Ponieważ niektóre informacje o lokalizacji myszy znajduje się w współrzędne klienta, a niektóre znajduje się w współrzędne ekranu, konieczne może być przekonwertować punkt z jednego systemu współrzędnych. Łatwo to zrobić, za pomocą <xref:System.Windows.Forms.Control.PointToClient%2A> i <xref:System.Windows.Forms.Control.PointToScreen%2A> metod dostępnych na <xref:System.Windows.Forms.Control> klasy.  
  
## <a name="standard-click-event-behavior"></a>Standardowa kliknij zachowania zdarzenia  
 Jeśli chcesz obsługiwać zdarzenia w odpowiedniej kolejności kliknięcie myszą, musisz znać kolejność, w której kliknij zdarzenia są wywoływane w kontrolkach formularzy Windows Forms. Wszystkie formularze Windows, które kontrolki podnieść kliknij przycisk zdarzenia w tej samej kolejności przycisk myszy jest wciśnięty i wydania (niezależnie od tego, który przycisk myszy), z wyjątkiem w przypadku, gdy podane poniżej dla pojedynczych formantów. Na poniższej liście przedstawiono kolejność zdarzeń wywołanych dla kliknięcia jednego przycisku myszy:  
  
1.  <xref:System.Windows.Forms.Control.MouseDown> zdarzenie.  
  
2.  <xref:System.Windows.Forms.Control.Click> zdarzenie.  
  
3.  <xref:System.Windows.Forms.Control.MouseClick> zdarzenie.  
  
4.  <xref:System.Windows.Forms.Control.MouseUp> zdarzenie.  
  
 Poniżej przedstawiono kolejność zdarzeń wywołanych dla przez kliknięcie przycisku myszy w podwójne:  
  
1.  <xref:System.Windows.Forms.Control.MouseDown> zdarzenie.  
  
2.  <xref:System.Windows.Forms.Control.Click> zdarzenie.  
  
3.  <xref:System.Windows.Forms.Control.MouseClick> zdarzenie.  
  
4.  <xref:System.Windows.Forms.Control.MouseUp> zdarzenie.  
  
5.  <xref:System.Windows.Forms.Control.MouseDown> zdarzenie.  
  
6.  <xref:System.Windows.Forms.Control.DoubleClick> zdarzenie. (To może się różnić, w zależności od tego, czy w danym kontroli ma <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> określony bit stylu do `true`. Aby uzyskać więcej informacji o sposobie ustawiania <xref:System.Windows.Forms.ControlStyles> bit, zobacz <xref:System.Windows.Forms.Control.SetStyle%2A> metody.)  
  
7.  <xref:System.Windows.Forms.Control.MouseDoubleClick> zdarzenie.  
  
8.  <xref:System.Windows.Forms.Control.MouseUp> zdarzenie.  
  
 Dla przykładu kodu, który demonstruje kolejność myszy zdarzenia kliknięcia, zobacz [porady: Obsługa zdarzeń danych wejściowych użytkownika w kontrolkach formularzy Windows Forms](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md).  
  
### <a name="individual-controls"></a>Pojedynczych formantów  
 Następujące elementy sterujące nie jest zgodny z standardowej myszki kliknij zachowania zdarzenia:  
  
-   <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, i <xref:System.Windows.Forms.RadioButton> formantów  
  
    > [!NOTE]
    >  Aby uzyskać <xref:System.Windows.Forms.ComboBox> kontroli zachowania zdarzenia, w dalszej części występuje, gdy użytkownik kliknie w polu edycji przycisku, lub element listy.  
  
    -   Kliknięcie lewym przyciskiem: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Kliknij prawym przyciskiem myszy: nie zdarzeń kliknij zgłaszanych  
  
    -   Po lewej stronie kliknij dwukrotnie plik: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Kliknij dwukrotnie przycisk z prawej: nie zdarzeń kliknij zgłaszanych  
  
-   <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, i <xref:System.Windows.Forms.CheckedListBox> formantów  
  
    > [!NOTE]
    >  Zachowanie zdarzeń szczegółowe później występuje, gdy użytkownik kliknie przycisk w dowolnym miejscu w ramach tych kontrolek.  
  
    -   Kliknięcie lewym przyciskiem: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Kliknij prawym przyciskiem myszy: nie zdarzeń kliknij zgłaszanych  
  
    -   Po lewej stronie kliknij dwukrotnie plik: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Kliknij dwukrotnie przycisk z prawej: nie zdarzeń kliknij zgłaszanych  
  
-   <xref:System.Windows.Forms.ListView> Kontrolki  
  
    > [!NOTE]
    >  Zachowanie zdarzeń, w dalszej części występuje tylko wtedy, gdy użytkownik kliknie elementów w <xref:System.Windows.Forms.ListView> kontroli. Żadne zdarzenia nie są zgłaszane dla kliknięcia miejscach w formancie. Oprócz zdarzeń opisanym w dalszej części, istnieją <xref:System.Windows.Forms.ListView.BeforeLabelEdit> i <xref:System.Windows.Forms.ListView.AfterLabelEdit> zdarzenia, które mogą być przydatne, jeśli chcesz używać Weryfikacja przy użyciu <xref:System.Windows.Forms.ListView> kontroli.  
  
    -   Kliknięcie lewym przyciskiem: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Po lewej stronie kliknij dwukrotnie plik: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Kliknij dwukrotnie przycisk z prawej: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
-   <xref:System.Windows.Forms.TreeView> Kontrolki  
  
    > [!NOTE]
    >  Zachowanie zdarzeń, w dalszej części występuje tylko po kliknięciu przez użytkownika na elementach, samodzielnie lub z prawej strony elementów w <xref:System.Windows.Forms.TreeView> kontroli. Żadne zdarzenia nie są zgłaszane dla kliknięcia miejscach w formancie. Oprócz tych opisanym w dalszej części istnieją <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, i <xref:System.Windows.Forms.TreeView.AfterLabelEdit> zdarzenia, które mogą być przydatne, jeśli chcesz używać Weryfikacja przy użyciu <xref:System.Windows.Forms.TreeView> kontroli .  
  
    -   Kliknięcie lewym przyciskiem: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Po lewej stronie kliknij dwukrotnie plik: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Kliknij dwukrotnie przycisk z prawej: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
### <a name="painting-behavior-of-toggle-controls"></a>Malowanie zachowanie kontrolki przełącznika  
 Przełącz formanty, takie jak formanty pochodząca od <xref:System.Windows.Forms.ButtonBase> klasy, mają następujące zachowanie szczególne malowania w połączeniu z myszy zdarzenia kliknięcia:  
  
1.  Użytkownik naciśnie przycisk myszy.  
  
2.  Malowanie kontrolki w stanie po naciśnięciu.  
  
3.  <xref:System.Windows.Forms.Control.MouseDown> Zdarzenie jest wywoływane.  
  
4.  Użytkownik zwolni przycisk myszy.  
  
5.  Malowanie kontrolki w stanie podniesione.  
  
6.  <xref:System.Windows.Forms.Control.Click> Zdarzenie jest wywoływane.  
  
7.  <xref:System.Windows.Forms.Control.MouseClick> Zdarzenie jest wywoływane.  
  
8.  <xref:System.Windows.Forms.Control.MouseUp> Zdarzenie jest wywoływane.  
  
    > [!NOTE]
    >  Gdy użytkownik przesuwa wskaźnik myszy poza formant przełączania, gdy przycisk myszy jest wciśnięty (np. przesuwanie wskaźnika myszy <xref:System.Windows.Forms.Button> kontroli, gdy naciśnięcia), kontrolki przełącznika namaluje w wypukły stanu i tylko <xref:System.Windows.Forms.Control.MouseUp> wystąpi zdarzenie. <xref:System.Windows.Forms.Control.Click> Lub <xref:System.Windows.Forms.Control.MouseClick> zdarzenia nie będzie występować w tej sytuacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
