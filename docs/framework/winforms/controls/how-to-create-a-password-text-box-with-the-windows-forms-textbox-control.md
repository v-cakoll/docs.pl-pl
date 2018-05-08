---
title: 'Porady: tworzenie pola tekstowego hasła za pomocą formantu TextBox formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: 41bfb2bc1a1ead5bb289264c44145b88721efe49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Porady: tworzenie pola tekstowego hasła za pomocą formantu TextBox formularzy systemu Windows
Pole hasła jest pole tekstowe formularzy systemu Windows, które wyświetla symboli zastępczych, gdy użytkownik wpisuje ciąg znaków.  
  
### <a name="to-create-a-password-text-box"></a>Aby utworzyć pole tekstowe hasła  
  
1.  Ustaw <xref:System.Windows.Forms.TextBox.PasswordChar%2A> właściwość <xref:System.Windows.Forms.TextBox> formantu do określonego znaku.  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Właściwość określa znak wyświetlany w polu tekstowym. Na przykład gwiazdki wyświetlana w polu hasła, określ * dla <xref:System.Windows.Forms.TextBox.PasswordChar%2A> właściwości w oknie właściwości. Następnie niezależnie od tego, jakie użytkownik wpisze w polu tekstowym znak, wyświetlana jest gwiazdka.  
  
2.  (Opcjonalnie) Ustaw <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> właściwości. Właściwość określa, ile znaków można wpisać w polu tekstowym. Po przekroczeniu maksymalnego system emituje sygnał dźwiękowy i pole tekstowe nie akceptuje żadnych więcej znaków. Należy pamiętać, że nie możesz w tym celu jako maksymalną długość hasła może być używany do hakerami próbuje odgadnąć hasło.  
  
     Poniższy przykład kodu pokazuje, jak zainicjować pole tekstowe, które będzie akceptować ciąg do 14 znaków i wyświetlić gwiazdki zamiast ciągu. `InitializeMyControl` Procedury nie będą automatycznie wykonywane; musi zostać wywołana.  
  
    > [!IMPORTANT]
    >  Przy użyciu <xref:System.Windows.Forms.TextBox.PasswordChar%2A> właściwości pola tekstowego pozwala zagwarantować, inne osoby nie będą mogli określić hasło użytkownika, jeśli one przestrzegać użytkownika, wprowadzając ją. To zabezpieczenie nie obejmuje dowolny rodzaj gromadzenia i przekazywania hasła, które może wystąpić z powodu logiki aplikacji. Ponieważ wprowadzony tekst nie są szyfrowane w dowolny sposób, należy traktować jak w przypadku innych poufnych danych. Mimo że nie ma tak, hasło nadal jest traktowana jako zwykły tekst (chyba że zaimplementowano pewne dodatkowe zabezpieczenie).  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Instrukcje: tworzenie pola tekstowego tylko do odczytu](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Instrukcje: umieszczanie cudzysłowu w ciągu](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox, kontrolka](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
