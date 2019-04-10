---
title: 'Instrukcje: Drukowanie grafiki w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 55459482d0994c581164128b17c08a7ca90d0717
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339102"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Instrukcje: Drukowanie grafiki w formularzach systemu Windows
Często mają drukowanie grafiki w aplikacji z systemem Windows. <xref:System.Drawing.Graphics> Klasa dostarcza metody do Rysowanie obiektów na urządzeniu, takie jak ekranu lub drukarki.  
  
### <a name="to-print-graphics"></a>Aby wydrukować grafiki  
  
1. Dodaj <xref:System.Drawing.Printing.PrintDocument> składnika do formularza.  
  
2. W <xref:System.Drawing.Printing.PrintDocument.PrintPage> programu obsługi zdarzeń, użyj <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy, aby nakazać drukarki na jakiego rodzaju grafiki do drukowania.  
  
     Poniższy przykład kodu pokazuje użyty do utworzenia niebieska elipsę w ramach prostokąt otaczający program obsługi zdarzeń. Prostokąt ma następujące lokalizacji i wymiarów: począwszy od 100, 150, za pomocą 250 wysokość i szerokość 250.  
  
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
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Obsługa drukowania w formularzach systemu Windows](windows-forms-print-support.md)
