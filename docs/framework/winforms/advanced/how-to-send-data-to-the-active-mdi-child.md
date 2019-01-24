---
title: 'Instrukcje: Wysyłanie danych do Active MDI Child'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms
- MDI [Windows Forms], sending data to forms
- Clipboard [Windows Forms], pasting
- Clipboard [Windows Forms], getting data from
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
ms.openlocfilehash: dab72d64cdd013125ae7c302ccf297ecdc0c98b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589971"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>Instrukcje: Wysyłanie danych do Active MDI Child
Często w kontekście [aplikacje interfejsu wielu dokumentów (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), konieczne będzie wysyłać dane do okno podrzędne aktywnego, na przykład gdy użytkownik wkleja danych ze Schowka w aplikacji MDI.  
  
> [!NOTE]
>  Aby uzyskać informacji na temat weryfikowania okno podrzędne, które ma fokus, a następnie wysyłając jego zawartość do Schowka, zobacz [Określanie Active MDI Child](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md).  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>Aby wysyłać dane do aktywnego okna podrzędnego MDI ze Schowka  
  
1.  Wewnątrz metody należy skopiować tekst do Schowka do aktywną kontrolkę formularza podrzędnego active.  
  
    > [!NOTE]
    >  W tym przykładzie przyjęto założenie, istnieje formularza nadrzędnego MDI (`Form1`) zawierający co najmniej jeden podrzędne MDI zawierający <xref:System.Windows.Forms.RichTextBox> kontroli. Aby uzyskać więcej informacji, zobacz [tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Aplikacje interfejsu wielu dokumentów (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)
- [Instrukcje: Tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [Instrukcje: Tworzenie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [Instrukcje: Określanie elementu podrzędnego Active MDI](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)
- [Instrukcje: Aranżowanie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
