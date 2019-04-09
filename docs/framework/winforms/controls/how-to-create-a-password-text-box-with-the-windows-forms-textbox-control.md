---
title: 'Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy systemu Windows'
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
ms.openlocfilehash: f2017ccfd6d8320d6afc7b5e8a2ce8349c4fbd17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110615"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy systemu Windows
Pole hasła jest polem tekstowym formularzy Windows, który wyświetla symboli zastępczych, gdy użytkownik wpisze ciąg.  
  
### <a name="to-create-a-password-text-box"></a>Aby utworzyć pole tekstowe hasła  
  
1.  Ustaw <xref:System.Windows.Forms.TextBox.PasswordChar%2A> właściwość <xref:System.Windows.Forms.TextBox> formant do określonego znaku.  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Właściwość określa znak wyświetlane w polu tekstowym. Na przykład, jeśli chcesz, aby były wyświetlane w polu hasło gwiazdki, określić * dla <xref:System.Windows.Forms.TextBox.PasswordChar%2A> właściwości w oknie dialogowym właściwości. Następnie niezależnie od tego, jakie znak użytkownik wpisze w polu tekstowym, gwiazdka jest wyświetlana.  
  
2.  (Opcjonalnie) Ustaw <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> właściwości. Właściwość określa, ile znaków można wpisać w polu tekstowym. Jeśli zostanie przekroczona maksymalna długość, system emituje sygnał dźwiękowy i pole tekstowe nie akceptuje żadnych więcej znaków. Należy pamiętać, że nie możesz to zrobić, ponieważ maksymalna długość hasła może być użytkowania, aby przed hakerami, którzy próby odgadnięcia hasła.  
  
     W poniższym przykładzie kodu pokazano, jak zainicjować pola tekstowego, które będzie akceptować ciągu maksymalnie 14 znaków i wyświetlić gwiazdki zamiast ciągu. `InitializeMyControl` Procedury nie zostanie wykonany automatycznie; musi zostać wywołana.  
  
    > [!IMPORTANT]
    >  Za pomocą <xref:System.Windows.Forms.TextBox.PasswordChar%2A> właściwości pola tekstowego może pomóc upewnić się, że inne osoby nie będzie można określić hasło użytkownika, czy ich obserwować użytkownika, wprowadzając ją. Ta miara zabezpieczeń nie obejmuje dowolny rodzaj gromadzenia i przekazywania haseł, które mogą wystąpić z powodu logiki aplikacji. Ponieważ wprowadzony tekst nie jest szyfrowany w jakikolwiek sposób, należy traktować jak w przypadku innych poufnych danych. Mimo że nie ma związku z tym, hasło jest nadal traktowanej jako ciąg w formacie zwykłego tekstu (chyba że zaimplementowano pewne dodatkowe zabezpieczenie).  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextBox>
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
- [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy systemu Windows](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy systemu Windows](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy systemu Windows](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
