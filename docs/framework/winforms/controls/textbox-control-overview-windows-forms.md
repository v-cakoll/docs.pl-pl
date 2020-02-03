---
title: TextBox, kontrolka — omówienie
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
ms.openlocfilehash: 06ab460d720d17331881b5ba653263160eaf3cb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742808"
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox — Informacje o formancie [Formularze systemu Windows]
Windows Forms pola tekstowe są używane do pobierania danych wejściowych od użytkownika lub do wyświetlania tekstu. Formant <xref:System.Windows.Forms.TextBox> jest zazwyczaj używany do edycji tekstu, chociaż może być również tylko do odczytu. Pola tekstowe mogą wyświetlać wiele wierszy, zawijać tekst do rozmiaru kontrolki i dodawać podstawowe formatowanie. Formant <xref:System.Windows.Forms.TextBox> zapewnia jeden styl formatu dla tekstu wyświetlanego lub wprowadzanego do kontrolki. Aby wyświetlić wiele typów formatowanego tekstu, użyj kontrolki <xref:System.Windows.Forms.RichTextBox>. Aby uzyskać więcej informacji, zobacz [RichTextBox Control — Omówienie](richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>Praca z kontrolką TextBox  
 Tekst wyświetlany przez formant jest zawarty we właściwości <xref:System.Windows.Forms.TextBox.Text%2A>. Domyślnie można wprowadzić do 2048 znaków w polu tekstowym. Jeśli ustawisz właściwość <xref:System.Windows.Forms.TextBox.Multiline%2A> na `true`, możesz wprowadzić do 32 KB tekstu. Właściwość <xref:System.Windows.Forms.TextBox.Text%2A> można ustawić w czasie projektowania przy użyciu okna właściwości, w czasie wykonywania w kodzie lub przez dane wejściowe użytkownika w czasie wykonywania. Bieżącą zawartość pola tekstowego można pobrać w czasie wykonywania, odczytując Właściwość <xref:System.Windows.Forms.TextBox.Text%2A>.  
  
 Poniższy przykład kodu ustawia tekst w kontrolce w czasie wykonywania. Procedura `InitializeMyControl` nie zostanie wykonana automatycznie. należy ją wywołać.  
  
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
- [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
