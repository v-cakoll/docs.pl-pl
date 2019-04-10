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
ms.openlocfilehash: 8170190145e76a86f5343bc42b39be7fb9d61a0f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344146"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="f4b58-102">Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="f4b58-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="f4b58-103">W każdym formularzu Windows, można wyznaczyć <xref:System.Windows.Forms.Button> formantu przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="f4b58-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="f4b58-104">Kliknięto przycisk Anuluj w każdym przypadku, gdy użytkownik naciśnie klawisz ESC, niezależnie od tego, którego fokus ma inne kontrolki na formularzu.</span><span class="sxs-lookup"><span data-stu-id="f4b58-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="f4b58-105">Taki przycisk jest zwykle zaprogramowane umożliwia użytkownikowi szybkie zakończyć operację bez zobowiązania do dowolnej akcji.</span><span class="sxs-lookup"><span data-stu-id="f4b58-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="f4b58-106">Aby wyznaczyć przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="f4b58-106">To designate the cancel button</span></span>  
  
1. <span data-ttu-id="f4b58-107">Ustaw dla formularza <xref:System.Windows.Forms.Form.CancelButton%2A> właściwości do odpowiednich <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f4b58-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4b58-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4b58-108">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="f4b58-109">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="f4b58-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="f4b58-110">Sposoby wyboru kontrolki przycisku formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f4b58-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="f4b58-111">Instrukcje: odpowiadanie na kliknięcia przycisków formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f4b58-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="f4b58-112">Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj</span><span class="sxs-lookup"><span data-stu-id="f4b58-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="f4b58-113">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="f4b58-113">Button Control</span></span>](button-control-windows-forms.md)
