---
title: 'Instrukcje: Wyznaczanie przycisku Windows Forms na przycisk Akceptuj'
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
ms.openlocfilehash: 00d9f4acffb88b5047b40df91799cea1caaf2cf2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714700"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="ddcc5-102">Instrukcje: Wyznaczanie przycisku Windows Forms na przycisk Akceptuj</span><span class="sxs-lookup"><span data-stu-id="ddcc5-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="ddcc5-103">W każdym formularzu Windows, można wyznaczyć <xref:System.Windows.Forms.Button> formantu na przycisk Akceptuj, znany także jako przycisk domyślny.</span><span class="sxs-lookup"><span data-stu-id="ddcc5-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="ddcc5-104">Zawsze wtedy, gdy użytkownik naciśnie klawisz ENTER, jest kliknięty przycisk domyślny, niezależnie od tego, którego fokus ma inne kontrolki na formularzu.</span><span class="sxs-lookup"><span data-stu-id="ddcc5-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddcc5-105">Wyjątki, aby się to w przypadku kontrolki z fokusem inny przycisk — w takim przypadku zostanie kliknięty przycisk z fokusem — lub wielowierszowego pola tekstowego lub formant niestandardowy, który traps klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="ddcc5-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="ddcc5-106">Aby wyznaczyć na przycisk Akceptuj</span><span class="sxs-lookup"><span data-stu-id="ddcc5-106">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="ddcc5-107">Ustaw dla formularza <xref:System.Windows.Forms.Form.AcceptButton%2A> właściwości do odpowiednich <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ddcc5-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ddcc5-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddcc5-108">See also</span></span>
- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="ddcc5-109">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="ddcc5-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="ddcc5-110">Sposoby wyboru kontrolki przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ddcc5-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="ddcc5-111">Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="ddcc5-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="ddcc5-112">Instrukcje: Wyznaczanie przycisku Windows Forms na przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="ddcc5-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="ddcc5-113">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="ddcc5-113">Button Control</span></span>](button-control-windows-forms.md)
