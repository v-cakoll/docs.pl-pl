---
title: 'Porady: określanie właściwości strony za pomocą składnika PageSetupDialog'
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
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 52ef02ccfe6586f89adabb30187aa48e5fe87349
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="d1459-102">Porady: określanie właściwości strony za pomocą składnika PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="d1459-102">How to: Determine Page Properties Using the PageSetupDialog Component</span></span>
<span data-ttu-id="d1459-103">[PageSetupDialog —](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) składnika wyświetla układ, rozmiar papieru i inne opcje układ strony użytkownikowi dla dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d1459-103">The [PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) component presents layout, paper size, and other page layout choices to the user for a document.</span></span>  
  
 <span data-ttu-id="d1459-104">Należy określić wystąpienie <xref:System.Drawing.Printing.PrintDocument> klasy — jest to wydrukować dokument.</span><span class="sxs-lookup"><span data-stu-id="d1459-104">You need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class—this is the document to be printed.</span></span> <span data-ttu-id="d1459-105">Ponadto użytkownicy muszą mieć zainstalowany na komputerze, lokalnie lub za pośrednictwem sieci, drukarki, jest częściowo jak <xref:System.Windows.Forms.PageSetupDialog> składnika Określa strony, użytkownik widzi opcji formatowania.</span><span class="sxs-lookup"><span data-stu-id="d1459-105">Additionally, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PageSetupDialog> component determines the page formatting choices presented to the user.</span></span>  
  
 <span data-ttu-id="d1459-106">Praca z ważnym aspektem <xref:System.Windows.Forms.PageSetupDialog> składnik jest sposób interakcji z <xref:System.Drawing.Printing.PageSettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="d1459-106">An important aspect of working with the <xref:System.Windows.Forms.PageSetupDialog> component is how it interacts with the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="d1459-107"><xref:System.Drawing.Printing.PageSettings> Klasa jest używana do określenia ustawień, które modyfikują sposób stronę wydruku, takich jak układ papieru, rozmiar strony i marginesów.</span><span class="sxs-lookup"><span data-stu-id="d1459-107">The <xref:System.Drawing.Printing.PageSettings> class is used to specify settings that modify the way a page will be printed, such as paper orientation, the size of the page, and the margins.</span></span> <span data-ttu-id="d1459-108">Każdy z tych ustawień jest reprezentowany jako właściwość <xref:System.Drawing.Printing.PageSettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="d1459-108">Each of these settings is represented as a property of the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="d1459-109"><xref:System.Windows.Forms.PageSetupDialog> Klasy Modyfikuje wartości tych właściwości dla danego wystąpienia <xref:System.Drawing.Printing.PageSettings> klasy, która jest skojarzona z dokumentu (i jest reprezentowany jako <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> właściwości).</span><span class="sxs-lookup"><span data-stu-id="d1459-109">The <xref:System.Windows.Forms.PageSetupDialog> class modifies these property values for a given instance of the <xref:System.Drawing.Printing.PageSettings> class that is associated with the document (and is represented as a <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> property).</span></span>  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="d1459-110">Aby ustawić właściwości strony za pomocą składnika PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="d1459-110">To set page properties using the PageSetupDialog component</span></span>  
  
1.  <span data-ttu-id="d1459-111">Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe, określając <xref:System.Drawing.Printing.PrintDocument> do użycia.</span><span class="sxs-lookup"><span data-stu-id="d1459-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="d1459-112">W poniższym przykładzie <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń otwiera wystąpienia <xref:System.Windows.Forms.PageSetupDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="d1459-112">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span> <span data-ttu-id="d1459-113">Istniejący dokument jest określona w <xref:System.Windows.Forms.PageSetupDialog.Document%2A> właściwości oraz jego <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> właściwość jest ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="d1459-113">An existing document is specified in the <xref:System.Windows.Forms.PageSetupDialog.Document%2A> property, and its <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> property is set to `false`.</span></span>  
  
     <span data-ttu-id="d1459-114">W przykładzie założono formularz zawiera <xref:System.Windows.Forms.Button> kontroli, <xref:System.Drawing.Printing.PrintDocument> składnika o nazwie `myDocument`, a <xref:System.Windows.Forms.PageSetupDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="d1459-114">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="d1459-115">(Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d1459-115">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d1459-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1459-116">See Also</span></span>  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [<span data-ttu-id="d1459-117">Instrukcje: tworzenie standardowych zadań drukowania formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1459-117">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="d1459-118">PageSetupDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="d1459-118">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
