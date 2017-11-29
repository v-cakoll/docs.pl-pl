---
title: "Porady: ustawianie wcięć, wysunięć i akapitów punktowanych za pomocą formantu RichTextBox formularzy systemu Windows"
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
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9b1398c0438f9ebe528e9394014f5f6529ea8f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Porady: ustawianie wcięć, wysunięć i akapitów punktowanych za pomocą formantu RichTextBox formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.RichTextBox> formant ma wiele opcji formatowania tekstu Wyświetla. Zaznaczonych akapitów można sformatować jako listy punktowane, ustawiając <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> właściwości. Można również użyć <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, i <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> właściwości, aby ustawić wcięcie akapitów względem lewej i prawej krawędzi formantu a lewą krawędzią innych wierszy tekstu.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Aby sformatować akapitu listy punktowanej  
  
1.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> właściwości `true`.  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a>Wcięcia akapitu  
  
1.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> właściwości na liczbę całkowitą reprezentującą odległość w pikselach między lewą krawędzią formantu a lewą krawędzią tekstu.  
  
2.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> właściwości na liczbę całkowitą reprezentującą odległość w pikselach między lewą krawędź pierwszego wiersza tekstu akapitu a lewą krawędzią kolejnych wierszy w tym samym obiekcie paragraph. Wartość <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> właściwość ma zastosowanie wyłącznie do wierszy akapitu, które zostały opakowane poniżej pierwszego wiersza.  
  
3.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> właściwości na liczbę całkowitą reprezentującą odległość w pikselach między prawą krawędzią formantu a prawej krawędzi tekstu.  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    >  Te właściwości mają wpływ na wszystkie akapitów, które zawierają zaznaczonego tekstu, a także tekst, który został wpisany po do bieżącego punkt wstawiania. Na przykład gdy użytkownik wybiera word akapitu i można dostosować wcięcie, nowe ustawienia będą stosowane do całego akapitu, który zawiera ten wyraz, a także do dowolnego akapitów, następnie wprowadzone po akapitów. Aby uzyskać informacje o programowy wybór tekstu, zobacz <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox — formant](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Formanty do użycia w formularzach systemu Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
