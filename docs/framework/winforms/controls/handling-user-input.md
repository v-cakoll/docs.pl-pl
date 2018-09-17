---
title: Obsługa danych wejściowych użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: 19bb494d6f478c8cb7adda770f441470c4b2d19f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677672"
---
# <a name="handling-user-input"></a><span data-ttu-id="a471a-102">Obsługa danych wejściowych użytkownika</span><span class="sxs-lookup"><span data-stu-id="a471a-102">Handling User Input</span></span>
<span data-ttu-id="a471a-103">W tym temacie opisano główne zdarzeń klawiatury oraz myszy dostarczone przez <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a471a-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a471a-104">Podczas obsługi zdarzenia, autorzy kontrolki powinien przesłonić chronionego `On` *EventName* metody zamiast dołączając delegata do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a471a-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="a471a-105">Aby uzyskać przegląd zdarzeń, zobacz [Raising Events ze składnika](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="a471a-105">For a review of events, see [Raising Events from a Component](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a471a-106">Jeśli nie ma żadnych danych, skojarzone ze zdarzeniem, wystąpienie klasy bazowej <xref:System.EventArgs> jest przekazywany jako argument do `On` *EventName* metody.</span><span class="sxs-lookup"><span data-stu-id="a471a-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="a471a-107">Zdarzenia klawiatury</span><span class="sxs-lookup"><span data-stu-id="a471a-107">Keyboard Events</span></span>  
 <span data-ttu-id="a471a-108">Typowe zdarzenia klawiatury, które może obsłużyć Twoją kontrolą są <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, i <xref:System.Windows.Forms.Control.KeyUp>.</span><span class="sxs-lookup"><span data-stu-id="a471a-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="a471a-109">Nazwa zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a471a-109">Event Name</span></span>|<span data-ttu-id="a471a-110">Metody do przesłonięcia</span><span class="sxs-lookup"><span data-stu-id="a471a-110">Method to Override</span></span>|<span data-ttu-id="a471a-111">Opis zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a471a-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="a471a-112">Wywoływane, tylko gdy naciśnięcia klawisza.</span><span class="sxs-lookup"><span data-stu-id="a471a-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="a471a-113">Wywoływane za każdym razem, gdy zostanie naciśnięty klawisz.</span><span class="sxs-lookup"><span data-stu-id="a471a-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="a471a-114">Jeśli klawisz jest wciśnięty, <xref:System.Windows.Forms.Control.KeyPress> zdarzenie jest zgłaszane w częstotliwość powtarzania zdefiniowane przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="a471a-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="a471a-115">Wywoływane po zwolnieniu klawisza.</span><span class="sxs-lookup"><span data-stu-id="a471a-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a471a-116">Obsługa danych wprowadzonych z klawiatury jest znacznie bardziej skomplikowane niż zastępowanie zdarzenia w powyższej tabeli i wykracza poza zakres tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a471a-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="a471a-117">Aby uzyskać więcej informacji, zobacz [dane wejściowe użytkownika w formularzach Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a471a-117">For more information, see [User Input in Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="a471a-118">Zdarzenia myszy</span><span class="sxs-lookup"><span data-stu-id="a471a-118">Mouse Events</span></span>  
 <span data-ttu-id="a471a-119">Zdarzenia myszy, które może obsłużyć Twoją kontrolą są <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, i <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="a471a-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="a471a-120">Nazwa zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a471a-120">Event Name</span></span>|<span data-ttu-id="a471a-121">Metody do przesłonięcia</span><span class="sxs-lookup"><span data-stu-id="a471a-121">Method to Override</span></span>|<span data-ttu-id="a471a-122">Opis zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a471a-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="a471a-123">Wywoływane, gdy przycisk myszy jest wciśnięty, gdy wskaźnik znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="a471a-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="a471a-124">Wywoływane, gdy kursor po raz pierwszy najedzie z regionem danej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a471a-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="a471a-125">Wywoływane, gdy wskaźnik myszy nad formant.</span><span class="sxs-lookup"><span data-stu-id="a471a-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="a471a-126">Wywoływane po odsunięciu wskaźnika z regionem danej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a471a-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="a471a-127">Wywoływane, gdy wskaźnik myszy jest przesuwany w regionie formantu.</span><span class="sxs-lookup"><span data-stu-id="a471a-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="a471a-128">Wywoływane po zwolnieniu przycisku myszy, gdy wskaźnik znajduje się nad kontrolką lub odsunięcia kursora z regionem danej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a471a-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="a471a-129">Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseDown> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a471a-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="a471a-130">Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseMove> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a471a-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="a471a-131">Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseUp> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a471a-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="a471a-132">Dla pełnego kodu źródłowego dla `FlashTrackBar` przykładowe, zobacz [porady: tworzenie Windows Forms kontroli, pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="a471a-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a471a-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a471a-133">See Also</span></span>  
 [<span data-ttu-id="a471a-134">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a471a-134">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="a471a-135">Definiowanie zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a471a-135">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="a471a-136">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a471a-136">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="a471a-137">Dane użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a471a-137">User Input in Windows Forms</span></span>](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
