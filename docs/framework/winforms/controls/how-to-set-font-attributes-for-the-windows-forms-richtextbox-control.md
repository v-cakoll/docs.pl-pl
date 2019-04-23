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
ms.openlocfilehash: a6fe5b30c457fae2d53c946092b214f492fe5e9b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331211"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Instrukcje: ustawianie atrybutów czcionki dla kontrolki RichTextBox formularzy systemu Windows
Formularze Windows <xref:System.Windows.Forms.RichTextBox> kontrolka ma wiele opcji formatowania tekstu, zostanie wyświetlony. Aby włączyć wybranych znaków pogrubienie, podkreślony lub kursywa, przy użyciu <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> właściwości. Ta właściwość umożliwia również zmienić rozmiar i krój czcionki wybranych znaków. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Właściwości umożliwia zmianę koloru zaznaczonych znaków.  
  
### <a name="to-change-the-appearance-of-characters"></a>Aby zmienić wygląd znaków  
  
1. Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> właściwość odpowiednią czcionkę.  
  
     Aby umożliwić użytkownikom ustawić rodzinę czcionek, rozmiar i krój czcionki w aplikacji, zazwyczaj używasz <xref:System.Windows.Forms.FontDialog> składnika. Aby uzyskać przegląd, zobacz [— informacje o składniku FontDialog](fontdialog-component-overview-windows-forms.md).  
  
2. Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> właściwość odpowiedni kolor.  
  
     Aby umożliwić użytkownikom ustawić kolor w aplikacji, zazwyczaj używasz <xref:System.Windows.Forms.ColorDialog> składnika. Aby uzyskać przegląd, zobacz [ColorDialog, składnik — omówienie](colordialog-component-overview-windows-forms.md).  
  
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
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
