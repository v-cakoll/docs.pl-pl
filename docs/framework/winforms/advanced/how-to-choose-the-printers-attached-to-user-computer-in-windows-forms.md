---
title: 'Jak: Wybierz drukarki podłączone do komputera użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 2afbccd02ef42a78d5eac1a01841516fca27c92e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182611"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a>Porady: wybieranie w formularzach systemu Windows drukarek podłączonych do komputera użytkownika
Często użytkownicy chcą wybrać drukarkę inną niż drukarka domyślna do wydrukowania. Można umożliwić użytkownikom wybranie drukarki spośród aktualnie zainstalowanych przy użyciu składnika. <xref:System.Windows.Forms.PrintDialog> Za <xref:System.Windows.Forms.PrintDialog> pośrednictwem komponentu <xref:System.Windows.Forms.DialogResult> <xref:System.Windows.Forms.PrintDialog> komponent jest przechwytywany i używany do wybierania drukarki.  
  
 W poniższej procedurze zostanie wybrany plik tekstowy do wydrukowania na drukarce domyślnej. Następnie <xref:System.Windows.Forms.PrintDialog> zostanie szesnasty.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Aby wybrać drukarkę, a następnie wydrukować plik  
  
1. Wybierz drukarkę, która <xref:System.Windows.Forms.PrintDialog> ma być używana przy użyciu komponentu.  
  
     W poniższym przykładzie kodu są obsługiwane dwa zdarzenia. W <xref:System.Windows.Forms.Button> pierwszym <xref:System.Windows.Forms.Control.Click> zdarzeniem <xref:System.Windows.Forms.PrintDialog> formantu, klasa jest tworzone, a drukarka wybrana przez <xref:System.Windows.Forms.DialogResult> użytkownika jest przechwytywany we właściwości.  
  
     W drugim <xref:System.Drawing.Printing.PrintDocument.PrintPage> przypadku, zdarzenie <xref:System.Drawing.Printing.PrintDocument> składnika, przykładowy dokument jest drukowany na drukarce określonej.  
  
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
  
     (Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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

- [Obsługa drukowania w formularzach systemu Windows](windows-forms-print-support.md)
