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
ms.openlocfilehash: de8af53bbf065047541e030de7a174987e5785df
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715987"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="f43eb-102">Instrukcje: Określanie, który klawisz modyfikujący został naciśnięty</span><span class="sxs-lookup"><span data-stu-id="f43eb-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="f43eb-103">Gdy tworzysz aplikację, która akceptuje naciśnięcia klawiszy przez użytkownika, można również monitorować klawisze modyfikujące, takie jak klawiszy SHIFT, ALT i CTRL.</span><span class="sxs-lookup"><span data-stu-id="f43eb-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="f43eb-104">Po naciśnięciu klawisza modyfikującego w połączeniu z innych kluczy lub za pomocą kliknięć myszą, aplikacja może reagować odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f43eb-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="f43eb-105">Na przykład jeśli jest wciśnięty literę S, po prostu może to spowodować "s" była wyświetlana na ekranie, ale jeśli naciskania klawiszy CTRL + S, mogą zostać zapisane bieżącego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f43eb-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="f43eb-106">Jeśli możesz obsługiwać <xref:System.Windows.Forms.Control.KeyDown> zdarzenia <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> odebrane przez zdarzenie kod obsługi wyjątku określa są naciśnięte klawisze modyfikujące, które.</span><span class="sxs-lookup"><span data-stu-id="f43eb-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="f43eb-107">Alternatywnie <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> określa znak, który został naciśnięty również wszelkie klawisze modyfikujące w połączeniu z bitowe OR.</span><span class="sxs-lookup"><span data-stu-id="f43eb-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="f43eb-108">Jednak jeśli obsługujesz <xref:System.Windows.Forms.Control.KeyPress> zdarzenia lub zdarzenia myszy, program obsługi zdarzeń nie otrzymuje tych informacji.</span><span class="sxs-lookup"><span data-stu-id="f43eb-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="f43eb-109">W takim przypadku należy użyć <xref:System.Windows.Forms.Control.ModifierKeys%2A> właściwość <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="f43eb-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="f43eb-110">W obu przypadkach należy wykonać bitowe AND odpowiednie <xref:System.Windows.Forms.Keys> wartości i wartości, które testujesz.</span><span class="sxs-lookup"><span data-stu-id="f43eb-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="f43eb-111"><xref:System.Windows.Forms.Keys> Wyliczenie oferuje odmiany każdego klawisz modyfikujący, więc jest ważne, aby przeprowadzić operatora testu koniunkcji i przy użyciu poprawnej wartości.</span><span class="sxs-lookup"><span data-stu-id="f43eb-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="f43eb-112">Na przykład klawisz SHIFT jest reprezentowany przez <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> i <xref:System.Windows.Forms.Keys.LShiftKey> poprawnej wartości, aby przetestować SHIFT, ponieważ klawisz modyfikujący <xref:System.Windows.Forms.Keys.Shift>.</span><span class="sxs-lookup"><span data-stu-id="f43eb-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="f43eb-113">Podobnie, aby klawisz CTRL i ALT jako modyfikatory można przetestować używać <xref:System.Windows.Forms.Keys.Control> i <xref:System.Windows.Forms.Keys.Alt> wartości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f43eb-113">Similarly, to test for CTRL and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f43eb-114">W programowaniu w języku Visual Basic mogą też uzyskiwać dostęp informacje o kluczu za pośrednictwem <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> właściwości</span><span class="sxs-lookup"><span data-stu-id="f43eb-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="f43eb-115">Aby ustalić, który klawisz modyfikujący został naciśnięty</span><span class="sxs-lookup"><span data-stu-id="f43eb-115">To determine which modifier key was pressed</span></span>  
  
-   <span data-ttu-id="f43eb-116">Użyj operatora testu koniunkcji `AND` operator <xref:System.Windows.Forms.Control.ModifierKeys%2A> właściwości i wartości <xref:System.Windows.Forms.Keys> wyliczeniu, aby ustalić, czy jest wciśnięty klawisz modyfikujący określonej.</span><span class="sxs-lookup"><span data-stu-id="f43eb-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="f43eb-117">Poniższy przykład kodu pokazuje, jak ustalić, czy w ramach zostanie naciśnięty klawisz SHIFT <xref:System.Windows.Forms.Control.KeyPress> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f43eb-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f43eb-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f43eb-118">See also</span></span>
- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [<span data-ttu-id="f43eb-119">Wprowadzanie z klawiatury w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f43eb-119">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- <span data-ttu-id="f43eb-120">[Instrukcje: Określić, że jeśli Caps Lock jest włączony w języku Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f43eb-120">[How to: Determine If CapsLock is On in Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span></span>
