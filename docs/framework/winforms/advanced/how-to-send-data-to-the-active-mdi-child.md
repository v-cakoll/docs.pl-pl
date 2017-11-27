---
title: "Porady: wysyłanie danych do Active MDI Child"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms
- MDI [Windows Forms], sending data to forms
- Clipboard [Windows Forms], pasting
- Clipboard [Windows Forms], getting data from
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b7f505d68bfd6d8c65104244f9583fd3cf975dd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>Porady: wysyłanie danych do Active MDI Child
Często w kontekście [aplikacje interfejsu wielu dokumentów (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), konieczne będzie wysyłać dane do okna podrzędnego active, np. gdy użytkownik wkleja danych ze Schowka do aplikacji MDI.  
  
> [!NOTE]
>  Uzyskać informacji o weryfikacji okno podrzędne, które ma fokus i wysyłanie zawartości do Schowka, zobacz [określania podrzędnego MDI Active](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md).  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>Aby wysyłać dane do aktywnego okna podrzędnego MDI ze Schowka  
  
1.  W metodzie skopiować tekst do Schowka aktywnym formantem formularza podrzędnego aktywne.  
  
    > [!NOTE]
    >  W tym przykładzie założono Brak formularza nadrzędnego MDI (`Form1`) mający okien podrzędnych co najmniej jeden MDI zawierający <xref:System.Windows.Forms.RichTextBox> formantu. Aby uzyskać więcej informacji, zobacz [tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).  
  
    ```vb  
    Public Sub mniPaste_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniPaste.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ParentForm.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Try  
             Dim theBox As RichTextBox = Ctype(activeChild.ActiveControl, RichTextBox)  
             If (Not theBox Is Nothing) Then  
                ' Create a new instance of the DataObject interface.  
                Dim data As IDataObject = Clipboard.GetDataObject()  
                ' If the data is text, then set the text of the   
                ' RichTextBox to the text in the clipboard.  
                If (data.GetDataPresent(DataFormats.Text)) Then  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString()  
                End If  
             End If  
          Catch  
             MessageBox.Show("You need to select a RichTextBox.")  
          End Try  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniPaste_Click (object sender, System.EventArgs e)  
    {  
      // Determine the active child form.  
       Form activeChild = this.ParentForm.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {  
          try   
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Create a new instance of the DataObject interface.  
                IDataObject data = Clipboard.GetDataObject();  
                // If the data is text, then set the text of the   
                // RichTextBox to the text in the clipboard.  
                if (data.GetDataPresent(DataFormats.Text))  
                {  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString();                 
                }  
             }  
          }  
          catch   
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje interfejsu wielu dokumentów (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Porady: tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Porady: tworzenie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Porady: ustalić podrzędnego Active MDI](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [Porady: Aranżowanie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
