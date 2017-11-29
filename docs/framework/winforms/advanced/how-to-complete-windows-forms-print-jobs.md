---
title: "Porady: kończenie zadań drukowania formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9decba052589bfcc3ecd7b2861dad51e9c51378a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Porady: kończenie zadań drukowania formularzy systemu Windows
Często edytory i inne aplikacje, które obejmują drukowanie zapewni opcję wyświetlania wiadomości do użytkowników o ukończeniu zadania drukowania. Możesz podać tę funkcję w formularzach systemu Windows, obsługa <xref:System.Drawing.Printing.PrintDocument.EndPrint> zdarzenie <xref:System.Drawing.Printing.PrintDocument> składnika.  
  
 Poniższa procedura wymaga, że utworzono aplikację systemu Windows z <xref:System.Drawing.Printing.PrintDocument> składnik go, co jest standardowy sposób włączania drukowanie z aplikacji opartych na systemie Windows. Aby uzyskać więcej informacji na temat drukowania z formularzy systemu Windows przy użyciu <xref:System.Drawing.Printing.PrintDocument> składników, zobacz [porady: tworzenie standardowych systemu Windows Forms zadania drukowania](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).  
  
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
  
2.  Napisać kod obsługujący <xref:System.Drawing.Printing.PrintDocument.EndPrint> zdarzeń.  
  
     W poniższym przykładzie kodu zostanie wyświetlone okno komunikatu, wskazujący, że zakończono drukowanie dokumentu.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
 <xref:System.Drawing.Printing.PrintDocument>  
 [Obsługa drukowania w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
