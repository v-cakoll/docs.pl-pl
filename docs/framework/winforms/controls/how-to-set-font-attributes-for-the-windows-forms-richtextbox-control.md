---
title: "Porady: ustawianie atrybutów czcionki dla formantu RichTextBox formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fe122f509890715c398bef728a98ff874b61817
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Porady: ustawianie atrybutów czcionki dla formantu RichTextBox formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.RichTextBox> formant ma wiele opcji formatowania tekstu Wyświetla. Możesz wprowadzić wybranych znaków pogrubiony, podkreślony lub kursywą, przy użyciu <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> właściwości. Ta właściwość umożliwia również zmienić rozmiar i krój wybranych znaków. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Właściwości umożliwia zmianę koloru wybranych znaków.  
  
### <a name="to-change-the-appearance-of-characters"></a>Aby zmienić wygląd znaków  
  
1.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> właściwości odpowiednią czcionkę.  
  
     Aby umożliwić użytkownikom ustawić rodziny czcionek, rozmiar i krój czcionki w aplikacji, należy zwykle użyć <xref:System.Windows.Forms.FontDialog> składnika. Aby uzyskać ogólne informacje, zobacz [informacje o składniku FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).  
  
2.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> kolor odpowiedniej dla właściwości.  
  
     Aby umożliwić użytkownikom ustawić kolor w aplikacji, należy zwykle użyć <xref:System.Windows.Forms.ColorDialog> składnika. Aby uzyskać ogólne informacje, zobacz [colordialog — informacje o składniku](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).  
  
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
    >  Te właściwości mają wpływ tylko na zaznaczony tekst lub, w przypadku żaden tekst nie jest zaznaczony, tekst, który jest wpisany w bieżącej lokalizacji punktu wstawiania. Aby uzyskać informacje na programowy wybór tekstu, zobacz <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox — formant](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Formanty do użycia w formularzach systemu Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
