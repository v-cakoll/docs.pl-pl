---
title: Sposoby wyboru kontrolki przycisku formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: f2881646a05d257044c6461f822a4c35a225f8c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759846"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="3e8e2-102">Sposoby wyboru kontrolki przycisku formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3e8e2-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="3e8e2-103">Można wybrać przycisk Windows Forms w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3e8e2-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
- <span data-ttu-id="3e8e2-104">Kliknij przycisk za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="3e8e2-104">Use a mouse to click the button.</span></span>  
  
- <span data-ttu-id="3e8e2-105">Wywoływanie przycisku <xref:System.Windows.Forms.Control.Click> zdarzenia w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3e8e2-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
- <span data-ttu-id="3e8e2-106">Przenieś fokus do przycisku, naciskając klawisz TAB, a następnie wybierz przycisk, naciskając klawisz spacji lub ENTER.</span><span class="sxs-lookup"><span data-stu-id="3e8e2-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
- <span data-ttu-id="3e8e2-107">Naciśnij klawisz dostępu (ALT + podkreślona litera) dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="3e8e2-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="3e8e2-108">Aby uzyskać więcej informacji na temat kluczy dostępu, zobacz [jak: Tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3e8e2-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
- <span data-ttu-id="3e8e2-109">Jeśli przycisk znajduje się przycisk "Zaakceptuj" formularza, naciskając klawisz ENTER wybierze przycisk, nawet wtedy, gdy inna kontrolka ma fokus, chyba że inne kontrola jest inny przycisk, pole tekstu wielowierszowego lub formant niestandardowy, który traps klawisz enter.</span><span class="sxs-lookup"><span data-stu-id="3e8e2-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
- <span data-ttu-id="3e8e2-110">Jeśli przycisk znajduje się przycisk "Anuluj" formularza, naciskając klawisz ESC wybierze przycisk, nawet wtedy, gdy inna kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="3e8e2-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
- <span data-ttu-id="3e8e2-111">Wywołaj <xref:System.Windows.Forms.Button.PerformClick%2A> metodę, aby wybrać przycisk programowo.</span><span class="sxs-lookup"><span data-stu-id="3e8e2-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e8e2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e8e2-112">See also</span></span>

- [<span data-ttu-id="3e8e2-113">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="3e8e2-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="3e8e2-114">Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="3e8e2-114">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="3e8e2-115">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="3e8e2-115">Button Control</span></span>](button-control-windows-forms.md)
