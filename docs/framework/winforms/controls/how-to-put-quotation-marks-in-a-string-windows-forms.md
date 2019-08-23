---
title: 'Instrukcje: Wprowadź cudzysłowy w ciągu (Windows Forms)'
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
ms.openlocfilehash: 20828f75eeae9df33fcc22d8558b26a8a1ab2bdc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910433"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Instrukcje: Wprowadź cudzysłowy w ciągu (Windows Forms)
Czasami warto umieścić znaki cudzysłowu ("") w ciągu tekstu. Przykład:  
  
 "Nie zawarto".  
  
 Alternatywnie można również użyć <xref:Microsoft.VisualBasic.ControlChars.Quote> pola jako stałej.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Aby umieścić znaki cudzysłowu w ciągu w kodzie  
  
1. W Visual Basic Wstaw dwa cudzysłowy w wierszu jako osadzony znak cudzysłowu. W wizualizacjach C# i C++wizualizacji Wstaw sekwencję \\ucieczki "jako osadzony znak cudzysłowu. Na przykład, aby utworzyć poprzedni ciąg, użyj poniższego kodu.  
  
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
  
     —lub—  
  
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
- [Instrukcje: Kontrolowanie punktu wstawiania w kontrolce TextBox Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: Tworzenie pola tekstowego hasła za pomocą kontrolki TextBox Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: Tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: Zaznacz tekst w kontrolce TextBox Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Instrukcje: Wyświetl wiele wierszy w kontrolce TextBox Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
