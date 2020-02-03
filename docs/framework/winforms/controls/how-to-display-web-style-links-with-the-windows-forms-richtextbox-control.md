---
title: Wyświetlanie łączy w stylu sieci Web z kontrolką RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: 78a07a250744018f121b03f2973b1661ed6bf764
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745530"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="37c71-102">Porady: wyświetlanie łączy stylu sieci Web za pomocą formantu RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="37c71-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="37c71-103">Kontrolka <xref:System.Windows.Forms.RichTextBox> Windows Forms może wyświetlać linki sieci Web jako kolorowe i podkreślone.</span><span class="sxs-lookup"><span data-stu-id="37c71-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="37c71-104">Można napisać kod, który otwiera okno przeglądarki pokazujące witrynę sieci Web określoną w polu tekst linku po kliknięciu linku.</span><span class="sxs-lookup"><span data-stu-id="37c71-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="37c71-105">Aby utworzyć link do strony sieci Web z kontrolką RichTextBox</span><span class="sxs-lookup"><span data-stu-id="37c71-105">To link to a Web page with the RichTextBox control</span></span>

1. <span data-ttu-id="37c71-106">Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.Text%2A> na ciąg zawierający prawidłowy adres URL (na przykład "http://www.microsoft.com/").</span><span class="sxs-lookup"><span data-stu-id="37c71-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>

2. <span data-ttu-id="37c71-107">Upewnij się, że właściwość <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> jest ustawiona na `true` (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="37c71-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>

3. <span data-ttu-id="37c71-108">Utwórz nowe wystąpienie globalne obiektu <xref:System.Diagnostics.Process>.</span><span class="sxs-lookup"><span data-stu-id="37c71-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>

4. <span data-ttu-id="37c71-109">Napisz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.RichTextBox.LinkClicked>, które wysyła przeglądarkę do żądanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="37c71-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>

    <span data-ttu-id="37c71-110">W poniższym przykładzie zdarzenie <xref:System.Windows.Forms.RichTextBox.LinkClicked> otwiera wystąpienie programu Internet Explorer na adres URL określony we właściwości <xref:System.Windows.Forms.RichTextBox.Text%2A> kontrolki <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="37c71-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="37c71-111">W tym przykładzie przyjęto, że formularz z kontrolką <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="37c71-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="37c71-112">W wywołaniu metody <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> wystąpi wyjątek <xref:System.Security.SecurityException>, jeśli używasz kodu w kontekście częściowego zaufania z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="37c71-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="37c71-113">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="37c71-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

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

    <span data-ttu-id="37c71-114">(Wizualizacja C++) Należy zainicjować `p`procesu, który można wykonać, dołączając następujące instrukcje w Konstruktorze formularza:</span><span class="sxs-lookup"><span data-stu-id="37c71-114">(Visual C++) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    <span data-ttu-id="37c71-115">(Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="37c71-115">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

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

    <span data-ttu-id="37c71-116">Ważne jest, aby natychmiast przerwać proces utworzony po zakończeniu pracy z nim.</span><span class="sxs-lookup"><span data-stu-id="37c71-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="37c71-117">W odniesieniu do kodu przedstawionego powyżej kod, aby zatrzymać proces, może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="37c71-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="37c71-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37c71-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="37c71-119">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="37c71-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="37c71-120">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37c71-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
