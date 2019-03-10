---
title: 'Instrukcje: Ustawianie wcięć, wysunięć i akapitów punktowanych za pomocą formantu RichTextBox formularzy Windows'
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
ms.openlocfilehash: b2173769634ddc4b7b42c822c3f60212eb8d8886
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713036"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Instrukcje: Ustawianie wcięć, wysunięć i akapitów punktowanych za pomocą formantu RichTextBox formularzy Windows
Formularze Windows <xref:System.Windows.Forms.RichTextBox> kontrolka ma wiele opcji formatowania tekstu, zostanie wyświetlony. Możesz sformatować zaznaczonych akapitów jako listy punktowane, ustawiając <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> właściwości. Można również użyć <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, i <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> właściwości, aby ustawić wcięcia akapitów względem lewej i prawej krawędzi formantu a lewą krawędzią innych wierszy tekstu.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Aby sformatować akapitu jako listy punktowane  
  
1.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> właściwość `true`.  
  
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
  
1.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> właściwości na liczbę całkowitą reprezentującą odległość w pikselach między lewą krawędzią kontrolki a lewą krawędzią tekstu.  
  
2.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> właściwości na liczbę całkowitą reprezentującą odległość w pikselach między lewą krawędzią pierwszy wiersz tekstu akapitu a lewą krawędzią kolejne wiersze, w tym samym akapicie. Wartość <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> właściwość ma zastosowanie tylko do wierszy w akapicie, które zostały opakowane poniżej pierwszego wiersza.  
  
3.  Ustaw <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> właściwości na liczbę całkowitą reprezentującą odległość w pikselach między prawą krawędzią kontrolki a prawej krawędzi tekstu.  
  
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
    >  Te właściwości mają wpływ na wszystkie akapitów, zawierające zaznaczony tekst i tekst, który bezpośrednio po bieżącym punkcie wstawiania. Na przykład gdy użytkownik zaznacza słowo akapitu, a następnie dopasowuje wcięcie, nowe ustawienia zostaną zastosowane cały akapit, który zawiera słowo, a także wszelkie akapitów, następnie wprowadzone po akapitów. Aby dowiedzieć się, jak programowy wybór tekstu, zobacz <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
