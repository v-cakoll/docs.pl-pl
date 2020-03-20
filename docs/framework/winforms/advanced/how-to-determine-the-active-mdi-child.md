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
ms.openlocfilehash: 57491faa10c182630d41565ba236d65e393929b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182543"
---
# <a name="how-to-determine-the-active-mdi-child"></a>Porady: określanie elementu podrzędnego MDI Active
Czasami należy podać polecenie, które działa na formancie, który koncentruje się na aktualnie aktywnym formularzu podrzędnym. Załóżmy na przykład, że chcesz skopiować zaznaczony tekst z pola tekstowego formularza podrzędnego do Schowka. Należy utworzyć procedurę kopiuje zaznaczony tekst do <xref:System.Windows.Forms.Control.Click> Schowka przy użyciu zdarzenia elementu menu Kopiuj w standardowym menu Edycja.  
  
 Ponieważ aplikacja MDI może mieć wiele wystąpień tego samego formularza podrzędnego, procedura musi wiedzieć, który formularz do użycia. Aby określić poprawny <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> formularz, należy użyć właściwości, która zwraca formularz podrzędny, który ma fokus lub który był ostatnio aktywny.  
  
 Jeśli masz kilka formantów w formularzu, należy również określić, który formant jest aktywny. Podobnie <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> jak <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> właściwość, właściwość zwraca formant z fokusem na aktywnym formularzu podrzędnym. Poniższa procedura ilustruje procedurę kopiowania, którą można wywołać z menu formularza podrzędnego, menu w formularzu MDI lub przycisku paska narzędzi.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Aby określić aktywne dziecko MDI (skopiować jego tekst do Schowka)  
  
1. W ramach metody skopiuj tekst aktywnego formantu aktywnego formularza podrzędnego do Schowka.  
  
    > [!NOTE]
    > W tym przykładzie przyjęto założenie,`Form1`że istnieje formularz nadrzędny MDI <xref:System.Windows.Forms.RichTextBox> ( ), który ma co najmniej jedno podrzędne okna MDI zawierające formant. Aby uzyskać więcej informacji, zobacz [Tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md).  
  
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

- [Aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md)
- [Porady: tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md)
- [Porady: tworzenie formularzy podrzędnych MDI](how-to-create-mdi-child-forms.md)
- [Instrukcje: wysyłanie danych do Active MDI Child](how-to-send-data-to-the-active-mdi-child.md)
- [Porady: aranżowanie formularzy podrzędnych MDI](how-to-arrange-mdi-child-forms.md)
