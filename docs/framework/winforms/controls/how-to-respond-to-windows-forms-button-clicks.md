---
title: 'Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows'
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
ms.openlocfilehash: e6e6d041422a79171ec4b6159f0789b8aa6a50d5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724989"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="a8e47-102">Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="a8e47-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="a8e47-103">Najbardziej podstawowa funkcja formularzy Windows <xref:System.Windows.Forms.Button> formant jest do uruchomienia kodu po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="a8e47-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="a8e47-104">Klikając <xref:System.Windows.Forms.Button> kontroli również generuje liczba innych zdarzeń, takich jak <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, i <xref:System.Windows.Forms.Control.MouseUp> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a8e47-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="a8e47-105">Jeśli zamierzasz dołączyć procedury obsługi zdarzeń dla tych zdarzeń powiązanych, pamiętaj, że ich działania nie wchodzą w konflikt.</span><span class="sxs-lookup"><span data-stu-id="a8e47-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="a8e47-106">Na przykład jeśli kliknięcie przycisku powoduje wyczyszczenie informacji wpisany w polu tekstowym, przytrzymanie wskaźnika myszy nad przyciskiem powinien Wyświetla etykietki narzędzia, dzięki tym informacjom nieistniejącej teraz.</span><span class="sxs-lookup"><span data-stu-id="a8e47-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="a8e47-107">Jeśli użytkownik próbuje kliknij dwukrotnie <xref:System.Windows.Forms.Button> kontrolki, każde kliknięcie będą przetwarzane oddzielnie; oznacza to, formant nie obsługuje zdarzeń kliknij dwukrotnie plik.</span><span class="sxs-lookup"><span data-stu-id="a8e47-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="a8e47-108">Aby odpowiedzieć na kliknięcie przycisku</span><span class="sxs-lookup"><span data-stu-id="a8e47-108">To respond to a button click</span></span>  
  
-   <span data-ttu-id="a8e47-109">W przycisku `Click` <xref:System.EventHandler> pisanie kodu do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="a8e47-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="a8e47-110">`Button1_Click` musi być powiązany do kontroli.</span><span class="sxs-lookup"><span data-stu-id="a8e47-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="a8e47-111">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie procedur obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a8e47-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8e47-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8e47-112">See also</span></span>
- [<span data-ttu-id="a8e47-113">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a8e47-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="a8e47-114">Sposoby wyboru kontrolki przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8e47-114">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="a8e47-115">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a8e47-115">Button Control</span></span>](button-control-windows-forms.md)
