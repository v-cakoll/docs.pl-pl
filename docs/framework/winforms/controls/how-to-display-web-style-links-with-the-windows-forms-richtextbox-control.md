---
title: 'Porady: wyświetlanie łączy stylu sieci Web za pomocą formantu RichTextBox formularzy systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
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
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b82a5251cb5e1f632d126105cfae5cf2b8f62fc0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="01d79-102">Porady: wyświetlanie łączy stylu sieci Web za pomocą formantu RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="01d79-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="01d79-103">Formularze systemu Windows <xref:System.Windows.Forms.RichTextBox> formant może wyświetlać linki sieci Web jako kolorowy i podkreślony.</span><span class="sxs-lookup"><span data-stu-id="01d79-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="01d79-104">Można napisać kod, który powoduje otwarcie okna przeglądarki przedstawiający witryny sieci Web określonego w tekst łącza, gdy łącze zostanie kliknięte.</span><span class="sxs-lookup"><span data-stu-id="01d79-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="01d79-105">Aby utworzyć łącze do strony sieci Web za pomocą formantu RichTextBox</span><span class="sxs-lookup"><span data-stu-id="01d79-105">To link to a Web page with the RichTextBox control</span></span>  
  
1.  <span data-ttu-id="01d79-106">Ustaw <xref:System.Windows.Forms.RichTextBox.Text%2A> właściwości na ciąg, który zawiera prawidłowy adres URL (na przykład "http://www.microsoft.com/").</span><span class="sxs-lookup"><span data-stu-id="01d79-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>  
  
2.  <span data-ttu-id="01d79-107">Upewnij się, że <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> właściwość jest ustawiona na `true` (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="01d79-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>  
  
3.  <span data-ttu-id="01d79-108">Utwórz nowe wystąpienie globalne <xref:System.Diagnostics.Process> obiektu.</span><span class="sxs-lookup"><span data-stu-id="01d79-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>  
  
4.  <span data-ttu-id="01d79-109">Pisanie programu obsługi zdarzeń dla <xref:System.Windows.Forms.RichTextBox.LinkClicked> zdarzenie, które wysyła odpowiedni tekst w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="01d79-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>  
  
     <span data-ttu-id="01d79-110">W poniższym przykładzie <xref:System.Windows.Forms.RichTextBox.LinkClicked> zdarzeń otwiera wystąpienia programu Internet Explorer na adres URL określony w <xref:System.Windows.Forms.RichTextBox.Text%2A> właściwość <xref:System.Windows.Forms.RichTextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="01d79-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="01d79-111">W tym przykładzie założono formularza z <xref:System.Windows.Forms.RichTextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="01d79-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="01d79-112">W wywołaniu <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> metody, można napotkać <xref:System.Security.SecurityException> wyjątek, jeśli używasz kod w kontekście częściowego zaufania ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="01d79-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="01d79-113">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="01d79-113">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
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
  
     <span data-ttu-id="01d79-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Należy zainicjować proces `p`, co można zrobić, umieszczając w niej następująca instrukcja w Konstruktorze formularza:</span><span class="sxs-lookup"><span data-stu-id="01d79-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     <span data-ttu-id="01d79-115">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="01d79-115">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="01d79-116">Jest ważne natychmiast zatrzymać proces, który został utworzony po zakończeniu pracy z nim.</span><span class="sxs-lookup"><span data-stu-id="01d79-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="01d79-117">Odwołanie do kod przedstawiony powyżej, swój kod, aby zatrzymać proces może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="01d79-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01d79-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01d79-118">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>  
 <xref:System.Windows.Forms.RichTextBox.LinkClicked>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="01d79-119">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="01d79-119">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="01d79-120">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01d79-120">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
