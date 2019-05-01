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
ms.openlocfilehash: 816da93218e20f73f16c14769ed1a549dd3d8eb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937660"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="3491c-102">Instrukcje: Tworzenie standardowych zadań drukowania formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3491c-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="3491c-103">Jest podstawą drukowanie w formularzach Windows Forms <xref:System.Drawing.Printing.PrintDocument> składnika — w szczególności <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3491c-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="3491c-104">Pisanie kodu do obsługi <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenia, można określić wydruku i jak go wydrukować.</span><span class="sxs-lookup"><span data-stu-id="3491c-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="3491c-105">Aby utworzyć zadanie drukowania</span><span class="sxs-lookup"><span data-stu-id="3491c-105">To create a print job</span></span>  
  
1. <span data-ttu-id="3491c-106">Dodaj <xref:System.Drawing.Printing.PrintDocument> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="3491c-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="3491c-107">Napisz kod obsługujący <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3491c-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="3491c-108">Trzeba będzie drukowania logikę kodu.</span><span class="sxs-lookup"><span data-stu-id="3491c-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="3491c-109">Ponadto należy określić materiału, który ma zostać wydrukowany.</span><span class="sxs-lookup"><span data-stu-id="3491c-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="3491c-110">W poniższym przykładzie kodu przykładowej grafiki w kształcie prostokąta czerwony jest tworzony w <xref:System.Drawing.Printing.PrintDocument.PrintPage> programu obsługi zdarzeń do działania jako materiałów, które ma zostać wydrukowany.</span><span class="sxs-lookup"><span data-stu-id="3491c-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="3491c-111">(Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3491c-111">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="3491c-112">Możesz również chcieć napisać kod dla <xref:System.Drawing.Printing.PrintDocument.BeginPrint> i <xref:System.Drawing.Printing.PrintDocument.EndPrint> zdarzenia, w tym może być liczbą całkowitą reprezentującą łączna liczba stron do wydrukowania wraz z przydzielaniem zgodnie z każdej strony wyświetli.</span><span class="sxs-lookup"><span data-stu-id="3491c-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3491c-113">Możesz dodać <xref:System.Windows.Forms.PrintDialog> składnika do formularza umożliwiającego użytkownikom udostępniać interfejs czyste i wydajne użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="3491c-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="3491c-114">Ustawienie <xref:System.Windows.Forms.PrintDialog.Document%2A> właściwość <xref:System.Windows.Forms.PrintDialog> składnika umożliwia ustawienie właściwości powiązanych z print dokumentu pracujesz w formularzu.</span><span class="sxs-lookup"><span data-stu-id="3491c-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="3491c-115">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.PrintDialog> składników, zobacz [składnika PrintDialog](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3491c-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="3491c-116">Aby uzyskać więcej informacji o specyfice formularzy Windows Forms zadania drukowania, w tym jak utworzyć zadanie drukowania programowo, zobacz <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="3491c-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3491c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3491c-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="3491c-118">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3491c-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
