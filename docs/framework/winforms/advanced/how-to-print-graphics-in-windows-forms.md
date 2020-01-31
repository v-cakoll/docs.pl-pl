---
title: 'Instrukcje: Drukowanie grafiki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 2435b3bc14747a00d2a0fc03a9ebd21ae43c5369
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740643"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Porady: drukowanie grafiki w formularzach systemu Windows
Często chcesz wydrukować grafikę w aplikacji opartej na systemie Windows. Klasa <xref:System.Drawing.Graphics> zapewnia metody rysowania obiektów na urządzeniu, takie jak ekran lub drukarka.  
  
### <a name="to-print-graphics"></a>Aby wydrukować grafikę  
  
1. Dodaj składnik <xref:System.Drawing.Printing.PrintDocument> do formularza.  
  
2. W obsłudze zdarzeń <xref:System.Drawing.Printing.PrintDocument.PrintPage> Użyj właściwości <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> klasy <xref:System.Drawing.Printing.PrintPageEventArgs>, aby poinstruować drukarkę, jakiego rodzaju grafika ma drukować.  
  
     Poniższy przykład kodu pokazuje procedurę obsługi zdarzeń użytą do utworzenia niebieską elipsę w obrębie prostokąta ograniczenia. Prostokąt ma następującą lokalizację i wymiary: od 100 do 150 z szerokością 250 i wysokością 250.  
  
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
  
     (Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
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
- [Obsługa drukowania w formularzach Windows Forms](windows-forms-print-support.md)
