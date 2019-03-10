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
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a>Instrukcje: Wybieranie drukarek podłączonych do komputera użytkownika w formularzach Windows Forms
Często chcą wybierz drukarek innych niż drukarki domyślnej wydrukowany do użytkowników. Można udostępnić użytkownikom wybór drukarek spośród aktualnie zainstalowane za pomocą <xref:System.Windows.Forms.PrintDialog> składnika. Za pomocą <xref:System.Windows.Forms.PrintDialog> składnika <xref:System.Windows.Forms.DialogResult> z <xref:System.Windows.Forms.PrintDialog> składnik jest przechwytywane i umożliwia wybranie drukarki.  
  
 W poniższej procedurze wybrano plik tekstowy, ma zostać wydrukowany zostanie użyta drukarka domyślna. <xref:System.Windows.Forms.PrintDialog> Następnie utworzyć wystąpienia klasy.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Aby wybrać drukarkę, a następnie wydrukować plik  
  
1.  Wybierz urządzenie, które można użyć za pomocą <xref:System.Windows.Forms.PrintDialog> składnika.  
  
     W poniższym przykładzie kodu istnieją dwa zdarzenia, które są obsługiwane. W pierwszym <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> zdarzenia <xref:System.Windows.Forms.PrintDialog> tworzenia wystąpienia klasy i drukarki wybrane przez użytkownika są przechwytywane w <xref:System.Windows.Forms.DialogResult> właściwości.  
  
     W drugim przypadku <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenia <xref:System.Drawing.Printing.PrintDocument> przykładowy dokument drukowania na drukarce określony składnik.  
  
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
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Obsługa drukowania w formularzach Windows Forms](windows-forms-print-support.md)
