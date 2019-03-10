---
title: Sposoby wyboru kontrolki przycisku formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 86ef0da37ec35b991557af97a97bc9ca3da2d68c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717261"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="f12ad-102">Sposoby wyboru kontrolki przycisku formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f12ad-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="f12ad-103">Można wybrać przycisk Windows Forms w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f12ad-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
-   <span data-ttu-id="f12ad-104">Kliknij przycisk za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="f12ad-104">Use a mouse to click the button.</span></span>  
  
-   <span data-ttu-id="f12ad-105">Wywoływanie przycisku <xref:System.Windows.Forms.Control.Click> zdarzenia w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f12ad-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
-   <span data-ttu-id="f12ad-106">Przenieś fokus do przycisku, naciskając klawisz TAB, a następnie wybierz przycisk, naciskając klawisz spacji lub ENTER.</span><span class="sxs-lookup"><span data-stu-id="f12ad-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
-   <span data-ttu-id="f12ad-107">Naciśnij klawisz dostępu (ALT + podkreślona litera) dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="f12ad-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="f12ad-108">Aby uzyskać więcej informacji na temat kluczy dostępu, zobacz [jak: Tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f12ad-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
-   <span data-ttu-id="f12ad-109">Jeśli przycisk znajduje się przycisk "Zaakceptuj" formularza, naciskając klawisz ENTER wybierze przycisk, nawet wtedy, gdy inna kontrolka ma fokus, chyba że inne kontrola jest inny przycisk, pole tekstu wielowierszowego lub formant niestandardowy, który traps klawisz enter.</span><span class="sxs-lookup"><span data-stu-id="f12ad-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
-   <span data-ttu-id="f12ad-110">Jeśli przycisk znajduje się przycisk "Anuluj" formularza, naciskając klawisz ESC wybierze przycisk, nawet wtedy, gdy inna kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="f12ad-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
-   <span data-ttu-id="f12ad-111">Wywołaj <xref:System.Windows.Forms.Button.PerformClick%2A> metodę, aby wybrać przycisk programowo.</span><span class="sxs-lookup"><span data-stu-id="f12ad-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12ad-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f12ad-112">See also</span></span>
- [<span data-ttu-id="f12ad-113">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="f12ad-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="f12ad-114">Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="f12ad-114">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="f12ad-115">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="f12ad-115">Button Control</span></span>](button-control-windows-forms.md)
