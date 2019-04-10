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
ms.openlocfilehash: 1e24e410681b03a92c8c48b187dde569eccdc1c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222149"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="eb768-102">Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj</span><span class="sxs-lookup"><span data-stu-id="eb768-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="eb768-103">W każdym formularzu Windows, można wyznaczyć <xref:System.Windows.Forms.Button> formantu na przycisk Akceptuj, znany także jako przycisk domyślny.</span><span class="sxs-lookup"><span data-stu-id="eb768-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="eb768-104">Zawsze wtedy, gdy użytkownik naciśnie klawisz ENTER, jest kliknięty przycisk domyślny, niezależnie od tego, którego fokus ma inne kontrolki na formularzu.</span><span class="sxs-lookup"><span data-stu-id="eb768-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb768-105">Wyjątki, aby się to w przypadku kontrolki z fokusem inny przycisk — w takim przypadku zostanie kliknięty przycisk z fokusem — lub wielowierszowego pola tekstowego lub formant niestandardowy, który traps klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="eb768-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="eb768-106">Aby wyznaczyć na przycisk Akceptuj</span><span class="sxs-lookup"><span data-stu-id="eb768-106">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="eb768-107">Ustaw dla formularza <xref:System.Windows.Forms.Form.AcceptButton%2A> właściwości do odpowiednich <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="eb768-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb768-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb768-108">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="eb768-109">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="eb768-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="eb768-110">Sposoby wyboru kontrolki przycisku formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="eb768-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="eb768-111">Instrukcje: odpowiadanie na kliknięcia przycisków formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="eb768-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="eb768-112">Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="eb768-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="eb768-113">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="eb768-113">Button Control</span></span>](button-control-windows-forms.md)
