---
title: 'Porady: zdarzenia wyzwalaczy menu dla przycisków paska narzędzi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], click event handlers
- ToolBar control [Windows Forms], coding button click events
- toolbars [Windows Forms], click event handlers
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
ms.openlocfilehash: 99db077b41a59fe9263f7283b58b8c31959c7c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182074"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a><span data-ttu-id="d7f4e-102">Porady: zdarzenia wyzwalaczy menu dla przycisków paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="d7f4e-102">How to: Trigger Menu Events for Toolbar Buttons</span></span>
> [!NOTE]
> <span data-ttu-id="d7f4e-103">Formant <xref:System.Windows.Forms.ToolStrip> zastępuje i dodaje funkcjonalność <xref:System.Windows.Forms.ToolBar> do formantu; jednak <xref:System.Windows.Forms.ToolBar> formant jest zachowywany zarówno dla zgodności z powrotem i przyszłego użycia, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="d7f4e-104">Jeśli formularz systemu <xref:System.Windows.Forms.ToolBar> Windows jest wyposażony w formant z przyciskami paska narzędzi, należy wiedzieć, który przycisk zostanie kliknięć przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-104">If your Windows Form features a <xref:System.Windows.Forms.ToolBar> control with toolbar buttons, you will want to know which button the user clicks.</span></span>  
  
 <span data-ttu-id="d7f4e-105">W <xref:System.Windows.Forms.ToolBar.ButtonClick> przypadku <xref:System.Windows.Forms.ToolBar> formantu można ocenić <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> właściwość <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> klasy.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-105">On the <xref:System.Windows.Forms.ToolBar.ButtonClick> event of the <xref:System.Windows.Forms.ToolBar> control, you can evaluate the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> property of the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class.</span></span> <span data-ttu-id="d7f4e-106">W poniższym przykładzie zostanie wyświetlone okno komunikatu wskazujące, który przycisk został kliknięty.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-106">In the example below, a message box is shown, indicating which button was clicked.</span></span> <span data-ttu-id="d7f4e-107">Aby uzyskać szczegółowe informacje, zobacz <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-107">For details, see <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="d7f4e-108">Poniższy przykład zakłada, <xref:System.Windows.Forms.ToolBar> że formant został dodany do formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-108">The example below assumes a <xref:System.Windows.Forms.ToolBar> control has been added to a Windows Form.</span></span>  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a><span data-ttu-id="d7f4e-109">Aby obsłużyć zdarzenie Click na pasku narzędzi</span><span class="sxs-lookup"><span data-stu-id="d7f4e-109">To handle the Click event on a toolbar</span></span>  
  
1. <span data-ttu-id="d7f4e-110">W procedurze dodaj przyciski <xref:System.Windows.Forms.ToolBar> paska narzędzi do formantu.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-110">In a procedure, add toolbar buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
    ```vb  
    Public Sub ToolBarConfig()  
    ' Instantiate the toolbar buttons, set their Text properties  
    ' and add them to the ToolBar control.  
       ToolBar1.Buttons.Add(New ToolBarButton("One"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Two"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Three"))  
    ' Add the event handler delegate.  
       AddHandler ToolBar1.ButtonClick, AddressOf Me.ToolBar1_ButtonClick  
    End Sub  
    ```  
  
    ```csharp  
    public void ToolBarConfig()
    {  
       toolBar1.Buttons.Add(new ToolBarButton("One"));  
       toolBar1.Buttons.Add(new ToolBarButton("Two"));  
       toolBar1.Buttons.Add(new ToolBarButton("Three"));  
  
       toolBar1.ButtonClick +=
          new ToolBarButtonClickEventHandler(this.toolBar1_ButtonClick);  
    }  
    ```  
  
    ```cpp  
    public:  
       void ToolBarConfig()  
       {  
          toolBar1->Buttons->Add(gcnew ToolBarButton("One"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Two"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Three"));  
  
          toolBar1->ButtonClick +=
             gcnew ToolBarButtonClickEventHandler(this,  
             &Form1::toolBar1_ButtonClick);  
       }  
    ```  
  
2. <span data-ttu-id="d7f4e-111">Dodaj program obsługi <xref:System.Windows.Forms.ToolBar> zdarzeń dla <xref:System.Windows.Forms.ToolBar.ButtonClick> zdarzenia formantu.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-111">Add an event handler for the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ButtonClick> event.</span></span> <span data-ttu-id="d7f4e-112">Użyj instrukcji przełączania spraw <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> i klasy, aby określić przycisk paska narzędzi, który został kliknięty.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-112">Use a case switching statement and the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class to determine the toolbar button that was clicked.</span></span> <span data-ttu-id="d7f4e-113">Na tej podstawie pokaż odpowiednie okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-113">Based on this, show an appropriate message box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d7f4e-114">Okno komunikatu jest używane wyłącznie jako symbol zastępczy w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-114">A message box is being used solely as a placeholder in this example.</span></span> <span data-ttu-id="d7f4e-115">Możesz dodać inny kod do wykonania po kliknięciu przycisków paska narzędzi.</span><span class="sxs-lookup"><span data-stu-id="d7f4e-115">Feel free to add other code to execute when the toolbar buttons are clicked.</span></span>  
  
    ```vb  
    Protected Sub ToolBar1_ButtonClick(ByVal sender As Object, _  
    ByVal e As ToolBarButtonClickEventArgs)  
    ' Evaluate the Button property of the ToolBarButtonClickEventArgs  
    ' to determine which button was clicked.  
       Select Case ToolBar1.Buttons.IndexOf(e.Button)  
         Case 0  
           MessageBox.Show("First toolbar button clicked")  
         Case 1  
           MessageBox.Show("Second toolbar button clicked")  
         Case 2  
           MessageBox.Show("Third toolbar button clicked")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    protected void toolBar1_ButtonClick(object sender,  
    ToolBarButtonClickEventArgs e)  
    {  
       // Evaluate the Button property of the ToolBarButtonClickEventArgs  
       // to determine which button was clicked.  
       switch (toolBar1.Buttons.IndexOf(e.Button))  
       {  
          case 0 :  
             MessageBox.Show("First toolbar button clicked");  
             break;  
          case 1 :  
             MessageBox.Show("Second toolbar button clicked");  
             break;  
          case 2 :  
             MessageBox.Show("Third toolbar button clicked");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    protected:  
       void toolBar1_ButtonClick(System::Object ^ sender,  
          ToolBarButtonClickEventArgs ^ e)  
       {  
         // Evaluate the Button property of the ToolBarButtonClickEventArgs  
         // to determine which button was clicked.  
          switch (toolBar1->Buttons->IndexOf(e->Button))  
          {  
             case 0 :  
                MessageBox::Show("First toolbar button clicked");  
                break;  
             case 1 :  
                MessageBox::Show("Second toolbar button clicked");  
                break;  
             case 2 :  
                MessageBox::Show("Third toolbar button clicked");  
                break;  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d7f4e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7f4e-116">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="d7f4e-117">Instrukcje: dodawanie przycisków do kontrolki ToolBar</span><span class="sxs-lookup"><span data-stu-id="d7f4e-117">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)
- [<span data-ttu-id="d7f4e-118">Instrukcje: określanie ikony dla przycisku kontrolki ToolBar</span><span class="sxs-lookup"><span data-stu-id="d7f4e-118">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="d7f4e-119">ToolBar — Formant</span><span class="sxs-lookup"><span data-stu-id="d7f4e-119">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
