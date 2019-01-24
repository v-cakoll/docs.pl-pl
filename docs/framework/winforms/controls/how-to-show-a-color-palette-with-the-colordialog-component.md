---
title: 'Instrukcje: Pokazywanie palety kolorów przy użyciu składnika ColorDialog'
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
ms.openlocfilehash: 34da70280ff6e5b850469e7ba041cc7c7aaf1f47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637128"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Instrukcje: Pokazywanie palety kolorów przy użyciu składnika ColorDialog
[ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) składnik wyświetla palety kolorów i zwraca właściwość zawierające kolor użytkownik wybrał.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>Wybierz kolor, przy użyciu składnika ColorDialog  
  
1.  Wyświetlane przy użyciu okno dialogowe <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
2.  Użyj <xref:System.Windows.Forms.DialogResult> właściwości w celu określenia, jak okno dialogowe zostało zamknięte.  
  
3.  Użyj <xref:System.Windows.Forms.ColorDialog.Color%2A> właściwość <xref:System.Windows.Forms.ColorDialog> składnika, aby ustawić kolor wybrany.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> zostanie otwarty program obsługi zdarzeń <xref:System.Windows.Forms.ColorDialog> składnika. Gdy kolor, który jest wybrane i użytkownik klika polecenie **OK**, <xref:System.Windows.Forms.Button> kolor tła kontrolki jest ustawiona na wybranym kolorze. W przykładzie założono, formularz ma <xref:System.Windows.Forms.Button> kontroli i <xref:System.Windows.Forms.ColorDialog> składnika.  
  
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
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog, składnik](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)
