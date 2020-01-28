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
ms.openlocfilehash: b8ef4fa05b2107247181e82b72389f9503507135
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746491"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Porady: kończenie zadań drukowania formularzy systemu Windows
Często procesory tekstów i inne aplikacje, które obejmują drukowanie, udostępniają opcję wyświetlania komunikatu dla użytkowników, że zadanie drukowania zostało ukończone. Tę funkcję można podać w Windows Forms przez obsługę zdarzenia <xref:System.Drawing.Printing.PrintDocument.EndPrint> składnika <xref:System.Drawing.Printing.PrintDocument>.  
  
 Poniższa procedura wymaga utworzenia aplikacji opartej na systemie Windows ze składnikiem <xref:System.Drawing.Printing.PrintDocument> na tym komputerze, który jest standardowym sposobem włączania drukowania z aplikacji opartej na systemie Windows. Aby uzyskać więcej informacji o drukowaniu z Windows Forms przy użyciu składnika <xref:System.Drawing.Printing.PrintDocument>, zobacz [How to: Create Standard Windows Forms Job Jobs](how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>Aby ukończyć zadanie drukowania  
  
1. Ustaw właściwość <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> składnika <xref:System.Drawing.Printing.PrintDocument>.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. Napisz kod, aby obsłużyć zdarzenie <xref:System.Drawing.Printing.PrintDocument.EndPrint>.  
  
     W poniższym przykładzie kodu zostanie wyświetlone okno komunikatu z informacją, że dokument zakończył drukowanie.  
  
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
  
     (Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
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
- [Obsługa drukowania w formularzach Windows Forms](windows-forms-print-support.md)
