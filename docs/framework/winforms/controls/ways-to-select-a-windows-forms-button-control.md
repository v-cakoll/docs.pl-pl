---
title: Sposoby wyboru kontrolki przycisku formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08b5359446a80da257f5afec07cc70e3d4aad46b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="1836a-102">Sposoby wyboru kontrolki przycisku formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1836a-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="1836a-103">Przycisku formularzy systemu Windows można wybrać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1836a-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
-   <span data-ttu-id="1836a-104">Kliknij przycisk za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="1836a-104">Use a mouse to click the button.</span></span>  
  
-   <span data-ttu-id="1836a-105">Wywołanie przycisku <xref:System.Windows.Forms.Control.Click> zdarzeń w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1836a-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
-   <span data-ttu-id="1836a-106">Przenieś fokus przycisku, naciskając klawisz TAB, a następnie wybierz przycisk, naciskając klawisz spacji lub ENTER.</span><span class="sxs-lookup"><span data-stu-id="1836a-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
-   <span data-ttu-id="1836a-107">Naciśnij klawisz dostępu (ALT + podkreślona litera) dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="1836a-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="1836a-108">Aby uzyskać więcej informacji na temat kluczy dostępu, zobacz [porady: tworzenie dostępu do kluczy dla formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1836a-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
-   <span data-ttu-id="1836a-109">Jeśli przycisk jest przycisk "Zaakceptuj" formularza, naciskając klawisz ENTER wybierze przycisk, nawet jeśli inny formant ma fokus, chyba że inne kontrola jest inny przycisk, wielowierszowego pola tekstowego lub kontrolki niestandardowej, która traps klawisz enter.</span><span class="sxs-lookup"><span data-stu-id="1836a-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
-   <span data-ttu-id="1836a-110">Jeśli przycisk jest przycisk "Anuluj" formularza, naciskając klawisz ESC wybierze przycisk, nawet jeśli inny formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="1836a-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
-   <span data-ttu-id="1836a-111">Wywołanie <xref:System.Windows.Forms.Button.PerformClick%2A> metodę, aby wybrać przycisk programowo.</span><span class="sxs-lookup"><span data-stu-id="1836a-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1836a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1836a-112">See Also</span></span>  
 [<span data-ttu-id="1836a-113">Informacje o kontrolce przycisku</span><span class="sxs-lookup"><span data-stu-id="1836a-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="1836a-114">Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1836a-114">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="1836a-115">Button — formant</span><span class="sxs-lookup"><span data-stu-id="1836a-115">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
