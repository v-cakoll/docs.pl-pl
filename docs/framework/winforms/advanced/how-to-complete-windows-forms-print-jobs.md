---
title: 'Instrukcje: Kończenie zadań drukowania formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: f8d0f1f067efbae6e2b667328e75996179b91737
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159825"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Instrukcje: Kończenie zadań drukowania formularzy systemu Windows
Często edytorów tekstów i inne aplikacje, które obejmują drukowanie zapewni opcji, aby wyświetlić komunikat do użytkowników o ukończeniu zadania drukowania. Możesz podać tę funkcję w formularzach Windows, obsługując <xref:System.Drawing.Printing.PrintDocument.EndPrint> zdarzenia <xref:System.Drawing.Printing.PrintDocument> składnika.  
  
 Poniższa procedura wymaga, że utworzono aplikację systemem Windows przy użyciu <xref:System.Drawing.Printing.PrintDocument> składnika na ich temat, który jest standardowy sposób włączania drukowaniem z aplikacji z systemem Windows. Aby uzyskać więcej informacji na temat drukowania z Windows Forms przy użyciu <xref:System.Drawing.Printing.PrintDocument> składników, zobacz [jak: Tworzenie zadań drukowania formularzy Windows Standard](how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>Aby ukończyć zadanie drukowania  
  
1.  Ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> właściwość <xref:System.Drawing.Printing.PrintDocument> składnika.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  Napisz kod obsługujący <xref:System.Drawing.Printing.PrintDocument.EndPrint> zdarzeń.  
  
     W poniższym przykładzie kodu zostanie wyświetlone okno komunikatu, wskazujący, że zakończone drukowania.  
  
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
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Printing.PrintDocument>
- [Obsługa drukowania w formularzach systemu Windows](windows-forms-print-support.md)
