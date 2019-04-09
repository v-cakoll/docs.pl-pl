---
title: 'Instrukcje: Przechwytywanie danych użytkownika ze składnika PrintDialog w czasie wykonywania'
ms.date: 03/30/2017
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
ms.openlocfilehash: c1b0a7e66a4c2050ea5b92a55a39ea46a7b762c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176725"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>Instrukcje: Przechwytywanie danych użytkownika ze składnika PrintDialog w czasie wykonywania
Chociaż można ustawić opcje związane z drukowaniem w czasie projektowania, czasami można zmieniać tych opcji w czasie wykonywania, najprawdopodobniej z powodu wyborów dokonanych przez użytkownika. Można przechwycić wprowadzanych przez użytkownika podczas drukowania dokumentów za pomocą <xref:System.Windows.Forms.PrintDialog> i <xref:System.Drawing.Printing.PrintDocument> składników.  
  
### <a name="to-change-print-options-programmatically"></a>Aby zmienić opcje wydruku programowe  
  
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
  
3.  Wyświetlanie <xref:System.Windows.Forms.PrintDialog> składnika za pomocą <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  Opcje drukowania użytkownika z poziomu okna dialogowego, które zostaną skopiowane do <xref:System.Drawing.Printing.PrinterSettings> właściwość <xref:System.Drawing.Printing.PrintDocument> składnika.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wyświetlanie podglądu wydruku w aplikacjach formularzy systemu Windows](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Obsługa drukowania w formularzach systemu Windows](windows-forms-print-support.md)
