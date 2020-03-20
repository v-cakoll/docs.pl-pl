---
title: 'Porady: pokazywanie palety kolorów przy użyciu składnika ColorDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: 0406ef7a32678bd149c0024348a7adf1f0b72926
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141786"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Porady: pokazywanie palety kolorów przy użyciu składnika ColorDialog
Składnik [ColorDialog](colordialog-component-windows-forms.md) wyświetla paletę kolorów i zwraca właściwość zawierającą kolor wybrany przez użytkownika.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>Aby wybrać kolor przy użyciu składnika ColorDialog  
  
1. Wyświetl okno dialogowe <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> przy użyciu metody.  
  
2. Użyj <xref:System.Windows.Forms.DialogResult> właściwości, aby określić, jak okno dialogowe zostało zamknięte.  
  
3. Użyj <xref:System.Windows.Forms.ColorDialog.Color%2A> właściwości komponentu, <xref:System.Windows.Forms.ColorDialog> aby ustawić wybrany kolor.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.Button> program <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń <xref:System.Windows.Forms.ColorDialog> formantu otwiera składnik. Po wybraniu koloru i kliknięciu **przycisku OK**kolor tła <xref:System.Windows.Forms.Button> formantu jest ustawiony na wybrany kolor. W przykładzie przyjęto <xref:System.Windows.Forms.Button> założenie, <xref:System.Windows.Forms.ColorDialog> że formularz ma formant i składnik.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     (Visual C#, Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog, składnik](colordialog-component-windows-forms.md)
