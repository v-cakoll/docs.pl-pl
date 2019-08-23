---
title: 'Instrukcje: ustawianie atrybutów czcionki dla kontrolki RichTextBox formularzy systemu Windows'
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
ms.openlocfilehash: 4919e94c23b1a67680ea0f360304ee0f75c7f425
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963222"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Instrukcje: ustawianie atrybutów czcionki dla kontrolki RichTextBox formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.RichTextBox> Windows Forms ma wiele opcji formatowania wyświetlanego tekstu. Można wybrać pogrubienie, podkreślenie lub kursywę przy użyciu <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> właściwości. Można także użyć tej właściwości, aby zmienić rozmiar i krój czcionki wybranych znaków. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Właściwość pozwala zmieniać kolor wybranych znaków.  
  
### <a name="to-change-the-appearance-of-characters"></a>Aby zmienić wygląd znaków  
  
1. <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> Ustaw właściwość na odpowiednią czcionkę.  
  
     Aby umożliwić użytkownikom ustawianie rodziny czcionek, rozmiaru i kroju pisma w aplikacji, zazwyczaj używany jest <xref:System.Windows.Forms.FontDialog> składnik. Aby zapoznać się z omówieniem, zobacz [Omówienie składnika FontDialog](fontdialog-component-overview-windows-forms.md).  
  
2. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Ustaw właściwość na odpowiedni kolor.  
  
     Aby umożliwić użytkownikom ustawianie koloru w aplikacji, zazwyczaj używany jest <xref:System.Windows.Forms.ColorDialog> składnik. Aby zapoznać się z omówieniem, zobacz [Omówienie składnika ColorDialog](colordialog-component-overview-windows-forms.md).  
  
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
    > Te właściwości mają wpływ tylko na zaznaczony tekst lub, jeśli nie wybrano tekstu, tekst, który jest wpisywany w bieżącej lokalizacji punktu wstawiania. Aby uzyskać informacje na temat wybierania tekstu programowo <xref:System.Windows.Forms.TextBoxBase.Select%2A>, zobacz.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
