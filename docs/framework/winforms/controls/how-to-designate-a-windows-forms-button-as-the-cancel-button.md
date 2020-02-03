---
title: Wyznacz przycisk jako przycisk Anuluj
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 123b3e275065efadd24815320ea7d855808e60b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743262"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="1801e-102">Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="1801e-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="1801e-103">Na dowolnym formularzu systemu Windows można wyznaczyć kontrolkę <xref:System.Windows.Forms.Button>, która będzie przyciskiem Anuluj.</span><span class="sxs-lookup"><span data-stu-id="1801e-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="1801e-104">Przycisk Anuluj jest klikany za każdym razem, gdy użytkownik naciśnie klawisz ESC, niezależnie od tego, który inny formant w formularzu ma fokus.</span><span class="sxs-lookup"><span data-stu-id="1801e-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="1801e-105">Taki przycisk jest zazwyczaj zaprogramowany, aby umożliwić użytkownikowi szybkie zakończenie operacji bez zatwierdzania żadnej akcji.</span><span class="sxs-lookup"><span data-stu-id="1801e-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="1801e-106">Aby wyznaczyć przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="1801e-106">To designate the cancel button</span></span>  
  
1. <span data-ttu-id="1801e-107">Ustaw właściwość <xref:System.Windows.Forms.Form.CancelButton%2A> formularza na odpowiednią kontrolkę <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="1801e-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1801e-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1801e-108">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="1801e-109">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="1801e-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="1801e-110">Sposoby wyboru kontrolki przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1801e-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="1801e-111">Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1801e-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="1801e-112">Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Akceptuj</span><span class="sxs-lookup"><span data-stu-id="1801e-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="1801e-113">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="1801e-113">Button Control</span></span>](button-control-windows-forms.md)
