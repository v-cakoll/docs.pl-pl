---
title: "PageSetupDialog — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 082dbff66c8a0f06635936011f802c99b88e41df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="49070-102">PageSetupDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="49070-102">PageSetupDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="49070-103">Formularze systemu Windows <xref:System.Windows.Forms.PageSetupDialog> składnik jest wstępnie skonfigurowana okno dialogowe służy do określania szczegóły strony do wydruku w aplikacjach opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="49070-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="49070-104">Użyj go w aplikacji systemu Windows jako prostym rozwiązaniem dla użytkowników, aby ustawić preferencje strony zamiast własne okno dialogowe Konfigurowanie.</span><span class="sxs-lookup"><span data-stu-id="49070-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="49070-105">Można umożliwić użytkownikom ustawić obramowania i margines, nagłówki i stopki i orientacji pionowej lub poziomej.</span><span class="sxs-lookup"><span data-stu-id="49070-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="49070-106">Polegając na standardowe okno dialogowe systemu Windows, możesz utworzyć aplikacje, których podstawowych funkcji jest znane użytkowników.</span><span class="sxs-lookup"><span data-stu-id="49070-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="49070-107">Właściwości klucza i metody</span><span class="sxs-lookup"><span data-stu-id="49070-107">Key Properties and Methods</span></span>  
 <span data-ttu-id="49070-108">Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę w celu wyświetlenia okna dialogowego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="49070-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="49070-109">Ten składnik zgłosił właściwości można ustawić, które dotyczą albo jednej strony (<xref:System.Drawing.Printing.PrintDocument> klasy) lub dokument (<xref:System.Drawing.Printing.PageSettings> klasy).</span><span class="sxs-lookup"><span data-stu-id="49070-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="49070-110">Ponadto <xref:System.Windows.Forms.PageSetupDialog> składnika może służyć do określenia ustawienia drukarki, które są przechowywane w <xref:System.Drawing.Printing.PrinterSettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="49070-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>  
  
 <span data-ttu-id="49070-111">Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.PageSetupDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="49070-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49070-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49070-112">See Also</span></span>  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [<span data-ttu-id="49070-113">PageSetupDialog — składnik</span><span class="sxs-lookup"><span data-stu-id="49070-113">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
