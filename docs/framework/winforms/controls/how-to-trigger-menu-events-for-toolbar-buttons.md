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
ms.openlocfilehash: 5256185104f7d22514eac2db93856d7c58f51fb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228357"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a><span data-ttu-id="c03f8-102">Instrukcje: zdarzenia wyzwalaczy menu dla przycisków paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="c03f8-102">How to: Trigger Menu Events for Toolbar Buttons</span></span>
> [!NOTE]
>  <span data-ttu-id="c03f8-103"><xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="c03f8-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="c03f8-104">Jeśli formularz Windows funkcji <xref:System.Windows.Forms.ToolBar> kontrolki przycisków na pasku narzędzi, warto wiedzieć, który przycisk użytkownik klika polecenie.</span><span class="sxs-lookup"><span data-stu-id="c03f8-104">If your Windows Form features a <xref:System.Windows.Forms.ToolBar> control with toolbar buttons, you will want to know which button the user clicks.</span></span>  
  
 <span data-ttu-id="c03f8-105">Na <xref:System.Windows.Forms.ToolBar.ButtonClick> zdarzenia <xref:System.Windows.Forms.ToolBar> kontrolki, możesz ocenić <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> właściwość <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> klasy.</span><span class="sxs-lookup"><span data-stu-id="c03f8-105">On the <xref:System.Windows.Forms.ToolBar.ButtonClick> event of the <xref:System.Windows.Forms.ToolBar> control, you can evaluate the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> property of the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class.</span></span> <span data-ttu-id="c03f8-106">W poniższym przykładzie zostanie wyświetlone okno komunikatu, wskazujące, której przycisk został kliknięty.</span><span class="sxs-lookup"><span data-stu-id="c03f8-106">In the example below, a message box is shown, indicating which button was clicked.</span></span> <span data-ttu-id="c03f8-107">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="c03f8-107">For details, see <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="c03f8-108">W poniższym przykładzie przyjęto założenie, <xref:System.Windows.Forms.ToolBar> formant został dodany do formularza Windows.</span><span class="sxs-lookup"><span data-stu-id="c03f8-108">The example below assumes a <xref:System.Windows.Forms.ToolBar> control has been added to a Windows Form.</span></span>  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a><span data-ttu-id="c03f8-109">Aby obsłużyć zdarzenie kliknij na pasku narzędzi</span><span class="sxs-lookup"><span data-stu-id="c03f8-109">To handle the Click event on a toolbar</span></span>  
  
1.  <span data-ttu-id="c03f8-110">W procedurze, Dodaj przyciski paska narzędzi na <xref:System.Windows.Forms.ToolBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="c03f8-110">In a procedure, add toolbar buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
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
  
2.  <span data-ttu-id="c03f8-111">Dodawanie obsługi zdarzeń dla <xref:System.Windows.Forms.ToolBar> kontrolki <xref:System.Windows.Forms.ToolBar.ButtonClick> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c03f8-111">Add an event handler for the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ButtonClick> event.</span></span> <span data-ttu-id="c03f8-112">Należy używać liter, przełączanie instrukcji i <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> klasę, aby określić przycisku paska narzędzi, który został kliknięty.</span><span class="sxs-lookup"><span data-stu-id="c03f8-112">Use a case switching statement and the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class to determine the toolbar button that was clicked.</span></span> <span data-ttu-id="c03f8-113">Na tej podstawie Pokaż pole odpowiedni komunikat.</span><span class="sxs-lookup"><span data-stu-id="c03f8-113">Based on this, show an appropriate message box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c03f8-114">Okno komunikatu jest używana wyłącznie jako symbol zastępczy w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c03f8-114">A message box is being used solely as a placeholder in this example.</span></span> <span data-ttu-id="c03f8-115">Możesz dodać innego kodu do wykonania po kliknięciu przycisku paska narzędzi.</span><span class="sxs-lookup"><span data-stu-id="c03f8-115">Feel free to add other code to execute when the toolbar buttons are clicked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c03f8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c03f8-116">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="c03f8-117">Instrukcje: dodawanie przycisków do kontrolki ToolBar</span><span class="sxs-lookup"><span data-stu-id="c03f8-117">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)
- [<span data-ttu-id="c03f8-118">Instrukcje: określanie ikony dla przycisku ToolBar</span><span class="sxs-lookup"><span data-stu-id="c03f8-118">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="c03f8-119">ToolBar — Formant</span><span class="sxs-lookup"><span data-stu-id="c03f8-119">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
