---
title: 'Instrukcje: wyświetlanie podglądu wydruku w aplikacjach formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: 8252906de9a574f49617609a4cb08a1e8aa6a992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929005"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="8ccb3-102">Instrukcje: wyświetlanie podglądu wydruku w aplikacjach formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="8ccb3-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="8ccb3-103">Możesz użyć <xref:System.Windows.Forms.PrintPreviewDialog> kontrolki, aby umożliwić użytkownikom wyświetlanie dokumentu, często przed jego wydrukowaniem.</span><span class="sxs-lookup"><span data-stu-id="8ccb3-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="8ccb3-104">W tym celu należy określić wystąpienie <xref:System.Drawing.Printing.PrintDocument> klasy; jest to dokument do wydrukowania.</span><span class="sxs-lookup"><span data-stu-id="8ccb3-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="8ccb3-105">Aby uzyskać więcej informacji na temat korzystania z podglądu <xref:System.Drawing.Printing.PrintDocument> wydruku ze składnikiem, zobacz [How to: Drukowanie w Windows Forms przy użyciu podglądu](../advanced/how-to-print-in-windows-forms-using-print-preview.md)wydruku.</span><span class="sxs-lookup"><span data-stu-id="8ccb3-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ccb3-106">Aby można było <xref:System.Windows.Forms.PrintPreviewDialog> korzystać z kontrolki w czasie wykonywania, użytkownicy muszą mieć zainstalowaną na komputerze lokalnie lub za pomocą sieci, ponieważ jest to część określająca <xref:System.Windows.Forms.PrintPreviewDialog> sposób, w jaki ten dokument będzie wyglądał po wydrukowaniu.</span><span class="sxs-lookup"><span data-stu-id="8ccb3-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="8ccb3-107">Kontrolka<xref:System.Drawing.Printing.PrinterSettings>używaklasy. <xref:System.Windows.Forms.PrintPreviewDialog></span><span class="sxs-lookup"><span data-stu-id="8ccb3-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="8ccb3-108">Ponadto kontrolka <xref:System.Drawing.Printing.PageSettings> używa<xref:System.Windows.Forms.PrintPreviewDialog> klasy, tak jak składnik. <xref:System.Windows.Forms.PrintPreviewDialog></span><span class="sxs-lookup"><span data-stu-id="8ccb3-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="8ccb3-109"><xref:System.Windows.Forms.PrintPreviewDialog> Dokument wydruku określony we <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> właściwości kontrolki odwołuje się <xref:System.Drawing.Printing.PrinterSettings> do wystąpień obu klas i <xref:System.Drawing.Printing.PageSettings> i służy do renderowania dokumentu w oknie podglądu.</span><span class="sxs-lookup"><span data-stu-id="8ccb3-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="8ccb3-110">Aby wyświetlić strony przy użyciu kontrolki PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="8ccb3-110">To view pages using the PrintPreviewDialog control</span></span>  
  
- <span data-ttu-id="8ccb3-111">Użyj metody, aby wyświetlić okno dialogowe, <xref:System.Drawing.Printing.PrintDocument> określając do użycia. <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A></span><span class="sxs-lookup"><span data-stu-id="8ccb3-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="8ccb3-112">W poniższym przykładzie <xref:System.Windows.Forms.Button> kodu procedura obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> otwiera wystąpienie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8ccb3-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="8ccb3-113">Dokument drukowania jest określony we <xref:System.Windows.Forms.PrintDialog.Document%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ccb3-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="8ccb3-114">W poniższym przykładzie nie określono dokumentu drukowania.</span><span class="sxs-lookup"><span data-stu-id="8ccb3-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="8ccb3-115">Przykład wymaga, aby formularz <xref:System.Windows.Forms.Button> miał kontrolkę <xref:System.Drawing.Printing.PrintDocument> , <xref:System.Windows.Forms.PrintPreviewDialog> składnik o nazwie `myDocument`i kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="8ccb3-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     <span data-ttu-id="8ccb3-116">(Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8ccb3-116">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8ccb3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ccb3-117">See also</span></span>

- [<span data-ttu-id="8ccb3-118">PrintDocument, składnik</span><span class="sxs-lookup"><span data-stu-id="8ccb3-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="8ccb3-119">PrintPreviewDialog, kontrolka</span><span class="sxs-lookup"><span data-stu-id="8ccb3-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="8ccb3-120">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ccb3-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="8ccb3-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ccb3-121">Windows Forms</span></span>](../index.md)
