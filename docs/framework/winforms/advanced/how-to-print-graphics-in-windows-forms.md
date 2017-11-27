---
title: 'Porady: drukowanie grafiki w formularzach systemu Windows'
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
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5f495135b3210f430c887451844bec8b154db33c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Porady: drukowanie grafiki w formularzach systemu Windows
Często mają drukowanie grafiki w aplikacji opartych na systemie Windows. <xref:System.Drawing.Graphics> Klasa zawiera metody służące do rysowania obiektów na urządzeniu, na przykład ekranu lub drukarki.  
  
### <a name="to-print-graphics"></a>Drukowanie grafiki  
  
1.  Dodaj <xref:System.Drawing.Printing.PrintDocument> składnika do formularza.  
  
2.  W <xref:System.Drawing.Printing.PrintDocument.PrintPage> program obsługi zdarzeń, użyj <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy nakazać drukarki na jakiego rodzaju grafiki do drukowania.  
  
     Poniższy przykład kodu pokazuje pozwala utworzyć niebieski elipsy w prostokąt ograniczający program obsługi zdarzeń. Prostokąt ma następujące wymiary i lokalizacji: począwszy od 100, 150 250 szerokości i wysokości 250.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [Obsługa drukowania w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
