---
title: 'Porady: wysyłanie danych do Active MDI Child'
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
ms.openlocfilehash: 563be8494cb84dc74b45985d3ba74e4b6a07eb8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182494"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>Porady: wysyłanie danych do Active MDI Child
Często w kontekście [aplikacji interfejsu wielokadowniczego (MDI)](multiple-document-interface-mdi-applications.md)należy wysłać dane do aktywnego okna podrzędnego, na przykład gdy użytkownik wkleja dane ze Schowka do aplikacji MDI.  
  
> [!NOTE]
> Aby uzyskać informacje dotyczące sprawdzania fokusu w oknie podrzędnym i wysyłania jego zawartości do Schowka, zobacz [Określanie aktywnego dziecka MDI](how-to-determine-the-active-mdi-child.md).  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>Aby wysłać dane do aktywnego okna podrzędnego MDI ze Schowka  
  
1. W ramach metody skopiuj tekst w Schowku do aktywnego formantu aktywnego formularza podrzędnego.  
  
    > [!NOTE]
    > W tym przykładzie przyjęto założenie,`Form1`że istnieje formularz nadrzędny MDI <xref:System.Windows.Forms.RichTextBox> ( ), który ma co najmniej jedno podrzędne okna MDI zawierające formant. Aby uzyskać więcej informacji, zobacz [Tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md).  
  
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

- [Aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md)
- [Porady: tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md)
- [Porady: tworzenie formularzy podrzędnych MDI](how-to-create-mdi-child-forms.md)
- [Instrukcje: określanie elementu podrzędnego MDI Active](how-to-determine-the-active-mdi-child.md)
- [Porady: aranżowanie formularzy podrzędnych MDI](how-to-arrange-mdi-child-forms.md)
