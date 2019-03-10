---
title: 'Instrukcje: Określanie elementu podrzędnego Active MDI'
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
ms.openlocfilehash: 95958491d624052922df9af37b188b9515480397
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714332"
---
# <a name="how-to-determine-the-active-mdi-child"></a>Instrukcje: Określanie elementu podrzędnego Active MDI
Czasami chcesz dostarczyć polecenia, który działa na formant, który ma fokus w formularzu podrzędnym aktualnie aktywne. Na przykład załóżmy, że chcesz skopiować zaznaczony tekst z pola tekstowego formularz podrzędny do Schowka. Należy utworzyć procedurę, która kopiuje zaznaczony tekst do Schowka z użyciem <xref:System.Windows.Forms.Control.Click> zdarzeń Kopiuj element menu standardowe menu Edycja.  
  
 Ponieważ aplikacja MDI może mieć wiele wystąpień tego samego formularza podrzędnego, procedury musi wiedzieć, który formularz do użycia. Aby określić poprawne formularza, należy użyć <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> właściwość, która zwraca formularz podrzędny, który ma fokus, lub który został ostatnio aktywne.  
  
 Jeśli masz kilka kontrolek w formularzu, należy określić, które określają jest aktywny. Podobnie jak <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> właściwości <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> właściwość zwraca kontrolki z fokusem w formularzu podrzędnym active. Poniżej przedstawiono procedurę kopiowania, który można wywoływać z poziomu menu formularza podrzędnego, menu na formularzu MDI, lub przycisk paska narzędzi.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Aby określić active MDI child (w celu skopiowania tekstu do Schowka)  
  
1.  Wewnątrz metody należy skopiować tekst z aktywną kontrolkę formularz podrzędny aktywnego do Schowka.  
  
    > [!NOTE]
    >  W tym przykładzie przyjęto założenie, istnieje formularza nadrzędnego MDI (`Form1`) zawierający co najmniej jeden podrzędne MDI zawierający <xref:System.Windows.Forms.RichTextBox> kontroli. Aby uzyskać więcej informacji, zobacz [tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md).  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md)
- [Instrukcje: Tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md)
- [Instrukcje: Tworzenie formularzy podrzędnych MDI](how-to-create-mdi-child-forms.md)
- [Instrukcje: Wysyłanie danych do Active MDI Child](how-to-send-data-to-the-active-mdi-child.md)
- [Instrukcje: Aranżowanie formularzy podrzędnych MDI](how-to-arrange-mdi-child-forms.md)
