---
title: 'Instrukcje: Określanie, który klawisz modyfikujący został naciśnięty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: 37fa897f5a2e1c65cbd5db9189f1500e3427c920
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964314"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="cdbb0-102">Instrukcje: Określanie, który klawisz modyfikujący został naciśnięty</span><span class="sxs-lookup"><span data-stu-id="cdbb0-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="cdbb0-103">Podczas tworzenia aplikacji, która akceptuje naciśnięcia klawiszy użytkownika, może być również konieczne monitorowanie klawiszy modyfikujących, takich jak klawisze SHIFT, ALT i CTRL.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="cdbb0-104">Gdy klawisz modyfikujący zostanie wciśnięty w połączeniu z innymi kluczami lub kliknięciem myszy, aplikacja może odpowiednio reagować.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="cdbb0-105">Na przykład po naciśnięciu litery S może to spowodować, że "S" pojawi się na ekranie, ale po naciśnięciu klawiszy CTRL + S bieżący dokument może zostać zapisany.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="cdbb0-106">W przypadku obsługi <xref:System.Windows.Forms.Control.KeyDown> zdarzenia <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> Właściwość <xref:System.Windows.Forms.KeyEventArgs> odebrana przez procedurę obsługi zdarzeń określa, które klawisze modyfikujące zostały naciśnięte.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="cdbb0-107"><xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> Alternatywnie<xref:System.Windows.Forms.KeyEventArgs> Właściwość określa znak, który został naciśnięty, a także wszystkie klawisze modyfikujące z bitowym lub.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="cdbb0-108">Jednak w przypadku obsługi <xref:System.Windows.Forms.Control.KeyPress> zdarzenia lub zdarzenia myszy program obsługi zdarzeń nie otrzymuje tych informacji.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="cdbb0-109">W takim przypadku należy użyć <xref:System.Windows.Forms.Control.ModifierKeys%2A> właściwości <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="cdbb0-110">W obu przypadkach należy wykonać bitowe i odpowiednią <xref:System.Windows.Forms.Keys> wartość oraz wartość, którą testujesz.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="cdbb0-111"><xref:System.Windows.Forms.Keys> Wyliczenie oferuje różne odmiany poszczególnych klawiszy modyfikujących, dlatego ważne jest, aby wykonać bitowe i z poprawną wartością.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="cdbb0-112">Na przykład klawisz Shift jest reprezentowany przez <xref:System.Windows.Forms.Keys.Shift> <xref:System.Windows.Forms.Keys.RShiftKey> , <xref:System.Windows.Forms.Keys.ShiftKey>i <xref:System.Windows.Forms.Keys.LShiftKey> poprawna wartość w celu przetestowania klawisza modyfikującego jest <xref:System.Windows.Forms.Keys.Shift>równa.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="cdbb0-113">Podobnie, aby testować pod kątem kombinacji klawiszy CTRL i Alt jako modyfikatorów <xref:System.Windows.Forms.Keys.Control> , <xref:System.Windows.Forms.Keys.Alt> należy odpowiednio użyć wartości i.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-113">Similarly, to test for CTRL and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdbb0-114">Visual Basic programiści mogą również uzyskać dostęp do kluczowych informacji <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> za pomocą właściwości</span><span class="sxs-lookup"><span data-stu-id="cdbb0-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="cdbb0-115">Aby określić, który klawisz modyfikujący został naciśnięty</span><span class="sxs-lookup"><span data-stu-id="cdbb0-115">To determine which modifier key was pressed</span></span>  
  
- <span data-ttu-id="cdbb0-116">Użyj operatora bitowego `AND` <xref:System.Windows.Forms.Control.ModifierKeys%2A> z właściwością <xref:System.Windows.Forms.Keys> i wartością wyliczenia, aby określić, czy określony klawisz modyfikujący został naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="cdbb0-117">Poniższy przykład kodu pokazuje, jak ustalić, czy klawisz Shift jest wciśnięty w ramach <xref:System.Windows.Forms.Control.KeyPress> procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cdbb0-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="cdbb0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdbb0-118">See also</span></span>

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [<span data-ttu-id="cdbb0-119">Wprowadzanie z klawiatury w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cdbb0-119">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- <span data-ttu-id="cdbb0-120">[Instrukcje: Określ, czy CapsLock jest włączona w Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cdbb0-120">[How to: Determine If CapsLock is On in Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span></span>
