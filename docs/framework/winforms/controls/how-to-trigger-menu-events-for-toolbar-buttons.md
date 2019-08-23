---
title: 'Instrukcje: zdarzenia wyzwalaczy menu dla przycisków paska narzędzi'
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
ms.openlocfilehash: 381b8ba08db6ff5bb817c9c89008dacb1085ac1b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956033"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a><span data-ttu-id="71698-102">Instrukcje: zdarzenia wyzwalaczy menu dla przycisków paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="71698-102">How to: Trigger Menu Events for Toolbar Buttons</span></span>
> [!NOTE]
> <span data-ttu-id="71698-103">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.ToolBar> do <xref:System.Windows.Forms.ToolBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="71698-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="71698-104">Jeśli formularz systemu Windows zawiera <xref:System.Windows.Forms.ToolBar> kontrolkę z przyciskami paska narzędzi, warto wiedzieć, który przycisk użytkownik klika.</span><span class="sxs-lookup"><span data-stu-id="71698-104">If your Windows Form features a <xref:System.Windows.Forms.ToolBar> control with toolbar buttons, you will want to know which button the user clicks.</span></span>  
  
 <span data-ttu-id="71698-105">Na zdarzeniu <xref:System.Windows.Forms.ToolBar> formantu można <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> oszacowaćwłaściwośćklasy.<xref:System.Windows.Forms.ToolBarButtonClickEventArgs> <xref:System.Windows.Forms.ToolBar.ButtonClick></span><span class="sxs-lookup"><span data-stu-id="71698-105">On the <xref:System.Windows.Forms.ToolBar.ButtonClick> event of the <xref:System.Windows.Forms.ToolBar> control, you can evaluate the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> property of the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class.</span></span> <span data-ttu-id="71698-106">W poniższym przykładzie zostanie wyświetlone okno komunikatu z informacją o tym, który przycisk został kliknięty.</span><span class="sxs-lookup"><span data-stu-id="71698-106">In the example below, a message box is shown, indicating which button was clicked.</span></span> <span data-ttu-id="71698-107">Aby uzyskać szczegółowe informacje <xref:System.Windows.Forms.MessageBox>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="71698-107">For details, see <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="71698-108">W poniższym przykładzie przyjęto <xref:System.Windows.Forms.ToolBar> założenie, że kontrolka została dodana do formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="71698-108">The example below assumes a <xref:System.Windows.Forms.ToolBar> control has been added to a Windows Form.</span></span>  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a><span data-ttu-id="71698-109">Aby obsłużyć zdarzenie kliknięcia na pasku narzędzi</span><span class="sxs-lookup"><span data-stu-id="71698-109">To handle the Click event on a toolbar</span></span>  
  
1. <span data-ttu-id="71698-110">W procedurze Dodaj przyciski paska narzędzi do <xref:System.Windows.Forms.ToolBar> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="71698-110">In a procedure, add toolbar buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
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
  
2. <span data-ttu-id="71698-111">Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar.ButtonClick> zdarzenia kontrolki.</span><span class="sxs-lookup"><span data-stu-id="71698-111">Add an event handler for the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ButtonClick> event.</span></span> <span data-ttu-id="71698-112">Użyj instrukcji przełączania przypadku i <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> klasy, aby określić kliknięty przycisk paska narzędzi.</span><span class="sxs-lookup"><span data-stu-id="71698-112">Use a case switching statement and the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class to determine the toolbar button that was clicked.</span></span> <span data-ttu-id="71698-113">W zależności od tego należy wyświetlić odpowiednie okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="71698-113">Based on this, show an appropriate message box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="71698-114">Okno komunikatu jest używane wyłącznie jako symbol zastępczy w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="71698-114">A message box is being used solely as a placeholder in this example.</span></span> <span data-ttu-id="71698-115">Możesz dodać inny kod do wykonania po kliknięciu przycisków paska narzędzi.</span><span class="sxs-lookup"><span data-stu-id="71698-115">Feel free to add other code to execute when the toolbar buttons are clicked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="71698-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71698-116">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="71698-117">Instrukcje: Dodawanie przycisków do kontrolki paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="71698-117">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)
- [<span data-ttu-id="71698-118">Instrukcje: Zdefiniuj ikonę dla przycisku paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="71698-118">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="71698-119">ToolBar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="71698-119">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
