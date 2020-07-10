---
title: Zdarzenia myszy
description: Dowiedz się, jak uzyskać lokalizację myszy ze zdarzeń myszy, i zrozumieć kolejność, w jakiej są wywoływane zdarzenia kliknięcia myszą w kontrolkach Windows Forms.
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
ms.openlocfilehash: 640448109961ea5fdf3600ef9e72d7d10e8c9e49
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174383"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="5e129-103">Zdarzenia myszy w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5e129-103">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="5e129-104">W przypadku obsługi danych wejściowych myszy zwykle potrzebna jest znajomość położenia wskaźnika myszy i stanu przycisków myszy.</span><span class="sxs-lookup"><span data-stu-id="5e129-104">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="5e129-105">Ten temat zawiera szczegółowe informacje o tym, jak uzyskać te informacje ze zdarzeń myszy, i wyjaśnienie kolejności, w której zdarzenia kliknięcia myszą są wywoływane w kontrolkach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5e129-105">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="5e129-106">Aby zapoznać się z listą i opisem wszystkich zdarzeń myszy, zobacz [jak działa wprowadzanie myszą w Windows Forms](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5e129-106">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="5e129-107">Zobacz także [Omówienie obsługi zdarzeń (Windows Forms)](event-handlers-overview-windows-forms.md) i [przegląd zdarzeń (Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5e129-107">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="5e129-108">Informacje o myszy</span><span class="sxs-lookup"><span data-stu-id="5e129-108">Mouse Information</span></span>

<span data-ttu-id="5e129-109"><xref:System.Windows.Forms.MouseEventArgs>Jest wysyłany do programów obsługi zdarzeń myszy związanych z kliknięciem przycisku myszy i śledzeniem ruchów myszy.</span><span class="sxs-lookup"><span data-stu-id="5e129-109">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="5e129-110"><xref:System.Windows.Forms.MouseEventArgs>zawiera informacje o bieżącym stanie myszy, w tym o lokalizacji wskaźnika myszy w współrzędnej klienta, które przyciski myszy są naciśnięte i czy kółko myszy zostało przeprzewijane.</span><span class="sxs-lookup"><span data-stu-id="5e129-110"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="5e129-111">Kilka zdarzeń myszy, takich jak te, które po prostu powiadamiają, gdy wskaźnik myszy został wprowadzony lub pozostawiono granice kontrolki, wysyła <xref:System.EventArgs> do programu obsługi zdarzeń bez dalszych informacji.</span><span class="sxs-lookup"><span data-stu-id="5e129-111">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="5e129-112">Jeśli chcesz znać bieżący stan przycisków myszy lub lokalizacji wskaźnika myszy, a chcesz uniknąć obsługi zdarzenia myszy, możesz również użyć <xref:System.Windows.Forms.Control.MouseButtons%2A> <xref:System.Windows.Forms.Control.MousePosition%2A> właściwości i <xref:System.Windows.Forms.Control> klasy w klasie.</span><span class="sxs-lookup"><span data-stu-id="5e129-112">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="5e129-113"><xref:System.Windows.Forms.Control.MouseButtons%2A>zwraca informacje o tym, które przyciski myszy są aktualnie naciśnięte.</span><span class="sxs-lookup"><span data-stu-id="5e129-113"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="5e129-114"><xref:System.Windows.Forms.Control.MousePosition%2A>Zwraca współrzędne ekranu wskaźnika myszy i jest równoważne wartości zwracanej przez <xref:System.Windows.Forms.Cursor.Position%2A> .</span><span class="sxs-lookup"><span data-stu-id="5e129-114">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="5e129-115">Konwersja między współrzędnymi ekranu i klienta</span><span class="sxs-lookup"><span data-stu-id="5e129-115">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="5e129-116">Ponieważ niektóre informacje o lokalizacji myszy znajdują się we współrzędnych klienta, a niektóre z nich są współrzędnymi ekranu, może być konieczne przekonwertowanie punktu z jednego systemu współrzędnych na drugi.</span><span class="sxs-lookup"><span data-stu-id="5e129-116">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="5e129-117">Można to łatwo zrobić przy użyciu <xref:System.Windows.Forms.Control.PointToClient%2A> <xref:System.Windows.Forms.Control.PointToScreen%2A> metod i dostępnych w <xref:System.Windows.Forms.Control> klasie.</span><span class="sxs-lookup"><span data-stu-id="5e129-117">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="5e129-118">Zachowanie zdarzenia standardowego kliknięcia</span><span class="sxs-lookup"><span data-stu-id="5e129-118">Standard Click Event Behavior</span></span>

<span data-ttu-id="5e129-119">Jeśli chcesz obsłużyć zdarzenia klikania myszą w odpowiedniej kolejności, musisz znać kolejność, w której zdarzenia kliknięcia są wywoływane w kontrolkach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5e129-119">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="5e129-120">Wszystkie kontrolki Windows Forms powodują wygenerowanie zdarzeń kliknięcia w tej samej kolejności, gdy przycisk myszy jest wciśnięty i wystawiony (niezależnie od tego, który przycisk myszy), z wyjątkiem tego, gdzie zaznaczono na poniższej liście dla poszczególnych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="5e129-120">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="5e129-121">Na poniższej liście przedstawiono kolejność zdarzeń wygenerowanych dla jednego kliknięcia przycisku myszy:</span><span class="sxs-lookup"><span data-stu-id="5e129-121">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="5e129-122"><xref:System.Windows.Forms.Control.MouseDown>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-122"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="5e129-123"><xref:System.Windows.Forms.Control.Click>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-123"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="5e129-124"><xref:System.Windows.Forms.Control.MouseClick>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-124"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="5e129-125"><xref:System.Windows.Forms.Control.MouseUp>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-125"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="5e129-126">Poniżej przedstawiono kolejność zdarzeń wywoływanych przez dwukrotne kliknięcie przycisku myszy:</span><span class="sxs-lookup"><span data-stu-id="5e129-126">The following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="5e129-127"><xref:System.Windows.Forms.Control.MouseDown>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-127"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="5e129-128"><xref:System.Windows.Forms.Control.Click>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-128"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="5e129-129"><xref:System.Windows.Forms.Control.MouseClick>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-129"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="5e129-130"><xref:System.Windows.Forms.Control.MouseUp>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-130"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="5e129-131"><xref:System.Windows.Forms.Control.MouseDown>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-131"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="5e129-132"><xref:System.Windows.Forms.Control.DoubleClick>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-132"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="5e129-133">(Może się to różnić w zależności od tego, czy dana kontrolka ma <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> ustawiony bit stylu `true` .</span><span class="sxs-lookup"><span data-stu-id="5e129-133">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="5e129-134">Aby uzyskać więcej informacji na temat sposobu ustawiania <xref:System.Windows.Forms.ControlStyles> bitu, zobacz <xref:System.Windows.Forms.Control.SetStyle%2A> metodę.)</span><span class="sxs-lookup"><span data-stu-id="5e129-134">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="5e129-135"><xref:System.Windows.Forms.Control.MouseDoubleClick>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-135"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="5e129-136"><xref:System.Windows.Forms.Control.MouseUp>wydarzen.</span><span class="sxs-lookup"><span data-stu-id="5e129-136"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="5e129-137">Przykładowy kod, który pokazuje kolejność zdarzeń kliknięcia myszą, znajduje [się w temacie How to: obsługa zdarzeń wejściowych użytkownika w kontrolkach Windows Forms](how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5e129-137">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="5e129-138">Poszczególne kontrolki</span><span class="sxs-lookup"><span data-stu-id="5e129-138">Individual Controls</span></span>

<span data-ttu-id="5e129-139">Następujące kontrolki nie są zgodne ze standardowym zachowaniem zdarzenia kliknięcia myszą:</span><span class="sxs-lookup"><span data-stu-id="5e129-139">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > <span data-ttu-id="5e129-140">W przypadku <xref:System.Windows.Forms.ComboBox> kontrolki, zachowanie zdarzenia w dalszej części występuje, gdy użytkownik kliknie pole edycji, przycisk lub element na liście.</span><span class="sxs-lookup"><span data-stu-id="5e129-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="5e129-141">Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="5e129-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="5e129-142">Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia</span><span class="sxs-lookup"><span data-stu-id="5e129-142">Right click: No click events raised</span></span>

  - <span data-ttu-id="5e129-143">Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="5e129-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="5e129-144">Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia</span><span class="sxs-lookup"><span data-stu-id="5e129-144">Right double-click: No click events raised</span></span>

- <span data-ttu-id="5e129-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox> ,,, <xref:System.Windows.Forms.ListBox> <xref:System.Windows.Forms.MaskedTextBox> i <xref:System.Windows.Forms.CheckedListBox> kontrolki</span><span class="sxs-lookup"><span data-stu-id="5e129-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="5e129-146">Zachowanie zdarzenia w dalszej części tego problemu występuje, gdy użytkownik kliknie dowolne miejsce w tych kontrolkach.</span><span class="sxs-lookup"><span data-stu-id="5e129-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="5e129-147">Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="5e129-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="5e129-148">Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia</span><span class="sxs-lookup"><span data-stu-id="5e129-148">Right click: No click events raised</span></span>

  - <span data-ttu-id="5e129-149">Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> , <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="5e129-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="5e129-150">Kliknięcie prawym przyciskiem myszy: nie zgłoszono zdarzeń kliknięcia</span><span class="sxs-lookup"><span data-stu-id="5e129-150">Right double-click: No click events raised</span></span>

- <span data-ttu-id="5e129-151"><xref:System.Windows.Forms.ListView>kontroli</span><span class="sxs-lookup"><span data-stu-id="5e129-151"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="5e129-152">Zachowanie zdarzenia w przyszłości występuje tylko wtedy, gdy użytkownik kliknie elementy w <xref:System.Windows.Forms.ListView> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="5e129-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="5e129-153">Żadne zdarzenia nie są wywoływane dla kliknięć w dowolnym miejscu w formancie.</span><span class="sxs-lookup"><span data-stu-id="5e129-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="5e129-154">Poza zdarzeniami opisanymi później istnieją <xref:System.Windows.Forms.ListView.BeforeLabelEdit> <xref:System.Windows.Forms.ListView.AfterLabelEdit> zdarzenia i, które mogą być przydatne, jeśli chcesz użyć walidacji z <xref:System.Windows.Forms.ListView> kontrolką.</span><span class="sxs-lookup"><span data-stu-id="5e129-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="5e129-155">Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="5e129-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="5e129-156">Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="5e129-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="5e129-157">Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="5e129-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="5e129-158">Kliknij dwukrotnie przycisk: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="5e129-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="5e129-159"><xref:System.Windows.Forms.TreeView>kontroli</span><span class="sxs-lookup"><span data-stu-id="5e129-159"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="5e129-160">Zachowanie zdarzenia w przyszłości występuje tylko wtedy, gdy użytkownik kliknie same elementy lub po prawej stronie elementów w <xref:System.Windows.Forms.TreeView> formancie.</span><span class="sxs-lookup"><span data-stu-id="5e129-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="5e129-161">Żadne zdarzenia nie są wywoływane dla kliknięć w dowolnym miejscu w formancie.</span><span class="sxs-lookup"><span data-stu-id="5e129-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="5e129-162">Oprócz tych opisanych później, istnieją zdarzenia,,, <xref:System.Windows.Forms.TreeView.BeforeCheck> , <xref:System.Windows.Forms.TreeView.BeforeSelect> <xref:System.Windows.Forms.TreeView.BeforeLabelEdit> <xref:System.Windows.Forms.TreeView.AfterSelect> <xref:System.Windows.Forms.TreeView.AfterCheck> i <xref:System.Windows.Forms.TreeView.AfterLabelEdit> , które mogą być przydatne, jeśli chcesz użyć walidacji z <xref:System.Windows.Forms.TreeView> kontrolką.</span><span class="sxs-lookup"><span data-stu-id="5e129-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="5e129-163">Kliknięcie lewym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="5e129-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="5e129-164">Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="5e129-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="5e129-165">Lewy dwukrotne kliknięcie: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="5e129-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="5e129-166">Kliknij dwukrotnie przycisk: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="5e129-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="5e129-167">Zachowanie podczas malowania kontrolek przełączników</span><span class="sxs-lookup"><span data-stu-id="5e129-167">Painting behavior of toggle controls</span></span>

<span data-ttu-id="5e129-168">Kontrolki przełączania, takie jak kontrolki pochodne <xref:System.Windows.Forms.ButtonBase> klasy, mają następujące wyraźne zachowanie rysowania w połączeniu z zdarzeniami kliknięcia myszą:</span><span class="sxs-lookup"><span data-stu-id="5e129-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="5e129-169">Użytkownik naciśnie przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="5e129-169">The user presses the mouse button.</span></span>

2. <span data-ttu-id="5e129-170">Kontrolka maluje w stanie naciśniętym.</span><span class="sxs-lookup"><span data-stu-id="5e129-170">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="5e129-171"><xref:System.Windows.Forms.Control.MouseDown>Zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="5e129-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="5e129-172">Użytkownik zwolni przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="5e129-172">The user releases the mouse button.</span></span>

5. <span data-ttu-id="5e129-173">Kontrolka maluje w stanie podniesiony.</span><span class="sxs-lookup"><span data-stu-id="5e129-173">The control paints in the raised state.</span></span>

6. <span data-ttu-id="5e129-174"><xref:System.Windows.Forms.Control.Click>Zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="5e129-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="5e129-175"><xref:System.Windows.Forms.Control.MouseClick>Zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="5e129-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="5e129-176"><xref:System.Windows.Forms.Control.MouseUp>Zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="5e129-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5e129-177">Jeśli użytkownik przesunie wskaźnik z kontrolki przełączania, gdy przycisk myszy nie działa (na przykład przesuwając mysz po <xref:System.Windows.Forms.Button> naciśnięciu kontrolki), formant przełączania będzie malowany w stanie podniesiony i <xref:System.Windows.Forms.Control.MouseUp> wystąpi tylko zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="5e129-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="5e129-178"><xref:System.Windows.Forms.Control.Click>Zdarzenia lub nie pojawią się <xref:System.Windows.Forms.Control.MouseClick> w tej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="5e129-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e129-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e129-179">See also</span></span>

- [<span data-ttu-id="5e129-180">Wprowadzanie za pomocą myszy w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e129-180">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
