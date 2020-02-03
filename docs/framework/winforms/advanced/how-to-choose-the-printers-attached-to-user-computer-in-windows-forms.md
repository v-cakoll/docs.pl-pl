---
title: 'Instrukcje: wybieranie drukarek podłączonych do komputera użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 7fc2427468540ac0a1480f6140cbb34c3a0f1ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746514"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a><span data-ttu-id="a9aff-102">Porady: wybieranie w formularzach systemu Windows drukarek podłączonych do komputera użytkownika</span><span class="sxs-lookup"><span data-stu-id="a9aff-102">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>
<span data-ttu-id="a9aff-103">Często użytkownicy chcą wybrać drukarkę inną niż domyślna drukarki do drukowania.</span><span class="sxs-lookup"><span data-stu-id="a9aff-103">Often, users want to choose a printer other than the default printer to print to.</span></span> <span data-ttu-id="a9aff-104">Można umożliwić użytkownikom wybranie drukarki spośród zainstalowanych obecnie przy użyciu składnika <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="a9aff-104">You can enable users to choose a printer from among those currently installed by using the <xref:System.Windows.Forms.PrintDialog> component.</span></span> <span data-ttu-id="a9aff-105">Za pomocą składnika <xref:System.Windows.Forms.PrintDialog>, <xref:System.Windows.Forms.DialogResult> składnik <xref:System.Windows.Forms.PrintDialog> jest przechwytywany i używany do wybierania drukarki.</span><span class="sxs-lookup"><span data-stu-id="a9aff-105">Through the <xref:System.Windows.Forms.PrintDialog> component, the <xref:System.Windows.Forms.DialogResult> of the <xref:System.Windows.Forms.PrintDialog> component is captured and used to select the printer.</span></span>  
  
 <span data-ttu-id="a9aff-106">W poniższej procedurze jest wybrany plik tekstowy do wydrukowania na drukarce domyślnej.</span><span class="sxs-lookup"><span data-stu-id="a9aff-106">In the following procedure, a text file is selected to be printed to the default printer.</span></span> <span data-ttu-id="a9aff-107">Następnie zostanie utworzona instancja klasy <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="a9aff-107">The <xref:System.Windows.Forms.PrintDialog> class is then instantiated.</span></span>  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a><span data-ttu-id="a9aff-108">Aby wybrać drukarkę, a następnie wydrukować plik</span><span class="sxs-lookup"><span data-stu-id="a9aff-108">To choose a printer and then print a file</span></span>  
  
1. <span data-ttu-id="a9aff-109">Wybierz drukarkę, która ma być używana przy użyciu składnika <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="a9aff-109">Select the printer to be used using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
     <span data-ttu-id="a9aff-110">W poniższym przykładzie kodu są obsługiwane dwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a9aff-110">In the following code example, there are two events being handled.</span></span> <span data-ttu-id="a9aff-111">W pierwszym zdarzeniu <xref:System.Windows.Forms.Control.Click> kontrolce <xref:System.Windows.Forms.Button> jest tworzona Klasa <xref:System.Windows.Forms.PrintDialog>, a drukarka wybrana przez użytkownika jest przechwytywana we właściwości <xref:System.Windows.Forms.DialogResult>.</span><span class="sxs-lookup"><span data-stu-id="a9aff-111">In the first, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event, the <xref:System.Windows.Forms.PrintDialog> class is instantiated and the printer selected by the user is captured in the <xref:System.Windows.Forms.DialogResult> property.</span></span>  
  
     <span data-ttu-id="a9aff-112">W drugim zdarzeniu <xref:System.Drawing.Printing.PrintDocument.PrintPage>m zdarzeniu składnika <xref:System.Drawing.Printing.PrintDocument> zostanie wydrukowany przykładowy dokument do określonej drukarki.</span><span class="sxs-lookup"><span data-stu-id="a9aff-112">In the second event, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event of the <xref:System.Drawing.Printing.PrintDocument> component, a sample document is printed to the printer specified.</span></span>  
  
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
  
     <span data-ttu-id="a9aff-113">(Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a9aff-113">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a9aff-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9aff-114">See also</span></span>

- [<span data-ttu-id="a9aff-115">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9aff-115">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
