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
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a>Instrukcje: zdarzenia wyzwalaczy menu dla przycisków paska narzędzi
> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.ToolBar> do <xref:System.Windows.Forms.ToolBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStrip>  
  
 Jeśli formularz systemu Windows zawiera <xref:System.Windows.Forms.ToolBar> kontrolkę z przyciskami paska narzędzi, warto wiedzieć, który przycisk użytkownik klika.  
  
 Na zdarzeniu <xref:System.Windows.Forms.ToolBar> formantu można <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> oszacowaćwłaściwośćklasy.<xref:System.Windows.Forms.ToolBarButtonClickEventArgs> <xref:System.Windows.Forms.ToolBar.ButtonClick> W poniższym przykładzie zostanie wyświetlone okno komunikatu z informacją o tym, który przycisk został kliknięty. Aby uzyskać szczegółowe informacje <xref:System.Windows.Forms.MessageBox>, zobacz.  
  
 W poniższym przykładzie przyjęto <xref:System.Windows.Forms.ToolBar> założenie, że kontrolka została dodana do formularza systemu Windows.  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a>Aby obsłużyć zdarzenie kliknięcia na pasku narzędzi  
  
1. W procedurze Dodaj przyciski paska narzędzi do <xref:System.Windows.Forms.ToolBar> kontrolki.  
  
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
  
2. Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar.ButtonClick> zdarzenia kontrolki. Użyj instrukcji przełączania przypadku i <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> klasy, aby określić kliknięty przycisk paska narzędzi. W zależności od tego należy wyświetlić odpowiednie okno komunikatu.  
  
    > [!NOTE]
    > Okno komunikatu jest używane wyłącznie jako symbol zastępczy w tym przykładzie. Możesz dodać inny kod do wykonania po kliknięciu przycisków paska narzędzi.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolBar>
- [Instrukcje: Dodawanie przycisków do kontrolki paska narzędzi](how-to-add-buttons-to-a-toolbar-control.md)
- [Instrukcje: Zdefiniuj ikonę dla przycisku paska narzędzi](how-to-define-an-icon-for-a-toolbar-button.md)
- [ToolBar, kontrolka](toolbar-control-windows-forms.md)
