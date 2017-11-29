---
title: "Porady: przechwytywanie danych użytkownika ze składnika PrintDialog w czasie wykonywania"
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
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c942cb5f005177b74dd25a9725b4990553adbb8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>Porady: przechwytywanie danych użytkownika ze składnika PrintDialog w czasie wykonywania
Podczas gdy można ustawić opcje związane z drukowaniem w czasie projektowania, czasami można zmienić tych opcji w czasie wykonywania, najprawdopodobniej z powodu wyborów dokonanych przez użytkownika. Można przechwytywać dane wejściowe użytkownika podczas drukowania dokumentów za pomocą <xref:System.Windows.Forms.PrintDialog> i <xref:System.Drawing.Printing.PrintDocument> składników.  
  
### <a name="to-change-print-options-programmatically"></a>Aby programowo zmienić opcje wydruku  
  
1.  Dodaj <xref:System.Windows.Forms.PrintDialog> i <xref:System.Drawing.Printing.PrintDocument> składnika do formularza.  
  
2.  Ustaw <xref:System.Windows.Forms.PrintDialog.Document%2A> właściwość <xref:System.Windows.Forms.PrintDialog> do <xref:System.Drawing.Printing.PrintDocument> dodany do formularza.  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  Wyświetl <xref:System.Windows.Forms.PrintDialog> składnika za pomocą <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  Opcje drukowania użytkownika w oknie dialogowym zostaną skopiowane do <xref:System.Drawing.Printing.PrinterSettings> właściwość <xref:System.Drawing.Printing.PrintDocument> składnika.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: drukowanie pliku tekstowego wiele stron w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [Obsługa drukowania w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
