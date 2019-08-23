---
title: 'Instrukcje: Tworzenie standardowych zadań drukowania formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
ms.openlocfilehash: 44673e6b26f088e71813aaac26c4b9a03429597a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938239"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="bb5b0-102">Instrukcje: Tworzenie standardowych zadań drukowania formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bb5b0-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="bb5b0-103">Podstawą drukowania w Windows Forms jest <xref:System.Drawing.Printing.PrintDocument> składnik — dokładniej <xref:System.Drawing.Printing.PrintDocument.PrintPage> , zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="bb5b0-104">Pisząc kod, aby obsłużyć <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie, możesz określić, co ma być drukowane i jak drukować.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="bb5b0-105">Aby utworzyć zadanie drukowania</span><span class="sxs-lookup"><span data-stu-id="bb5b0-105">To create a print job</span></span>  
  
1. <span data-ttu-id="bb5b0-106"><xref:System.Drawing.Printing.PrintDocument> Dodaj składnik do formularza.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="bb5b0-107">Napisz kod, aby obsłużyć <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="bb5b0-108">Konieczne będzie zakodowanie własnej logiki drukowania.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="bb5b0-109">Ponadto trzeba będzie określić materiał do wydrukowania.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="bb5b0-110">W poniższym przykładzie kodu Przykładowa grafika w kształcie czerwonego prostokąta jest tworzona w programie <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzeń, aby można było wydrukować materiał.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="bb5b0-111">(Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     <span data-ttu-id="bb5b0-112">Możesz również napisać kod dla <xref:System.Drawing.Printing.PrintDocument.BeginPrint> zdarzeń i <xref:System.Drawing.Printing.PrintDocument.EndPrint> , na przykład liczbę całkowitą reprezentującą łączną liczbę stron do drukowania, która jest zmniejszana w miarę drukowania każdej strony.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bb5b0-113">Możesz dodać <xref:System.Windows.Forms.PrintDialog> składnik do formularza, aby zapewnić użytkownikom czysty i wydajny interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="bb5b0-114"><xref:System.Windows.Forms.PrintDialog.Document%2A> Ustawienie właściwości <xref:System.Windows.Forms.PrintDialog> składnika umożliwia ustawianie właściwości związanych z dokumentem drukowania, z którym pracujesz w formularzu.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="bb5b0-115">Aby uzyskać więcej informacji na <xref:System.Windows.Forms.PrintDialog> temat składnika, zobacz [składnik PrintDialog](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="bb5b0-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="bb5b0-116">Aby uzyskać więcej informacji na temat określonych Windows Forms zadań drukowania, w tym jak utworzyć zadanie drukowania programowo, zobacz <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5b0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb5b0-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="bb5b0-118">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb5b0-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
