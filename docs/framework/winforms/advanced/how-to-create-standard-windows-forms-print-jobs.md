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
ms.openlocfilehash: 816da93218e20f73f16c14769ed1a549dd3d8eb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937660"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Instrukcje: Tworzenie standardowych zadań drukowania formularzy systemu Windows
Jest podstawą drukowanie w formularzach Windows Forms <xref:System.Drawing.Printing.PrintDocument> składnika — w szczególności <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń. Pisanie kodu do obsługi <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenia, można określić wydruku i jak go wydrukować.  
  
### <a name="to-create-a-print-job"></a>Aby utworzyć zadanie drukowania  
  
1. Dodaj <xref:System.Drawing.Printing.PrintDocument> składnika do formularza.  
  
2. Napisz kod obsługujący <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń.  
  
     Trzeba będzie drukowania logikę kodu. Ponadto należy określić materiału, który ma zostać wydrukowany.  
  
     W poniższym przykładzie kodu przykładowej grafiki w kształcie prostokąta czerwony jest tworzony w <xref:System.Drawing.Printing.PrintDocument.PrintPage> programu obsługi zdarzeń do działania jako materiałów, które ma zostać wydrukowany.  
  
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
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
     Możesz również chcieć napisać kod dla <xref:System.Drawing.Printing.PrintDocument.BeginPrint> i <xref:System.Drawing.Printing.PrintDocument.EndPrint> zdarzenia, w tym może być liczbą całkowitą reprezentującą łączna liczba stron do wydrukowania wraz z przydzielaniem zgodnie z każdej strony wyświetli.  
  
    > [!NOTE]
    >  Możesz dodać <xref:System.Windows.Forms.PrintDialog> składnika do formularza umożliwiającego użytkownikom udostępniać interfejs czyste i wydajne użytkownika (UI). Ustawienie <xref:System.Windows.Forms.PrintDialog.Document%2A> właściwość <xref:System.Windows.Forms.PrintDialog> składnika umożliwia ustawienie właściwości powiązanych z print dokumentu pracujesz w formularzu. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.PrintDialog> składników, zobacz [składnika PrintDialog](../controls/printdialog-component-windows-forms.md).  
  
     Aby uzyskać więcej informacji o specyfice formularzy Windows Forms zadania drukowania, w tym jak utworzyć zadanie drukowania programowo, zobacz <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Printing.PrintDocument>
- [Obsługa drukowania w formularzach Windows Forms](windows-forms-print-support.md)
