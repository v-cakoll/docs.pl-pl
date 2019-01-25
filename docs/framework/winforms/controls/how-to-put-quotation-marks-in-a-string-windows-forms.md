---
title: 'Instrukcje: Umieszczanie cudzysłowu w ciągu (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 24d7ea17384a912fda454bfb1136696ab18d9843
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651646"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Instrukcje: Umieszczanie cudzysłowu w ciągu (Windows Forms)
Czasami możesz chcieć umieścić znaki cudzysłowu ("") w ciągu tekstowym. Na przykład:  
  
 Ona twierdzi "Oferującego Traktuj!"  
  
 Alternatywnie, można również użyć <xref:Microsoft.VisualBasic.ControlChars.Quote> pola jako stała.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Aby umieścić znaki cudzysłowu w ciągu w kodzie  
  
1.  W języku Visual Basic należy wstawić dwa znaki cudzysłowu w wierszu jako osadzonego znaku cudzysłowu. W elemencie wizualnym C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], Wstaw sekwencja unikowa \\"jako osadzonego znak cudzysłowu. Na przykład utworzyć poprzedniego parametry, należy użyć następującego kodu.  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     —lub—  
  
2.  Wstaw znak ASCII lub Unicode dla znaku cudzysłowu. W języku Visual Basic należy użyć znaku ASCII (34). W elemencie wizualnym C#, należy użyć znaku Unicode (\u0022).  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  W tym przykładzie nie można użyć \u0022, ponieważ nie można użyć nazwy znaki uniwersalne, opisująca do znaku w podstawowym zestawie znaków. W przeciwnym razie zostanie wyświetlony C3851. Aby uzyskać więcej informacji, zobacz [błąd kompilatora C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).  
  
     —lub—  
  
3.  Można również zdefiniować stałą znaku i używać jej w razie potrzeby.  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [TextBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
- [Instrukcje: Kontrolowanie punktu wstawiania w formancie TextBox formularzy Windows](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: Tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: Tworzenie pola tekstowego tylko do odczytu](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: Zaznaczanie tekstu w formancie TextBox formularzy Windows](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Instrukcje: Wyświetlanie wielu wierszy w formancie TextBox formularzy Windows](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
