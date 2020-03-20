---
title: Ukończ zadania drukowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 62f67002bfbaf46e73bae06fdaff26efde865c06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182598"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Porady: kończenie zadań drukowania formularzy systemu Windows
Często edytory tekstu i inne aplikacje, które wymagają drukowania, umożliwiają wyświetlenie użytkownikom komunikatu o zakończeniu zadania drukowania. Tę funkcję można udostępnić w formularzach <xref:System.Drawing.Printing.PrintDocument.EndPrint> systemu <xref:System.Drawing.Printing.PrintDocument> Windows, obsługując zdarzenie składnika.  
  
 Poniższa procedura wymaga utworzenia aplikacji opartej <xref:System.Drawing.Printing.PrintDocument> na systemie Windows ze składnikiem, który jest standardowym sposobem włączania drukowania z aplikacji opartej na systemie Windows. Aby uzyskać więcej informacji na <xref:System.Drawing.Printing.PrintDocument> temat drukowania z formularzy systemu Windows przy użyciu tego składnika, zobacz [Jak: Tworzenie standardowych zadań drukowania formularzy systemu Windows](how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>Aby wykonać zadanie drukowania  
  
1. Ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> właściwość <xref:System.Drawing.Printing.PrintDocument> komponentu.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. Napisz kod do <xref:System.Drawing.Printing.PrintDocument.EndPrint> obsługi zdarzenia.  
  
     W poniższym przykładzie kodu jest wyświetlany komunikat informujący, że dokument zakończył drukowanie.  
  
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
  
     (Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Drawing.Printing.PrintDocument>
- [Obsługa drukowania w formularzach systemu Windows](windows-forms-print-support.md)
