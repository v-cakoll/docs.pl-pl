---
title: Wyświetlanie składnika PrintDialog
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: 198ae75d407bd1837033a1cc186d84ff972fdc2f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285158"
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="734fa-102">Wyświetlanie składnika PrintDialog</span><span class="sxs-lookup"><span data-stu-id="734fa-102">How to display the PrintDialog component</span></span>

<span data-ttu-id="734fa-103"><xref:System.Windows.Forms.PrintDialog> Składnik to standardowe okno dialogowe drukowania Windows wielu użytkowników należy zapoznać się z.</span><span class="sxs-lookup"><span data-stu-id="734fa-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="734fa-104">Ponieważ użytkownicy będą natychmiast doświadczenia z nią, korzystne byłoby do użycia <xref:System.Windows.Forms.PrintDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="734fa-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>

## <a name="to-display-the-printdialog-component"></a><span data-ttu-id="734fa-105">Aby Wyświetlanie składnika PrintDialog</span><span class="sxs-lookup"><span data-stu-id="734fa-105">To display the PrintDialog component</span></span>

- <span data-ttu-id="734fa-106">Wywołaj <xref:System.Windows.Forms.Form.ShowDialog%2A> metody z kodem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="734fa-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>

     <span data-ttu-id="734fa-107">Gdy składnik zostanie wyświetlone, użytkownicy będą korzystać z niego, ustawienie właściwości zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="734fa-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="734fa-108">Są one zapisywane w <xref:System.Drawing.Printing.PrinterSettings> klasy (i <xref:System.Drawing.Printing.PageSettings> klasy, jeśli użytkownik uzyskuje dostęp do [PageSetupDialog, składnik](pagesetupdialog-component-windows-forms.md) za pośrednictwem <xref:System.Windows.Forms.PrintDialog> składnika) skojarzonego z tym zadaniem drukowania.</span><span class="sxs-lookup"><span data-stu-id="734fa-108">These are saved in the  <xref:System.Drawing.Printing.PrinterSettings> class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="734fa-109">Następnie można prowadzić rozmowy właściwości zestawu określić szczegóły zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="734fa-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>

## <a name="see-also"></a><span data-ttu-id="734fa-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="734fa-110">See also</span></span>

- [<span data-ttu-id="734fa-111">Instrukcje: Tworzenie zadań drukowania formularzy Windows Standard</span><span class="sxs-lookup"><span data-stu-id="734fa-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="734fa-112">Instrukcje: Przechwytywanie danych wejściowych użytkownika ze składnika PrintDialog w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="734fa-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [<span data-ttu-id="734fa-113">PrintPreviewDialog, kontrolka</span><span class="sxs-lookup"><span data-stu-id="734fa-113">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="734fa-114">PrintDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="734fa-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
- [<span data-ttu-id="734fa-115">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="734fa-115">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="734fa-116">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="734fa-116">Windows Forms Controls</span></span>](index.md)