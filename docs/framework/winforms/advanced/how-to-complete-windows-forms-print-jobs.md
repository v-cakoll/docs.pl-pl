---
title: Ukończ zadania drukowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 62f67002bfbaf46e73bae06fdaff26efde865c06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182598"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="1529c-102">Porady: kończenie zadań drukowania formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1529c-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="1529c-103">Często edytory tekstu i inne aplikacje, które wymagają drukowania, umożliwiają wyświetlenie użytkownikom komunikatu o zakończeniu zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="1529c-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="1529c-104">Tę funkcję można udostępnić w formularzach <xref:System.Drawing.Printing.PrintDocument.EndPrint> systemu <xref:System.Drawing.Printing.PrintDocument> Windows, obsługując zdarzenie składnika.</span><span class="sxs-lookup"><span data-stu-id="1529c-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="1529c-105">Poniższa procedura wymaga utworzenia aplikacji opartej <xref:System.Drawing.Printing.PrintDocument> na systemie Windows ze składnikiem, który jest standardowym sposobem włączania drukowania z aplikacji opartej na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="1529c-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="1529c-106">Aby uzyskać więcej informacji na <xref:System.Drawing.Printing.PrintDocument> temat drukowania z formularzy systemu Windows przy użyciu tego składnika, zobacz [Jak: Tworzenie standardowych zadań drukowania formularzy systemu Windows](how-to-create-standard-windows-forms-print-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="1529c-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="1529c-107">Aby wykonać zadanie drukowania</span><span class="sxs-lookup"><span data-stu-id="1529c-107">To complete a print job</span></span>  
  
1. <span data-ttu-id="1529c-108">Ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> właściwość <xref:System.Drawing.Printing.PrintDocument> komponentu.</span><span class="sxs-lookup"><span data-stu-id="1529c-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <span data-ttu-id="1529c-109">Napisz kod do <xref:System.Drawing.Printing.PrintDocument.EndPrint> obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1529c-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="1529c-110">W poniższym przykładzie kodu jest wyświetlany komunikat informujący, że dokument zakończył drukowanie.</span><span class="sxs-lookup"><span data-stu-id="1529c-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +
          " has finished printing.");  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     <span data-ttu-id="1529c-111">(Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1529c-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1529c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1529c-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="1529c-113">Obsługa drukowania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1529c-113">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
