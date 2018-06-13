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
ms.openlocfilehash: a230611bfbb0a7f21a96de22674377887cc93c2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527803"
---
# <a name="handling-user-input"></a><span data-ttu-id="b3e85-102">Obsługa danych wejściowych użytkownika</span><span class="sxs-lookup"><span data-stu-id="b3e85-102">Handling User Input</span></span>
<span data-ttu-id="b3e85-103">W tym temacie opisano głównego zdarzenia klawiatury i myszy pochodzącymi <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b3e85-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b3e85-104">Podczas obsługi zdarzenia, autorzy kontroli powinny zastępować chronionej `On` *EventName* zamiast dołączanie delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b3e85-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="b3e85-105">Przegląd zdarzeń, zobacz [wywoływanie zdarzeń od składnika](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="b3e85-105">For a review of events, see [Raising Events from a Component](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3e85-106">Jeśli nie ma danych skojarzonych z zdarzenie wystąpienia klasy podstawowej <xref:System.EventArgs> jest przekazywany jako argument `On` *EventName* metody.</span><span class="sxs-lookup"><span data-stu-id="b3e85-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="b3e85-107">Zdarzenia klawiatury</span><span class="sxs-lookup"><span data-stu-id="b3e85-107">Keyboard Events</span></span>  
 <span data-ttu-id="b3e85-108">Typowe zdarzenia klawiatury, jaką może obsłużyć spod kontroli są <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, i <xref:System.Windows.Forms.Control.KeyUp>.</span><span class="sxs-lookup"><span data-stu-id="b3e85-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="b3e85-109">Nazwa zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b3e85-109">Event Name</span></span>|<span data-ttu-id="b3e85-110">Metoda zastąpienia</span><span class="sxs-lookup"><span data-stu-id="b3e85-110">Method to Override</span></span>|<span data-ttu-id="b3e85-111">Opis zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b3e85-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="b3e85-112">Uruchamiany, tylko gdy naciśnięcia klawisza.</span><span class="sxs-lookup"><span data-stu-id="b3e85-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="b3e85-113">Wywoływane za każdym razem, gdy zostanie naciśnięty klawisz.</span><span class="sxs-lookup"><span data-stu-id="b3e85-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="b3e85-114">Jeśli klawisz jest wciśnięty, <xref:System.Windows.Forms.Control.KeyPress> zdarzenie jest zgłaszane w częstotliwość powtarzania zdefiniowane przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="b3e85-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="b3e85-115">Wywoływane, gdy klawisz zostanie zwolniony.</span><span class="sxs-lookup"><span data-stu-id="b3e85-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="b3e85-116">Obsługa danych wprowadzonych z klawiatury jest znacznie bardziej skomplikowane niż zastępowanie zdarzeń w powyższej tabeli i wykracza poza zakres tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b3e85-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="b3e85-117">Aby uzyskać więcej informacji, zobacz [dane wejściowe użytkownika w formularzach systemu Windows](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b3e85-117">For more information, see [User Input in Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="b3e85-118">Zdarzenia myszy</span><span class="sxs-lookup"><span data-stu-id="b3e85-118">Mouse Events</span></span>  
 <span data-ttu-id="b3e85-119">Zdarzenia myszy, jaką może obsłużyć spod kontroli są <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, i <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="b3e85-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="b3e85-120">Nazwa zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b3e85-120">Event Name</span></span>|<span data-ttu-id="b3e85-121">Metoda zastąpienia</span><span class="sxs-lookup"><span data-stu-id="b3e85-121">Method to Override</span></span>|<span data-ttu-id="b3e85-122">Opis zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b3e85-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="b3e85-123">Wywoływane, gdy zostanie naciśnięty przycisk myszy, gdy wskaźnik znajduje się nad formantem.</span><span class="sxs-lookup"><span data-stu-id="b3e85-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="b3e85-124">Wywoływane, gdy wskaźnik myszy jest przesuwany najpierw region formantu.</span><span class="sxs-lookup"><span data-stu-id="b3e85-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="b3e85-125">Wywoływane, gdy wskaźnik myszy jest przesuwany nad formantem.</span><span class="sxs-lookup"><span data-stu-id="b3e85-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="b3e85-126">Wywoływane, gdy wskaźnik myszy opuści obszaru formantu.</span><span class="sxs-lookup"><span data-stu-id="b3e85-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="b3e85-127">Wywoływane, gdy wskaźnik myszy przesuwa się w regionie formantu.</span><span class="sxs-lookup"><span data-stu-id="b3e85-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="b3e85-128">Uruchamiany po zwolnieniu przycisku myszy, gdy wskaźnik myszy znajduje się nad formantem lub wskaźnik myszy opuści obszaru formantu.</span><span class="sxs-lookup"><span data-stu-id="b3e85-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="b3e85-129">Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseDown> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b3e85-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="b3e85-130">Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseMove> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b3e85-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="b3e85-131">Poniższy fragment kodu przedstawia przykład zastępowanie <xref:System.Windows.Forms.Control.MouseUp> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b3e85-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="b3e85-132">Dla kodu źródłowego pełną `FlashTrackBar` przykładowe, zobacz [jak: utworzyć Windows formularze kontroli czy pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="b3e85-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3e85-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3e85-133">See Also</span></span>  
 [<span data-ttu-id="b3e85-134">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b3e85-134">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="b3e85-135">Definiowanie zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b3e85-135">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="b3e85-136">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b3e85-136">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="b3e85-137">Dane użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b3e85-137">User Input in Windows Forms</span></span>](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
