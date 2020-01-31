---
title: Kontrolowanie punktu wstawiania w kontrolce TextBox
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
ms.openlocfilehash: fd4803820921f0c922a4ce885f809abee8fd4c6c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742203"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>Porady: kontrolowanie punktu wstawiania w formancie TextBox formularzy systemu Windows
Gdy kontrolka <xref:System.Windows.Forms.TextBox> Windows Forms po raz pierwszy uzyska fokus, domyślne Wstawianie w polu tekstowym znajduje się po lewej stronie dowolnego istniejącego tekstu. Użytkownik może przenieść punkt wstawiania za pomocą klawiatury lub myszy. Jeśli pole tekstowe utraci, a następnie odzyska fokus, punkt wstawiania będzie wszędzie tam, gdzie został on ostatnio umieszczony.  
  
 W niektórych przypadkach takie zachowanie może być rozuzgadniane z użytkownikiem. W aplikacji do przetwarzania tekstu użytkownik może oczekiwać, że nowe znaki pojawiają się po dowolnym istniejącym tekście. W aplikacji do wprowadzania danych użytkownik może oczekiwać, że nowe znaki zastąpią wszelkie istniejące wpisy. Właściwości <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> i <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> umożliwiają modyfikowanie zachowania odpowiednio do potrzeb.  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>Aby kontrolować punkt wstawiania w kontrolce TextBox  
  
1. Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> na odpowiednią wartość. Zero umieszcza punkt wstawiania bezpośrednio z lewej strony pierwszego znaku.  
  
2. Obowiązkowe Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na długość tekstu, który chcesz wybrać.  
  
     Poniższy kod zawsze zwraca punkt wstawiania do 0. Procedura obsługi zdarzeń `TextBox1_Enter` musi być powiązana z kontrolką; Aby uzyskać więcej informacji, zobacz [Tworzenie programów obsługi zdarzeń w Windows Forms](../creating-event-handlers-in-windows-forms.md).  
  
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
  
## <a name="making-the-insertion-point-visible-by-default"></a>Uwidacznianie domyślnego punktu wstawiania  
 <xref:System.Windows.Forms.TextBox> punkt wstawiania jest domyślnie widoczny w nowym formularzu tylko wtedy, gdy formant <xref:System.Windows.Forms.TextBox> jest pierwszy w kolejności tabulacji. W przeciwnym razie punkt wstawiania pojawia się tylko wtedy, gdy podajesz <xref:System.Windows.Forms.TextBox> fokus przy użyciu klawiatury lub myszy.  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>Aby punkt wstawiania pola tekstowego był widoczny domyślnie w nowym formularzu  
  
- Ustaw właściwość <xref:System.Windows.Forms.Control.TabIndex%2A> kontrolki <xref:System.Windows.Forms.TextBox> na `0`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextBox>
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
- [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
