---
title: 'Porady: wyświetlanie podglądu wydruku w aplikacjach Windows Forms'
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
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4868187e860afe8004742365465baf8c57e312a4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="8f27e-102">Porady: wyświetlanie podglądu wydruku w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f27e-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="8f27e-103">Można użyć <xref:System.Windows.Forms.PrintPreviewDialog> sterowania, aby użytkownicy mogli wyświetlić dokument, często, zanim zostanie do drukowania.</span><span class="sxs-lookup"><span data-stu-id="8f27e-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="8f27e-104">Aby to zrobić, należy określić wystąpienie <xref:System.Drawing.Printing.PrintDocument> klasy; to wydrukować dokument.</span><span class="sxs-lookup"><span data-stu-id="8f27e-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="8f27e-105">Aby uzyskać więcej informacji o korzystaniu z podglądu wydruku z <xref:System.Drawing.Printing.PrintDocument> składników, zobacz [porady: drukowanie w Windows Forms przy użyciu podglądu wydruku](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).</span><span class="sxs-lookup"><span data-stu-id="8f27e-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f27e-106">Aby użyć <xref:System.Windows.Forms.PrintPreviewDialog> kontroli w czasie wykonywania, użytkownicy muszą mieć zainstalowany na komputerze, lokalnie lub za pośrednictwem sieci, drukarki, jest częściowo jak <xref:System.Windows.Forms.PrintPreviewDialog> składnika określa wygląd dokumentu po wydrukowaniu.</span><span class="sxs-lookup"><span data-stu-id="8f27e-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="8f27e-107"><xref:System.Windows.Forms.PrintPreviewDialog> Kontrolować używa <xref:System.Drawing.Printing.PrinterSettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="8f27e-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="8f27e-108">Ponadto <xref:System.Windows.Forms.PrintPreviewDialog> kontrolować używa <xref:System.Drawing.Printing.PageSettings> klasy, podobnie jak <xref:System.Windows.Forms.PrintPreviewDialog> składników.</span><span class="sxs-lookup"><span data-stu-id="8f27e-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="8f27e-109">Dokument wydruku określone w <xref:System.Windows.Forms.PrintPreviewDialog> formantu <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> właściwość odwołuje się do wystąpienia obu <xref:System.Drawing.Printing.PrinterSettings> i <xref:System.Drawing.Printing.PageSettings> klasy i te, które są używane do renderowania dokumentu w oknie Podgląd.</span><span class="sxs-lookup"><span data-stu-id="8f27e-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="8f27e-110">Aby wyświetlić strony za pomocą printpreviewdialog — formant</span><span class="sxs-lookup"><span data-stu-id="8f27e-110">To view pages using the PrintPreviewDialog control</span></span>  
  
-   <span data-ttu-id="8f27e-111">Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe, określając <xref:System.Drawing.Printing.PrintDocument> do użycia.</span><span class="sxs-lookup"><span data-stu-id="8f27e-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="8f27e-112">W poniższym przykładzie kodu <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń otwiera wystąpienia <xref:System.Windows.Forms.PrintPreviewDialog> formantu.</span><span class="sxs-lookup"><span data-stu-id="8f27e-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="8f27e-113">Dokument wydruku jest określona w <xref:System.Windows.Forms.PrintDialog.Document%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8f27e-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="8f27e-114">W poniższym przykładzie jest określony żaden dokument wydruku.</span><span class="sxs-lookup"><span data-stu-id="8f27e-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="8f27e-115">Przykład wymaga, aby miało formularza <xref:System.Windows.Forms.Button> kontroli, <xref:System.Drawing.Printing.PrintDocument> składnika o nazwie `myDocument`i <xref:System.Windows.Forms.PrintPreviewDialog> formantu.</span><span class="sxs-lookup"><span data-stu-id="8f27e-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
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
  
     <span data-ttu-id="8f27e-116">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8f27e-116">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8f27e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f27e-117">See Also</span></span>  
 [<span data-ttu-id="8f27e-118">PrintDocument, składnik</span><span class="sxs-lookup"><span data-stu-id="8f27e-118">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 [<span data-ttu-id="8f27e-119">PrintPreviewDialog, kontrolka</span><span class="sxs-lookup"><span data-stu-id="8f27e-119">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="8f27e-120">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f27e-120">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="8f27e-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f27e-121">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
