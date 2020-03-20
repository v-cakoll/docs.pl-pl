---
title: Tworzenie standardowych zadań drukowania
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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182565"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="a100c-102">Porady: tworzenie standardowych zadań drukowania formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a100c-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="a100c-103">Podstawą drukowania w formularzach <xref:System.Drawing.Printing.PrintDocument> systemu Windows jest <xref:System.Drawing.Printing.PrintDocument.PrintPage> składnik — a dokładniej zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a100c-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="a100c-104">Pisząc kod do <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzenia, można określić, co ma być drukowane i jak go wydrukować.</span><span class="sxs-lookup"><span data-stu-id="a100c-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="a100c-105">Aby utworzyć zadanie drukowania</span><span class="sxs-lookup"><span data-stu-id="a100c-105">To create a print job</span></span>  
  
1. <span data-ttu-id="a100c-106">Dodaj <xref:System.Drawing.Printing.PrintDocument> składnik do formularza.</span><span class="sxs-lookup"><span data-stu-id="a100c-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="a100c-107">Napisz kod do <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a100c-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="a100c-108">Będziesz musiał zakodować własną logikę drukowania.</span><span class="sxs-lookup"><span data-stu-id="a100c-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="a100c-109">Ponadto należy określić materiał do wydrukowania.</span><span class="sxs-lookup"><span data-stu-id="a100c-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="a100c-110">W poniższym przykładzie kodu przykładowa grafika w kształcie czerwonego prostokąta jest tworzona w programie obsługi <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń, aby działać jako materiał do wydrukowania.</span><span class="sxs-lookup"><span data-stu-id="a100c-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="a100c-111">(Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a100c-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="a100c-112">Można również napisać kod <xref:System.Drawing.Printing.PrintDocument.BeginPrint> dla <xref:System.Drawing.Printing.PrintDocument.EndPrint> zdarzeń i, być może w tym liczby całkowitej reprezentującej całkowitą liczbę stron do wydrukowania, która jest zmniejszana podczas drukowania każdej strony.</span><span class="sxs-lookup"><span data-stu-id="a100c-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a100c-113">Można dodać <xref:System.Windows.Forms.PrintDialog> składnik do formularza, aby zapewnić użytkownikom czysty i wydajny interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a100c-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="a100c-114">Ustawienie <xref:System.Windows.Forms.PrintDialog.Document%2A> właściwości składnika <xref:System.Windows.Forms.PrintDialog> umożliwia ustawienie właściwości związanych z dokumentem drukowania, z którymi pracujesz nad formularzem.</span><span class="sxs-lookup"><span data-stu-id="a100c-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="a100c-115">Aby uzyskać więcej <xref:System.Windows.Forms.PrintDialog> informacji na temat składnika, zobacz [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a100c-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="a100c-116">Aby uzyskać więcej informacji na temat specyfiki zadań drukowania formularzy systemu <xref:System.Drawing.Printing.PrintPageEventArgs>Windows, w tym sposobu programowania tworzenia zadania drukowania, zobacz .</span><span class="sxs-lookup"><span data-stu-id="a100c-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a100c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a100c-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="a100c-118">Obsługa drukowania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a100c-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
