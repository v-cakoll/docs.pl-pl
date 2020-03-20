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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182565"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Porady: tworzenie standardowych zadań drukowania formularzy systemu Windows
Podstawą drukowania w formularzach <xref:System.Drawing.Printing.PrintDocument> systemu Windows jest <xref:System.Drawing.Printing.PrintDocument.PrintPage> składnik — a dokładniej zdarzenie. Pisząc kod do <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzenia, można określić, co ma być drukowane i jak go wydrukować.  
  
### <a name="to-create-a-print-job"></a>Aby utworzyć zadanie drukowania  
  
1. Dodaj <xref:System.Drawing.Printing.PrintDocument> składnik do formularza.  
  
2. Napisz kod do <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzenia.  
  
     Będziesz musiał zakodować własną logikę drukowania. Ponadto należy określić materiał do wydrukowania.  
  
     W poniższym przykładzie kodu przykładowa grafika w kształcie czerwonego prostokąta jest tworzona w programie obsługi <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń, aby działać jako materiał do wydrukowania.  
  
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
  
     (Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
     Można również napisać kod <xref:System.Drawing.Printing.PrintDocument.BeginPrint> dla <xref:System.Drawing.Printing.PrintDocument.EndPrint> zdarzeń i, być może w tym liczby całkowitej reprezentującej całkowitą liczbę stron do wydrukowania, która jest zmniejszana podczas drukowania każdej strony.  
  
    > [!NOTE]
    > Można dodać <xref:System.Windows.Forms.PrintDialog> składnik do formularza, aby zapewnić użytkownikom czysty i wydajny interfejs użytkownika. Ustawienie <xref:System.Windows.Forms.PrintDialog.Document%2A> właściwości składnika <xref:System.Windows.Forms.PrintDialog> umożliwia ustawienie właściwości związanych z dokumentem drukowania, z którymi pracujesz nad formularzem. Aby uzyskać więcej <xref:System.Windows.Forms.PrintDialog> informacji na temat składnika, zobacz [PrintDialog Component](../controls/printdialog-component-windows-forms.md).  
  
     Aby uzyskać więcej informacji na temat specyfiki zadań drukowania formularzy systemu <xref:System.Drawing.Printing.PrintPageEventArgs>Windows, w tym sposobu programowania tworzenia zadania drukowania, zobacz .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Drawing.Printing.PrintDocument>
- [Obsługa drukowania w formularzach systemu Windows](windows-forms-print-support.md)
