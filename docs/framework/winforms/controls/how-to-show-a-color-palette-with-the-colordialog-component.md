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
ms.openlocfilehash: ea12fe19b6c8c7464f0820267face8a1d66de784
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536930"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Porady: pokazywanie palety kolorów przy użyciu składnika ColorDialog
[ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) składnika wyświetla paletę kolorów i zwraca wartość właściwości zawierająca kolor użytkownik wybrał.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>Aby wybrać kolor przy użyciu składnika ColorDialog  
  
1.  Wyświetlać przy użyciu — okno dialogowe <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
2.  Użyj <xref:System.Windows.Forms.DialogResult> właściwości, aby określić sposób zamknięcia okna dialogowego.  
  
3.  Użyj <xref:System.Windows.Forms.ColorDialog.Color%2A> właściwość <xref:System.Windows.Forms.ColorDialog> składnika, aby ustawić kolor wybrany.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń otwiera <xref:System.Windows.Forms.ColorDialog> składnika. Gdy kolor jest wybrany, a użytkownik kliknie **OK**, <xref:System.Windows.Forms.Button> kolor tła formantu ma ustawioną wartość wybranego koloru. W przykładzie założono formularz zawiera <xref:System.Windows.Forms.Button> kontroli i <xref:System.Windows.Forms.ColorDialog> składnika.  
  
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
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog, składnik](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)
