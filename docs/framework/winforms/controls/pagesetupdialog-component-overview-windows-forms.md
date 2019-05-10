---
title: PageSetupDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 989183b6152dfccb6167d89433317cea596d83c5
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211742"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="40a72-102">PageSetupDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="40a72-102">PageSetupDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="40a72-103">Formularze Windows <xref:System.Windows.Forms.PageSetupDialog> składnik to wstępnie skonfigurowane okno dialogowe umożliwia określanie szczegółów strony do drukowania w aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="40a72-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="40a72-104">Użycie go w aplikacji opartych na Windows jako proste rozwiązanie dla użytkowników, aby ustawić preferencje strony audytów Konfigurowanie własnego okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="40a72-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="40a72-105">Umożliwia użytkownikom ustawienie dopasowania obramowanie i marża, nagłówki i stopki i orientacji pionowej lub poziomej.</span><span class="sxs-lookup"><span data-stu-id="40a72-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="40a72-106">Opierając się na standardowych okien dialogowych Windows, możesz tworzyć aplikacje, w których podstawowych funkcji jest natychmiast dobrze znanym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="40a72-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="40a72-107">Kluczowe właściwości i metody</span><span class="sxs-lookup"><span data-stu-id="40a72-107">Key Properties and Methods</span></span>

<span data-ttu-id="40a72-108">Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="40a72-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="40a72-109">Ten składnik zgłosił można ustawić właściwości, które odnoszą się do albo jednej strony (<xref:System.Drawing.Printing.PrintDocument> klasy) lub dowolny dokument (<xref:System.Drawing.Printing.PageSettings> klasy).</span><span class="sxs-lookup"><span data-stu-id="40a72-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="40a72-110">Ponadto <xref:System.Windows.Forms.PageSetupDialog> składnika może służyć do określenia ustawień określonej drukarki, które są przechowywane w <xref:System.Drawing.Printing.PrinterSettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="40a72-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>

<span data-ttu-id="40a72-111">Gdy zostanie dodany do formularza, <xref:System.Windows.Forms.PageSetupDialog> składnika, który pojawia się na pasku w dolnej części projektanta Windows Forms w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40a72-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="40a72-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40a72-112">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="40a72-113">PageSetupDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="40a72-113">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
