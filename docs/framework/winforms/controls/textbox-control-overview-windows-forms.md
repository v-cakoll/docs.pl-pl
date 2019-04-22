---
title: TextBox — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: a91b67df1071c79707bb20a68efb4d5e6f083ae0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162140"
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox — Informacje o formancie [Formularze systemu Windows]
Windows Forms, pola tekstowe są używane do pobrać dane wejściowe od użytkownika lub do wyświetlania tekstu. <xref:System.Windows.Forms.TextBox> Kontroli jest zazwyczaj używana do edycji tekstu, mimo że można również on tylko do odczytu. Pola tekstowe można wyświetlić wiele wierszy, zawijanie tekstu do rozmiaru formantu i dodać podstawowe formatowanie. <xref:System.Windows.Forms.TextBox> Control oferuje jeden format stylu tekstu wyświetlane lub wprowadzone w formancie. Aby wyświetlić wiele typów tekstu sformatowanego, użyj <xref:System.Windows.Forms.RichTextBox> kontroli. Aby uzyskać więcej informacji, zobacz [informacje o formancie RichTextBox](richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>Praca z kontrolki TextBox  
 Tekst wyświetlany przez kontrolkę znajduje się w <xref:System.Windows.Forms.TextBox.Text%2A> właściwości. Domyślnie można wprowadzić do 2048 znaków w polu tekstowym. Jeśli ustawisz <xref:System.Windows.Forms.TextBox.Multiline%2A> właściwości `true`, możesz wprowadzić maksymalnie 32 KB tekstu. <xref:System.Windows.Forms.TextBox.Text%2A> Właściwość można ustawić w czasie projektowania w oknie właściwości w czasie wykonywania w kodzie lub w danych wejściowych użytkownika w czasie wykonywania. W czasie wykonywania można pobrać bieżącą zawartość pola tekstowego, czytając <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.  
  
 Poniższy przykład kodu ustawia tekst w kontrolce, w czasie wykonywania. `InitializeMyControl` Procedury nie zostanie wykonany automatycznie; musi zostać wywołana.  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextBox>
- [Instrukcje: Kontrolowanie punktu wstawiania w formancie TextBox formularzy Windows](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: Tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: Tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: Umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: Zaznaczanie tekstu w formancie TextBox formularzy Windows](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Instrukcje: Wyświetlanie wielu wierszy w formancie TextBox formularzy Windows](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
