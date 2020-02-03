---
title: Reagowanie na kliknięcia kontrolki Button
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: dd6cf75a316257c86a23b44a818422336c12aa67
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735719"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="1379b-102">Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1379b-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="1379b-103">Najbardziej podstawowym zastosowaniem formantu Windows Forms <xref:System.Windows.Forms.Button> jest uruchomienie pewnego kodu po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="1379b-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="1379b-104">Kliknięcie kontrolki <xref:System.Windows.Forms.Button> powoduje także wygenerowanie wielu innych zdarzeń, takich jak zdarzenia <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>i <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="1379b-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="1379b-105">Jeśli zamierzasz dołączyć procedury obsługi zdarzeń dla tych powiązanych zdarzeń, upewnij się, że ich akcje nie powodują konfliktu.</span><span class="sxs-lookup"><span data-stu-id="1379b-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="1379b-106">Jeśli na przykład klikniesz przycisk czyści informacje wpisane przez użytkownika w polu tekstowym, zatrzymując wskaźnik myszy nad przyciskiem nie powinien wyświetlać etykietki narzędzia z tym, że te informacje są teraz nieistniejące.</span><span class="sxs-lookup"><span data-stu-id="1379b-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="1379b-107">Jeśli użytkownik spróbuje dwukrotnie kliknąć kontrolkę <xref:System.Windows.Forms.Button>, każde kliknięcie zostanie przetworzone osobno; oznacza to, że formant nie obsługuje zdarzenia podwójnego kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="1379b-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="1379b-108">Aby odpowiedzieć na przycisk kliknij</span><span class="sxs-lookup"><span data-stu-id="1379b-108">To respond to a button click</span></span>  
  
- <span data-ttu-id="1379b-109">Na `Click` przycisku <xref:System.EventHandler> Napisz kod do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="1379b-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="1379b-110">`Button1_Click` musi być powiązany z kontrolką.</span><span class="sxs-lookup"><span data-stu-id="1379b-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="1379b-111">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń w czasie wykonywania dla Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1379b-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1379b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1379b-112">See also</span></span>

- [<span data-ttu-id="1379b-113">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="1379b-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="1379b-114">Sposoby wyboru kontrolki przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1379b-114">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="1379b-115">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="1379b-115">Button Control</span></span>](button-control-windows-forms.md)
