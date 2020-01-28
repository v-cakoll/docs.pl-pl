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
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a>Porady: wybieranie w formularzach systemu Windows drukarek podłączonych do komputera użytkownika
Często użytkownicy chcą wybrać drukarkę inną niż domyślna drukarki do drukowania. Można umożliwić użytkownikom wybranie drukarki spośród zainstalowanych obecnie przy użyciu składnika <xref:System.Windows.Forms.PrintDialog>. Za pomocą składnika <xref:System.Windows.Forms.PrintDialog>, <xref:System.Windows.Forms.DialogResult> składnik <xref:System.Windows.Forms.PrintDialog> jest przechwytywany i używany do wybierania drukarki.  
  
 W poniższej procedurze jest wybrany plik tekstowy do wydrukowania na drukarce domyślnej. Następnie zostanie utworzona instancja klasy <xref:System.Windows.Forms.PrintDialog>.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Aby wybrać drukarkę, a następnie wydrukować plik  
  
1. Wybierz drukarkę, która ma być używana przy użyciu składnika <xref:System.Windows.Forms.PrintDialog>.  
  
     W poniższym przykładzie kodu są obsługiwane dwa zdarzenia. W pierwszym zdarzeniu <xref:System.Windows.Forms.Control.Click> kontrolce <xref:System.Windows.Forms.Button> jest tworzona Klasa <xref:System.Windows.Forms.PrintDialog>, a drukarka wybrana przez użytkownika jest przechwytywana we właściwości <xref:System.Windows.Forms.DialogResult>.  
  
     W drugim zdarzeniu <xref:System.Drawing.Printing.PrintDocument.PrintPage>m zdarzeniu składnika <xref:System.Drawing.Printing.PrintDocument> zostanie wydrukowany przykładowy dokument do określonej drukarki.  
  
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
  
     (Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
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
