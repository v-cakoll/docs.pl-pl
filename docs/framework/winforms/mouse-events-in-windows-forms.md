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
ms.openlocfilehash: 181d01f6e688b94876f77155bf598aba129e9fbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949910"
---
# <a name="mouse-events-in-windows-forms"></a>Zdarzenia myszy w formularzach systemu Windows

W przypadku obsługi danych wejściowych myszy zwykle potrzebna jest znajomość położenia wskaźnika myszy i stanu przycisków myszy. Ten temat zawiera szczegółowe informacje o tym, jak uzyskać te informacje ze zdarzeń myszy, i wyjaśnienie kolejności, w której zdarzenia kliknięcia myszą są wywoływane w kontrolkach Windows Forms. Aby zapoznać się z listą i opisem wszystkich zdarzeń myszy, zobacz [jak działa wprowadzanie myszą w Windows Forms](how-mouse-input-works-in-windows-forms.md).  Zobacz także [Omówienie obsługi zdarzeń (Windows Forms)](event-handlers-overview-windows-forms.md) i [przegląd zdarzeń (Windows Forms)](events-overview-windows-forms.md).

## <a name="mouse-information"></a>Informacje o myszy

<xref:System.Windows.Forms.MouseEventArgs> Jest wysyłany do programów obsługi zdarzeń myszy związanych z kliknięciem przycisku myszy i śledzeniem ruchów myszy. <xref:System.Windows.Forms.MouseEventArgs>zawiera informacje o bieżącym stanie myszy, w tym o lokalizacji wskaźnika myszy w współrzędnej klienta, które przyciski myszy są naciśnięte i czy kółko myszy zostało przeprzewijane. Kilka zdarzeń myszy, takich jak te, które po prostu powiadamiają, gdy wskaźnik myszy został wprowadzony lub pozostawiono granice kontrolki, wysyła <xref:System.EventArgs> do programu obsługi zdarzeń bez dalszych informacji.

Jeśli chcesz znać bieżący stan przycisków myszy lub lokalizacji wskaźnika myszy, a chcesz uniknąć obsługi zdarzenia myszy, możesz również użyć <xref:System.Windows.Forms.Control.MouseButtons%2A> właściwości i <xref:System.Windows.Forms.Control.MousePosition%2A> klasy w <xref:System.Windows.Forms.Control> klasie. <xref:System.Windows.Forms.Control.MouseButtons%2A>zwraca informacje o tym, które przyciski myszy są aktualnie naciśnięte. Zwraca współrzędne ekranu wskaźnika myszy i jest równoważne wartości zwracanej przez <xref:System.Windows.Forms.Cursor.Position%2A>. <xref:System.Windows.Forms.Control.MousePosition%2A>

## <a name="converting-between-screen-and-client-coordinates"></a>Konwersja między współrzędnymi ekranu i klienta

Ponieważ niektóre informacje o lokalizacji myszy znajdują się we współrzędnych klienta, a niektóre z nich są współrzędnymi ekranu, może być konieczne przekonwertowanie punktu z jednego systemu współrzędnych na drugi. Można to łatwo zrobić przy użyciu <xref:System.Windows.Forms.Control.PointToClient%2A> metod i <xref:System.Windows.Forms.Control.PointToScreen%2A> dostępnych w <xref:System.Windows.Forms.Control> klasie.

## <a name="standard-click-event-behavior"></a>Zachowanie zdarzenia standardowego kliknięcia

Jeśli chcesz obsłużyć zdarzenia klikania myszą w odpowiedniej kolejności, musisz znać kolejność, w której zdarzenia kliknięcia są wywoływane w kontrolkach Windows Forms. Wszystkie kontrolki Windows Forms powodują wygenerowanie zdarzeń kliknięcia w tej samej kolejności, gdy przycisk myszy jest wciśnięty i wystawiony (niezależnie od tego, który przycisk myszy), z wyjątkiem tego, gdzie zaznaczono na poniższej liście dla poszczególnych kontrolek. Na poniższej liście przedstawiono kolejność zdarzeń wygenerowanych dla jednego kliknięcia przycisku myszy:

1. <xref:System.Windows.Forms.Control.MouseDown>wydarzen.

2. <xref:System.Windows.Forms.Control.Click>wydarzen.

3. <xref:System.Windows.Forms.Control.MouseClick>wydarzen.

4. <xref:System.Windows.Forms.Control.MouseUp>wydarzen.

Poniżej znajduje się kolejność zdarzeń wywoływanych przez dwukrotne kliknięcie przycisku myszy:

1. <xref:System.Windows.Forms.Control.MouseDown>wydarzen.

2. <xref:System.Windows.Forms.Control.Click>wydarzen.

3. <xref:System.Windows.Forms.Control.MouseClick>wydarzen.

4. <xref:System.Windows.Forms.Control.MouseUp>wydarzen.

5. <xref:System.Windows.Forms.Control.MouseDown>wydarzen.

6. <xref:System.Windows.Forms.Control.DoubleClick>wydarzen. (Może się to różnić w zależności od tego, czy dana kontrolka ma <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> `true`ustawiony bit stylu. Aby uzyskać więcej informacji na temat sposobu ustawiania <xref:System.Windows.Forms.ControlStyles> bitu, <xref:System.Windows.Forms.Control.SetStyle%2A> Zobacz metodę.)

7. <xref:System.Windows.Forms.Control.MouseDoubleClick>wydarzen.

8. <xref:System.Windows.Forms.Control.MouseUp>wydarzen.

Przykładowy kod, który pokazuje kolejność zdarzeń kliknięcia myszą, znajduje się w temacie [How to: Obsłuż zdarzenia wejściowe użytkownika w kontrolkach](how-to-handle-user-input-events-in-windows-forms-controls.md)Windows Forms.

### <a name="individual-controls"></a>Poszczególne kontrolki

Następujące kontrolki nie są zgodne ze standardowym zachowaniem zdarzenia kliknięcia myszą:

- <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, i<xref:System.Windows.Forms.RadioButton> kontrolki

  > [!NOTE]
  > W przypadku <xref:System.Windows.Forms.ComboBox> kontrolki, zachowanie zdarzenia w dalszej części występuje, gdy użytkownik kliknie pole edycji, przycisk lub element na liście.

  - Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>

  - Kliknij prawym przyciskiem myszy: Nie zgłoszono żadnych zdarzeń kliknięcia

  - Lewy dwukrotne kliknięcie <xref:System.Windows.Forms.Control.Click>: <xref:System.Windows.Forms.Control.MouseClick>,; <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>

  - Kliknięcie prawym przyciskiem myszy: Nie zgłoszono żadnych zdarzeń kliknięcia

- <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox> ,<xref:System.Windows.Forms.ListBox>,, i<xref:System.Windows.Forms.CheckedListBox> kontrolki <xref:System.Windows.Forms.MaskedTextBox>

  > [!NOTE]
  > Zachowanie zdarzenia w dalszej części tego problemu występuje, gdy użytkownik kliknie dowolne miejsce w tych kontrolkach.

  - Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>

  - Kliknij prawym przyciskiem myszy: Nie zgłoszono żadnych zdarzeń kliknięcia

  - Lewy dwukrotne kliknięcie <xref:System.Windows.Forms.Control.Click>: <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>,,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Kliknięcie prawym przyciskiem myszy: Nie zgłoszono żadnych zdarzeń kliknięcia

- <xref:System.Windows.Forms.ListView>kontroli

  > [!NOTE]
  > Zachowanie zdarzenia w przyszłości występuje tylko wtedy, gdy użytkownik kliknie elementy w <xref:System.Windows.Forms.ListView> kontrolce. Żadne zdarzenia nie są wywoływane dla kliknięć w dowolnym miejscu w formancie. Poza zdarzeniami opisanymi później istnieją <xref:System.Windows.Forms.ListView.BeforeLabelEdit> zdarzenia i <xref:System.Windows.Forms.ListView.AfterLabelEdit> , które mogą być przydatne, jeśli chcesz użyć walidacji z <xref:System.Windows.Forms.ListView> kontrolką.

  - Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>

  - Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>

  - Lewy dwukrotne kliknięcie <xref:System.Windows.Forms.Control.Click>: <xref:System.Windows.Forms.Control.MouseClick>,; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Kliknij dwukrotnie przycisk: <xref:System.Windows.Forms.Control.Click>,; <xref:System.Windows.Forms.Control.MouseClick> <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

- <xref:System.Windows.Forms.TreeView>kontroli

  > [!NOTE]
  > Zachowanie zdarzenia w przyszłości występuje tylko wtedy, gdy użytkownik kliknie same elementy lub po prawej stronie elementów w <xref:System.Windows.Forms.TreeView> formancie. Żadne zdarzenia nie są wywoływane dla kliknięć w dowolnym miejscu w formancie. Oprócz tych <xref:System.Windows.Forms.TreeView.BeforeCheck>opisanych później, istnieją <xref:System.Windows.Forms.TreeView.BeforeLabelEdit> <xref:System.Windows.Forms.TreeView.AfterSelect> <xref:System.Windows.Forms.TreeView.BeforeSelect> zdarzenia,<xref:System.Windows.Forms.TreeView.AfterCheck>,,, i <xref:System.Windows.Forms.TreeView.AfterLabelEdit> , które mogą być przydatne, jeśli chcesz użyć walidacji z kontrolką<xref:System.Windows.Forms.TreeView> .

  - Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>

  - Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick>

  - Lewy dwukrotne kliknięcie <xref:System.Windows.Forms.Control.Click>: <xref:System.Windows.Forms.Control.MouseClick>,; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Kliknij dwukrotnie przycisk: <xref:System.Windows.Forms.Control.Click>,; <xref:System.Windows.Forms.Control.MouseClick> <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick>

### <a name="painting-behavior-of-toggle-controls"></a>Zachowanie podczas malowania kontrolek przełączników

Kontrolki przełączania, takie jak kontrolki pochodne <xref:System.Windows.Forms.ButtonBase> klasy, mają następujące wyraźne zachowanie rysowania w połączeniu z zdarzeniami kliknięcia myszą:

1. Użytkownik naciśnie przycisk myszy.

2. Kontrolka maluje w stanie naciśniętym.

3. <xref:System.Windows.Forms.Control.MouseDown> Zdarzenie jest zgłaszane.

4. Użytkownik zwolni przycisk myszy.

5. Kontrolka maluje w stanie podniesiony.

6. <xref:System.Windows.Forms.Control.Click> Zdarzenie jest zgłaszane.

7. <xref:System.Windows.Forms.Control.MouseClick> Zdarzenie jest zgłaszane.

8. <xref:System.Windows.Forms.Control.MouseUp> Zdarzenie jest zgłaszane.

    > [!NOTE]
    > Jeśli użytkownik przesunie wskaźnik z kontrolki przełączania, gdy przycisk myszy nie działa (na przykład przesuwając mysz <xref:System.Windows.Forms.Button> po naciśnięciu kontrolki), formant przełączania będzie malowany w stanie podniesiony i wystąpi <xref:System.Windows.Forms.Control.MouseUp> tylko zdarzenie. Zdarzenia <xref:System.Windows.Forms.Control.Click> lub<xref:System.Windows.Forms.Control.MouseClick> nie pojawią się w tej sytuacji.

## <a name="see-also"></a>Zobacz także

- [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](mouse-input-in-a-windows-forms-application.md)
