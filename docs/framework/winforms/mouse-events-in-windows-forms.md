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
ms.workload: dotnet
ms.openlocfilehash: 5bde1c1045849fe5507081171711d5a00e99b0b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="a0ddf-102">Zdarzenia myszy w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a0ddf-102">Mouse Events in Windows Forms</span></span>
<span data-ttu-id="a0ddf-103">Podczas obsługi myszy w danych wejściowych, zwykle zapoznać się położenie myszy wskaźnik i stan przycisku myszy.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="a0ddf-104">Ten temat zawiera szczegółowe informacje dotyczące sposobu uzyskania tych informacji ze zdarzeń myszy i wyjaśniono kolejności, w których kliknięcie zdarzenia są generowane w formantach formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="a0ddf-105">Aby uzyskać listę i opis wszystkich zdarzeń myszy, zobacz [sposób działania wejście myszy w formularzach systemu Windows](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a0ddf-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="a0ddf-106">Zobacz też [Przegląd obsługi zdarzeń (formularze systemu Windows)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [Przegląd zdarzeń (formularze systemu Windows)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a0ddf-106">Also see [Event Handlers Overview (Windows Forms)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [Events Overview (Windows Forms)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))</span></span>  
  
## <a name="mouse-information"></a><span data-ttu-id="a0ddf-107">Informacje o myszy</span><span class="sxs-lookup"><span data-stu-id="a0ddf-107">Mouse Information</span></span>  
 <span data-ttu-id="a0ddf-108">A <xref:System.Windows.Forms.MouseEventArgs> są wysyłane do obsługi zdarzeń myszy związanych z kliknięcie przycisku myszy i śledzenie ruchów myszy.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="a0ddf-109"><xref:System.Windows.Forms.MouseEventArgs>zawiera informacje o bieżącym stanie mysz, takich jak lokalizacja wskaźnika myszy we współrzędnych klienta, które naciśnięciu przycisku myszy, i czy ma być przewijane kółka myszy.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="a0ddf-110">Kilka razy zdarzeń, takich jak te, które po prostu powiadomić podczas obliczania wskaźnika myszy wprowadzona lub granice formantu w lewo, wysyłanie <xref:System.EventArgs> obsługi zdarzeń z dalsze informacje.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>  
  
 <span data-ttu-id="a0ddf-111">Jeśli chcesz wiedzieć, bieżący stan przycisku myszy lub położenia wskaźnika myszy, a chce się uniknąć obsługi zdarzeń myszy, można również użyć <xref:System.Windows.Forms.Control.MouseButtons%2A> i <xref:System.Windows.Forms.Control.MousePosition%2A> właściwości <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="a0ddf-112"><xref:System.Windows.Forms.Control.MouseButtons%2A>Zwraca informacje o tym, które są aktualnie naciśnięcia przycisku myszy.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="a0ddf-113"><xref:System.Windows.Forms.Control.MousePosition%2A> Zwraca współrzędne ekranu wskaźnika myszy i jest odpowiednikiem wartości zwróconej przez <xref:System.Windows.Forms.Cursor.Position%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>  
  
## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="a0ddf-114">Konwertowanie pomiędzy ekranu i klienta koordynuje</span><span class="sxs-lookup"><span data-stu-id="a0ddf-114">Converting Between Screen and Client Coordinates</span></span>  
 <span data-ttu-id="a0ddf-115">Ponieważ niektóre informacje o lokalizacji myszy współrzędne klienta i niektóre jest we współrzędnych ekranu, konieczne może być przekonwertować punkt z jednego systemu współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="a0ddf-116">Łatwo to zrobić, za pomocą <xref:System.Windows.Forms.Control.PointToClient%2A> i <xref:System.Windows.Forms.Control.PointToScreen%2A> metod na <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>  
  
## <a name="standard-click-event-behavior"></a><span data-ttu-id="a0ddf-117">Standard kliknij zachowania zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a0ddf-117">Standard Click Event Behavior</span></span>  
 <span data-ttu-id="a0ddf-118">Jeśli chcesz obsługiwać zdarzenia w prawidłowej kolejności kliknięcia myszą, należy znać kolejności, w których kliknij zdarzenia są generowane w formantach formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="a0ddf-119">Po przycisk myszy jest wciśnięty i wydane (niezależnie od tego, który przycisk myszy), chyba że zaznaczono inaczej na poniższej liście dla pojedynczych formantów, wszystkich formularzy systemu Windows, które kontrolki podnieść kliknij zdarzenia w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="a0ddf-120">Na poniższej liście przedstawiono kolejność zdarzeń zgłaszanych Click pojedynczego przycisku myszy:</span><span class="sxs-lookup"><span data-stu-id="a0ddf-120">The following list shows the order of events raised for a single mouse-button click:</span></span>  
  
1.  <span data-ttu-id="a0ddf-121"><xref:System.Windows.Forms.Control.MouseDown>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
2.  <span data-ttu-id="a0ddf-122"><xref:System.Windows.Forms.Control.Click>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
3.  <span data-ttu-id="a0ddf-123"><xref:System.Windows.Forms.Control.MouseClick>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>  
  
4.  <span data-ttu-id="a0ddf-124"><xref:System.Windows.Forms.Control.MouseUp>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 <span data-ttu-id="a0ddf-125">Poniżej przedstawiono kolejność zdarzeń dla kliknij dwa razy przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-125">Following is the order of events raised for a double mouse-button click:</span></span>  
  
1.  <span data-ttu-id="a0ddf-126"><xref:System.Windows.Forms.Control.MouseDown>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
2.  <span data-ttu-id="a0ddf-127"><xref:System.Windows.Forms.Control.Click>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
3.  <span data-ttu-id="a0ddf-128"><xref:System.Windows.Forms.Control.MouseClick>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>  
  
4.  <span data-ttu-id="a0ddf-129"><xref:System.Windows.Forms.Control.MouseUp>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
5.  <span data-ttu-id="a0ddf-130"><xref:System.Windows.Forms.Control.MouseDown>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
6.  <span data-ttu-id="a0ddf-131"><xref:System.Windows.Forms.Control.DoubleClick>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="a0ddf-132">(To może się różnić w zależności od tego, czy w formancie ma <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> bitu stylu do `true`.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="a0ddf-133">Aby uzyskać więcej informacji na temat sposobu ustawiania <xref:System.Windows.Forms.ControlStyles> bit, zobacz <xref:System.Windows.Forms.Control.SetStyle%2A> metody.)</span><span class="sxs-lookup"><span data-stu-id="a0ddf-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>  
  
7.  <span data-ttu-id="a0ddf-134"><xref:System.Windows.Forms.Control.MouseDoubleClick>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>  
  
8.  <span data-ttu-id="a0ddf-135"><xref:System.Windows.Forms.Control.MouseUp>zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 <span data-ttu-id="a0ddf-136">Na przykład kod, który demonstruje kolejność myszy zdarzenia kliknięcia, zobacz [porady: Obsługa zdarzeń danych wejściowych użytkownika w formantach formularzy systemu Windows](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a0ddf-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>  
  
### <a name="individual-controls"></a><span data-ttu-id="a0ddf-137">Pojedynczych formantów</span><span class="sxs-lookup"><span data-stu-id="a0ddf-137">Individual Controls</span></span>  
 <span data-ttu-id="a0ddf-138">Następujące formanty nie są zgodne ze standardowej myszki kliknij zachowania zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="a0ddf-138">The following controls do not conform to the standard mouse click event behavior:</span></span>  
  
-   <span data-ttu-id="a0ddf-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, i <xref:System.Windows.Forms.RadioButton> formantów</span><span class="sxs-lookup"><span data-stu-id="a0ddf-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, and <xref:System.Windows.Forms.RadioButton> controls</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0ddf-140">Aby uzyskać <xref:System.Windows.Forms.ComboBox> kontroli zachowania zdarzenia szczegółowe później występuje, gdy użytkownik kliknie w polu edycji, po kliknięciu przycisku lub element na liście.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>  
  
    -   <span data-ttu-id="a0ddf-141">Lewy przycisk: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="a0ddf-142">Kliknij prawym przyciskiem myszy: Brak zdarzeń kliknij wywoływane</span><span class="sxs-lookup"><span data-stu-id="a0ddf-142">Right click: No click events raised</span></span>  
  
    -   <span data-ttu-id="a0ddf-143">Po lewej stronie kliknij dwukrotnie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="a0ddf-144">Kliknij dwukrotnie ikonę prawym: żadne zdarzenia kliknij wywoływane</span><span class="sxs-lookup"><span data-stu-id="a0ddf-144">Right double-click: No click events raised</span></span>  
  
-   <span data-ttu-id="a0ddf-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, i <xref:System.Windows.Forms.CheckedListBox> formantów</span><span class="sxs-lookup"><span data-stu-id="a0ddf-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0ddf-146">Zachowanie zdarzeń szczegółowe później występuje, gdy użytkownik kliknie w dowolnym miejscu w ramach tych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>  
  
    -   <span data-ttu-id="a0ddf-147">Lewy przycisk: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="a0ddf-148">Kliknij prawym przyciskiem myszy: Brak zdarzeń kliknij wywoływane</span><span class="sxs-lookup"><span data-stu-id="a0ddf-148">Right click: No click events raised</span></span>  
  
    -   <span data-ttu-id="a0ddf-149">Po lewej stronie kliknij dwukrotnie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
    -   <span data-ttu-id="a0ddf-150">Kliknij dwukrotnie ikonę prawym: żadne zdarzenia kliknij wywoływane</span><span class="sxs-lookup"><span data-stu-id="a0ddf-150">Right double-click: No click events raised</span></span>  
  
-   <span data-ttu-id="a0ddf-151"><xref:System.Windows.Forms.ListView>Formant</span><span class="sxs-lookup"><span data-stu-id="a0ddf-151"><xref:System.Windows.Forms.ListView> control</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0ddf-152">Zachowanie zdarzeń szczegółowe później występuje tylko po kliknięciu przez użytkownika dla elementów w <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="a0ddf-153">Żadne zdarzenia nie są zgłaszane dla kliknięć miejscach w formancie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="a0ddf-154">Oprócz zdarzenia w dalszej części, istnieją <xref:System.Windows.Forms.ListView.BeforeLabelEdit> i <xref:System.Windows.Forms.ListView.AfterLabelEdit> zdarzenia, które mogą być przydatne, jeśli chcesz używać weryfikacji z <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    -   <span data-ttu-id="a0ddf-155">Lewy przycisk: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="a0ddf-156">Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="a0ddf-157">Po lewej stronie kliknij dwukrotnie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
    -   <span data-ttu-id="a0ddf-158">Kliknij dwukrotnie ikonę prawym: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
-   <span data-ttu-id="a0ddf-159"><xref:System.Windows.Forms.TreeView>Formant</span><span class="sxs-lookup"><span data-stu-id="a0ddf-159"><xref:System.Windows.Forms.TreeView> control</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0ddf-160">Zachowanie zdarzeń szczegółowe później występuje tylko po kliknięciu przez użytkownika na elementach, samodzielnie lub w prawo elementów w <xref:System.Windows.Forms.TreeView> formantu.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="a0ddf-161">Żadne zdarzenia nie są zgłaszane dla kliknięć miejscach w formancie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="a0ddf-162">Oprócz tych w dalszej części, istnieją <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, i <xref:System.Windows.Forms.TreeView.AfterLabelEdit> zdarzenia, które mogą być przydatne, jeśli chcesz używać weryfikacji z <xref:System.Windows.Forms.TreeView> formantu .</span><span class="sxs-lookup"><span data-stu-id="a0ddf-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
    -   <span data-ttu-id="a0ddf-163">Lewy przycisk: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="a0ddf-164">Kliknij prawym przyciskiem myszy: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="a0ddf-165">Po lewej stronie kliknij dwukrotnie: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
    -   <span data-ttu-id="a0ddf-166">Kliknij dwukrotnie ikonę prawym: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="a0ddf-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="a0ddf-167">Malowanie zachowanie przełączania formantów</span><span class="sxs-lookup"><span data-stu-id="a0ddf-167">Painting Behavior of Toggle Controls</span></span>  
 <span data-ttu-id="a0ddf-168">Przełącz formanty, takie jak formanty wynikających z <xref:System.Windows.Forms.ButtonBase> klasa, ma następujące zachowanie charakterystyczne malowania w połączeniu z myszy zdarzenia kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="a0ddf-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>  
  
1.  <span data-ttu-id="a0ddf-169">Użytkownik naciśnie przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-169">The user presses the mouse button.</span></span>  
  
2.  <span data-ttu-id="a0ddf-170">W stan naciśnięcia umożliwia malowanie formantu.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-170">The control paints in the pressed state.</span></span>  
  
3.  <span data-ttu-id="a0ddf-171"><xref:System.Windows.Forms.Control.MouseDown> Zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>  
  
4.  <span data-ttu-id="a0ddf-172">Użytkownik zwolni przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-172">The user releases the mouse button.</span></span>  
  
5.  <span data-ttu-id="a0ddf-173">W stanie zgłoszono umożliwia malowanie formantu.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-173">The control paints in the raised state.</span></span>  
  
6.  <span data-ttu-id="a0ddf-174"><xref:System.Windows.Forms.Control.Click> Zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>  
  
7.  <span data-ttu-id="a0ddf-175"><xref:System.Windows.Forms.Control.MouseClick> Zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>  
  
8.  <span data-ttu-id="a0ddf-176"><xref:System.Windows.Forms.Control.MouseUp> Zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0ddf-177">Jeśli użytkownik przesuwa wskaźnik poza formantu przełącznika, gdy przycisk myszy jest wciśnięty (takie jak przesuwanie wskaźnika myszy <xref:System.Windows.Forms.Button> kontrolować naciśniętym zostanie), Przełącz sterowanie namaluje w zgłoszono stanu i to tylko <xref:System.Windows.Forms.Control.MouseUp> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="a0ddf-178"><xref:System.Windows.Forms.Control.Click> Lub <xref:System.Windows.Forms.Control.MouseClick> w takiej sytuacji nie nastąpi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0ddf-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0ddf-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0ddf-179">See Also</span></span>  
 [<span data-ttu-id="a0ddf-180">Wprowadzanie za pomocą myszy w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0ddf-180">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
