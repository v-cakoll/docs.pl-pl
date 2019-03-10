---
title: 'Instrukcje: Przechwytywanie danych wejściowych użytkownika ze składnika PrintDialog w czasie wykonywania'
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
ms.openlocfilehash: 69a3632ddb4d68f5a916f5ffca020630abe1bd68
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707338"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a><span data-ttu-id="3e928-102">Instrukcje: Przechwytywanie danych wejściowych użytkownika ze składnika PrintDialog w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="3e928-102">How to: Capture User Input from a PrintDialog at Run Time</span></span>
<span data-ttu-id="3e928-103">Chociaż można ustawić opcje związane z drukowaniem w czasie projektowania, czasami można zmieniać tych opcji w czasie wykonywania, najprawdopodobniej z powodu wyborów dokonanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3e928-103">While you can set options related to printing at design time, you will sometimes want to change these options at run time, most likely because of choices made by the user.</span></span> <span data-ttu-id="3e928-104">Można przechwycić wprowadzanych przez użytkownika podczas drukowania dokumentów za pomocą <xref:System.Windows.Forms.PrintDialog> i <xref:System.Drawing.Printing.PrintDocument> składników.</span><span class="sxs-lookup"><span data-stu-id="3e928-104">You can capture user input for printing a document using the <xref:System.Windows.Forms.PrintDialog> and the <xref:System.Drawing.Printing.PrintDocument> components.</span></span>  
  
### <a name="to-change-print-options-programmatically"></a><span data-ttu-id="3e928-105">Aby zmienić opcje wydruku programowe</span><span class="sxs-lookup"><span data-stu-id="3e928-105">To change print options programmatically</span></span>  
  
1.  <span data-ttu-id="3e928-106">Dodaj <xref:System.Windows.Forms.PrintDialog> i <xref:System.Drawing.Printing.PrintDocument> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="3e928-106">Add a <xref:System.Windows.Forms.PrintDialog> and a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="3e928-107">Ustaw <xref:System.Windows.Forms.PrintDialog.Document%2A> właściwość <xref:System.Windows.Forms.PrintDialog> do <xref:System.Drawing.Printing.PrintDocument> dodany do formularza.</span><span class="sxs-lookup"><span data-stu-id="3e928-107">Set the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> to the <xref:System.Drawing.Printing.PrintDocument> added to the form.</span></span>  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  <span data-ttu-id="3e928-108">Wyświetlanie <xref:System.Windows.Forms.PrintDialog> składnika za pomocą <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3e928-108">Display the <xref:System.Windows.Forms.PrintDialog> component by using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  <span data-ttu-id="3e928-109">Opcje drukowania użytkownika z poziomu okna dialogowego, które zostaną skopiowane do <xref:System.Drawing.Printing.PrinterSettings> właściwość <xref:System.Drawing.Printing.PrintDocument> składnika.</span><span class="sxs-lookup"><span data-stu-id="3e928-109">The user's printing choices from the dialog will be copied to the <xref:System.Drawing.Printing.PrinterSettings> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e928-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e928-110">See also</span></span>
- [<span data-ttu-id="3e928-111">Instrukcje: Podglądu wydruku w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e928-111">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="3e928-112">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e928-112">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
