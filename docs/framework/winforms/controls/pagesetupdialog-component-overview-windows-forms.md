---
title: PageSetupDialog — Informacje o składniku
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: a891cb8cc77007d7591d41461c94f61c077eb300
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744341"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="d0e43-102">PageSetupDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="d0e43-102">PageSetupDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="d0e43-103">Składnik <xref:System.Windows.Forms.PageSetupDialog> Windows Forms jest wstępnie skonfigurowanym oknem dialogowym używanym do ustawiania szczegółów strony do drukowania w aplikacjach opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="d0e43-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="d0e43-104">Użyj go w aplikacji opartej na systemie Windows jako proste rozwiązanie dla użytkowników, aby ustawić preferencje strony zamiast konfigurowania własnego okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="d0e43-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="d0e43-105">Można umożliwić użytkownikom ustawianie korekt obramowania, nagłówków i stopek oraz orientacji pionowej lub poziomej.</span><span class="sxs-lookup"><span data-stu-id="d0e43-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="d0e43-106">Polegając na standardowych oknach dialogowych systemu Windows, można tworzyć aplikacje, których podstawowe funkcje są bezpośrednio znane użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="d0e43-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="d0e43-107">Właściwości i metody klucza</span><span class="sxs-lookup"><span data-stu-id="d0e43-107">Key Properties and Methods</span></span>

<span data-ttu-id="d0e43-108">Użyj metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>, aby wyświetlić okno dialogowe w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d0e43-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="d0e43-109">Ten składnik ma właściwości, które można ustawić, odnoszące się do jednej strony (<xref:System.Drawing.Printing.PrintDocument> Class) lub dowolnego dokumentu (klasy<xref:System.Drawing.Printing.PageSettings>).</span><span class="sxs-lookup"><span data-stu-id="d0e43-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="d0e43-110">Ponadto składnik <xref:System.Windows.Forms.PageSetupDialog> może służyć do określenia określonych ustawień drukarki, które są przechowywane w klasie <xref:System.Drawing.Printing.PrinterSettings>.</span><span class="sxs-lookup"><span data-stu-id="d0e43-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>

<span data-ttu-id="d0e43-111">Po dodaniu do formularza składnik <xref:System.Windows.Forms.PageSetupDialog> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0e43-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0e43-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0e43-112">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="d0e43-113">PageSetupDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="d0e43-113">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
