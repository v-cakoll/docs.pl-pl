---
title: 'Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj'
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
ms.openlocfilehash: 5b21ee7da7a666a391be3bc5be57855eaa7ec8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967366"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="d0acd-102">Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj</span><span class="sxs-lookup"><span data-stu-id="d0acd-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="d0acd-103">Na dowolnym formularzu systemu Windows można wyznaczyć <xref:System.Windows.Forms.Button> kontrolkę jako przycisk Akceptuj, znaną również jako przycisk domyślny.</span><span class="sxs-lookup"><span data-stu-id="d0acd-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="d0acd-104">Za każdym razem, gdy użytkownik naciśnie klawisz ENTER, przycisk domyślny zostanie kliknięty niezależnie od tego, który inny formant w formularzu ma fokus.</span><span class="sxs-lookup"><span data-stu-id="d0acd-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0acd-105">Wyjątkami jest to, gdy kontrolka z fokusem jest innym przyciskiem. w takim przypadku zostanie kliknięty przycisk z fokusem — lub wielowierszowe pole tekstowe lub kontrolka niestandardowa, która Zalewka klawisza ENTER.</span><span class="sxs-lookup"><span data-stu-id="d0acd-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="d0acd-106">Aby wyznaczyć przycisk Akceptuj</span><span class="sxs-lookup"><span data-stu-id="d0acd-106">To designate the accept button</span></span>  
  
1. <span data-ttu-id="d0acd-107">Ustaw <xref:System.Windows.Forms.Form.AcceptButton%2A> właściwość formularza na odpowiednią <xref:System.Windows.Forms.Button> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="d0acd-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0acd-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0acd-108">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="d0acd-109">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="d0acd-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="d0acd-110">Sposoby wyboru kontrolki przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0acd-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="d0acd-111">Instrukcje: Odpowiadanie na kliknięcia przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0acd-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="d0acd-112">Instrukcje: Wyznacz przycisk Windows Forms jako przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="d0acd-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="d0acd-113">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d0acd-113">Button Control</span></span>](button-control-windows-forms.md)
