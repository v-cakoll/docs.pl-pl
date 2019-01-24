---
title: 'Instrukcje: Ustawianie atrybutów czcionki dla formantu RichTextBox formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: 3793c33d378ee242656889434c7b29c415e9ec9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496208"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Instrukcje: Ustawianie atrybutów czcionki dla formantu RichTextBox formularzy Windows
Formularze Windows <xref:System.Windows.Forms.RichTextBox> kontrolka ma wiele opcji formatowania tekstu, zostanie wyświetlony. Aby włączyć wybranych znaków pogrubienie, podkreślony lub kursywa, przy użyciu <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> właściwości. Ta właściwość umożliwia również zmienić rozmiar i krój czcionki wybranych znaków. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Właściwości umożliwia zmianę koloru zaznaczonych znaków.  
  
### <a name="to-change-the-appearance-of-characters"></a>Aby zmienić wygląd znaków  
  
1.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> właściwość odpowiednią czcionkę.  
  
     Aby umożliwić użytkownikom ustawić rodzinę czcionek, rozmiar i krój czcionki w aplikacji, zazwyczaj używasz <xref:System.Windows.Forms.FontDialog> składnika. Aby uzyskać przegląd, zobacz [— informacje o składniku FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).  
  
2.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> właściwość odpowiedni kolor.  
  
     Aby umożliwić użytkownikom ustawić kolor w aplikacji, zazwyczaj używasz <xref:System.Windows.Forms.ColorDialog> składnika. Aby uzyskać przegląd, zobacz [ColorDialog, składnik — omówienie](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  Te właściwości mają wpływ tylko na zaznaczony tekst lub, jeśli nie wybrano tekstu, tekst jest wpisane w bieżącej lokalizacji punktu wstawiania. Aby uzyskać informacji na temat programowy wybór tekstu, zobacz <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
