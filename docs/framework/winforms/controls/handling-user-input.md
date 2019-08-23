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
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934095"
---
# <a name="handling-user-input"></a><span data-ttu-id="4fd8b-102">Obsługa danych wejściowych użytkownika</span><span class="sxs-lookup"><span data-stu-id="4fd8b-102">Handling User Input</span></span>
<span data-ttu-id="4fd8b-103">W tym temacie opisano główne zdarzenia klawiatury i myszy udostępniane przez <xref:System.Windows.Forms.Control?displayProperty=nameWithType>program.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4fd8b-104">Podczas obsługi zdarzenia, autorzy kontroli powinny zastąpić `On`metodę *EventName* , zamiast dołączać delegata do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="4fd8b-105">Aby zapoznać się z przeglądem zdarzeń, zobacz Wywoływanie [zdarzeń ze składnika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="4fd8b-105">For a review of events, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fd8b-106">Jeśli żadne dane nie są skojarzone ze zdarzeniem, wystąpienie klasy <xref:System.EventArgs> bazowej jest przesyłane jako argument `On`do metody *EventName* .</span><span class="sxs-lookup"><span data-stu-id="4fd8b-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="4fd8b-107">Zdarzenia klawiatury</span><span class="sxs-lookup"><span data-stu-id="4fd8b-107">Keyboard Events</span></span>  
 <span data-ttu-id="4fd8b-108">Typowe zdarzenia klawiatury, które może obsłużyć formant <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>to, <xref:System.Windows.Forms.Control.KeyUp>i.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="4fd8b-109">Nazwa zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4fd8b-109">Event Name</span></span>|<span data-ttu-id="4fd8b-110">Metoda przesłonięcia</span><span class="sxs-lookup"><span data-stu-id="4fd8b-110">Method to Override</span></span>|<span data-ttu-id="4fd8b-111">Opis zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4fd8b-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="4fd8b-112">Uruchamiany tylko po pierwszym naciśnięciu klawisza.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="4fd8b-113">Uruchamiany przy każdym naciśnięciu klawisza.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="4fd8b-114">Jeśli klucz jest wyłączony, <xref:System.Windows.Forms.Control.KeyPress> zdarzenie jest zgłaszane według częstotliwości powtarzania zdefiniowanej przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="4fd8b-115">Uruchamiany po wydaniu klucza.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="4fd8b-116">Obsługa wprowadzania z klawiatury jest znacznie bardziej skomplikowane niż Przesłanianie zdarzeń w powyższej tabeli i wykracza poza zakres tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="4fd8b-117">Aby uzyskać więcej informacji, zobacz [dane wejściowe użytkownika w Windows Forms](../user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4fd8b-117">For more information, see [User Input in Windows Forms](../user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="4fd8b-118">Zdarzenia myszy</span><span class="sxs-lookup"><span data-stu-id="4fd8b-118">Mouse Events</span></span>  
 <span data-ttu-id="4fd8b-119">Zdarzenia myszy, które może obsłużyć formant <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseEnter> <xref:System.Windows.Forms.Control.MouseLeave> <xref:System.Windows.Forms.Control.MouseMove>to,,,, <xref:System.Windows.Forms.Control.MouseUp>i.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="4fd8b-120">Nazwa zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4fd8b-120">Event Name</span></span>|<span data-ttu-id="4fd8b-121">Metoda przesłonięcia</span><span class="sxs-lookup"><span data-stu-id="4fd8b-121">Method to Override</span></span>|<span data-ttu-id="4fd8b-122">Opis zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4fd8b-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="4fd8b-123">Uruchamiany po naciśnięciu przycisku myszy, gdy wskaźnik znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="4fd8b-124">Uruchamiany, gdy wskaźnik wprowadzi pierwszy region kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="4fd8b-125">Uruchamiany, gdy wskaźnik myszy znajduje się nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="4fd8b-126">Uruchamiany, gdy wskaźnik opuści region kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="4fd8b-127">Uruchamiany, gdy wskaźnik zostanie przesunięty w region formantu.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="4fd8b-128">Uruchamiany po udostępnieniu przycisku myszy, gdy wskaźnik znajduje się nad kontrolką lub wskaźnik opuszcza region kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="4fd8b-129">Poniższy fragment kodu przedstawia przykład zastępowania <xref:System.Windows.Forms.Control.MouseDown> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="4fd8b-130">Poniższy fragment kodu przedstawia przykład zastępowania <xref:System.Windows.Forms.Control.MouseMove> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="4fd8b-131">Poniższy fragment kodu przedstawia przykład zastępowania <xref:System.Windows.Forms.Control.MouseUp> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4fd8b-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="4fd8b-132">Aby uzyskać pełny kod źródłowy dla `FlashTrackBar` przykładu, zobacz [How to: Utwórz formant Windows Forms, który pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="4fd8b-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd8b-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fd8b-133">See also</span></span>

- [<span data-ttu-id="4fd8b-134">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4fd8b-134">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="4fd8b-135">Definiowanie zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4fd8b-135">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="4fd8b-136">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4fd8b-136">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="4fd8b-137">Dane użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4fd8b-137">User Input in Windows Forms</span></span>](../user-input-in-windows-forms.md)
