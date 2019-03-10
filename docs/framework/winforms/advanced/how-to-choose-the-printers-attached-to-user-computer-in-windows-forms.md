---
title: 'Instrukcje: Wybieranie drukarek podłączonych do komputera użytkownika w formularzach Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 8c29a90cf4aa7380297cc2776123fb353b07d8c5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702740"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a><span data-ttu-id="5cf6b-102">Instrukcje: Wybieranie drukarek podłączonych do komputera użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cf6b-102">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>
<span data-ttu-id="5cf6b-103">Często chcą wybierz drukarek innych niż drukarki domyślnej wydrukowany do użytkowników.</span><span class="sxs-lookup"><span data-stu-id="5cf6b-103">Often, users want to choose a printer other than the default printer to print to.</span></span> <span data-ttu-id="5cf6b-104">Można udostępnić użytkownikom wybór drukarek spośród aktualnie zainstalowane za pomocą <xref:System.Windows.Forms.PrintDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="5cf6b-104">You can enable users to choose a printer from among those currently installed by using the <xref:System.Windows.Forms.PrintDialog> component.</span></span> <span data-ttu-id="5cf6b-105">Za pomocą <xref:System.Windows.Forms.PrintDialog> składnika <xref:System.Windows.Forms.DialogResult> z <xref:System.Windows.Forms.PrintDialog> składnik jest przechwytywane i umożliwia wybranie drukarki.</span><span class="sxs-lookup"><span data-stu-id="5cf6b-105">Through the <xref:System.Windows.Forms.PrintDialog> component, the <xref:System.Windows.Forms.DialogResult> of the <xref:System.Windows.Forms.PrintDialog> component is captured and used to select the printer.</span></span>  
  
 <span data-ttu-id="5cf6b-106">W poniższej procedurze wybrano plik tekstowy, ma zostać wydrukowany zostanie użyta drukarka domyślna.</span><span class="sxs-lookup"><span data-stu-id="5cf6b-106">In the following procedure, a text file is selected to be printed to the default printer.</span></span> <span data-ttu-id="5cf6b-107"><xref:System.Windows.Forms.PrintDialog> Następnie utworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="5cf6b-107">The <xref:System.Windows.Forms.PrintDialog> class is then instantiated.</span></span>  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a><span data-ttu-id="5cf6b-108">Aby wybrać drukarkę, a następnie wydrukować plik</span><span class="sxs-lookup"><span data-stu-id="5cf6b-108">To choose a printer and then print a file</span></span>  
  
1.  <span data-ttu-id="5cf6b-109">Wybierz urządzenie, które można użyć za pomocą <xref:System.Windows.Forms.PrintDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="5cf6b-109">Select the printer to be used using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
     <span data-ttu-id="5cf6b-110">W poniższym przykładzie kodu istnieją dwa zdarzenia, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5cf6b-110">In the following code example, there are two events being handled.</span></span> <span data-ttu-id="5cf6b-111">W pierwszym <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> zdarzenia <xref:System.Windows.Forms.PrintDialog> tworzenia wystąpienia klasy i drukarki wybrane przez użytkownika są przechwytywane w <xref:System.Windows.Forms.DialogResult> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5cf6b-111">In the first, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event, the <xref:System.Windows.Forms.PrintDialog> class is instantiated and the printer selected by the user is captured in the <xref:System.Windows.Forms.DialogResult> property.</span></span>  
  
     <span data-ttu-id="5cf6b-112">W drugim przypadku <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenia <xref:System.Drawing.Printing.PrintDocument> przykładowy dokument drukowania na drukarce określony składnik.</span><span class="sxs-lookup"><span data-stu-id="5cf6b-112">In the second event, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event of the <xref:System.Drawing.Printing.PrintDocument> component, a sample document is printed to the printer specified.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If   
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))          
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =   
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="5cf6b-113">(Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5cf6b-113">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5cf6b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cf6b-114">See also</span></span>
- [<span data-ttu-id="5cf6b-115">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cf6b-115">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
