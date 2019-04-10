---
title: 'Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: ad95a527ea72858cc106c87d8712110e018e97b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231438"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="c48d8-102">Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="c48d8-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="c48d8-103">W każdym formularzu Windows, można wyznaczyć <xref:System.Windows.Forms.Button> formantu przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="c48d8-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="c48d8-104">Kliknięto przycisk Anuluj w każdym przypadku, gdy użytkownik naciśnie klawisz ESC, niezależnie od tego, którego fokus ma inne kontrolki na formularzu.</span><span class="sxs-lookup"><span data-stu-id="c48d8-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="c48d8-105">Taki przycisk jest zwykle zaprogramowane umożliwia użytkownikowi szybkie zakończyć operację bez zobowiązania do dowolnej akcji.</span><span class="sxs-lookup"><span data-stu-id="c48d8-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="c48d8-106">Aby wyznaczyć przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="c48d8-106">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="c48d8-107">Ustaw dla formularza <xref:System.Windows.Forms.Form.CancelButton%2A> właściwości do odpowiednich <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="c48d8-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c48d8-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c48d8-108">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="c48d8-109">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="c48d8-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="c48d8-110">Sposoby wyboru kontrolki przycisku formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c48d8-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="c48d8-111">Instrukcje: odpowiadanie na kliknięcia przycisków formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c48d8-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="c48d8-112">Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj</span><span class="sxs-lookup"><span data-stu-id="c48d8-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="c48d8-113">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c48d8-113">Button Control</span></span>](button-control-windows-forms.md)
