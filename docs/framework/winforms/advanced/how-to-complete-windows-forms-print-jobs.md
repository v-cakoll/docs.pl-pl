---
title: 'Porady: kończenie zadań drukowania formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 74a8e3721df72415437dd0c39b3298d67c19990b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="13b94-102">Porady: kończenie zadań drukowania formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="13b94-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="13b94-103">Często edytory i inne aplikacje, które obejmują drukowanie zapewni opcję wyświetlania wiadomości do użytkowników o ukończeniu zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="13b94-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="13b94-104">Możesz podać tę funkcję w formularzach systemu Windows, obsługa <xref:System.Drawing.Printing.PrintDocument.EndPrint> zdarzenie <xref:System.Drawing.Printing.PrintDocument> składnika.</span><span class="sxs-lookup"><span data-stu-id="13b94-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="13b94-105">Poniższa procedura wymaga, że utworzono aplikację systemu Windows z <xref:System.Drawing.Printing.PrintDocument> składnik go, co jest standardowy sposób włączania drukowanie z aplikacji opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="13b94-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="13b94-106">Aby uzyskać więcej informacji na temat drukowania z formularzy systemu Windows przy użyciu <xref:System.Drawing.Printing.PrintDocument> składników, zobacz [porady: tworzenie standardowych systemu Windows Forms zadania drukowania](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="13b94-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="13b94-107">Aby ukończyć zadanie drukowania</span><span class="sxs-lookup"><span data-stu-id="13b94-107">To complete a print job</span></span>  
  
1.  <span data-ttu-id="13b94-108">Ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> właściwość <xref:System.Drawing.Printing.PrintDocument> składnika.</span><span class="sxs-lookup"><span data-stu-id="13b94-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  <span data-ttu-id="13b94-109">Napisać kod obsługujący <xref:System.Drawing.Printing.PrintDocument.EndPrint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="13b94-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="13b94-110">W poniższym przykładzie kodu zostanie wyświetlone okno komunikatu, wskazujący, że zakończono drukowanie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="13b94-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
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
  
     <span data-ttu-id="13b94-111">(Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="13b94-111">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13b94-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13b94-112">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="13b94-113">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13b94-113">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
