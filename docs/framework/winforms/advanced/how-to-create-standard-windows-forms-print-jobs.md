---
title: 'Instrukcje: Tworzenie standardowych zadań drukowania formularzy systemu Windows'
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
ms.openlocfilehash: 44673e6b26f088e71813aaac26c4b9a03429597a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938239"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Instrukcje: Tworzenie standardowych zadań drukowania formularzy systemu Windows
Podstawą drukowania w Windows Forms jest <xref:System.Drawing.Printing.PrintDocument> składnik — dokładniej <xref:System.Drawing.Printing.PrintDocument.PrintPage> , zdarzenie. Pisząc kod, aby obsłużyć <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie, możesz określić, co ma być drukowane i jak drukować.  
  
### <a name="to-create-a-print-job"></a>Aby utworzyć zadanie drukowania  
  
1. <xref:System.Drawing.Printing.PrintDocument> Dodaj składnik do formularza.  
  
2. Napisz kod, aby obsłużyć <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie.  
  
     Konieczne będzie zakodowanie własnej logiki drukowania. Ponadto trzeba będzie określić materiał do wydrukowania.  
  
     W poniższym przykładzie kodu Przykładowa grafika w kształcie czerwonego prostokąta jest tworzona w programie <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzeń, aby można było wydrukować materiał.  
  
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
  
     Możesz również napisać kod dla <xref:System.Drawing.Printing.PrintDocument.BeginPrint> zdarzeń i <xref:System.Drawing.Printing.PrintDocument.EndPrint> , na przykład liczbę całkowitą reprezentującą łączną liczbę stron do drukowania, która jest zmniejszana w miarę drukowania każdej strony.  
  
    > [!NOTE]
    > Możesz dodać <xref:System.Windows.Forms.PrintDialog> składnik do formularza, aby zapewnić użytkownikom czysty i wydajny interfejs użytkownika. <xref:System.Windows.Forms.PrintDialog.Document%2A> Ustawienie właściwości <xref:System.Windows.Forms.PrintDialog> składnika umożliwia ustawianie właściwości związanych z dokumentem drukowania, z którym pracujesz w formularzu. Aby uzyskać więcej informacji na <xref:System.Windows.Forms.PrintDialog> temat składnika, zobacz [składnik PrintDialog](../controls/printdialog-component-windows-forms.md).  
  
     Aby uzyskać więcej informacji na temat określonych Windows Forms zadań drukowania, w tym jak utworzyć zadanie drukowania programowo, zobacz <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Printing.PrintDocument>
- [Obsługa drukowania w formularzach Windows Forms](windows-forms-print-support.md)
