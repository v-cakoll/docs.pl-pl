---
title: "Porady: wyświetlanie łączy stylu sieci Web za pomocą formantu RichTextBox formularzy systemu Windows"
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
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5391c48720e68a8a7e6e0fb7735252d00025adc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>Porady: wyświetlanie łączy stylu sieci Web za pomocą formantu RichTextBox formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.RichTextBox> formant może wyświetlać linki sieci Web jako kolorowy i podkreślony. Można napisać kod, który powoduje otwarcie okna przeglądarki przedstawiający witryny sieci Web określonego w tekst łącza, gdy łącze zostanie kliknięte.  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>Aby utworzyć łącze do strony sieci Web za pomocą formantu RichTextBox  
  
1.  Ustaw <xref:System.Windows.Forms.RichTextBox.Text%2A> właściwości na ciąg, który zawiera nieprawidłowy adres URL (na przykład "http://www.microsoft.com/").  
  
2.  Upewnij się, że <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> właściwość jest ustawiona na `true` (ustawienie domyślne).  
  
3.  Utwórz nowe wystąpienie globalne <xref:System.Diagnostics.Process> obiektu.  
  
4.  Pisanie programu obsługi zdarzeń dla <xref:System.Windows.Forms.RichTextBox.LinkClicked> zdarzenie, które wysyła odpowiedni tekst w przeglądarce.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.RichTextBox.LinkClicked> zdarzeń otwiera wystąpienia programu Internet Explorer na adres URL określony w <xref:System.Windows.Forms.RichTextBox.Text%2A> właściwość <xref:System.Windows.Forms.RichTextBox> formantu. W tym przykładzie założono formularza z <xref:System.Windows.Forms.RichTextBox> formantu.  
  
    > [!IMPORTANT]
    >  W wywołaniu <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> metody, można napotkać <xref:System.Security.SecurityException> wyjątek, jeśli używasz kod w kontekście częściowego zaufania ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
    ```vb  
    Public p As New System.Diagnostics.Process  
    Private Sub RichTextBox1_LinkClicked _  
       (ByVal sender As Object, ByVal e As _  
       System.Windows.Forms.LinkClickedEventArgs) _  
       Handles RichTextBox1.LinkClicked  
          ' Call Process.Start method to open a browser  
          ' with link text as URL.  
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)  
    End Sub  
    ```  
  
    ```csharp  
    public System.Diagnostics.Process p = new System.Diagnostics.Process();  
  
    private void richTextBox1_LinkClicked(object sender,   
    System.Windows.Forms.LinkClickedEventArgs e)  
    {  
       // Call Process.Start method to open a browser  
       // with link text as URL.  
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);  
    }  
    ```  
  
    ```cpp  
    public:  
       System::Diagnostics::Process ^ p;  
  
    private:  
       void richTextBox1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkClickedEventArgs ^  e)  
       {  
          // Call Process.Start method to open a browser  
          // with link text as URL.  
          p = System::Diagnostics::Process::Start("IExplore.exe",  
             e->LinkText);  
       }  
    ```  
  
     ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Należy zainicjować proces `p`, co można zrobić, umieszczając w niej następująca instrukcja w Konstruktorze formularza:  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.richTextBox1.LinkClicked += new   
       System.Windows.Forms.LinkClickedEventHandler  
       (this.richTextBox1_LinkClicked);  
    ```  
  
    ```cpp  
    this->richTextBox1->LinkClicked += gcnew  
       System::Windows::Forms::LinkClickedEventHandler  
       (this, &Form1::richTextBox1_LinkClicked);  
    ```  
  
     Jest ważne natychmiast zatrzymać proces, który został utworzony po zakończeniu pracy z nim. Odwołanie do kod przedstawiony powyżej, swój kod, aby zatrzymać proces może wyglądać następująco:  
  
    ```vb  
    Public Sub StopWebProcess()  
       p.Kill()  
    End Sub  
    ```  
  
    ```csharp  
    public void StopWebProcess()  
    {  
       p.Kill();  
    }  
    ```  
  
    ```cpp  
    public: void StopWebProcess()  
    {  
       p->Kill();  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>  
 <xref:System.Windows.Forms.RichTextBox.LinkClicked>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox — formant](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Formanty do użycia w formularzach systemu Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
