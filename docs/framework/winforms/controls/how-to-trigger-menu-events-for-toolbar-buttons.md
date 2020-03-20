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
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a>Porady: zdarzenia wyzwalaczy menu dla przycisków paska narzędzi
> [!NOTE]
> Formant <xref:System.Windows.Forms.ToolStrip> zastępuje i dodaje funkcjonalność <xref:System.Windows.Forms.ToolBar> do formantu; jednak <xref:System.Windows.Forms.ToolBar> formant jest zachowywany zarówno dla zgodności z powrotem i przyszłego użycia, jeśli wybierzesz.  
  
 Jeśli formularz systemu <xref:System.Windows.Forms.ToolBar> Windows jest wyposażony w formant z przyciskami paska narzędzi, należy wiedzieć, który przycisk zostanie kliknięć przez użytkownika.  
  
 W <xref:System.Windows.Forms.ToolBar.ButtonClick> przypadku <xref:System.Windows.Forms.ToolBar> formantu można ocenić <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> właściwość <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> klasy. W poniższym przykładzie zostanie wyświetlone okno komunikatu wskazujące, który przycisk został kliknięty. Aby uzyskać szczegółowe informacje, zobacz <xref:System.Windows.Forms.MessageBox>.  
  
 Poniższy przykład zakłada, <xref:System.Windows.Forms.ToolBar> że formant został dodany do formularza systemu Windows.  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a>Aby obsłużyć zdarzenie Click na pasku narzędzi  
  
1. W procedurze dodaj przyciski <xref:System.Windows.Forms.ToolBar> paska narzędzi do formantu.  
  
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
  
2. Dodaj program obsługi <xref:System.Windows.Forms.ToolBar> zdarzeń dla <xref:System.Windows.Forms.ToolBar.ButtonClick> zdarzenia formantu. Użyj instrukcji przełączania spraw <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> i klasy, aby określić przycisk paska narzędzi, który został kliknięty. Na tej podstawie pokaż odpowiednie okno komunikatu.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ToolBar>
- [Instrukcje: dodawanie przycisków do kontrolki ToolBar](how-to-add-buttons-to-a-toolbar-control.md)
- [Instrukcje: określanie ikony dla przycisku kontrolki ToolBar](how-to-define-an-icon-for-a-toolbar-button.md)
- [ToolBar — Formant](toolbar-control-windows-forms.md)
