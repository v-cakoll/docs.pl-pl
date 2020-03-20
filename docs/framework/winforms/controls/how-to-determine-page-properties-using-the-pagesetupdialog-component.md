---
title: 'Porady: określanie właściwości strony za pomocą składnika PageSetupDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
ms.openlocfilehash: 8a015c199193dfd9c43bec53cc93cbf9dc201413
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142046"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="2885d-102">Porady: określanie właściwości strony za pomocą składnika PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="2885d-102">How to: Determine Page Properties Using the PageSetupDialog Component</span></span>
<span data-ttu-id="2885d-103">[Składnik PageSetupDialog](pagesetupdialog-component-windows-forms.md) przedstawia użytkownikowi wybór układu, rozmiaru papieru i innego układu strony dla dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2885d-103">The [PageSetupDialog](pagesetupdialog-component-windows-forms.md) component presents layout, paper size, and other page layout choices to the user for a document.</span></span>  
  
 <span data-ttu-id="2885d-104">Należy określić wystąpienie <xref:System.Drawing.Printing.PrintDocument> klasy — jest to dokument, który ma zostać wydrukowany.</span><span class="sxs-lookup"><span data-stu-id="2885d-104">You need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class—this is the document to be printed.</span></span> <span data-ttu-id="2885d-105">Ponadto użytkownicy muszą mieć zainstalowaną drukarkę na swoim komputerze, lokalnie lub za <xref:System.Windows.Forms.PageSetupDialog> pośrednictwem sieci, ponieważ jest to częściowo sposób, w jaki składnik określa opcje formatowania strony prezentowane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="2885d-105">Additionally, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PageSetupDialog> component determines the page formatting choices presented to the user.</span></span>  
  
 <span data-ttu-id="2885d-106">Ważnym aspektem pracy <xref:System.Windows.Forms.PageSetupDialog> z komponentem jest sposób <xref:System.Drawing.Printing.PageSettings> interakcji z klasą.</span><span class="sxs-lookup"><span data-stu-id="2885d-106">An important aspect of working with the <xref:System.Windows.Forms.PageSetupDialog> component is how it interacts with the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="2885d-107">Klasa <xref:System.Drawing.Printing.PageSettings> służy do określania ustawień, które modyfikują sposób drukowania strony, takich jak orientacja papieru, rozmiar strony i marginesy.</span><span class="sxs-lookup"><span data-stu-id="2885d-107">The <xref:System.Drawing.Printing.PageSettings> class is used to specify settings that modify the way a page will be printed, such as paper orientation, the size of the page, and the margins.</span></span> <span data-ttu-id="2885d-108">Każde z tych ustawień jest reprezentowane <xref:System.Drawing.Printing.PageSettings> jako właściwość klasy.</span><span class="sxs-lookup"><span data-stu-id="2885d-108">Each of these settings is represented as a property of the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="2885d-109">Klasa <xref:System.Windows.Forms.PageSetupDialog> modyfikuje te wartości właściwości dla <xref:System.Drawing.Printing.PageSettings> danego wystąpienia klasy, która jest skojarzona <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> z dokumentem (i jest reprezentowana jako właściwość).</span><span class="sxs-lookup"><span data-stu-id="2885d-109">The <xref:System.Windows.Forms.PageSetupDialog> class modifies these property values for a given instance of the <xref:System.Drawing.Printing.PageSettings> class that is associated with the document (and is represented as a <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> property).</span></span>  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="2885d-110">Aby ustawić właściwości strony przy użyciu składnika PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="2885d-110">To set page properties using the PageSetupDialog component</span></span>  
  
1. <span data-ttu-id="2885d-111">Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody, aby wyświetlić okno <xref:System.Drawing.Printing.PrintDocument> dialogowe, określając do użycia.</span><span class="sxs-lookup"><span data-stu-id="2885d-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="2885d-112">W poniższym przykładzie <xref:System.Windows.Forms.Button> program <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń formantu otwiera wystąpienie składnika. <xref:System.Windows.Forms.PageSetupDialog></span><span class="sxs-lookup"><span data-stu-id="2885d-112">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span> <span data-ttu-id="2885d-113">Istniejący dokument jest <xref:System.Windows.Forms.PageSetupDialog.Document%2A> określony we <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> właściwości, a `false`jego właściwość jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="2885d-113">An existing document is specified in the <xref:System.Windows.Forms.PageSetupDialog.Document%2A> property, and its <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> property is set to `false`.</span></span>  
  
     <span data-ttu-id="2885d-114">W przykładzie przyjęto <xref:System.Windows.Forms.Button> założenie, <xref:System.Drawing.Printing.PrintDocument> że `myDocument`formularz ma <xref:System.Windows.Forms.PageSetupDialog> formant, składnik o nazwie i składnik.</span><span class="sxs-lookup"><span data-stu-id="2885d-114">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       'You will have to specify your own print document.  
       PageSetupDialog1.Document = myDocument  
       ' Sets the print document's color setting to false,  
       ' so that the page will not be printed in color.  
       PageSetupDialog1.Document.DefaultPageSettings.Color = False  
       PageSetupDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       pageSetupDialog1.Document = myDocument;  
       // Sets the print document's color setting to false,  
       // so that the page will not be printed in color.  
       pageSetupDialog1.Document.DefaultPageSettings.Color = false;  
       pageSetupDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button1_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          pageSetupDialog1->Document = myDocument;  
          // Sets the print document's color setting to false,  
          // so that the page will not be printed in color.  
          pageSetupDialog1->Document->DefaultPageSettings->Color = false;  
          pageSetupDialog1->ShowDialog();  
       }  
    ```  
  
     <span data-ttu-id="2885d-115">(Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2885d-115">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2885d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2885d-116">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="2885d-117">Instrukcje: tworzenie standardowych zadań drukowania formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2885d-117">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="2885d-118">PageSetupDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="2885d-118">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
