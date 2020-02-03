---
title: PrintDialog — Informacje o składniku
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728667"
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="576d5-102">PrintDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="576d5-102">PrintDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="576d5-103">Windows Forms składnik [PrintDialog](printdialog-component-windows-forms.md) jest wstępnie skonfigurowanym oknem dialogowym używanym do wybierania drukarki, wybierania stron do drukowania i określania innych ustawień związanych z drukowaniem w aplikacjach opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="576d5-103">The Windows Forms [PrintDialog](printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="576d5-104">Użyj go jako prostego rozwiązania do wybierania ustawień drukarki i drukowania zamiast konfigurowania własnego okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="576d5-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="576d5-105">Można umożliwić użytkownikom drukowanie wielu części dokumentów: Drukuj wszystko, Drukuj wybrany zakres stron lub wydrukuj zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="576d5-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="576d5-106">Polegając na standardowych oknach dialogowych systemu Windows, można tworzyć aplikacje, których podstawowe funkcje są bezpośrednio znane użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="576d5-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="576d5-107">Składnik <xref:System.Windows.Forms.PrintDialog> dziedziczy z klasy <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="576d5-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-component"></a><span data-ttu-id="576d5-108">Praca ze składnikiem</span><span class="sxs-lookup"><span data-stu-id="576d5-108">Working with the Component</span></span>

<span data-ttu-id="576d5-109">Użyj metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>, aby wyświetlić okno dialogowe w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="576d5-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="576d5-110">Ten składnik ma właściwości, które odnoszą się do jednego zadania drukowania (klasy<xref:System.Drawing.Printing.PrintDocument>) lub ustawień pojedynczej drukarki (klasy<xref:System.Drawing.Printing.PrinterSettings>).</span><span class="sxs-lookup"><span data-stu-id="576d5-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="576d5-111">Z kolei mogą być współużytkowane przez wiele drukarek.</span><span class="sxs-lookup"><span data-stu-id="576d5-111">Either of these, in turn, may be shared by multiple printers.</span></span>

<span data-ttu-id="576d5-112">Po dodaniu do formularza składnik <xref:System.Windows.Forms.PrintDialog> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="576d5-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="576d5-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="576d5-113">See also</span></span>

- <xref:System.Windows.Forms.PrintDialog>
- [<span data-ttu-id="576d5-114">PrintDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="576d5-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
