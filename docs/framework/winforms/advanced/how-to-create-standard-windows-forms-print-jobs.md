---
title: "Porady: tworzenie standardowych zadań drukowania formularzy systemu Windows"
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
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2b0ce30f76fe7f8cbdc156c4a8ff5abffafae10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Porady: tworzenie standardowych zadań drukowania formularzy systemu Windows
Podstawę drukowanie w formularzach systemu Windows jest <xref:System.Drawing.Printing.PrintDocument> składnik — w szczególności <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń. Pisanie kodu do obsługi <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń, można określić wydruku i jak go wydrukować.  
  
### <a name="to-create-a-print-job"></a>Aby utworzyć zadanie drukowania  
  
1.  Dodaj <xref:System.Drawing.Printing.PrintDocument> składnika do formularza.  
  
2.  Napisać kod obsługujący <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń.  
  
     Konieczne będzie kodu logiki drukowania. Ponadto należy określić materiały do drukowania.  
  
     W poniższym przykładzie kodu, przykładowe grafiki w kształcie czerwonym prostokątem jest tworzony w <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzeń do działania jako materiały do drukowania.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
     Można również napisać kod dla <xref:System.Drawing.Printing.PrintDocument.BeginPrint> i <xref:System.Drawing.Printing.PrintDocument.EndPrint> zdarzeń może obejmować całkowitą reprezentującą łączną liczbą stron do drukowania, który jest zmniejszana, jak drukuje każdej strony.  
  
    > [!NOTE]
    >  Możesz dodać <xref:System.Windows.Forms.PrintDialog> składnika do formularza zapewnia interfejs czyste i wydajne użytkownika (UI) dla użytkowników. Ustawienie <xref:System.Windows.Forms.PrintDialog.Document%2A> właściwość <xref:System.Windows.Forms.PrintDialog> umożliwia składnika można ustawić właściwości powiązanych z print dokumentu pracuje w formularzu. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.PrintDialog> składników, zobacz [składnika PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).  
  
     Aby uzyskać więcej informacji o specyfice formularzy systemu Windows zadania drukowania, łącznie ze sposobem tworzenia zadania drukowania programowo, zobacz <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Obsługa drukowania w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
