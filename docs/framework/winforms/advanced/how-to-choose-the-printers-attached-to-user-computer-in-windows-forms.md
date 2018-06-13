---
title: 'Porady: wybieranie drukarek podłączonych do użytkownika&#39;s komputera w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 5f54a74dc8118d2ebcb2df7e91f229c1807b0297
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522711"
---
# <a name="how-to-choose-the-printers-attached-to-a-user39s-computer-in-windows-forms"></a>Porady: wybieranie drukarek podłączonych do użytkownika&#39;s komputera w formularzach systemu Windows
Często użytkownicy chcą wybierz drukarkę innego niż drukarki domyślnej do drukowania. Można udostępnić użytkownikom wybór drukarek spośród aktualnie zainstalowane za pomocą <xref:System.Windows.Forms.PrintDialog> składnika. Za pomocą <xref:System.Windows.Forms.PrintDialog> składnika <xref:System.Windows.Forms.DialogResult> z <xref:System.Windows.Forms.PrintDialog> składnika zostaną zebrane i umożliwia wybranie drukarki.  
  
 W poniższej procedurze plik tekstowy został wybrany do wydrukowania do drukarki domyślnej. <xref:System.Windows.Forms.PrintDialog> Następnie utworzyć wystąpienia klasy.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Wybierz drukarkę i następnie drukowania pliku  
  
1.  Wybierz urządzenie, które można użyć przy użyciu <xref:System.Windows.Forms.PrintDialog> składnika.  
  
     W poniższym przykładzie kodu istnieją dwa zdarzenia obsługiwane. W pierwszym <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Click> zdarzenia <xref:System.Windows.Forms.PrintDialog> tworzenia wystąpienia klasy i drukarki wybrane przez użytkownika są przechwytywane w <xref:System.Windows.Forms.DialogResult> właściwości.  
  
     W drugim przypadku <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie <xref:System.Drawing.Printing.PrintDocument> przykładowy dokument jest wydrukowany na drukarce określony składnik.  
  
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
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa drukowania w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
