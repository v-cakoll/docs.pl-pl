---
title: Reagowanie na kliknięcia kontrolki Button
description: Dowiedz się, jak reagować na kliknięcia przycisku Windows Forms. Najbardziej podstawowym zastosowaniem kontrolki przycisku Windows Forms jest uruchomienie pewnego kodu po kliknięciu przycisku.
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
ms.openlocfilehash: 5c458d56dbd6f1cab8e88bdbb86ede958367e5c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619731"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="02476-104">Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="02476-104">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="02476-105">Najbardziej podstawowym <xref:System.Windows.Forms.Button> sposobem użycia formantu Windows Forms jest uruchomienie pewnego kodu po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="02476-105">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="02476-106">Kliknięcie <xref:System.Windows.Forms.Button> kontrolki powoduje także wygenerowanie wielu innych zdarzeń, takich jak <xref:System.Windows.Forms.Control.MouseEnter> zdarzenia, <xref:System.Windows.Forms.Control.MouseDown> i <xref:System.Windows.Forms.Control.MouseUp> .</span><span class="sxs-lookup"><span data-stu-id="02476-106">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="02476-107">Jeśli zamierzasz dołączyć procedury obsługi zdarzeń dla tych powiązanych zdarzeń, upewnij się, że ich akcje nie powodują konfliktu.</span><span class="sxs-lookup"><span data-stu-id="02476-107">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="02476-108">Jeśli na przykład klikniesz przycisk czyści informacje wpisane przez użytkownika w polu tekstowym, zatrzymując wskaźnik myszy nad przyciskiem nie powinien wyświetlać etykietki narzędzia z tym, że te informacje są teraz nieistniejące.</span><span class="sxs-lookup"><span data-stu-id="02476-108">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="02476-109">Jeśli użytkownik spróbuje dwukrotnie kliknąć <xref:System.Windows.Forms.Button> kontrolkę, każde kliknięcie zostanie przetworzone oddzielnie. oznacza to, że formant nie obsługuje zdarzenia podwójnego kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="02476-109">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="02476-110">Aby odpowiedzieć na przycisk kliknij</span><span class="sxs-lookup"><span data-stu-id="02476-110">To respond to a button click</span></span>  
  
- <span data-ttu-id="02476-111">Na przycisku `Click` <xref:System.EventHandler> Napisz kod do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="02476-111">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="02476-112">`Button1_Click`musi być powiązany z kontrolką.</span><span class="sxs-lookup"><span data-stu-id="02476-112">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="02476-113">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń w czasie wykonywania dla Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="02476-113">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="02476-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02476-114">See also</span></span>

- [<span data-ttu-id="02476-115">Button — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="02476-115">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="02476-116">Sposoby wyboru kontrolki przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02476-116">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="02476-117">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="02476-117">Button Control</span></span>](button-control-windows-forms.md)
