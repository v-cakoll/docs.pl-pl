---
title: Ustawianie wcięć, wysunięć i akapitów punktowanych za pomocą kontrolki RichTextBox
ms.date: 03/30/2017
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
ms.openlocfilehash: 4dcd5691f328eac6d94675c50ed41a7d7cc36596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743014"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Porady: ustawianie wcięć, wysunięć i akapitów punktowanych za pomocą formantu RichTextBox formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.RichTextBox> Windows Forms ma wiele opcji formatowania wyświetlanego tekstu. Można sformatować wybrane akapity jako listy punktowane przez ustawienie właściwości <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>. Można również użyć właściwości <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>i <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>, aby ustawić wcięcia akapitów względem lewej i prawej krawędzi kontrolki oraz lewą krawędź tekstu.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Aby sformatować akapit jako listę punktowaną  
  
1. Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> właściwość `true`.  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a>Aby zwiększyć wcięcie akapitu  
  
1. Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> na liczbę całkowitą reprezentującą odległość (w pikselach) między lewą krawędzią kontrolki a lewą krawędzią tekstu.  
  
2. Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> na liczbę całkowitą reprezentującą odległość w pikselach między lewą krawędzią pierwszego wiersza tekstu w akapicie a lewą krawędzią kolejnych wierszy w tym samym akapicie. Wartość właściwości <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> dotyczy tylko wierszy w akapicie, które zostały opakowane poniżej pierwszego wiersza.  
  
3. Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> na liczbę całkowitą reprezentującą odległość w pikselach między prawą krawędzią kontrolki a prawą krawędzią tekstu.  
  
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
    > Wszystkie te właściwości mają wpływ na wszystkie akapity, które zawierają zaznaczony tekst, a także tekst, który jest wpisywany po bieżącym punkcie wstawiania. Na przykład gdy użytkownik wybierze wyraz w akapicie, a następnie dostosowuje wcięcia, nowe ustawienia zostaną zastosowane do całego akapitu zawierającego ten wyraz, a także do każdego akapitu wprowadzonego po wybranym akapicie. Aby uzyskać informacje na temat programistycznego wybierania tekstu, zobacz <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
