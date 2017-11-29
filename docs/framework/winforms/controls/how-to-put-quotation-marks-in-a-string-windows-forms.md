---
title: "Porady: umieszczanie cudzysłowu w ciągu (Formularze systemu Windows)"
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
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a4141a27a3b195dbb747a827d2bd9426a948f83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Porady: umieszczanie cudzysłowu w ciągu (Formularze systemu Windows)
Czasami może chcesz umieścić znaki cudzysłowu ("") w ciągu tekstowego. Na przykład:  
  
 Użytkownik nazywany "Wymagają Traktuj!"  
  
 Alternatywnie, można również użyć <xref:Microsoft.VisualBasic.ControlChars.Quote> pole jako stała.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Aby umieścić znaki cudzysłowu w ciągu w kodzie  
  
1.  W [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], Wstaw dwa znaki cudzysłowu w wierszu jako osadzony znaku cudzysłowu. W [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], Wstaw sekwencji unikowej \\"jako osadzony znaku cudzysłowu. Na przykład aby utworzyć parametry poprzedniego, należy użyć poniższego kodu.  
  
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
  
2.  Wstaw znak ASCII lub Unicode dla znaku cudzysłowu. W [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], użyj znaków ASCII (34). W [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], użyj znaku Unicode (\u0022).  
  
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
    >  W tym przykładzie można użyć \u0022, ponieważ nie można użyć nazwa zawierająca znaki uniwersalne określający znaku w podstawowym zestawie znaków. W przeciwnym razie należy utworzyć C3851. Aby uzyskać więcej informacji, zobacz [C3851 błąd kompilatora](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).  
  
     —lub—  
  
3.  Można również zdefiniować stałą znaku i użyć go w razie potrzeby.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [Informacje o formancie TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Porady: kontrolowanie punktu wstawiania w formancie TextBox formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Porady: Tworzenie pola tekstowego hasła za pomocą formantu TextBox formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Porady: Tworzenie pola tekstowego tylko do odczytu](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Porady: Zaznaczanie tekstu w oknach formantu TextBox formularzy](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Porady: wyświetlanie wielu wierszy w oknach formantu TextBox formularzy](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox — formant](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
