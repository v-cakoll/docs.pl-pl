---
title: PrintDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0b0e516364277133efc83e7324345ccea8328690
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="1a3e1-102">PrintDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="1a3e1-102">PrintDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="1a3e1-103">Formularze systemu Windows [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) składnik jest wstępnie skonfigurowana okno dialogowe umożliwia wybranie drukarki, wybierz stron i określić inne ustawienia związane z drukowaniem w aplikacjach opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="1a3e1-103">The Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="1a3e1-104">Używać go jako prostym rozwiązaniem dla drukarki i Wybieranie ustawienia związane z drukowaniem zamiast własne okno dialogowe Konfigurowanie.</span><span class="sxs-lookup"><span data-stu-id="1a3e1-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="1a3e1-105">Aby umożliwić użytkownikom na drukowanie wielu części dokumentów: drukowanie wszystkich, wydrukować zakres wybranej strony lub Drukowanie zaznaczonych.</span><span class="sxs-lookup"><span data-stu-id="1a3e1-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="1a3e1-106">Polegając na standardowe okno dialogowe systemu Windows, możesz utworzyć aplikacje, których podstawowych funkcji jest znane użytkowników.</span><span class="sxs-lookup"><span data-stu-id="1a3e1-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="1a3e1-107"><xref:System.Windows.Forms.PrintDialog> Składników dziedziczy <xref:System.Windows.Forms.CommonDialog> klasy.</span><span class="sxs-lookup"><span data-stu-id="1a3e1-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-component"></a><span data-ttu-id="1a3e1-108">Praca z składnika</span><span class="sxs-lookup"><span data-stu-id="1a3e1-108">Working with the Component</span></span>  
 <span data-ttu-id="1a3e1-109">Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1a3e1-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="1a3e1-110">Ten składnik ma właściwości, które odnoszą się do każdego pojedynczego zadania drukowania (<xref:System.Drawing.Printing.PrintDocument> klasy) lub w ustawieniach poszczególnych drukarek (<xref:System.Drawing.Printing.PrinterSettings> klasy).</span><span class="sxs-lookup"><span data-stu-id="1a3e1-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="1a3e1-111">Z kolei każda z tych, może być współużytkowany przez wiele drukarek.</span><span class="sxs-lookup"><span data-stu-id="1a3e1-111">Either of these, in turn, may be shared by multiple printers.</span></span>  
  
 <span data-ttu-id="1a3e1-112">Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.PrintDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1a3e1-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3e1-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a3e1-113">See Also</span></span>  
 <xref:System.Windows.Forms.PrintDialog>  
 [<span data-ttu-id="1a3e1-114">PrintDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="1a3e1-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
