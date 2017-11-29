---
title: "Porady: określanie, który klawisz modyfikujący został naciśnięty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6fdc93063bbc8c9428f2f01c6cd5c0578e77ab01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="32a33-102">Porady: określanie, który klawisz modyfikujący został naciśnięty</span><span class="sxs-lookup"><span data-stu-id="32a33-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="32a33-103">Podczas tworzenia aplikacji, która akceptuje naciśnięcia klawiszy przez użytkownika, można również monitorować klawisze modyfikujące, takie jak klawiszy SHIFT, ALT i CTRL.</span><span class="sxs-lookup"><span data-stu-id="32a33-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="32a33-104">Po naciśnięciu klawisza modyfikator w połączeniu z kluczy lub kliknięcie myszą, aplikacja może odpowiadać odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="32a33-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="32a33-105">Na przykład jeśli litera S zostanie naciśnięty, po prostu może to spowodować "s" na ekranie, ale jeśli naciskania klawiszy CTRL + S, mogą zostać zapisane bieżącego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="32a33-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="32a33-106">Jeśli można obsługiwać <xref:System.Windows.Forms.Control.KeyDown> zdarzenia <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> odebranych przez zdarzenie obsługi Określa, które klawisze modyfikujące naciśnięciu.</span><span class="sxs-lookup"><span data-stu-id="32a33-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="32a33-107">Alternatywnie <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> określa znak, który został naciśnięty również jako wszystkie klawisze modyfikujące, w połączeniu z bitowego OR.</span><span class="sxs-lookup"><span data-stu-id="32a33-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="32a33-108">Jednak jeśli jest obsługa <xref:System.Windows.Forms.Control.KeyPress> zdarzenie lub zdarzenia myszy programu obsługi zdarzeń nie otrzymuje informacji.</span><span class="sxs-lookup"><span data-stu-id="32a33-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="32a33-109">W takim przypadku należy użyć <xref:System.Windows.Forms.Control.ModifierKeys%2A> właściwość <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="32a33-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="32a33-110">W obu przypadkach należy wykonać iloczynu bitowego AND z odpowiednią <xref:System.Windows.Forms.Keys> wartości i wartości podczas testowania.</span><span class="sxs-lookup"><span data-stu-id="32a33-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="32a33-111"><xref:System.Windows.Forms.Keys> Wyliczenie oferuje zmian każdego klawisz modyfikujący, dlatego należy przeprowadzić operatora testu koniunkcji i z poprawną wartość.</span><span class="sxs-lookup"><span data-stu-id="32a33-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="32a33-112">Na przykład klawisz SHIFT jest reprezentowana przez <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> i <xref:System.Windows.Forms.Keys.LShiftKey> poprawną wartość do testowania SHIFT, ponieważ jest klawisz modyfikujący <xref:System.Windows.Forms.Keys.Shift>.</span><span class="sxs-lookup"><span data-stu-id="32a33-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="32a33-113">Podobnie do testowania TROLERA i ALT jako modyfikatory możesz należy używać <xref:System.Windows.Forms.Keys.Control> i <xref:System.Windows.Forms.Keys.Alt> wartości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="32a33-113">Similarly, to test for CTLR and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32a33-114">Języka Visual Basic można również dostęp do kluczowych informacji za pośrednictwem <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> właściwości</span><span class="sxs-lookup"><span data-stu-id="32a33-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="32a33-115">Aby ustalić, który klawisz modyfikujący został naciśnięty</span><span class="sxs-lookup"><span data-stu-id="32a33-115">To determine which modifier key was pressed</span></span>  
  
-   <span data-ttu-id="32a33-116">Użyj operatora testu koniunkcji `AND` operatora z <xref:System.Windows.Forms.Control.ModifierKeys%2A> właściwości i wartości <xref:System.Windows.Forms.Keys> wyliczeniu, aby określić, czy zostanie naciśnięty klawisz modyfikujący konkretnego.</span><span class="sxs-lookup"><span data-stu-id="32a33-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="32a33-117">Poniższy przykład kodu pokazuje sposób określania, czy w ramach zostanie naciśnięty klawisz SHIFT <xref:System.Windows.Forms.Control.KeyPress> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32a33-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="32a33-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32a33-118">See Also</span></span>  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [<span data-ttu-id="32a33-119">Wprowadzanie z klawiatury w systemie Windows formularzy aplikacji</span><span class="sxs-lookup"><span data-stu-id="32a33-119">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="32a33-120">Porady: Określ, czy CapsLock występuje na w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32a33-120">How to: Determine If CapsLock is On in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/91e60f5c-dd61-4222-ba5f-39af803afd8c)
