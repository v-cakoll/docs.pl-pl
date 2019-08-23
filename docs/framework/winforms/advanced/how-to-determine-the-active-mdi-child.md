---
title: 'Instrukcje: Określanie elementu podrzędnego MDI Active'
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
ms.openlocfilehash: 91100b37e4cae9041479b209e40034efe376df5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946222"
---
# <a name="how-to-determine-the-active-mdi-child"></a>Instrukcje: Określanie elementu podrzędnego MDI Active
W razie potrzeby należy udostępnić polecenie, które będzie działać na formancie, który ma fokus w aktualnie aktywnym formularzu podrzędnym. Załóżmy na przykład, że chcesz skopiować zaznaczony tekst z pola tekstowego formularza podrzędnego do Schowka. Należy utworzyć procedurę, która kopiuje zaznaczony tekst do schowka przy użyciu <xref:System.Windows.Forms.Control.Click> zdarzenia menu Kopiuj w standardowym menu edycji.  
  
 Ponieważ aplikacja MDI może mieć wiele wystąpień tego samego formularza podrzędnego, procedura musi wiedzieć, którego formularza użyć. Aby określić poprawną formę, użyj <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> właściwości, która zwraca formularz podrzędny, który ma fokus lub który był ostatnio aktywny.  
  
 Jeśli masz kilka kontrolek w formularzu, musisz również określić, który formant jest aktywny. Podobnie jak <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> właściwość, właściwość zwraca formant z fokusem na aktywnym formularzu podrzędnym. <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> Poniższa procedura ilustruje procedurę kopiowania, którą można wywołać z menu formularza podrzędnego, menu w formularzu MDI lub przycisk paska narzędzi.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Aby określić aktywny element podrzędny MDI (aby skopiować jego tekst do schowka)  
  
1. W ramach metody skopiuj tekst aktywnej kontrolki aktywnego formularza podrzędnego do Schowka.  
  
    > [!NOTE]
    > W tym przykładzie założono, że istnieje formularz nadrzędny`Form1`MDI (), który ma co najmniej jeden Windows podrzędny <xref:System.Windows.Forms.RichTextBox> MDI zawierający formant. Aby uzyskać więcej informacji, zobacz [Tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md).  
  
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
- [Instrukcje: Wyślij dane do aktywnego elementu podrzędnego MDI](how-to-send-data-to-the-active-mdi-child.md)
- [Instrukcje: Rozmieść formularze podrzędne MDI](how-to-arrange-mdi-child-forms.md)
