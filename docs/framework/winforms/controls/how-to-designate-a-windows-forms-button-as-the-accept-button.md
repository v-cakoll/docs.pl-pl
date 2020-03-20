---
title: Wyznacz przycisk jako przycisk Zaakceptuj
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: ca5f691fb26db5c4adcb48405c9600b54827104c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142150"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="4b86d-102">Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj</span><span class="sxs-lookup"><span data-stu-id="4b86d-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="4b86d-103">W dowolnym formularzu systemu Windows <xref:System.Windows.Forms.Button> można wyznaczyć formant jako przycisk accept, znany również jako przycisk domyślny.</span><span class="sxs-lookup"><span data-stu-id="4b86d-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="4b86d-104">Za każdym razem, gdy użytkownik naciśnie klawisz ENTER, przycisk domyślny jest klikany niezależnie od tego, który inny formant w formularzu ma fokus.</span><span class="sxs-lookup"><span data-stu-id="4b86d-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b86d-105">Wyjątkami są to, gdy formant z fokusem jest inny przycisk — w tym przypadku przycisk z fokusem zostanie kliknięty — lub wielowierszowe pole tekstowe lub niestandardowy formant, który zalewkuje klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="4b86d-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="4b86d-106">Aby wyznaczyć przycisk akceptuję</span><span class="sxs-lookup"><span data-stu-id="4b86d-106">To designate the accept button</span></span>  
  
1. <span data-ttu-id="4b86d-107">Ustaw <xref:System.Windows.Forms.Form.AcceptButton%2A> właściwość formularza na <xref:System.Windows.Forms.Button> odpowiednią formant.</span><span class="sxs-lookup"><span data-stu-id="4b86d-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4b86d-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b86d-108">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="4b86d-109">Button — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="4b86d-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="4b86d-110">Sposoby wyboru kontrolki przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b86d-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="4b86d-111">Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b86d-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="4b86d-112">Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="4b86d-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="4b86d-113">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="4b86d-113">Button Control</span></span>](button-control-windows-forms.md)
