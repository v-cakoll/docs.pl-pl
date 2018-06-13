---
title: 'Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows'
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
ms.openlocfilehash: 14a880c34f163dc6fece44c24d377822a741b0f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534254"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="7131e-102">Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7131e-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="7131e-103">Najbardziej podstawowa funkcja formularzy systemu Windows <xref:System.Windows.Forms.Button> formant jest do uruchomienia kodu po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="7131e-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="7131e-104">Kliknięcie przycisku <xref:System.Windows.Forms.Button> kontroli generowany jest również liczba innych zdarzeń, takich jak <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, i <xref:System.Windows.Forms.Control.MouseUp> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7131e-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="7131e-105">Jeśli zamierzasz dołączyć obsługi zdarzeń dla tych zdarzeń powiązanych, należy się upewnić, że ich działania nie pozostają w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="7131e-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="7131e-106">Na przykład jeśli kliknięcie przycisku czyści informacje, które użytkownik ma wpisane w polu tekstowym, wstrzymanie wskaźnik myszy nad przyciskiem powinien nie zawiera podpowiedzi z nieistniejącą teraz informacje.</span><span class="sxs-lookup"><span data-stu-id="7131e-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="7131e-107">Jeśli użytkownik próbuje kliknij dwukrotnie <xref:System.Windows.Forms.Button> formantu, kliknij każdy będą przetwarzane oddzielnie; oznacza to, formantu nie obsługuje kliknij dwukrotnie zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="7131e-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="7131e-108">Aby odpowiedzieć kliknij przycisk</span><span class="sxs-lookup"><span data-stu-id="7131e-108">To respond to a button click</span></span>  
  
-   <span data-ttu-id="7131e-109">Przycisk `Click` <xref:System.EventHandler> pisania kodu do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="7131e-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="7131e-110">`Button1_Click` muszą być powiązane z formantem.</span><span class="sxs-lookup"><span data-stu-id="7131e-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="7131e-111">Aby uzyskać więcej informacji, zobacz [porady: tworzenie obsługi zdarzeń w Uruchom czasu dla formularzy systemu Windows](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7131e-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7131e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7131e-112">See Also</span></span>  
 [<span data-ttu-id="7131e-113">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="7131e-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="7131e-114">Sposoby wyboru kontrolki przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7131e-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="7131e-115">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7131e-115">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
