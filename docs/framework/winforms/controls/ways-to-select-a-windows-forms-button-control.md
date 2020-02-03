---
title: Sposoby zaznaczania kontrolki przycisku
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740007"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="01a41-102">Sposoby wyboru kontrolki przycisku formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="01a41-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="01a41-103">Przycisk Windows Forms można wybrać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="01a41-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
- <span data-ttu-id="01a41-104">Za pomocą myszy kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="01a41-104">Use a mouse to click the button.</span></span>  
  
- <span data-ttu-id="01a41-105">Wywołaj zdarzenie <xref:System.Windows.Forms.Control.Click> przycisku w kodzie.</span><span class="sxs-lookup"><span data-stu-id="01a41-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
- <span data-ttu-id="01a41-106">Przenieś fokus na przycisk, naciskając klawisz TAB, a następnie wybierz przycisk, naciskając klawisz spacji lub ENTER.</span><span class="sxs-lookup"><span data-stu-id="01a41-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
- <span data-ttu-id="01a41-107">Naciśnij klawisz dostępu (ALT + podkreślona litera) dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="01a41-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="01a41-108">Aby uzyskać więcej informacji o kluczach dostępu, zobacz [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="01a41-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
- <span data-ttu-id="01a41-109">Jeśli przycisk jest przyciskiem "Akceptuj" formularza, naciśnięcie klawisza ENTER wybiera przycisk, nawet jeśli inny formant ma fokus — chyba że inny formant jest innym przyciskiem, wielowierszowym polem tekstowym lub kontrolką niestandardową, która Zalewka klawisza ENTER.</span><span class="sxs-lookup"><span data-stu-id="01a41-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
- <span data-ttu-id="01a41-110">Jeśli przycisk jest przycisk "Anuluj" w formularzu, naciśnięcie klawisza ESC wybiera przycisk, nawet jeśli inny formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="01a41-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
- <span data-ttu-id="01a41-111">Wywołaj metodę <xref:System.Windows.Forms.Button.PerformClick%2A>, aby wybrać przycisk programowo.</span><span class="sxs-lookup"><span data-stu-id="01a41-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a41-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01a41-112">See also</span></span>

- [<span data-ttu-id="01a41-113">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="01a41-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="01a41-114">Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01a41-114">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="01a41-115">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="01a41-115">Button Control</span></span>](button-control-windows-forms.md)
