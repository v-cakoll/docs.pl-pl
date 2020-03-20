---
title: 'Jak: Drukowanie grafiki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 15f3a507839430ce058302e7f5abd317ef84626f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182536"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Porady: drukowanie grafiki w formularzach systemu Windows
Często należy drukować grafiki w aplikacji systemu Windows. Klasa <xref:System.Drawing.Graphics> udostępnia metody rysowania obiektów do urządzenia, takich jak ekran lub drukarka.  
  
### <a name="to-print-graphics"></a>Aby wydrukować grafikę  
  
1. Dodaj <xref:System.Drawing.Printing.PrintDocument> składnik do formularza.  
  
2. W <xref:System.Drawing.Printing.PrintDocument.PrintPage> programie obsługi zdarzeń <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> użyj <xref:System.Drawing.Printing.PrintPageEventArgs> właściwości klasy, aby poinstruować drukarkę o rodzaju grafiki do wydrukowania.  
  
     Poniższy przykład kodu pokazuje program obsługi zdarzeń używany do tworzenia niebieskiej elipsy w prostokątze ograniczającym. Prostokąt ma następującą lokalizację i wymiary: zaczynając od 100, 150 o szerokości 250 i wysokości 250.  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,
         new Rectangle(100, 150, 250, 250));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     (Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Obsługa drukowania w formularzach systemu Windows](windows-forms-print-support.md)
