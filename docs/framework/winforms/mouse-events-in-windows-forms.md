---
title: Zdarzenia myszy w Windows Forms
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
ms.openlocfilehash: a61f4eedde611cfb7598d55465103924516e06c6
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834606"
---
# <a name="mouse-events-in-windows-forms"></a>Zdarzenia myszy w Windows Forms

W przypadku obsługi danych wejściowych myszy zwykle potrzebna jest znajomość położenia wskaźnika myszy i stanu przycisków myszy. Ten temat zawiera szczegółowe informacje o tym, jak uzyskać te informacje ze zdarzeń myszy, i wyjaśnienie kolejności, w której zdarzenia kliknięcia myszą są wywoływane w kontrolkach Windows Forms. Aby zapoznać się z listą i opisem wszystkich zdarzeń myszy, zobacz [jak działa wprowadzanie myszą w Windows Forms](how-mouse-input-works-in-windows-forms.md).  Zobacz także [Omówienie obsługi zdarzeń (Windows Forms)](event-handlers-overview-windows-forms.md) i [przegląd zdarzeń (Windows Forms)](events-overview-windows-forms.md).

## <a name="mouse-information"></a>Informacje o myszy

@No__t-0 jest wysyłana do programów obsługi zdarzeń myszy związanych z kliknięciem przycisku myszy i śledzeniem ruchów myszy. <xref:System.Windows.Forms.MouseEventArgs> zawiera informacje o bieżącym stanie myszy, w tym o lokalizacji wskaźnika myszy w współrzędnej klienta, które przyciski myszy są naciśnięte i czy kółko myszy zostało przewijane. Kilka zdarzeń myszy, takich jak te, które po prostu powiadamiają, gdy wskaźnik myszy został wprowadzony lub pozostawiono granice kontrolki, wysyła <xref:System.EventArgs> do procedury obsługi zdarzeń bez dalszych informacji.

Jeśli chcesz znać bieżący stan przycisków myszy lub lokalizacji wskaźnika myszy, a chcesz uniknąć obsługi zdarzenia myszy, możesz również użyć właściwości <xref:System.Windows.Forms.Control.MouseButtons%2A> i <xref:System.Windows.Forms.Control.MousePosition%2A> klasy <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.MouseButtons%2A> zwraca informacje o tym, które przyciski myszy są aktualnie naciśnięte. @No__t-0 zwraca współrzędne ekranu wskaźnika myszy i jest równoważne wartości zwracanej przez <xref:System.Windows.Forms.Cursor.Position%2A>.

## <a name="converting-between-screen-and-client-coordinates"></a>Konwersja między współrzędnymi ekranu i klienta

Ponieważ niektóre informacje o lokalizacji myszy znajdują się we współrzędnych klienta, a niektóre z nich są współrzędnymi ekranu, może być konieczne przekonwertowanie punktu z jednego systemu współrzędnych na drugi. Można to łatwo zrobić, korzystając z metod <xref:System.Windows.Forms.Control.PointToClient%2A> i <xref:System.Windows.Forms.Control.PointToScreen%2A> dostępnych w klasie <xref:System.Windows.Forms.Control>.

## <a name="standard-click-event-behavior"></a>Zachowanie zdarzenia standardowego kliknięcia

Jeśli chcesz obsłużyć zdarzenia klikania myszą w odpowiedniej kolejności, musisz znać kolejność, w której zdarzenia kliknięcia są wywoływane w kontrolkach Windows Forms. Wszystkie kontrolki Windows Forms powodują wygenerowanie zdarzeń kliknięcia w tej samej kolejności, gdy przycisk myszy jest wciśnięty i wystawiony (niezależnie od tego, który przycisk myszy), z wyjątkiem tego, gdzie zaznaczono na poniższej liście dla poszczególnych kontrolek. Na poniższej liście przedstawiono kolejność zdarzeń wygenerowanych dla jednego kliknięcia przycisku myszy:

1. zdarzenie <xref:System.Windows.Forms.Control.MouseDown>.

2. zdarzenie <xref:System.Windows.Forms.Control.Click>.

3. zdarzenie <xref:System.Windows.Forms.Control.MouseClick>.

4. zdarzenie <xref:System.Windows.Forms.Control.MouseUp>.

Poniżej przedstawiono kolejność zdarzeń wywoływanych przez dwukrotne kliknięcie przycisku myszy:

1. zdarzenie <xref:System.Windows.Forms.Control.MouseDown>.

2. zdarzenie <xref:System.Windows.Forms.Control.Click>.

3. zdarzenie <xref:System.Windows.Forms.Control.MouseClick>.

4. zdarzenie <xref:System.Windows.Forms.Control.MouseUp>.

5. zdarzenie <xref:System.Windows.Forms.Control.MouseDown>.

6. zdarzenie <xref:System.Windows.Forms.Control.DoubleClick>. (Może się to różnić w zależności od tego, czy dana Kontrola ma bit stylu <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> ustawiony na `true`. Aby uzyskać więcej informacji na temat sposobu ustawiania bitu <xref:System.Windows.Forms.ControlStyles>, zobacz metodę <xref:System.Windows.Forms.Control.SetStyle%2A>.

7. zdarzenie <xref:System.Windows.Forms.Control.MouseDoubleClick>.

8. zdarzenie <xref:System.Windows.Forms.Control.MouseUp>.

Przykładowy kod, który pokazuje kolejność zdarzeń kliknięcia myszą, znajduje [się w temacie How to: obsługa zdarzeń wejściowych użytkownika w kontrolkach Windows Forms](how-to-handle-user-input-events-in-windows-forms-controls.md).

### <a name="individual-controls"></a>Poszczególne kontrolki

Następujące kontrolki nie są zgodne ze standardowym zachowaniem zdarzenia kliknięcia myszą:

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > W przypadku kontrolki <xref:System.Windows.Forms.ComboBox>, zachowanie zdarzenia w dalszej części występuje, gdy użytkownik kliknie pole edycji, przycisk lub element na liście.

  - Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia

  - Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia

- <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox> i <xref:System.Windows.Forms.CheckedListBox> formantów

  > [!NOTE]
  > Zachowanie zdarzenia w dalszej części tego problemu występuje, gdy użytkownik kliknie dowolne miejsce w tych kontrolkach.

  - Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia

  - Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia

- Kontrolka <xref:System.Windows.Forms.ListView>

  > [!NOTE]
  > Zachowanie zdarzenia w przyszłości występuje tylko wtedy, gdy użytkownik kliknie elementy w kontrolce <xref:System.Windows.Forms.ListView>. Żadne zdarzenia nie są wywoływane dla kliknięć w dowolnym miejscu w formancie. Poza zdarzeniami opisanymi później istnieją zdarzenia <xref:System.Windows.Forms.ListView.BeforeLabelEdit> i <xref:System.Windows.Forms.ListView.AfterLabelEdit>, które mogą być interesujące dla użytkownika, jeśli chcesz użyć walidacji z kontrolką <xref:System.Windows.Forms.ListView>.

  - Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Kliknij dwukrotnie pozycję: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

- Kontrolka <xref:System.Windows.Forms.TreeView>

  > [!NOTE]
  > Zachowanie zdarzenia w przyszłości występuje tylko wtedy, gdy użytkownik kliknie same elementy lub po prawej stronie elementów w kontrolce <xref:System.Windows.Forms.TreeView>. Żadne zdarzenia nie są wywoływane dla kliknięć w dowolnym miejscu w formancie. Oprócz tych opisanych później istnieje <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck> i <xref:System.Windows.Forms.TreeView.AfterLabelEdit> zdarzeń, które mogą być przydatne, jeśli chcesz użyć walidacji z kontrolką <xref:System.Windows.Forms.TreeView>.

  - Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Kliknij dwukrotnie pozycję: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

### <a name="painting-behavior-of-toggle-controls"></a>Zachowanie podczas malowania kontrolek przełączników

Kontrolki przełączania, takie jak kontrolki pochodne klasy <xref:System.Windows.Forms.ButtonBase>, mają następujące wyraźne zachowanie rysowania w połączeniu z zdarzeniami kliknięcia myszą:

1. Użytkownik naciśnie przycisk myszy.

2. Kontrolka maluje w stanie naciśniętym.

3. Zdarzenie <xref:System.Windows.Forms.Control.MouseDown> jest zgłaszane.

4. Użytkownik zwolni przycisk myszy.

5. Kontrolka maluje w stanie podniesiony.

6. Zdarzenie <xref:System.Windows.Forms.Control.Click> jest zgłaszane.

7. Zdarzenie <xref:System.Windows.Forms.Control.MouseClick> jest zgłaszane.

8. Zdarzenie <xref:System.Windows.Forms.Control.MouseUp> jest zgłaszane.

    > [!NOTE]
    > Jeśli użytkownik przesuwa wskaźnik poza formant przełączania, gdy przycisk myszy nie działa (na przykład przesuwając mysz po naciśnięciu kontrolki <xref:System.Windows.Forms.Button>), formant przełączania będzie malować w stanie podniesiony i wystąpi tylko zdarzenie <xref:System.Windows.Forms.Control.MouseUp>. W tej sytuacji nie będą występować zdarzenia <xref:System.Windows.Forms.Control.Click> lub <xref:System.Windows.Forms.Control.MouseClick>.

## <a name="see-also"></a>Zobacz także

- [Dane wejściowe myszy w aplikacji Windows Forms](mouse-input-in-a-windows-forms-application.md)
