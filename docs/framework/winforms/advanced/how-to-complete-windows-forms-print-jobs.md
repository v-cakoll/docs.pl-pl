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
ms.openlocfilehash: b8ef4fa05b2107247181e82b72389f9503507135
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746491"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="39f3a-102">Porady: kończenie zadań drukowania formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="39f3a-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="39f3a-103">Często procesory tekstów i inne aplikacje, które obejmują drukowanie, udostępniają opcję wyświetlania komunikatu dla użytkowników, że zadanie drukowania zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="39f3a-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="39f3a-104">Tę funkcję można podać w Windows Forms przez obsługę zdarzenia <xref:System.Drawing.Printing.PrintDocument.EndPrint> składnika <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="39f3a-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="39f3a-105">Poniższa procedura wymaga utworzenia aplikacji opartej na systemie Windows ze składnikiem <xref:System.Drawing.Printing.PrintDocument> na tym komputerze, który jest standardowym sposobem włączania drukowania z aplikacji opartej na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="39f3a-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="39f3a-106">Aby uzyskać więcej informacji o drukowaniu z Windows Forms przy użyciu składnika <xref:System.Drawing.Printing.PrintDocument>, zobacz [How to: Create Standard Windows Forms Job Jobs](how-to-create-standard-windows-forms-print-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="39f3a-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="39f3a-107">Aby ukończyć zadanie drukowania</span><span class="sxs-lookup"><span data-stu-id="39f3a-107">To complete a print job</span></span>  
  
1. <span data-ttu-id="39f3a-108">Ustaw właściwość <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> składnika <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="39f3a-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <span data-ttu-id="39f3a-109">Napisz kod, aby obsłużyć zdarzenie <xref:System.Drawing.Printing.PrintDocument.EndPrint>.</span><span class="sxs-lookup"><span data-stu-id="39f3a-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="39f3a-110">W poniższym przykładzie kodu zostanie wyświetlone okno komunikatu z informacją, że dokument zakończył drukowanie.</span><span class="sxs-lookup"><span data-stu-id="39f3a-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
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
  
     <span data-ttu-id="39f3a-111">(Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="39f3a-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39f3a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39f3a-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="39f3a-113">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="39f3a-113">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
