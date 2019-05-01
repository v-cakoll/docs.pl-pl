---
title: PrintDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 982c52dbe9243e69bbb0452513e78798f4d1fd0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903412"
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="7c345-102">PrintDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="7c345-102">PrintDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="7c345-103">Formularze Windows [PrintDialog](printdialog-component-windows-forms.md) składnik to wstępnie skonfigurowane okno dialogowe umożliwia wybranie drukarki, wybierz stron do wydrukowania i określ inne ustawienia związane z drukowaniem w aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7c345-103">The Windows Forms [PrintDialog](printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="7c345-104">Używać go jako proste rozwiązanie dla drukarki i Wybieranie ustawienia związane z drukowaniem audytów Konfigurowanie własnego okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="7c345-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="7c345-105">Możesz umożliwić użytkownikom wydrukować wiele części dokumentów: wydrukowanie wszystkich zakres wybranej strony wydruku i Drukuj zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="7c345-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="7c345-106">Opierając się na standardowych okien dialogowych Windows, możesz tworzyć aplikacje, w których podstawowych funkcji jest natychmiast dobrze znanym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="7c345-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="7c345-107"><xref:System.Windows.Forms.PrintDialog> Składników dziedziczy <xref:System.Windows.Forms.CommonDialog> klasy.</span><span class="sxs-lookup"><span data-stu-id="7c345-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-component"></a><span data-ttu-id="7c345-108">Praca ze składnikiem</span><span class="sxs-lookup"><span data-stu-id="7c345-108">Working with the Component</span></span>  
 <span data-ttu-id="7c345-109">Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7c345-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="7c345-110">Ten składnik ma właściwości, które odnoszą się do każdego pojedynczego zadania drukowania (<xref:System.Drawing.Printing.PrintDocument> klasy) lub ustawienia poszczególnych drukarek (<xref:System.Drawing.Printing.PrinterSettings> klasy).</span><span class="sxs-lookup"><span data-stu-id="7c345-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="7c345-111">Z kolei jedną z tych wersji, może być współużytkowany przez wiele drukarek.</span><span class="sxs-lookup"><span data-stu-id="7c345-111">Either of these, in turn, may be shared by multiple printers.</span></span>  
  
 <span data-ttu-id="7c345-112">Gdy zostanie dodany do formularza, <xref:System.Windows.Forms.PrintDialog> składnika, który pojawia się na pasku w dolnej części projektanta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7c345-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c345-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c345-113">See also</span></span>

- <xref:System.Windows.Forms.PrintDialog>
- [<span data-ttu-id="7c345-114">PrintDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="7c345-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
