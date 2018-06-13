---
title: 'Porady: kontrolowanie punktu wstawiania w formancie TextBox formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: ced563eb063bbcc429cdf1447a0158459e5d5c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530741"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>Porady: kontrolowanie punktu wstawiania w formancie TextBox formularzy systemu Windows
Gdy program Windows Forms <xref:System.Windows.Forms.TextBox> formant najpierw uzyskuje fokus, wstawiania domyślną w polu tekstowym znajduje się na lewo od istniejącego tekstu. Użytkownik może przenieść punkt wstawiania z klawiatury lub myszy. Jeśli pole tekstowe utraci i ponownie otrzymuje fokus, punkt wstawiania będzie wszędzie tam, gdzie użytkownika ostatniego umieszczenia go.  
  
 W niektórych przypadkach to zachowanie może być niejasna dla użytkownika. W edytorze tekstu aplikacji, użytkownik może spodziewać się nowe znaki są wyświetlane po istniejącego tekstu. W aplikacji zapisu danych użytkownik może spodziewać się nowych znaków, aby zastąpić istniejący wpis. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> i <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości umożliwia modyfikowanie zachowania do własnych potrzeb.  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>Aby kontrolować punktu wstawiania w formancie TextBox  
  
1.  Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwości odpowiednią wartość. Zero umieszcza punkt wstawiania natychmiast po lewej stronie pierwszego znaku.  
  
2.  (Opcjonalnie) Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości długość tekstu, aby wybrać.  
  
     Poniższy kod zawsze zwraca punkt wstawiania na 0. `TextBox1_Enter` Obsługi zdarzeń musi być powiązana do formantu, aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach systemu Windows](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a>Zapewnienie widoczności domyślnie punkt wstawiania  
 <xref:System.Windows.Forms.TextBox> Jest widoczne domyślnie w nowego formularza tylko wtedy, gdy punkt wstawiania <xref:System.Windows.Forms.TextBox> formant jest pierwszy w kolejności tabulacji. W przeciwnym razie punkt wstawiania jest wyświetlana tylko wtedy, gdy przekażesz <xref:System.Windows.Forms.TextBox> fokus klawiatury lub myszy.  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>Aby punkt wstawiania pole tekstowe widoczne domyślnie na nowy formularz  
  
-   Ustaw <xref:System.Windows.Forms.TextBox> formantu <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości `0`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Instrukcje: tworzenie pola tekstowego tylko do odczytu](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Instrukcje: umieszczanie cudzysłowu w ciągu](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox, kontrolka](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
