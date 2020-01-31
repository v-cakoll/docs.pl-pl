---
title: Tworzenie standardowych zadań drukowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
ms.openlocfilehash: 4850dc901630179cc44fefda7e25bbabcfb4725f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741519"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Porady: tworzenie standardowych zadań drukowania formularzy systemu Windows
Podstawą drukowania w Windows Forms jest składnik <xref:System.Drawing.Printing.PrintDocument> — dokładniej, <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie. Pisząc kod obsługujący zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage>, możesz określić, co ma być drukowane i jak drukować.  
  
### <a name="to-create-a-print-job"></a>Aby utworzyć zadanie drukowania  
  
1. Dodaj składnik <xref:System.Drawing.Printing.PrintDocument> do formularza.  
  
2. Napisz kod, aby obsłużyć zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  
  
     Konieczne będzie zakodowanie własnej logiki drukowania. Ponadto trzeba będzie określić materiał do wydrukowania.  
  
     W poniższym przykładzie kodu Przykładowa grafika w kształcie czerwonego prostokąta jest tworzona w programie obsługi zdarzeń <xref:System.Drawing.Printing.PrintDocument.PrintPage>, aby działać jako materiał do wydrukowania.  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
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
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     Warto również napisać kod dla <xref:System.Drawing.Printing.PrintDocument.BeginPrint> i zdarzeń <xref:System.Drawing.Printing.PrintDocument.EndPrint>, na przykład liczbę całkowitą reprezentującą łączną liczbę stron do drukowania, która jest zmniejszana w miarę drukowania każdej strony.  
  
    > [!NOTE]
    > Do formularza można dodać składnik <xref:System.Windows.Forms.PrintDialog>, aby zapewnić użytkownikom czysty i wydajny interfejs użytkownika. Ustawienie właściwości <xref:System.Windows.Forms.PrintDialog.Document%2A> składnika <xref:System.Windows.Forms.PrintDialog> umożliwia ustawianie właściwości związanych z dokumentem drukowania, z którym pracujesz w formularzu. Aby uzyskać więcej informacji na temat składnika <xref:System.Windows.Forms.PrintDialog>, zobacz [składnik PrintDialog](../controls/printdialog-component-windows-forms.md).  
  
     Aby uzyskać więcej informacji na temat określonych Windows Forms zadań drukowania, w tym w celu programistycznego tworzenia zadania drukowania, zobacz <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Printing.PrintDocument>
- [Obsługa drukowania w formularzach Windows Forms](windows-forms-print-support.md)
