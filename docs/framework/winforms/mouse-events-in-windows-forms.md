---
title: Zdarzenia myszy
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
ms.openlocfilehash: 4909f56fc3935848fd18bc35c1cb56b5407a24c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740964"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="de37a-102">Zdarzenia myszy w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="de37a-102">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="de37a-103">W przypadku obsługi danych wejściowych myszy zwykle potrzebna jest znajomość położenia wskaźnika myszy i stanu przycisków myszy.</span><span class="sxs-lookup"><span data-stu-id="de37a-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="de37a-104">Ten temat zawiera szczegółowe informacje o tym, jak uzyskać te informacje ze zdarzeń myszy, i wyjaśnienie kolejności, w której zdarzenia kliknięcia myszą są wywoływane w kontrolkach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="de37a-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="de37a-105">Aby zapoznać się z listą i opisem wszystkich zdarzeń myszy, zobacz [jak działa wprowadzanie myszą w Windows Forms](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="de37a-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="de37a-106">Zobacz także [Omówienie obsługi zdarzeń (Windows Forms)](event-handlers-overview-windows-forms.md) i [przegląd zdarzeń (Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="de37a-106">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="de37a-107">Informacje o myszy</span><span class="sxs-lookup"><span data-stu-id="de37a-107">Mouse Information</span></span>

<span data-ttu-id="de37a-108"><xref:System.Windows.Forms.MouseEventArgs> jest wysyłana do programów obsługi zdarzeń myszy związanych z kliknięciem przycisku myszy i śledzeniem ruchów myszy.</span><span class="sxs-lookup"><span data-stu-id="de37a-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="de37a-109"><xref:System.Windows.Forms.MouseEventArgs> zawiera informacje o bieżącym stanie myszy, w tym o lokalizacji wskaźnika myszy w współrzędnej klienta, które przyciski myszy są naciśnięte i czy kółko myszy zostało przeprzewijane.</span><span class="sxs-lookup"><span data-stu-id="de37a-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="de37a-110">Kilka zdarzeń myszy, takich jak te, które po prostu powiadamiają, gdy wskaźnik myszy został wprowadzony lub pozostawiono granice kontrolki, wysyła <xref:System.EventArgs> do procedury obsługi zdarzeń bez dalszych informacji.</span><span class="sxs-lookup"><span data-stu-id="de37a-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="de37a-111">Jeśli chcesz znać bieżący stan przycisków myszy lub lokalizacji wskaźnika myszy, a chcesz uniknąć obsługi zdarzenia myszy, możesz również użyć właściwości <xref:System.Windows.Forms.Control.MouseButtons%2A> i <xref:System.Windows.Forms.Control.MousePosition%2A> klasy <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="de37a-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="de37a-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> zwraca informacje o tym, które przyciski myszy są aktualnie naciśnięte.</span><span class="sxs-lookup"><span data-stu-id="de37a-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="de37a-113"><xref:System.Windows.Forms.Control.MousePosition%2A> zwraca współrzędne ekranu wskaźnika myszy i jest równoważne wartości zwracanej przez <xref:System.Windows.Forms.Cursor.Position%2A>.</span><span class="sxs-lookup"><span data-stu-id="de37a-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="de37a-114">Konwersja między współrzędnymi ekranu i klienta</span><span class="sxs-lookup"><span data-stu-id="de37a-114">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="de37a-115">Ponieważ niektóre informacje o lokalizacji myszy znajdują się we współrzędnych klienta, a niektóre z nich są współrzędnymi ekranu, może być konieczne przekonwertowanie punktu z jednego systemu współrzędnych na drugi.</span><span class="sxs-lookup"><span data-stu-id="de37a-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="de37a-116">Można to łatwo zrobić przy użyciu <xref:System.Windows.Forms.Control.PointToClient%2A> i <xref:System.Windows.Forms.Control.PointToScreen%2A> metod dostępnych w klasie <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="de37a-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="de37a-117">Zachowanie zdarzenia standardowego kliknięcia</span><span class="sxs-lookup"><span data-stu-id="de37a-117">Standard Click Event Behavior</span></span>

<span data-ttu-id="de37a-118">Jeśli chcesz obsłużyć zdarzenia klikania myszą w odpowiedniej kolejności, musisz znać kolejność, w której zdarzenia kliknięcia są wywoływane w kontrolkach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="de37a-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="de37a-119">Wszystkie kontrolki Windows Forms powodują wygenerowanie zdarzeń kliknięcia w tej samej kolejności, gdy przycisk myszy jest wciśnięty i wystawiony (niezależnie od tego, który przycisk myszy), z wyjątkiem tego, gdzie zaznaczono na poniższej liście dla poszczególnych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="de37a-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="de37a-120">Na poniższej liście przedstawiono kolejność zdarzeń wygenerowanych dla jednego kliknięcia przycisku myszy:</span><span class="sxs-lookup"><span data-stu-id="de37a-120">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="de37a-121">zdarzenie <xref:System.Windows.Forms.Control.MouseDown>.</span><span class="sxs-lookup"><span data-stu-id="de37a-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="de37a-122">zdarzenie <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="de37a-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="de37a-123">zdarzenie <xref:System.Windows.Forms.Control.MouseClick>.</span><span class="sxs-lookup"><span data-stu-id="de37a-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="de37a-124">zdarzenie <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="de37a-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="de37a-125">Poniżej przedstawiono kolejność zdarzeń wywoływanych przez dwukrotne kliknięcie przycisku myszy:</span><span class="sxs-lookup"><span data-stu-id="de37a-125">The following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="de37a-126">zdarzenie <xref:System.Windows.Forms.Control.MouseDown>.</span><span class="sxs-lookup"><span data-stu-id="de37a-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="de37a-127">zdarzenie <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="de37a-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="de37a-128">zdarzenie <xref:System.Windows.Forms.Control.MouseClick>.</span><span class="sxs-lookup"><span data-stu-id="de37a-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="de37a-129">zdarzenie <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="de37a-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="de37a-130">zdarzenie <xref:System.Windows.Forms.Control.MouseDown>.</span><span class="sxs-lookup"><span data-stu-id="de37a-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="de37a-131">zdarzenie <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="de37a-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="de37a-132">(Może się to różnić w zależności od tego, czy dana Kontrola ma ustawiony bit <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> stylu `true`.</span><span class="sxs-lookup"><span data-stu-id="de37a-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="de37a-133">Aby uzyskać więcej informacji na temat sposobu ustawiania bitu <xref:System.Windows.Forms.ControlStyles>, zobacz metodę <xref:System.Windows.Forms.Control.SetStyle%2A>.)</span><span class="sxs-lookup"><span data-stu-id="de37a-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="de37a-134">zdarzenie <xref:System.Windows.Forms.Control.MouseDoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="de37a-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="de37a-135">zdarzenie <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="de37a-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="de37a-136">Przykładowy kod, który pokazuje kolejność zdarzeń kliknięcia myszą, znajduje [się w temacie How to: obsługa zdarzeń wejściowych użytkownika w kontrolkach Windows Forms](how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="de37a-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="de37a-137">Poszczególne kontrolki</span><span class="sxs-lookup"><span data-stu-id="de37a-137">Individual Controls</span></span>

<span data-ttu-id="de37a-138">Następujące kontrolki nie są zgodne ze standardowym zachowaniem zdarzenia kliknięcia myszą:</span><span class="sxs-lookup"><span data-stu-id="de37a-138">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > <span data-ttu-id="de37a-139">W przypadku kontrolki <xref:System.Windows.Forms.ComboBox> zachowanie zdarzenia w dalszej części występuje, gdy użytkownik kliknie pole edycji, przycisk lub element na liście.</span><span class="sxs-lookup"><span data-stu-id="de37a-139">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="de37a-140">Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="de37a-140">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="de37a-141">Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia</span><span class="sxs-lookup"><span data-stu-id="de37a-141">Right click: No click events raised</span></span>

  - <span data-ttu-id="de37a-142">Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="de37a-142">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="de37a-143">Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia</span><span class="sxs-lookup"><span data-stu-id="de37a-143">Right double-click: No click events raised</span></span>

- <span data-ttu-id="de37a-144">kontrolki <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>i <xref:System.Windows.Forms.CheckedListBox></span><span class="sxs-lookup"><span data-stu-id="de37a-144"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="de37a-145">Zachowanie zdarzenia w dalszej części tego problemu występuje, gdy użytkownik kliknie dowolne miejsce w tych kontrolkach.</span><span class="sxs-lookup"><span data-stu-id="de37a-145">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="de37a-146">Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="de37a-146">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="de37a-147">Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia</span><span class="sxs-lookup"><span data-stu-id="de37a-147">Right click: No click events raised</span></span>

  - <span data-ttu-id="de37a-148">Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick><xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="de37a-148">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="de37a-149">Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia</span><span class="sxs-lookup"><span data-stu-id="de37a-149">Right double-click: No click events raised</span></span>

- <span data-ttu-id="de37a-150">Kontrolka <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="de37a-150"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="de37a-151">Zachowanie zdarzenia w przyszłości występuje tylko wtedy, gdy użytkownik kliknie elementy w kontrolce <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="de37a-151">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="de37a-152">Żadne zdarzenia nie są wywoływane dla kliknięć w dowolnym miejscu w formancie.</span><span class="sxs-lookup"><span data-stu-id="de37a-152">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="de37a-153">Poza zdarzeniami opisanymi w późniejszym czasie istnieją zdarzenia <xref:System.Windows.Forms.ListView.BeforeLabelEdit> i <xref:System.Windows.Forms.ListView.AfterLabelEdit>, które mogą być przydatne, jeśli chcesz użyć walidacji przy użyciu kontrolki <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="de37a-153">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="de37a-154">Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="de37a-154">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="de37a-155">Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="de37a-155">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="de37a-156">Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="de37a-156">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="de37a-157">Kliknij dwukrotnie przycisk: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="de37a-157">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="de37a-158">Kontrolka <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="de37a-158"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="de37a-159">Zachowanie zdarzenia w przyszłości występuje tylko wtedy, gdy użytkownik kliknie same elementy lub po prawej stronie elementów w kontrolce <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="de37a-159">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="de37a-160">Żadne zdarzenia nie są wywoływane dla kliknięć w dowolnym miejscu w formancie.</span><span class="sxs-lookup"><span data-stu-id="de37a-160">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="de37a-161">Oprócz tych opisanych w późniejszym czasie istnieją zdarzenia <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>i <xref:System.Windows.Forms.TreeView.AfterLabelEdit>, które mogą być przydatne, jeśli chcesz użyć walidacji z kontrolką <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="de37a-161">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="de37a-162">Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="de37a-162">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="de37a-163">Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="de37a-163">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="de37a-164">Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="de37a-164">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="de37a-165">Kliknij dwukrotnie przycisk: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="de37a-165">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="de37a-166">Zachowanie podczas malowania kontrolek przełączników</span><span class="sxs-lookup"><span data-stu-id="de37a-166">Painting behavior of toggle controls</span></span>

<span data-ttu-id="de37a-167">Kontrolki przełączania, takie jak kontrolki pochodne klasy <xref:System.Windows.Forms.ButtonBase>, mają następujące wyraźne zachowanie rysowania w połączeniu z zdarzeniami kliknięcia myszą:</span><span class="sxs-lookup"><span data-stu-id="de37a-167">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="de37a-168">Użytkownik naciśnie przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="de37a-168">The user presses the mouse button.</span></span>

2. <span data-ttu-id="de37a-169">Kontrolka maluje w stanie naciśniętym.</span><span class="sxs-lookup"><span data-stu-id="de37a-169">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="de37a-170">Zostanie zgłoszone zdarzenie <xref:System.Windows.Forms.Control.MouseDown>.</span><span class="sxs-lookup"><span data-stu-id="de37a-170">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="de37a-171">Użytkownik zwolni przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="de37a-171">The user releases the mouse button.</span></span>

5. <span data-ttu-id="de37a-172">Kontrolka maluje w stanie podniesiony.</span><span class="sxs-lookup"><span data-stu-id="de37a-172">The control paints in the raised state.</span></span>

6. <span data-ttu-id="de37a-173">Zostanie zgłoszone zdarzenie <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="de37a-173">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="de37a-174">Zostanie zgłoszone zdarzenie <xref:System.Windows.Forms.Control.MouseClick>.</span><span class="sxs-lookup"><span data-stu-id="de37a-174">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="de37a-175">Zostanie zgłoszone zdarzenie <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="de37a-175">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="de37a-176">Jeśli użytkownik przesuwa wskaźnik poza formant przełączania, gdy przycisk myszy nie działa (na przykład przesuwając mysz po naciśnięciu kontrolki <xref:System.Windows.Forms.Button> w trakcie jej naciskania), formant przełączania będzie malowany w stanie podniesiony i wystąpi tylko zdarzenie <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="de37a-176">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="de37a-177">W tej sytuacji nie będą występować zdarzenia <xref:System.Windows.Forms.Control.Click> lub <xref:System.Windows.Forms.Control.MouseClick>.</span><span class="sxs-lookup"><span data-stu-id="de37a-177">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="de37a-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de37a-178">See also</span></span>

- [<span data-ttu-id="de37a-179">Wprowadzanie za pomocą myszy w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de37a-179">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
