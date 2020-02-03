---
title: Wyświetlanie podglądu wydruku w aplikacjach Windows Forms
titleSuffix: ''
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
ms.openlocfilehash: ac02339ad86e491cd047dcd4b0c8841374b3bb2e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745571"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="ec0f7-102">Porady: wyświetlanie podglądu wydruku w aplikacjach formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="ec0f7-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="ec0f7-103">Można użyć kontrolki <xref:System.Windows.Forms.PrintPreviewDialog>, aby umożliwić użytkownikom wyświetlanie dokumentu, często przed jego wydrukowaniem.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="ec0f7-104">W tym celu należy określić wystąpienie klasy <xref:System.Drawing.Printing.PrintDocument>; jest to dokument do wydrukowania.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="ec0f7-105">Aby uzyskać więcej informacji o korzystaniu z podglądu wydruku w składniku <xref:System.Drawing.Printing.PrintDocument>, zobacz [How to: Print in Windows Forms using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span><span class="sxs-lookup"><span data-stu-id="ec0f7-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec0f7-106">Aby można było korzystać z kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> w czasie wykonywania, użytkownicy muszą mieć zainstalowaną na komputerze lokalnie lub za pomocą sieci, ponieważ w ten sposób składnik <xref:System.Windows.Forms.PrintPreviewDialog> określa sposób, w jaki dokument będzie wyglądał po wydrukowaniu.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="ec0f7-107">Kontrolka <xref:System.Windows.Forms.PrintPreviewDialog> używa klasy <xref:System.Drawing.Printing.PrinterSettings>.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="ec0f7-108">Ponadto formant <xref:System.Windows.Forms.PrintPreviewDialog> używa klasy <xref:System.Drawing.Printing.PageSettings>, tak jak składnik <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="ec0f7-109">Dokument drukowania określony we właściwości <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> odwołuje się do wystąpień obu klas <xref:System.Drawing.Printing.PrinterSettings> i <xref:System.Drawing.Printing.PageSettings>, które są używane do renderowania dokumentu w oknie podglądu.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="ec0f7-110">Aby wyświetlić strony przy użyciu kontrolki PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="ec0f7-110">To view pages using the PrintPreviewDialog control</span></span>  
  
- <span data-ttu-id="ec0f7-111">Użyj metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>, aby wyświetlić okno dialogowe, określając <xref:System.Drawing.Printing.PrintDocument> do użycia.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="ec0f7-112">W poniższym przykładzie kodu <xref:System.Windows.Forms.Button> kontrolka <xref:System.Windows.Forms.Control.Click> do obsługi zdarzeń otwiera wystąpienie kontrolki <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="ec0f7-113">Dokument drukowania jest określony we właściwości <xref:System.Windows.Forms.PrintDialog.Document%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="ec0f7-114">W poniższym przykładzie nie określono dokumentu drukowania.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="ec0f7-115">Przykład wymaga, aby formularz miał formant <xref:System.Windows.Forms.Button>, składnik <xref:System.Drawing.Printing.PrintDocument> o nazwie `myDocument`i formant <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
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
  
     <span data-ttu-id="ec0f7-116">(Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ec0f7-116">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ec0f7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec0f7-117">See also</span></span>

- [<span data-ttu-id="ec0f7-118">PrintDocument, składnik</span><span class="sxs-lookup"><span data-stu-id="ec0f7-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="ec0f7-119">PrintPreviewDialog, kontrolka</span><span class="sxs-lookup"><span data-stu-id="ec0f7-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="ec0f7-120">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec0f7-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="ec0f7-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec0f7-121">Windows Forms</span></span>](../index.md)
