---
title: 'Instrukcje: Pokazywanie listy czcionek przy użyciu składnika FontDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- fonts [Windows Forms], showing list
- FontDialog component [Windows Forms]
- fonts [Windows Forms], attributes
- Font property [Windows Forms], setting with FontDialog component
- Font dialog box [Windows Forms], displaying
- fonts [Windows Forms], selecting
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
ms.openlocfilehash: 18a9a4bca42117233c4b01a4aeb6cffcb79119d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726406"
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a>Instrukcje: Pokazywanie listy czcionek przy użyciu składnika FontDialog
[FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md) składnika pozwala użytkownikom na wybór czcionki, a także zmienić jego aspektach wyświetlania, takie jak rozmiar i grubość.  
  
 Czcionka zaznaczona w oknie dialogowym są zwracane w <xref:System.Windows.Forms.FontDialog.Font%2A> właściwości. W związku z tym wykorzystując czcionkę wybrane przez użytkownika jest równie proste jak odczytywanie właściwości.  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a>Aby wybrać właściwości czcionki przy użyciu składnika FontDialog  
  
1.  Wyświetlane przy użyciu okno dialogowe <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
2.  Użyj <xref:System.Windows.Forms.DialogResult> właściwości w celu określenia, jak okno dialogowe zostało zamknięte.  
  
3.  Użyj <xref:System.Windows.Forms.FontDialog.Font%2A> właściwość umożliwiająca ustawienie wymaganej czcionki.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> zostanie otwarty program obsługi zdarzeń <xref:System.Windows.Forms.FontDialog> składnika. Gdy czcionka jest wybrana, a użytkownik kliknie **OK**, <xref:System.Windows.Forms.FontDialog.Font%2A> właściwość <xref:System.Windows.Forms.TextBox> formant, który znajduje się w formularzu jest ustawiona na wybranej czcionki. W przykładzie założono, formularz ma <xref:System.Windows.Forms.Button> kontroli <xref:System.Windows.Forms.TextBox> kontroli i <xref:System.Windows.Forms.FontDialog> składnika.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.FontDialog>
- [FontDialog, składnik](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
