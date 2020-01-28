---
title: 'Porady: umieszczanie cudzysłowu w ciągu'
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
ms.openlocfilehash: c14747291d6c41144eef97b258f852bbe14ef07d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735901"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Porady: umieszczanie cudzysłowu w ciągu (Formularze systemu Windows)
Czasami warto umieścić znaki cudzysłowu ("") w ciągu tekstu. Na przykład:  
  
 "Nie zawarto".  
  
 Alternatywnie można również użyć pola <xref:Microsoft.VisualBasic.ControlChars.Quote> jako stałej.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Aby umieścić znaki cudzysłowu w ciągu w kodzie  
  
1. W Visual Basic Wstaw dwa cudzysłowy w wierszu jako osadzony znak cudzysłowu. W wizualizacjach C# i C++wizualizacji Wstaw sekwencję ucieczki \\"jako osadzony cudzysłów. Na przykład, aby utworzyć poprzedni ciąg, użyj poniższego kodu.  
  
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
  
     lub  
  
2. Wstaw znak ASCII lub Unicode dla znaku cudzysłowu. W Visual Basic Użyj znaku ASCII (34). W wizualizacji C#Użyj znaku Unicode (\u0022).  
  
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
    > W tym przykładzie nie można użyć \u0022, ponieważ nie można użyć uniwersalnej nazwy znaku, która określa znak w podstawowym zestawie znaków. W przeciwnym razie utworzysz C3851. Aby uzyskać więcej informacji, zobacz [błąd kompilatora C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).  
  
     lub  
  
3. Możesz również zdefiniować stałą dla znaku i użyć go w razie potrzeby.  
  
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
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
- [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
