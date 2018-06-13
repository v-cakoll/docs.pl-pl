---
title: 'Porady: określanie elementu podrzędnego MDI Active'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
ms.openlocfilehash: 0b084d204361764af1b36b154acfc5b360fc977e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521721"
---
# <a name="how-to-determine-the-active-mdi-child"></a>Porady: określanie elementu podrzędnego MDI Active
Czasem można udostępnić polecenia, który działa na formant, który ma fokus w formularzu podrzędnym obecnie aktywne. Na przykład załóżmy, że chcesz skopiować zaznaczonego tekstu w polu tekstowym formularz podrzędny do Schowka. Należy utworzyć procedury, która kopiuje zaznaczonego tekstu do Schowka przy użyciu <xref:System.Windows.Forms.Control.Click> zdarzeń Kopiuj element menu standardowe menu Edycja.  
  
 Ponieważ aplikacja MDI może mieć wiele wystąpień tego samego formularza podrzędnego, procedury musi wiedzieć, który formularz do użycia. Aby określić właściwego formularza, użyj <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> właściwość, która zwraca formularz podrzędny, który ma fokus lub który został ostatnio aktywne.  
  
 Jeśli masz kilka formantów w formularzu, należy również określić, które sterowania jest aktywna. Podobnie jak <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> właściwość <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> właściwość zwraca formantu z fokusem w formularzu podrzędnym aktywne. Poniżej przedstawiono procedurę kopiowania, który można wywołać z menu formularza podrzędnego, menu MDI formularza lub przycisku paska narzędzi.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Aby określić podrzędnego MDI active (można skopiować tekstu do Schowka)  
  
1.  W metodzie należy skopiować tekst aktywnym formantem formularza podrzędnego active do Schowka.  
  
    > [!NOTE]
    >  W tym przykładzie założono Brak formularza nadrzędnego MDI (`Form1`) mający okien podrzędnych co najmniej jeden MDI zawierający <xref:System.Windows.Forms.RichTextBox> formantu. Aby uzyskać więcej informacji, zobacz [tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {    
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
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
 [Instrukcje: tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Instrukcje: tworzenie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Instrukcje: wysyłanie danych do Active MDI Child](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Instrukcje: aranżowanie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
